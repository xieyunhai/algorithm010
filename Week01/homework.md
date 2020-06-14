# 删除排序数组中的重复项
    1. 暴力: 两层loop, O(n^3), O(1)
    2. 双指针: i = 0; j = 1, O(n), O(1)
```
var removeDuplicates = function(nums) {
    if (nums.length == 0) return 0;
    for (var i = 0, j = 1; j < nums.length; j++) {
        if (nums[i] != nums[j]) {
            i++;
            nums[i] = nums[j];
        }
    }
    return i + 1;
};
```

# 旋转数组
    1. 暴力: 循环 K 次, 每次旋转 1 个数字, O(k * n), O(1)
    2. 循环交换: start++, count < nums.length; 通过 +k 循环, O(n), O(1)
```
var rotate = function(nums, k) {
    k = k % nums.length;
    for (var start = 0, count = 0; count < nums.length; start++) {
        var current = start;
        var preValue = nums[start]; // 保留前值用于下一次交换
        do {
            var next = (current + k) % nums.length;
            var temp = nums[next];
            nums[next] = preValue;
            preValue = temp;
            current = next;
            count++; // 如果 count 个数全部够了, 就终止了
        } while(current != start) // 保证每个数字只交换一次
    }
};
```

# 合并两个有序链表
    1. 双指针: 前置 prev 记录当前位置, O(i + j), O(1) 

```
var mergeTwoLists = function(l1, l2) {
    var head = new ListNode();
    var pre = head;
    while(l1 != null && l2 != null) {
        if (l1.val <= l2.val) {
            pre.next = l1;
            pre = l1; 
            l1 = l1.next;
        } else {
            pre.next = l2;
            pre = l2;
            l2 = l2.next;
        }
    }
    // 优化判断
    pre.next = l1 == null ? l2 : l1;
    return head.next;
};
```

# 合并两个有序数组
    1. 新数组: 时间复杂度 O(m+n), O(m+n)
    2. 双指针法: 从后往前排序, O(m+n), O(1) 

```
var merge = function(nums1, m, nums2, n) {
    var len1 = m - 1;
    var len2 = n - 1;
    var p = m + n - 1;
    while (len1 >= 0 && len2 >= 0) {
        nums1[p--] = nums1[len1] > nums2[len2] ? nums1[len1--] : nums2[len2--];
    }
    // 把 nums2 直到 len2 的数字填充到 nums1中
    len2 >= 0 && nums1.splice(0, len2 + 1, ...nums2.slice(0, len2 + 1));
};
```

# 两数之和
    1. 暴力: 两层 loop, O(n^2), O(1)
    2. 数组索引: target - nums[i], O(n), O(n)
    3. map 索引: ([key: value]: [value: index]), O(n), O(n)
```
var twoSum = function(nums, target) {
    var result = [];
    for (var i = 0; i < nums.length - 1; i++) {
        var current = target - nums[i];
        var index = nums.slice(i + 1).indexOf(current) + i + 1;
        if (index > -1 && index > i) {
            result = [i, index];
        }
    }
    return result;
};
```

# 移动零
    1. loop循环, 开辟新数组, 非0复制, 再补全, O(n), O(n)
    2. loop循环, i, j 头尾指针, i 往后, 为0, 则与j位置互换, O(n), O(1)
    3. loop循环, i 为 0, 则先删除再补充在末尾, O(n^k), O(1)
```
var moveZeroes = function(nums) {
    let i, j = 0, temp;
    for (i = 0; i < nums.length; i++) {
        if (nums[i] !== 0) {
            temp = nums[j];
            nums[j] = nums[i];
            nums[i] = temp;
            j++;
        }   
    }
};
```

# 加一
    1. 反向遍历: O(n), O(1)
```
var plusOne = function(digits) {
    var len = digits.length;
    // 从后往前, 进位则 +1
    for (var i = len - 1; i >= 0; i--) {
        digits[i]++;
        digits[i] = digits[i] % 10;
        if (digits[i] != 0) {
            return digits;
        }
    }
    // 处理类似[9,9]情况的数据
    var result = [...Array(len + 1)].map(_ => 0);
    result[0] = 1;
    return result;
};
```

# 设计循环双端队列

```
var MyCircularDeque = function(k) {
    
};

MyCircularDeque.prototype.insertFront = function(value) {

};

MyCircularDeque.prototype.insertLast = function(value) {

};

MyCircularDeque.prototype.deleteFront = function() {

};

MyCircularDeque.prototype.deleteLast = function() {

};

MyCircularDeque.prototype.getFront = function() {

};

MyCircularDeque.prototype.getRear = function() {

};

MyCircularDeque.prototype.isEmpty = function() {

};

MyCircularDeque.prototype.isFull = function() {

};
```

# 接雨水
```
var trap = function(height) {
    
};  
```