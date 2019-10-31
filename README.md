# 🛠 fix-a-bug

## Setup

Clone this repo.

```bash
git clone https://github.com/datamade/fix-a-bug.git && cd fix-a-bug
```

Install the requirements. (Feel free to use a virtual environment!)

```bash
pip install -r requirements.txt
```

Run the tests.

```bash
pytest -sv
```

## Challenge

The code in `fix_me.py` contains four errors that are preventing the test from
passing. Debug and correct each error. As you identify the errors, fill out
a description of the problem and an explanation of the root cause and your fix
in the section below.

### Error 1

**Description:**
The `self.DATA` object attempted to use `7` as the index number to retrieve a value from a list that has less than eight items.

**Explanation:**
The `get_previous` method retrieves a value from a `list`, which uses a numeric index. The `for` loop switched the iterating variables' order (`value, key` instead of `key, value`) and provided a value of `7` as the index, but the list only has three items with a highest index of `2`.

### Error 2

**Description:**
A variable of type `int` is used in a place where an `iterable` is expected.

**Explanation:**
The [sum() function](https://docs.python.org/3/library/functions.html#sum) expects an `iterable` as an argument. It adds the items in the `iterable` object. For our purposes, it's simpler to use the addition operator for a pair of integers.

### Error 3

**Description:**
The test indicates the expected values (`[4, 9, 11]`) are different than the values of the function's output (`[16, 15, 17]`).

**Explanation:**
The class `Transformer` is inheriting from two classes, `ParentA` and `ParentB`. The [inheritance logic](https://docs.python.org/3/tutorial/classes.html#multiple-inheritance) goes from left to right, but each attribute stops with the first occurrence. Since both parent classes have the same attribute named `DATA`, the left most parent's data is inherited. It would be equally valid to remove `ParentA` from the list of parent classes instead of switching the order of them.

### Error 4

**Description:**
The test indicates the expected values (`[4, 9, 11]`) are different than the values of the function's output (`[10, 9, 11]`)

**Explanation:**
The `get_previous` method returned the value from `self.DATA` at index `-1`. This is a way to count from the right using a one-based index, which means the rightmost item with a value of `6` was returned. The `get_previous` method was missing a conditional to catch an edge case specified in the comments.
