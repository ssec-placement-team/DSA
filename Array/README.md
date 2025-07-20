
# 📊 Arrays (C Language)

This section of the placement preparation repository is dedicated to mastering **Arrays**, a fundamental data structure frequently tested in coding rounds and interviews.

---

## 📚 Resources for Further Practice

- [GeeksforGeeks - Arrays in C](https://www.geeksforgeeks.org/arrays-in-c-cpp/)
- [InterviewBit Practice: Arrays](https://www.interviewbit.com/practice/arrays/)
- [Programiz: Arrays in C](https://www.programiz.com/c-programming/c-arrays)

---

## 📘 Topics Covered

1. What is an Array?
2. Declaration and Traversal
3. Time Complexities of Operations
4. Real-life and Technical Use Cases
5. Solved Interview-Oriented Questions
6. Frequently Asked Questions (for Practice)

---

## 🧠 Core Concepts Explained

### What is an Array?
An array is a collection of elements of the same data type stored in contiguous memory locations, allowing efficient access and manipulation using an index.
It is the most basic linear data structure used for storing data sequentially.

### 🧠 Key Characteristics:
- Fixed-size (in static arrays).
- All elements are of the same type (int, char, float, etc.).
- Indexed from 0 to n-1.
- Stored in adjacent memory cells.
- Random access supported (you can access any element in O(1) time).

### 📄 Static Array Declaration (Compile-time Size)
```c
int arr[5]; // Declares a fixed-size array of 5 integers
arr[0] = 10;
printf("%d", arr[0]); // Output: 10
```
*Memory Representation:*
```c
Index:     0     1     2     3     4
Value:   [10]  [  ]  [  ]  [  ]  [  ]
Address: 1000  1004  1008  1012  1016  (assuming int = 4 bytes)
```

### 🧾 Dynamic Array Declaration (Run-time Size)
When the size of the array is not known at compile time, dynamic memory allocation is used with functions like malloc() or calloc() from stdlib.h.
```c
#include <stdio.h>
#include <stdlib.h>
int main() {
    int n;
    printf("Enter size of array: ");
    scanf("%d", &n);

    int *arr = (int *)malloc(n * sizeof(int)); // Allocating memory dynamically
    for (int i = 0; i < n; i++) {
        arr[i] = i + 1;
    }
    for (int i = 0; i < n; i++) {
        printf("%d ", arr[i]);
    }
    free(arr); // Always free dynamically allocated memory
    return 0;
}
```
*Memory Representation:*
```c
Index:     0     1     2     3     4
Value:   [10]  [  ]  [  ]  [  ]  [  ]
Address: 1000  1004  1008  1012  1016  (assuming int = 4 bytes)
```

### Common Operations:
| Operation       | Time Complexity |
|----------------|-----------------|
| Access         | O(1)            |
| Traversal      | O(n)            |
| Insertion      | O(n)            |
| Deletion       | O(n)            |
| Linear Search  | O(n)            |

### Use Cases:
*Use Cases of Arrays Real-life:*
- Marks of students in an exam.
- Monthly temperature records.
- Seat numbers in a cinema.

*Technical/Programming:*
- Storing list of items (e.g., cart in shopping apps).
- Lookup tables (e.g., frequency count).
- Implementing other data structures (stacks, queues, matrices).
- Storing pixel data in image processing.

---

## 🧩 Static vs Dynamic Arrays in C

Arrays in C can be allocated **statically** (at compile-time) or **dynamically** (at run-time). Understanding the differences is crucial for memory management and writing scalable code.

### 🔍 Comparison Table

| Feature             | Static Array                             | Dynamic Array                                 |
|---------------------|-------------------------------------------|-----------------------------------------------|
| Memory Allocation   | At **compile-time**                      | At **run-time** using `malloc()` or `calloc()` |
| Size                | **Fixed** after declaration              | **Flexible**, can be defined at runtime        |
| Resizing            | ❌ Not possible                          | ✅ Can be resized using `realloc()`            |
| Memory Efficiency   | May **waste memory** if oversized        | **More efficient** if allocated carefully      |
| Memory Location     | **Stack**                                | **Heap**                                       |
| Memory Management   | Automatically handled                    | Requires `free()` to release memory            |

---

## ✅ Solutions to Important Array Questions (with Code in C)

---

### 🔁 1. Reverse an Array or String

**📝 Problem:**  
Reverse all elements so the last becomes the first and vice versa.

**📌 Example:**  
Input: `[1, 2, 3, 4, 5]`  
Output: `[5, 4, 3, 2, 1]`

**🧠 Algorithm:**

1. Use two pointers: `start` and `end`.
2. Swap `arr[start]` with `arr[end]`.
3. Move `start++` and `end--` until `start < end`.

**💻 Code in C:**

```c
void reverse(int arr[], int n) {
    int start = 0, end = n - 1;
    while (start < end) {
        int temp = arr[start];
        arr[start] = arr[end];
        arr[end] = temp;
        start++;
        end--;
    }
}
```

### 🔍 2. Find Maximum or Minimum Element
**📝 Problem:**
Find the largest and smallest elements in the array.

**📌 Example:**
Input: [10, 4, 2, 20, 5]
Output: Max = 20, Min = 2

**🧠 Algorithm:**

Initialize max and min as the first element.
Loop from index 1 to n-1.
Update max if a larger value is found.
Update min if a smaller value is found.

**💻 Code in C:**
```c 
void findMaxMin(int arr[], int n, int *max, int *min) {
    *max = arr[0];
    *min = arr[0];
    for (int i = 1; i < n; i++) {
        if (arr[i] > *max)
            *max = arr[i];
        if (arr[i] < *min)
            *min = arr[i];
    }
}
```

### 🥉 3. Find 3rd Largest Unique Element
**📝 Problem:**
Find the third largest unique number from the array.

**📌 Example:**
Input: [10, 20, 5, 8, 15]
Output: 10

**🧠 Algorithm:**

1. Initialize first, second, third as INT_MIN.
2. Traverse the array:
    - If current > first → update all three
    - If current > second (not equal to first) → update second and third
    - If current > third (not equal to first & second) → update third

**💻 Code in C:**
```c 
#include <limits.h>
int thirdLargest(int arr[], int n) {
    int first = INT_MIN, second = INT_MIN, third = INT_MIN;
    for (int i = 0; i < n; i++) {
        if (arr[i] > first) {
            third = second;
            second = first;
            first = arr[i];
        } else if (arr[i] > second && arr[i] != first) {
            third = second;
            second = arr[i];
        } else if (arr[i] > third && arr[i] != second && arr[i] != first) {
            third = arr[i];
        }
    }
    return third;
}
```

### 🔄 4. Remove Duplicates from Array
**📝 Problem:**
Remove all duplicate values and retain only unique elements.

**📌 Example:**
Input: [1, 2, 2, 3, 4, 4]
Output: [1, 2, 3, 4]

**🧠 Algorithm:**

1. Create a temporary array to store unique elements.
2. For every element in the original array:
3. Check if it already exists in the temp array.\
4. If not, copy it to temp.
5. Copy the contents of temp back to original.

**💻 Code in C:**
```c 
int removeDuplicates(int arr[], int n) {
    if (n == 0 || n == 1)
        return n;
    int temp[n];
    int j = 0;
    for (int i = 0; i < n; i++) {
        int isDuplicate = 0;
        for (int k = 0; k < j; k++) {
            if (arr[i] == temp[k]) {
                isDuplicate = 1;
                break;
            }
        }
        if (!isDuplicate)
            temp[j++] = arr[i];
    }
    for (int i = 0; i < j; i++)
        arr[i] = temp[i];
    return j; // returns new size
}

```

## 🎯 Frequently Asked Interview Questions on Arrays

You are encouraged to solve these on your own after reviewing the concepts.
## 🎯 Array Interview Problems - Quick Summary

This section lists frequently asked array problems with brief descriptions and examples to help you understand and recognize them during coding interviews.

---

### 1. ✅ Check if Array is Sorted
**Problem:** Determine if the array is sorted in ascending order.  
**Example:** `[1, 2, 3, 4] → Yes`, `[1, 3, 2] → No`

---

### 2. 🥈 Find Second Largest Element
**Problem:** Identify the second largest **unique** element.  
**Example:** `[10, 20, 15] → 15`

---

### 3. 🔢 Find K-th Smallest/Largest
**Problem:** Return the k-th smallest/largest element.  
**Example:** 2nd smallest in `[3, 1, 5, 2] → 2`

---

### 4. 🔄 Rotate Array by K Positions
**Problem:** Shift array elements to the right/left by `k` steps.  
**Example:** `[1, 2, 3, 4, 5]` rotated by 2 → `[4, 5, 1, 2, 3]`

---

### 5. 🧼 Move All Zeros to the End
**Problem:** Move all 0s to the end while keeping the order of non-zero elements.  
**Example:** `[1, 0, 2, 0, 3] → [1, 2, 3, 0, 0]`

---

### 6. 🔗 Merge Two Sorted Arrays
**Problem:** Merge two sorted arrays into a single sorted array.  
**Example:** `[1, 3, 5] + [2, 4, 6] → [1, 2, 3, 4, 5, 6]`

---

### 7. ❓ Find Missing Number (1 to n)
**Problem:** Find the missing number from 1 to n.  
**Example:** `[1, 2, 4, 5] → Missing: 3`

---

### 8. 🔂 Find Element Appearing Once
**Problem:** Find the element that occurs once, others occur twice.  
**Example:** `[1, 2, 3, 2, 1] → 3`

---

### 9. ➕ Find All Pairs with Given Sum
**Problem:** Find all pairs whose sum is equal to a given value.  
**Example:** Sum = 5 in `[1, 2, 3, 4] → (1,4), (2,3)`

---

### 10. 📊 Majority Element
**Problem:** Find the element that appears more than n/2 times.  
**Example:** `[2, 2, 1, 2] → 2`

---

### 11. 📈 Subarray with Maximum Sum (Kadane’s Algorithm)
**Problem:** Find the contiguous subarray with the largest sum.  
**Example:** `[1, -2, 3, 4] → Max sum = 7 from [3, 4]`

---

### 12. 🔢 Count Even and Odd Numbers
**Problem:** Count how many numbers are even vs odd.  
**Example:** `[1, 2, 3, 4] → Even: 2, Odd: 2`

---

### 13. 🔁 Check if Array is a Palindrome
**Problem:** Check if the array reads the same forward and backward.  
**Example:** `[1, 2, 3, 2, 1] → Yes`

---

### 14. 🔃 Minimum Swaps to Sort
**Problem:** Find the minimum number of swaps needed to sort the array.  
**Example:** `[2, 3, 1] → 2 swaps`

---

### 15. 🔍 Find Duplicate in Range 1 to n
**Problem:** Find duplicate elements where values are in the range 1 to n.  
**Example:** `[1, 3, 4, 2, 2] → 2`

---

### 16. 📉 Longest Increasing Subsequence (LIS)
**Problem:** Find the length of the longest strictly increasing subsequence.  
**Example:** `[10, 9, 2, 5, 3, 7, 101] → LIS: [2, 3, 7, 101] → Length: 4`

---

### 17. 👑 Replace Each Element with Next Greatest
**Problem:** Replace each element with the greatest element to its right.  
**Example:** `[16, 17, 4, 3, 5, 2] → [17, 5, 5, 5, 2, -1]`

---

### 18. ⚖️ Find Equilibrium Index
**Problem:** Find index where sum of elements on left = right.  
**Example:** `[1, 3, 5, 2, 2] → Index: 2`

---

📌 These problems are commonly asked in coding interviews. Mastering them will build strong problem-solving skills for placement rounds.

> You can find this list at the end of:  
> 📄 `Array Questions Explained.pdf`

---

## 📂 Included Files

- `Array Questions Explained.pdf` → Detailed theory + solved questions
- `Remove_Duplicates_Explained.pdf` → Visual diagram to teach removal logic
- `README.md` → You're reading it!


---

## 💡 Recommended Flow

1. Understand concepts using this README or PDF
2. Try solving the 4 given problems in C
3. Attempt the 20+ practice problems on your own
4. Create your own variations for each problem
5. Practice writing code on paper & IDE
