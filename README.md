# Javascript Memoization
- Programs often waste time calling functions which recalculate the same results over and over again.

A perfect example of this is the Fibonacci number generator. The Fibonacci sequence is a series of integers, beginning with zero and one, in which each value is the sum of the previous two numbers in the series. Based on this definition, the first ten Fibonacci numbers are: 0, 1, 1, 2, 3, 5, 8, 13, 21, 34. From a programming perspective, the nth Fibonacci number is typically computed recursively using the following function.

```javascript
function fibonacci(n) {
  if (n === 0 || n === 1)
    return n;
  else
    return fibonacci(n - 1) + fibonacci(n - 2);
}
```

## Memoization Basics
Memoization is a programming technique which attempts to increase a function’s performance by caching its previously computed results. Because JavaScript objects behave like associative arrays, they are ideal candidates to act as caches. Each time a memoized function is called, its parameters are used to index the cache. If the data is present, then it can be returned, without executing the entire function.  However, if the data is not cached, then the function is executed, and the result is added to the cache

```javascript
var fibonacci = (function() {
  var memo = {};

  function f(n) {
    var value;

    if (n in memo) {
      value = memo[n];
    } else {
      if (n === 0 || n === 1)
        value = n;
      else
        value = f(n - 1) + f(n - 2);

      memo[n] = value;
    }

    return value;
  }

  return f;
})();
```

##### Reference
https://www.sitepoint.com/implementing-memoization-in-javascript/
