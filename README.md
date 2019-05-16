# Beyond ES6: 

## Intro

This are [finished proposals](https://github.com/tc39/proposals/blob/master/finished-proposals.md) from [TC39](https://www.ecma-international.org/memento/tc39-rf-tg.htm)

TC39 is the body that standardizes the JS language.
Finished proposals are proposals that have been approved by the body and are now considered part of the language (even if they're not published yet)

## Repo
This project can be found at https://github.com/raveneyex/beyondes6

## Snippets
Runnable snippets can be found at https://codepen.io/collection/DwqaRQ/

## How to Run
`npm i && npm start`

## Content

1. String goodies
    * String.prototype.trimStart
    * String.prototype.trimEnd
    * String.prototype.padStart
    * String.prototype.padEnd
2. Array goodies
    * Array.prototype.includes
    * Array.prototype.flat
    * Array.prototype.flatMap
3. Object goodies
    * Object rest operator
    * Object spread operator
    * Object.values
    * Object.entries
    * Object.fromEntries
    * Object.getOwnPropertyDescriptors
4. Asynchronous goodies
    * Async/Await
    * Asynchronous iteration
    * Promise.prototype.finally
5. Misc Goodies
    * Exponentiation Operator
    * Optional catch binding
    * Trailing commas
    * Function.prototype.toString

## String Goodies
#### String.prototype.trimStart

##### What is it?
A method to remove whitespace at the start of a string. 
It doesn't alter the original string.

##### Can I use it now?
Partially.
No Edge and no IE.

##### Talk is cheap, show me the code
```
let message = "            The future is already here        ";
console.log(JSON.stringify(message.trimStart())); // "The future is already here        ";
```

#### String.prototype.trimEnd

##### What is it?
A method to remove whitespace at the end of a string.
It doesn't alter the original string.

##### Can I use it now?
Partially.
No Edge and no IE.

##### Talk is cheap, show me the code
```
let message = "            I want to believe        ";
console.log(JSON.stringify(message.trimEnd())); // "            I want to believe";
```

#### String.prototype.padStart

##### What is it?
A method to insert characters into the beggining of a string until a certain length is achieved.

##### Can I use it now?
Yes, on all modern* browsers
\* = Yes to Edge, no to IE.

##### Talk is cheap, show me the code
```
// String.prototype.padStart(desiredLength, stringToPad);

let message = "I want to believe";
console.log(message.padStart(21, '🛸')); // 🛸🛸I want to believe
```

#### String.prototype.padEnd

##### What is it?
A method to insert characters into the end of a string until a certain length is achieved.

##### Can I use it now?
Yes, on all modern* browsers
\* = Yes to Edge, no to IE.

##### Talk is cheap, show me the code
```
// String.prototype.padEnd(desiredLength, stringToPad);

let message = "I want to believe";
console.log(message.padEnd(21, '🛸')); // I want to believe🛸🛸
```

## Array Goodies
#### Array.prototype.includes

##### What is it?
A method to test the presence of an element in an array.
The main difference with all the already-existing methods is its ability to find `NaN`.

##### Can I use it now?
Yes, on all modern* browsers
\* = Yes to Edge, no to IE.

##### Talk is cheap, show me the code
```
let isAlphaPresent, isNaNPresent;
const arr = ['alpha', 'beta', 'gamma', NaN];

// Before
isAlphaPresent = (arr.indexOf('alpha') !== -1);
isNaNPresent = (arr.indexOf(NaN) !== -1);
console.log('Before - isAlphaPresent:', isAlphaPresent);
console.log('Before - isNaNPresent:', isNaNPresent);

// Now
isAlphaPresent = arr.includes('alpha');
isNaNPresent = arr.includes(NaN);
console.log('Now - IsAlphaPresent:', isAlphaPresent);
console.log('Now - IsNaNPresent:', isNaNPresent);
```

#### Array.prototype.flat

##### What is it?
A method that creates a new array with all sub-array elements concatenated into it recursively up to the specified depth.

##### Can I use it now?
Partially.
No Edge and no IE.

##### Talk is cheap, show me the code
```
// Array.prototype.flat(depth);

const arr = [1, 2, [3, 4, [5, 6, [7, 8]]]];
const flatOne = arr.flat(); // [1, 2, 3, 4, [5, 6, [7, 8]]]
const flatTwo_Chained = arr.flat().flat(); // [1, 2, 3, 4, 5, 6, [7, 8]]
const flatTwo_Parameterized = arr.flat(2); // [1, 2, 3, 4, 5, 6, [7, 8]]
const flatAll = arr.flat(Infinity); // [1, 2, 3, 4, 5, 6, 7, 8]
```

#### Array.prototype.flatMap

##### What is it?
The flatMap method is identical to calling `Array.prototype.map` followed by a call to `Array.prototype.flat` with depth 1.

##### Can I use it now?
Partially.
No Edge and no IE.

##### Talk is cheap, show me the code
```
  // Array.prototype.flatMap(callback(element, index, originalArray), thisArg);

  const arr3 = [1, 2, 3, 4];
  const pow = arr3.flatMap((x) => x**2);
  const pow2 = arr3.flatMap((x) => [x**2]);
  console.log('Pow:', pow);
  console.log('Pow2:', pow2);
```
## Object goodies
#### Object rest operator

##### What is it?
A way to destructure an object allowing you to collect the remaining properties onto a new object.

##### Can I use it now?
Partially.
No Edge and no IE.

##### Talk is cheap, show me the code
```
  const {name, occupation, ...rest} = {
    name: 'Molly Millions',
    occupation: 'Hi-Tech Spy',
    enhancements: ['Blade-Nails', 'Nightvision'],
    employer: 'None'
  };
  console.log(name); // Molly Millions
  console.log(occupation); // Hi-Tech Spy
  console.log(rest); //{enhancements: ['Blade-Nails', 'Nightvision'], employer: "None"}
```

#### Object spread operator

##### What is it?
A way to spread the properties of an object.

##### Can I use it now?
Partially.
No Edge and no IE.

##### Talk is cheap, show me the code
```
  const meta_info = { date: '12/02/2018', views: 666 };
  const info = { title: 'The Necronomicon', ISBN: '666azrl' };
  const full_info = {
    ...meta_info,
    ...info
  };
  console.log(full_info); // { date: "12/02/2018", views: 666, title: "The Necronomicon", ISBN: "666azrl" }
```

#### Object.values

##### What is it?
A function that returns all the values from an object _own_ properties.

##### Can I use it now?
Yes, on all modern* browsers
\* = Yes to Edge, no to IE.

##### Talk is cheap, show me the code
```
  const cyborg = {
    model: '2097',
    make: 'Mitsubishi',
    enhancements: ['weapons', 'nightvision']
  };
  const values = Object.values(cyborg);
  console.log(values); // ["2097", "Mitsubishi", ['weapons', 'nightvision']]
```

#### Object.entries

##### What is it?
A function that return an array of the key-value pairs of an object properties in array form.

##### Can I use it now?
Yes, on all modern* browsers
\* = Yes to Edge, no to IE.

##### Talk is cheap, show me the code
```
  const android = {
    model: '2097',
    make: 'Mitsubishi',
    enhancements: ['weapons', 'nightvision']
  };
  const entries = Object.entries(android);
  console.log(entries); // [["model","2097"],["make","Mitsubishi"],["enhancements",["weapons","nightvision"]]]
```

#### Object.fromEntries

##### What is it?
A function that transforms an array (or map) of key-value pairs into an object.

##### Can I use it now?
Partially.
No Edge and no IE.

##### Talk is cheap, show me the code
```
  // Using array
  const description = [['name', 'Cthulu'], ['race', 'Ancient Ones'], ['location', 'Rlyeh']];
  const cthulhu = Object.fromEntries();
  console.log(cthulhu); // {name: "Cthulu", race: "Ancient Ones", location: "Rlyeh"}

  // Using map
  const mapDescriptor = new Map([
    ['name', 'Azathot'],
    ['race', 'Outer God']
  ]);
  const azathot = Object.fromEntries(mapDescriptor);
  console.log(azathot); // {name: "Azathot", race: "Outer God"}
```

#### Object.getOwnPropertyDescriptors

##### What is it?
A function that returns descriptors for all the properties of an object, including getters and setters.

##### Can I use it now?
Yes, on all modern* browsers
\* = Yes to Edge, no to IE.

##### Talk is cheap, show me the code
```
const azrael = {
  name: "Azrael",
  race: "Angel",
  get mission() {
    return this._mission;
  },
  set mission(value) {
    this._mission = value;
  }
};
const objDescriptor = Object.getOwnPropertyDescriptors(azrael);
console.log(objDescriptor); // {name: {…}, race: {…}, mission: {…}}
// name: {value: "Azrael", writable: true, enumerable: true, configurable: true}
// race: {value: "Angel", writable: true, enumerable: true, configurable: true}
// mission: {get: ƒ, set: ƒ, enumerable: true, configurable: true}

const basicClone = Object.assign({}, azrael);
const spreadClone = {...azrael};
const fullClone = Object.defineProperties({}, objDescriptor);
console.log(basicClone); // {name: "Azrael", race: "Angel", mission: undefined}
console.log(spreadClone); // {name: "Azrael", race: "Angel", mission: undefined}
console.log(fullClone);
// {name: "Azrael", race: "Angel", get mission: ƒ mission(), set mission: ƒ mission(value)}
```
## Asynchronous Goodies
#### Async / Await

##### What is it?
Operators for handling asynchronous operations.
* `async` is an operator used to denote that a function is performing asynchronous operation
* `await` is an operator used to denote a variable whose value is the result of an asynchronous request. 
  Can only be used inside `async` functions.

##### Can I use it now?
Yes, on all modern* browsers
\* = Yes to Edge, no to IE.

##### Talk is cheap, show me the code
```
async function fetchPost() {
  try {
    const promise = fetch('https://jsonplaceholder.typicode.com/todos/1');
    const resp = await promise;
    const data = await resp.json();
    console.log(data);
  } catch {
    console.log("Oops!");
  }
}
fetchPost();
// {userId: 1, id: 1, title: "delectus aut autem", completed: false}
```

#### Asynchronous Iteration

##### What is it
Iterable capabilities for asynchronous data using async generators

##### Can I use it now?
Partially.
No Edge and no IE.

##### Talk is cheap, show me the code
```
async function* fetchUsers() {
  const promise = fetch('https://jsonplaceholder.typicode.com/users');
  const resp = await promise;
  const data = await resp.json();
  while (data.length) {
    yield data.shift();
  }
}

async function printUsers() {
  for await (const user of fetchUsers()) {
    console.log(user);
  }
}
printUsers();
```

#### Promise.prototype.finally

##### What is it?
A native implementation of the finally method for promises.

##### Can I use it now?
Yes, on all modern* browsers
\* = Yes to Edge, no to IE.

##### Talk is cheap, show me the code
```
function mockPromise() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      reject("Bad Request");
    }, 2000);
  })
}

async function exampleAsyncFinally() {
  try {
    const data = await mockPromise();
  } catch {
    console.log("Oops! something went wrong");
  } finally {
    console.log("Async operation done");
  }
}
exampleAsyncFinally();

function examplePromiseFinally() {
  mockPromise()
    .then(() => {
      console.log("Success");
    })
    .catch(() => {
      console.log("Oops! something went wrong");
    })
    .finally(() => {
      console.log("Operation done");
    })
}
examplePromiseFinally();
```
## Misc Goodies
#### Exponentiation Operator

##### What is it? 
A simple exponentiation operator `**`

##### Can I use it now?
Yes, on all modern* browsers
\* = Yes to Edge, no to IE.

##### Talk is cheap, show me the code
```
let power;
// Before
power = Math.pow(7, 2);
console.log(power); // 49

// Now
power = 7**2;
console.log(power); // 49
```

#### Optional catch binding

##### What is it?
Catch blocks no longer demand a parameter to take in.

##### Can I use it now?
Partially.
No Edge and no IE.

##### Talk is cheap, show me the code
```
// before
try {
  // Some error-prone function
} catch(err) {
  // Most linters will complain for the unused variable `err`
}

// now
try {
  // Some error-prone function
} catch {
  // Clean
}
```

#### Trailing Commas

##### What is it?
Parameters list and calls now are able to handle trailing commas.

##### Can I use it now?
Yes, on all modern* browsers
\* = Yes to Edge, no to IE.

##### Talk is cheap, show me the code
```
let arr = [
  'alpha',
  'beta',
  'gamma', // this is valid now.
];

fooFn(param1, param2, param3,); // Also valid.
```