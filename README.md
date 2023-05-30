# Python-Interview_Questions
# Interview questions for Python and it's libraries added from various sources.

# Describe the core principles of a REST API. How is this a different philosophy from RPC?

The core principles of a REST (Representational State Transfer) API are as follows:

* Stateless Communication: REST APIs are designed to be stateless, meaning that each request from a client to a server must contain all the necessary information for the server to understand and process it. The server does not maintain any client state between requests, which allows for better scalability and reliability.

* Uniform Interface: REST APIs adhere to a uniform and standardized set of rules for communication. They typically use standard HTTP methods such as GET, POST, PUT, and DELETE to perform operations on resources. Resources are identified by unique URLs (Uniform Resource Locators), and responses are typically returned in a consistent format, such as JSON (JavaScript Object Notation) or XML (eXtensible Markup Language).

* Resource-Oriented: REST APIs are focused on resources rather than actions. Resources can be any entity or object that needs to be exposed and manipulated through the API, such as users, products, or documents. Each resource is typically represented by a unique URL, and clients can interact with these resources using the appropriate HTTP methods.

* State Transfer through Representations: When a client interacts with a REST API, the server transfers the state of a resource to the client through representations. These representations can be in various formats like JSON or XML, and they contain the data and metadata associated with the resource. The client can then manipulate the resource's state by sending these representations back to the server in subsequent requests.

Now, let's compare the philosophy of REST APIs with RPC (Remote Procedure Call):

* RPC is a different approach to building APIs that focuses on invoking remote methods or procedures. Unlike REST, RPC typically abstracts the communication details and provides a more procedural interface. Here are some key differences:

* Interface Style: REST APIs follow a resource-oriented and uniform interface style, while RPC APIs provide a more procedure-oriented interface. In RPC, clients typically invoke specific methods on a remote server, passing parameters and expecting a specific result.

* Communication Protocol: REST APIs commonly use HTTP as the underlying communication protocol. They leverage the standard methods, status codes, and headers provided by HTTP. In contrast, RPC can use various protocols such as Remote Procedure Call Protocol (RPCP), Simple Object Access Protocol (SOAP), or custom protocols.

* State Management: REST APIs are stateless, meaning the server does not store any client-specific information between requests. Each request is self-contained. In RPC, there may be a need for maintaining state, and the server can store information about the client's session or context.

* Error Handling: REST APIs use HTTP status codes to indicate the success or failure of a request. Different status codes provide information about the result of the operation. RPC typically handles errors by returning error codes or exceptions specific to the RPC framework being used.

* Data Format: REST APIs often use lightweight and widely supported data formats like JSON or XML to represent the resources being exchanged. RPC can also use these formats but may have additional flexibility to define custom data formats.

 REST APIs emphasize a stateless, uniform, resource-oriented approach with a focus on leveraging standard protocols, while RPC APIs provide a more procedure-oriented approach with potential flexibility in communication protocols and error handling mechanisms.
 
 # Do arguments in Python get passed by reference or by value?

In Python, arguments are passed by object reference, which means that when a function is called, the references to objects are passed as arguments rather than the actual values of the objects. This behavior is often described as "pass by assignment" or "pass by object reference."

When you pass an argument to a function in Python, a new local variable is created within the function scope, which initially references the same object as the argument passed. Any changes made to the object within the function will affect the original object outside the function as well.

However, it's important to note that the distinction between "pass by reference" and "pass by value" can be a bit misleading in Python compared to other programming languages. This is because objects in Python can be mutable or immutable.

Immutable objects, such as numbers, strings, and tuples, behave as if they are passed by value. When you pass an immutable object as an argument to a function and modify it within the function, a new object is created with the modified value, and the original object remains unchanged.

On the other hand, mutable objects, such as lists, dictionaries, and user-defined objects, behave as if they are passed by reference. If you pass a mutable object as an argument to a function and modify it within the function, the changes will be reflected in the original object since they both refer to the same underlying object.

To summarize, Python uses a form of "pass by object reference" where the references to objects are passed as arguments, and changes to mutable objects can be seen outside the function, while immutable objects create new objects when modified within a function.






# Why are functions considered first class objects in Python?

Functions are considered first-class objects in Python because they possess the following characteristics:

Assignability: Functions can be assigned to variables, just like any other object in Python. You can assign a function to a variable, making the variable refer to the function. This allows functions to be treated as values and passed around in the same way as other data types.

