---
jupytext:
  formats: ipynb,md:myst
  text_representation:
    extension: .md
    format_name: myst
    format_version: 0.13
    jupytext_version: 1.16.1
kernelspec:
  display_name: Python 3 (ipykernel)
  language: python
  name: python3
---

# Introduction to NumPy

## What is NumPy

NumPy (Numerical Python) is an open-source Python library that supports large, multi-dimensional arrays and matrices, along with a collection of mathematical functions to operate on these arrays.

**Definition:**
NumPy is a key package for scientific computing in Python, providing efficient array operations and numerous mathematical functions.

Purpose:

1. Efficient Computation: NumPy arrays are faster and more memory-efficient than Python lists.
2. Mathematical Functions: It offers a variety of functions for statistical analysis, algebra, and more.
3. Data Handling: Simplifies the manipulation and computation of large datasets.
4. Integration: Works seamlessly with other scientific libraries like Pandas, SciPy, and Matplotlib.

````{admonition} Importance in Data Science and Machine Learning
:class: dropdown
Data Science:
1. Data Manipulation: Makes reshaping, slicing, and indexing large datasets easier.
2. Performance: Optimized for speed, crucial for big data operations.
3. Statistical Analysis: Facilitates quick and accurate statistical computations.

Machine Learning:
1. Foundation for Libraries: Underpins many ML libraries like TensorFlow and scikit-learn.
2. Matrix Operations: Efficiently handles matrix multiplication and other linear algebra tasks.
3. Data Preparation: Aids in data normalization and preprocessing.
4. Prototyping: Supports rapid prototyping of ML algorithms due to its simplicity and performance.
````

## Installing NumPy
To use NumPy in your Python projects, you need to install it first. Here’s how you can do it by using `pip`:

```bash
pip install numpy
```

Once NumPy is installed, you can start using it in your Python scripts by importing it.
It's a common practice to import NumPy with the alias `np`:
```python
import numpy as np
```

This alias `np` makes it easier and quicker to access NumPy functions and features throughout your code.

## Basics of NumPy Arrays

### Creating Arrays from Python Objects

Using `np.array()`: 
You can create a NumPy array using the `np.array()` function. This function can convert Python lists and tuples into NumPy arrays.

Creating an array from a list:

```{code-cell} ipython3
import numpy as np

array_from_list = np.array([1, 2, 3, 4, 5])
print(array_from_list)
```

Creating an array from a tuple:

```{code-cell} ipython3
array_from_tuple = np.array((1, 2, 3, 4, 5))
print(array_from_tuple)
```

```{admonition} NumPy arrays vs Python Lists
:class: note
NumPy arrays enforce **homogeneity**, requiring all elements to be of the same data type, which enhances efficiency. 
They also support **advanced functionalities** like broadcasting and multi-dimensional slicing. 
In contrast, Python lists are more flexible with data types but lack the performance optimization of NumPy arrays. 
Lists also do not support element-wise operations or advanced indexing and slicing natively.
```

### Creating Arrays from Scratch

NumPy provides several functions to create arrays from scratch with specific values and shapes. Here are some commonly used functions:

1. **`np.zeros`**:
   - Creates an array filled with zeros.
   - **Example:**
     ```python
     # Creates a 3x4 array of zeros
     zeros_array = np.zeros((3, 4))  
     print(zeros_array)
     ```
   
2. **`np.ones`**:
   - Creates an array filled with ones.
   - **Example:**
     ```python
     # Creates a 2x5 array of ones
     ones_array = np.ones((2, 5))  
     print(ones_array)
     ```

3. **`np.arange`**:
   - Creates an array with a range of values, similar to Python’s `range` but returns an array.
   - **Example:**
     ```python
     # Creates an array with values from 0 to 9
     arange_array = np.arange(10)  
     print(arange_array)
     ```
   - You can also specify the start, stop, and step values:
     ```python
     # Creates an array with values from 1 to 9, with a step of 2
     arange_array_step = np.arange(1, 10, 2)  
     print(arange_array_step)
     ```

