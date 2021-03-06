# Complete Data Handler

## Introduction

Complete data handler is a Python class that emulates dictionaries with list indexing, arithmetic operators, set theory operators.

## Release Notes:

- 1.0.0 Initial Release
- 2.0.0 Lightweight Release
  - Completely rewritten optimized code.
  - Increased performance over long iterations.
  - Removed auto string-number conversion on operators.
  - Operators no longer support strings operations.
  - Removed get and set methods, aliasing is avoided using a new object instance.
  - Added append, join, merge, common methods on returning a cdh.
  - Added update, append, pop methods on modifying existing cdh.
- 2.0.1 
	- Fixed initialization indexing on multiple dicts or cdhs arguments
- 2.0.3
    - Optimized code
	- Fixed pop method on duplicate keys
- 2.0.5
	- Fixed duplicate keys overwrite on arithmetic operators
	- Added ids, keys, values getter methods.
	
## Requirements

- Python >=3.9

## Install

source install:
- copy cdh_main.py in your root folder and add _from cdh_main.py import *_ in .py source file.

pip install:
- from dist folder: pip install cdh_main-1.0-py3-none-any.whl add _from cdh_main import *_ in .py source file.

## Methods

**\_\_init\_\_**

Cdh objects can be created using one or more arguments. In the case of numbers, strings and lists each element given as argument gets added to the object istance using as key the ID converted to string. Example:

a = cdh(1, 2) → a = {(0) 0 : 1, (1) 1 : 2}

b = cdh('a', 'b') → b = {(0) 0 : a, (1) 1 : b}

c = cdh([1,'a'], [2,['b','c']]) → c = {(0) 0 : [1,’a’], (1) 1 : [2, [‘b’,’c’]]}


While any dictionary or cdh given as argument will produce an object in which each element is an element of the firsts. 

Example:

d = cdh({'zero' : 0, 1 : 'one'}, {'three' : 3}) → d = {(0) zero: 0, (1) 1: one, (2) three: 3}

e = cdh(d, {'a': 'b'}) → d = {(0) zero: 0, (1) 1: one, (2) three: 3, (3) a: b}

**\_\_getitem\_\_	\_\_setitem\_\_**

Both used as square braket operator [ ] can be used in the most intuitive way, by calling it with an integer ID argument to read or modify the corresponding dictionary or using a string Key argument to read or modify the corresponding Value.

Example:

a = cdh(1,2)

print(a[0]) → {0 : 1}

print(a[‘0’]) → 1

a[0] = {0:0}

a['1'] = 1

print(a) → {(0) 0: 0, (1) 1: 1}

a[0:1] = {1:1,2:2}

print(a) → {(0) 1: 1, (1) 2: 2}

Note that slice indexing is transposed on mathematical notation where the slice starts and ends at the square brakets instructions’.

**\_\_add\_\_	\_\_sub\_\_	\_\_mult\_\_	\_\_truediv\_\_**

These opeators return a cdh in which each element is the arithmetic operation of the two corresponding operands elements. For this reason both operands must be cdhs of same length.

**ids	keys	values**

Returns a list of cdh's ids, keys or values respectively.

**update**

Used to add an element to a cdh, same keys’ values are replaced with the argument value.

**append**

Used to add an element to a cdh, same keys’ are duplicated.

**pop**

Removes an element from a cdh. The element to be removed is defined using a key or an ID.

**join**

Returns a cdh buildt using the two arguments. Same keys are duplicated.

**merge**

Returns a cdh buildt using the two arguments. Same keys’ values are chosen from the argument’s ones.

**common**

Returns a cdh buildt using common keys using ‘key’ as second argument, or common values using ‘val’ as second argument.

## Contacts

Please report any bugs at robiamado@gmail.com