Storage: Functions can be stored in data structures such as lists, dictionaries, or sets. This means you can create collections of functions and manipulate them like any other data structure.

Passing as Arguments: Functions can be passed as arguments to other functions. This is a fundamental feature of higher-order functions, which can take functions as input and use them to perform specific operations or transformations.

Returning as Values: Functions can be returned as values from other functions. A function can create and return another function dynamically, allowing for dynamic behavior and customization.

Methods and Attributes: Functions can have methods and attributes associated with them. Methods are functions that are defined within a class and are associated with objects of that class. Functions can also have attributes added to them dynamically, just like any other object.

The ability of functions to be assigned to variables, stored in data structures, passed as arguments, and returned as values makes them first-class objects. This characteristic enables a powerful and flexible programming paradigm called functional programming, where functions can be used to build higher-level abstractions, compose complex behavior, and provide modular and reusable code.






# Give an example of filter and reduce over an iterable object in python

Certainly! Here's an example that demonstrates the use of filter() and reduce() functions over an iterable object in Python:

```
from functools import reduce

# Example list of numbers
numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

# Example using filter()
# Filter out even numbers from the list
even_numbers = list(filter(lambda x: x % 2 == 0, numbers))
print(even_numbers)
# Output: [2, 4, 6, 8, 10]

# Example using reduce()
# Compute the product of all numbers in the list
product = reduce(lambda x, y: x * y, numbers)
print(product)
# Output: 3628800

```

In the above code, filter() is used to filter out even numbers from the numbers list. The lambda function lambda x: x % 2 == 0 is used as the filter condition to keep only the elements that satisfy the condition, i.e., even numbers. The filtered numbers are stored in the even_numbers list.

On the other hand, reduce() is used to compute the product of all the numbers in the numbers list. The lambda function lambda x, y: x * y represents the multiplication operation between two elements. The reduce() function applies this lambda function cumulatively to the elements of the list, reducing it to a single value.

Note that the reduce() function is imported from the functools module in Python, as it is not a built-in function like filter() and map(). Therefore, you need to import it explicitly before using it.






# What do we mean when we say that a certain Lambda expression forms a closure?

When we say that a lambda expression forms a closure, it means that the lambda function captures and remembers the values of variables from its surrounding environment, even if those variables are no longer in scope.

In Python, a closure is a function object that has access to variables in its enclosing lexical scope, even when the function is called outside that scope. The closure "closes over" the variables it references, forming a self-contained unit that retains access to those variables.

Here's an example to illustrate the concept of closures:
```
def outer_function(x):
    def inner_function(y):
        return x + y
    return inner_function

closure = outer_function(10)
result = closure(5)
print(result)
# Output: 15
```
In the above code, outer_function defines an inner function called inner_function. The inner_function references the variable x from its enclosing scope, even though x is no longer in scope when inner_function is called. This is because inner_function forms a closure that captures the value of x at the time it was defined.

When outer_function(10) is called, it returns the inner_function, which is assigned to the closure variable. The closure now acts as a function with the captured value of x (which is 10) as a constant. When closure(5) is called, it adds the argument 5 to the captured value of x (which is 10) and returns the result, which is 15.

Closures are powerful because they allow functions to retain and access the state of variables from their defining environment, even after that environment has ceased to exist. They enable functions to maintain private data and encapsulate behavior with their associated data, leading to more modular and flexible code structures.






# Python uses a Global Interpreter Lock. Does that mean it doesn’t use real threads?

Python does use threads, but due to the Global Interpreter Lock (GIL), it implements a form of concurrency known as "threading" rather than "parallelism." The GIL is a mechanism in CPython (the reference implementation of Python) that ensures only one thread executes Python bytecode at a time.

The GIL exists to simplify memory management and protect Python's internal data structures from concurrent access issues. It helps to prevent race conditions and simplifies the implementation of CPython itself. However, it also means that multiple threads within the same process cannot execute Python bytecode simultaneously on multiple CPU cores.

Although Python threads cannot achieve true parallelism by running simultaneously on multiple CPU cores, they can still be beneficial in certain scenarios. Threads can be useful for I/O-bound tasks, such as waiting for network responses or accessing files, where the performance is not primarily limited by CPU computations.

It's important to note that Python provides several alternative concurrency models that allow for parallelism, such as multiprocessing and asynchronous programming. These models enable Python to leverage multiple CPU cores effectively by using processes or event-driven programming, respectively. By using these approaches, developers can overcome the limitations imposed by the GIL and achieve true parallel execution.

