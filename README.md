# A Review of Julia Programming Language

This repo holds a basics review of the Julia programming language.

## Importing packages
We can import packages by `using` keyword:
```julia
using Printf
println("Hello World!")
```
> Hello World!

## Variables
Variables can be either dynamically or strictly typed. Following shows an example variable declaration:
```julia
using Printf
name :: String = "John"

println("Hello " * name * "!")
```
> Hello John!

The following is a list of primitive types in Julia:
- Number types:
  - `Number` is the abstract number type which all numbers are an instance of.
  - `Integer` is the asbtract integer type with `Signed` and `Unsigned`.
    - `Int8`, `Int16`, `Int32`, `Int64`, `Int128` are different signed integer types with specific sizes.
    - `UInt8`, `UInt16`, `UInt32`, `UInt64`, `UInt128` are different signed integer types with specific sizes.
  - `AbstractFloat` is the abstract float which can be of any size. `Float16`, `Float32`, `Float64` are float types with specific sizes.
- Character types:
  - `Char` is a single char such as `'a'`. Characters in Julia must be surrounded with single qoutes.
  - `String` is a string of chars such as `"Hello!"`. In Julia, double qoutation **must** be used with strings.
- Boolean type which is with `Bool`.

Finally, the following figure shows the number types hierarchy in Julia:
| ![julia number types](./_doc_images/Julia-number-type-hierarchy.svg.png) | 
|:--:| 
| *Number type hierarchy in Julia [^1]* |

### Casting primitive types
Following shows how different types in Julia can be cast into one another:
```julia
using Printf

# Int to Char
a1 :: Char = Char(100)
println(a1)

# Char to Int
a2 :: Int = Int(a1)
println(a2)

# Float to Int
b :: Int = Int(trunc(2.713))
println(b)

# Int to Float
b2 :: Float32 = Float32(1231)
println(b2)

# String to Number
c :: Float32 = parse(Float32, "2.141")
println(c)

# Number to String
c2 :: String = string(12.31)
println(c2)
```
> d  
100  
2  
1231.0  
2.141  
12.31  

## Basic `String` operations
Following is an example code depicting some basic operations with strings:
```julia
using Printf

s = "Hello you!"

# String size
println(length(s))

# String interpolation
println("Size of string 's' is $(length(s))")
println("The sum of 2 and 3 is $(2+3)")

# String indexing
println(s[1]) # the first Char in string
println(s[end]) # the last Char in string
println(s[2:5]) # string slicing

# String concatenation
s2 = "What is your name?"
println(s * ", " * s2)
println(string(s, ", ", s2))

# String comparisons
println("Tokyo" == "London")
println("Tokyo" != "London")

# Multi-line strings
s3 = """
This is a multi-line string.
This is the second line.
"""
println(s3)
```
>10  
Size of string 's' is 10  
The sum of 2 and 3 is 5  
H  
!  
ello  
Hello you!, What is your name?  
Hello you!, What is your name?  
false  
true  
This is a multi-line string.  
This is the second line.  

## Functions
In the simplest way, functions can be defined and called as follows. Please note that the indentation inside the function body is **not required** as it is in Python. The indentation is however used for better readibility.
```julia
using Printf

function helloWorld()
    println("Hello World!")
end

helloWorld()
```

[^1]: https://en.wikibooks.org/wiki/Introducing_Julia/Types
