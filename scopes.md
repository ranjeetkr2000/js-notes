# Scopes

A scope in JavaScript defines what variables you have access to. There are two kinds of scope – **global scope and local scope.**

## Global Scope

If a variable is declared outside all functions or curly braces ({}), it is said to be defined in the global scope.

- Although you can declare variables in the global scope, it is advised not to. This is because there is a chance of naming collisions, where two or more variables are named the same. If you declared your variables with const or let, you would receive an error whenever a name collision happens. This is undesirable.

```js
// Don't do this!
let thing = 'something'
let thing = 'something else' // Error, thing has already been declared
```

If you declare your variables with **var**, your **second variable overwrites the first one after it is declared**. This also undesirable as you make your code hard to debug.

```js

// Don't do this!
var thing = 'something'
var thing = 'something else' // perhaps somewhere totally different in your code
console.log(thing) // 'something else'

```

## **So, you should always declare local variables, not global variables.**

## Local Scope

If a variable is declared inside a functions or a block, its called local scope.

**Local scope variable is only accessible to a particular function of a block where that variable is declared.**

**Function Scope** :

```js
function sayHello () {
  const hello = 'Hello CSS-Tricks Reader!'
  console.log(hello)
}

sayHello() // 'Hello CSS-Tricks Reader!'
console.log(hello) // Error, hello is not defined
```

**Block Scope** :

```js
{
  const hello = 'Hello CSS-Tricks Reader!'
  console.log(hello) // 'Hello CSS-Tricks Reader!'
}

console.log(hello) // Error, hello is not defined
```

## Functions hoisting and scopes

Functions declared using the function keyword are always hoisted at the top of their current scope.

Eg.

```js
// This is the same as the one below
sayHello()
function sayHello () {
  console.log('Hello CSS-Tricks Reader!')
}
```

```js
// This is the same as the code above
function sayHello () {
  console.log('Hello CSS-Tricks Reader!')
}
sayHello()
```

But when a function is declared with expression, it is not hoisted.

```js
sayHello() // Error, sayHello is not defined
const sayHello = function () {
  console.log(aFunction)
}
```

**Functions do not have access to each other's scope.**

### Nested scopes

When a function is defined in another function, the inner function has access to the outer function’s variables. This behavior is called lexical scoping.

However, the **outer function does not have access to the inner function’s variables.**