In summary, Python does use threads, but the Global Interpreter Lock restricts the execution of Python bytecode to one thread at a time. While this limits true parallelism within the Python interpreter, other concurrency models like multiprocessing and asynchronous programming can be utilized to achieve parallel execution when necessary.






# Is it possible to have a producer thread reading from the network and a consumer thread writing to a file, really work in parallel? What about the GIL?

Yes, it is possible to have a producer thread reading from the network and a consumer thread writing to a file work concurrently, even though the Global Interpreter Lock (GIL) exists in Python. This is because the GIL primarily affects CPU-bound tasks where multiple threads are executing Python bytecode simultaneously.

In scenarios involving I/O-bound tasks, such as network I/O or disk I/O, the GIL's impact is significantly reduced. When a thread is waiting for I/O operations, it releases the GIL, allowing other threads to acquire it and continue execution. This enables concurrent I/O operations from multiple threads, resulting in effective parallelism for I/O-bound tasks.

In the case of a producer thread reading from the network and a consumer thread writing to a file, the GIL will not significantly hinder their concurrent execution. The producer thread can make network requests and receive responses without being blocked by the GIL, while the consumer thread can write to the file without significant GIL interference.

It's worth noting that if the tasks involve significant CPU computations or heavy manipulation of Python objects, the GIL might have a more noticeable impact. In such cases, alternative approaches like multiprocessing or asynchronous programming can be employed to achieve parallelism without the limitations of the GIL.

To summarize, while the GIL restricts simultaneous execution of Python bytecode by multiple threads, it has less impact on I/O-bound tasks. Consequently, a producer thread reading from the network and a consumer thread writing to a file can effectively work in parallel, making concurrent progress despite the GIL's presence.


# Why does a child class constructor cannot make use of this reference until the super() method has been called?

In object-oriented programming, when you create a child class that extends a parent class, the child class inherits the properties and behaviors of the parent class. This inheritance includes the constructors of the parent class.

When you create an instance of the child class, the constructor of the child class is called. At this point, the constructor needs to initialize the state of the child class and possibly perform some additional actions specific to the child class.

However, before the child class constructor can do its own initialization, it needs to ensure that the parent class has been properly initialized. This is because the child class depends on the state and behavior provided by the parent class.

To ensure proper initialization of the parent class, the child class constructor must call the constructor of the parent class using the super() method. The super() method is used to invoke the constructor of the parent class and allows the parent class to initialize its own state.

Once the super() method is called and the parent class has been initialized, the child class constructor can safely make use of the this reference to access its own properties and methods, as well as any inherited properties and methods from the parent class.

If the child class constructor were to use the this reference before the super() method is called, it could potentially access uninitialized properties or methods inherited from the parent class, leading to undefined behavior or errors. Therefore, it is a language rule to call the super() method as the first statement in the child class constructor to ensure proper initialization of the parent class before the child class can use the this reference.


#  What is map function in Python?

In Python, the `map()` function is a built-in higher-order function that applies a given function to each item of an iterable (e.g., a list, tuple, or string) and returns an iterator with the results. It allows you to transform the elements of the iterable based on the provided function.

The syntax of the `map()` function is as follows:

```python
map(function, iterable)
```

- `function`: The function to be applied to each element of the iterable. It can be a built-in function, a lambda function, or a custom-defined function.
- `iterable`: An iterable object (e.g., list, tuple, string) whose elements will be passed to the function.

Here's an example to illustrate the usage of `map()`:

```python
def square(x):
    return x ** 2

numbers = [1, 2, 3, 4, 5]
squared_numbers = map(square, numbers)

print(list(squared_numbers))  # Output: [1, 4, 9, 16, 25]
```

In the example above, the `map()` function applies the `square()` function to each element of the `numbers` list. It returns an iterator, which is converted to a list using `list()`. The resulting `squared_numbers` list contains the squares of the original numbers.

`map()` can also be used with lambda functions for more concise and inline transformations. Here's an example:

```python
numbers = [1, 2, 3, 4, 5]
squared_numbers = map(lambda x: x ** 2, numbers)

print(list(squared_numbers))  # Output: [1, 4, 9, 16, 25]
```

In this case, a lambda function is defined directly inside the `map()` function, eliminating the need for a separate `square()` function.

The `map()` function is a powerful tool in Python for applying a function to multiple elements of an iterable and obtaining the transformed results. It provides a concise and expressive way to perform element-wise operations.
