# 第一周

## 题目1

Given a sorted array nums, remove the duplicates in-place such that each element appear only once and return the new length.

Do not allocate extra space for another array, you must do this by modifying the input array in-place with O(1) extra memory.

Example 1:

```
Given nums = [1,1,2],

Your function should return length = 2, with the first two elements of nums being 1 and 2 respectively.

It doesn't matter what you leave beyond the returned length.
```

## 解答

### 思路一 
首先记录第一次出现重复的位置index，该位置数字将会被下一个不同的数字替换，完成替换后index+1；同时，记录用来与下一个数字比较的当前数字now，且当前数字now位置为index-1。

```Python
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        if len(nums) <= 0:
            return 0
        now = nums[0]
        flag = 1
        for i in range(0, len(nums)):
            if nums[i] == now and flag:
                index = i + 1
                flag = 0
                continue
            if nums[i] != now:
                now = nums[i]
                nums[index] = nums[i]
                index = index + 1
        return index
```

### 思路一简洁版
使用一个指针j，当i向后遍历数组时，如果遇到与`num[j]`不同的，将`num[i]`和`num[j+1]`交换，同时j=j+1，即j向后移动一个位置，然后i继续向后遍历.

```Python
class Solution:
    def removeDuplicates(self, nums: List[int]) -> int:
        if len(nums) == 0:
            return 0
        j = 0
        for i in range(0, len(nums)):
            if nums[i] != nums[j]:
                nums[j+1] = nums[i]
                j = j + 1
        return j+1
 ```
 
