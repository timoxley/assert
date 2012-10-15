# assert

This module is used for writing unit tests for your applications, you can
access it with `require('assert')`.

`assert` module ported from Node.JS for use as a component in the browser.

## Installation

```
$ component install timoxley/assert
```

## Example

```js

var assert = require('assert')

assert(document.contains(document.body)) // => undefined
assert.strictEqual(Math.sqrt(9), 3) // => undefined
assert.strictEqual(Math.sqrt(9), '3') // => AssertionError: 3 === "3"

assert.equal([1, 2], [1, 2]) // => AssertionError: [1,2] == [1,2]
assert.deepEqual([1, 2], [1, 2]) // => undefined
```

## API

Note: These docs have been adapted from the same markdown that
produces the [official node assert documentation](http://nodejs.org/docs/v0.8.12/api/assert.html#assert_assert).

### assert.fail(actual, expected, message, operator)

Throws an exception that displays the values for `actual` and `expected` separated by the provided operator.

### assert(value, message), assert.ok(value, [message])

Tests if value is truthy, it is equivalent to `assert.equal(true, !!value, message);`

### assert.equal(actual, expected, [message])

Tests shallow, coercive equality with the equal comparison operator ( `==` ).

### assert.notEqual(actual, expected, [message])

Tests shallow, coercive non-equality with the not equal comparison operator ( `!=` ).

### assert.deepEqual(actual, expected, [message])

Tests for deep equality.

### assert.notDeepEqual(actual, expected, [message])

Tests for any deep inequality.

### assert.strictEqual(actual, expected, [message])

Tests strict equality, as determined by the strict equality operator ( `===` )

### assert.notStrictEqual(actual, expected, [message])

Tests strict non-equality, as determined by the strict not equal operator ( `!==` )

### assert.throws(block, [error], [message])

Expects `block` to throw an error. `error` can be constructor, regexp or 
validation function.

Validate instanceof using constructor:

```js
    assert.throws(
      function() {
        throw new Error("Wrong value");
      },
      Error
    );
```

Validate error message using RegExp:

```js
    assert.throws(
      function() {
        throw new Error("Wrong value");
      },
      /value/
    );
```
Custom error validation:

```js 
    assert.throws(
      function() {
        throw new Error("Wrong value");
      },
      function(err) {
        if ( (err instanceof Error) && /value/.test(err) ) {
          return true;
        }
      },
      "unexpected error"
    );
```

### assert.doesNotThrow(block, [message])

Expects `block` not to throw an error, see assert.throws for details.

### assert.ifError(value)

Tests if value is not a false value, throws if it is a true value. Useful when
testing the first argument, `error` in callbacks.


## Changes from Node's assert
Removed `deepEqual` checks for the `Buffer` type as it's not native in
the browser.

## Credit

Extracted /lib/assert.js from joyent/node master branch on 16/10/2012.
https://github.com/joyent/node/blob/e4cef1a0833e6d677298600e205a142d15639bf2/lib/assert.js
