---
theme: seriph
class: text-left
---

# Functions in JavaScript

Functions are blocks of code designed to perform a particular task.  
They help organize and reuse code in a program.  
A function can accept input (parameters), perform operations, and return an output.

---

## Function Declaration

Functions are declared using the `function` keyword. They can take parameters and return values.

```js
function greet(name) {
  return `Hello, ${name}!`;
}
console.log(greet('Alice'));
```

**Output:**  
Hello, Alice!

---

## Basic Functions

Functions allow for reusable logic, like this simple addition example.

```js
function add(a, b) {
  return a + b;
}
console.log(add(2, 3));
```

**Output:**  
5

---

## Arrow Functions

Arrow functions are a concise way to write functions, introduced in ES6.

```js
const multiply = (a, b) => a * b;
console.log(multiply(4, 5));
```

**Output:**  
20

---

## Default Parameters

You can define default values for parameters, which are used if no argument is provided.

```js
function bookRoom(roomType = 'Standard') {
  return `Room booked: ${roomType}`;
}
console.log(bookRoom());
```

**Output:**  
Room booked: Standard

---

## Optional Chaining

Optional chaining allows safe access to nested object properties without causing errors.

```js
const user = { profile: { name: 'Bob' } };
console.log(user?.profile?.name);
console.log(user?.contact?.email);
```

**Output:**  
Bob  
undefined

---

## Asynchronous Functions

`async` and `await` simplify asynchronous operations and make them easier to read.

```js
async function fetchData() {
  const response = await fetch('https://api.example.com/data');
  const data = await response.json();
  console.log(data);
}
fetchData();
```

---

## Callback Pattern

Before async/await, callbacks were used to handle asynchronous code.

```js
function getUserData(callback) {
  setTimeout(() => {
    callback({ name: 'Jane' });
  }, 1000);
}
getUserData(user => console.log(user.name));
```

**Output:**  
Jane (after 1 second)

---

## Closures

Closures allow functions to retain access to their lexical scope even after the outer function has executed.

```js
function makeCounter() {
  let count = 0;
  return function() {
    count++;
    return count;
  };
}
const counter = makeCounter();
console.log(counter());
```

**Output:**  
1

---

## Lexical Scope

Lexical scope defines how variable names are resolved in nested functions.

```js
function outer() {
  let outerVar = 'I am outer';
  function inner() {
    console.log(outerVar);
  }
  return inner;
}
const innerFunc = outer();
innerFunc();
```

**Output:**  
I am outer

---

## Hoisting

Hoisting allows function declarations to be used before they are defined in the code.

```js
console.log(square(3));
function square(x) {
  return x * x;
}
```

**Output:**  
9

---

## Passing Functions as Arguments

Functions can be passed as arguments, enabling high-order functions.

```js
function logGreeting(fn) {
  console.log(fn('Charlie'));
}
logGreeting(name => `Hello, ${name}!`);
```

**Output:**  
Hello, Charlie!

---

## Implicit Return (Arrow Functions)

Arrow functions can return values implicitly if they consist of a single expression.

```js
const isEven = num => num % 2 === 0;
console.log(isEven(4));
```

**Output:**  
true

---

## Generator Functions

Generator functions use `yield` to pause and resume execution, producing a series of values.

```js
function* idGenerator() {
  let id = 1;
  while (true) {
    yield id++;
  }
}
const gen = idGenerator();
console.log(gen.next().value);
console.log(gen.next().value);
```

**Output:**  
1  
2

---

## Yield Keyword

The `yield` keyword pauses a generator function and returns a value to the caller.

```js
function* fruitList() {
  yield 'Apple';
  yield 'Banana';
  yield 'Cherry';
}
const fruits = fruitList();
console.log(fruits.next().value);
console.log(fruits.next().value);
```

**Output:**  
Apple  
Banana

---

## yield* Delegation

`yield*` allows a generator to delegate part of its iteration process to another generator.

```js
function* numbers() {
  yield 1;
  yield 2;
}

function* moreNumbers() {
  yield* numbers();
  yield 3;
}
const genNums = moreNumbers();
console.log(genNums.next().value);
console.log(genNums.next().value);
console.log(genNums.next().value);
```

**Output:**  
1  
2  
3