4. **`np.linspace`**:
   - Creates an array of evenly spaced values between a specified start and stop value.
   - **Example:**
     ```python
     # Creates an array with 5 evenly spaced values between 0 and 1
     linspace_array = np.linspace(0, 1, 5)  
     print(linspace_array)
     ```

These functions allow you to quickly generate arrays with specific values and structures, making it easy to initialize data for various computations and analyses.


## NumPy Standard Data Types

NumPy supports a wide range of data types that are crucial for handling various kinds of numerical and non-numerical data efficiently. Here are some of the standard data types in NumPy:

1. **Integer Types**:
   - **`np.int8`**: 8-bit integer (-128 to 127)
   - **`np.int16`**: 16-bit integer (-32,768 to 32,767)
   - **`np.int32`**: 32-bit integer (-2,147,483,648 to 2,147,483,647)
   - **`np.int64`**: 64-bit integer (-9,223,372,036,854,775,808 to 9,223,372,036,854,775,807)

2. **Unsigned Integer Types**:
   - **`np.uint8`**: 8-bit unsigned integer (0 to 255)
   - **`np.uint16`**: 16-bit unsigned integer (0 to 65,535)
   - **`np.uint32`**: 32-bit unsigned integer (0 to 4,294,967,295)
   - **`np.uint64`**: 64-bit unsigned integer (0 to 18,446,744,073,709,551,615)

3. **Floating-Point Types**:
   - **`np.float16`**: 16-bit floating-point number
   - **`np.float32`**: 32-bit floating-point number
   - **`np.float64`**: 64-bit floating-point number (double precision)

4. **Complex Number Types**:
   - **`np.complex64`**: Complex number represented by two 32-bit floats (real and imaginary parts)
   - **`np.complex128`**: Complex number represented by two 64-bit floats (real and imaginary parts)

5. **Boolean Type**:
   - **`np.bool_`**: Boolean (True or False)

6. **String Types**:
   - **`np.str_`**: Fixed-length Unicode string
   - **`np.bytes_`**: Fixed-length byte string

7. **Other Types**:
   - **`np.object_`**: Object type (any Python object)
   - **`np.void`**: Void type (for custom or raw data)

**Examples:**

Creating arrays with specific data types:

```{code-cell} ipython3
:tags: [hide-output]

# Integer array
int_array = np.array([1, 2, 3], dtype=np.int32)
print(int_array.dtype)

# Float array
float_array = np.array([1.0, 2.0, 3.0], dtype=np.float64)
print(float_array.dtype)

# Complex array
complex_array = np.array([1+2j, 3+4j], dtype=np.complex128)
print(complex_array.dtype)

# Boolean array
bool_array = np.array([True, False, True], dtype=np.bool_)
print(bool_array.dtype)
```

Understanding these data types helps in selecting the appropriate type for efficient computation and memory usage.



<!-- In this chapter, we will delve into the world of NumPy arrays and learn how to harness their power for efficient data manipulation and numerical computations. 
NumPy, short for Numerical Python, is a fundamental library in the Python ecosystem, providing convenient and high-performance functionality for a wide range of mathematical operations.

We will explore how to create, manipulate, and perform complex operations on NumPy arrays, enabling us to handle large datasets with ease and precision. 
From basic array creation and reshaping to advanced indexing, slicing, and broadcasting, this chapter will equip you with the essential skills to leverage NumPy for your data science and machine learning projects.

```{note}
NumPy arrays have a fixed type, meaning all elements are of the same data type. 
This consistency allows for optimized memory usage and faster computation compared to Python lists. 
The fixed type also enables efficient vectorized operations on the entire array at once.
```

## NumPy installation via PIP

To install the `numpy` package, use the following command:
```bash
pip install numpy
```

## Creating NumPy arrays

Just want to check how it works now

Let's try to create our first numpy array.
Here is the code snippet:

Just a test -->


<!-- ```{code-cell} ipython3
import numpy as np

v = np.array([1, -1, 1, -1])
print(v)
``` -->
