# The Basics of Big-O - Developing an intuition about the performance of your code

This workshop accompanies a talk by Ilya Sabanin given as an introduction to Big-O notation.

The workshop is broken up into 3 exercises.

MOAR WORDS!

## Examples
To get started we're going to practice counting complexity with a few simple examples. Here's an example to get you started.

```javascript
function includes (xs, y) {
  console.log(`We're checking to see if ${x} is in ${xs}`) // Complexity: 1
  for (x in xs) { // Complexity: n
    if (x === y) { // Complexity: 1
      return true;
    }
  }
  return false;
}
/*
 * The console.log has complexity 1
 * The for loop has complexity n because it loops every item
 * The if has complexity 1
 *
 * This gives us a total of 2+n, which simplifies to n
 */
```

```javascript
function countEvensAndOdds (xs) {
  let evens = 0 // Complexity: 1
  let odds = 0 // Complexity: 1

  for (x in xs) { // Complexity: n
    if (x % 2 == 0) { // Complexity: 1
      evens++ // Complexity: 1
    }
  }

  for (x in xs) { // Complexity: n
    if (x % 2 == 1) { // Complexity: 1
      odds++ // Complexity: 1
    }
  }

  return {evens, odds} // Complexity: 1
}
/*
 * We've got a complexity of 3 to define even, odd, and return the results
 * Each loop has a complexity of 2 + n
 *
 * Using teh maths:
 * 3 + (2 + n) + (2 + n)
 *
 * If we simplify out the constants like before we end up with:
 * n + n = 2n
 *
 * Interestingly enough, we can simply this to just n!
 */
```

## Exercise
In the exercises, we will test your knowledge with some real examples. Good Luck!

```javascript
function first (xs) {
  if (xs.length > 0) {
      return xs[0];
    } else {
      return null;
    }
}
```

```javascript
function count (xs) {
  let count = 0
  for (x in xs) {
    count++
  }
  return count
}
```

```javascript
function take (xs, n) {
  let results = []
  for (let i=0; i<n; i++) {
    results.push(xs[i])
  }
  return results
}
```

```javascript
// Assuming xs is a sorted array of numbers
function binarySearch(xs, x, start=0, stop=xs.length) {
  const mid = Math.floor((start + stop) / 2)
  if (x === xs[mid]) {
    // base case, we found it. Stop searching
    return mid
  } else if (x < xs[mid]) {
    // divide the search area in half. Search first half
    return binarySearch(xs, x, 0, mid)
  } else if (x > xs[mid]) {
    // divide the search area in half. Search second half
    return binarySearch(xs, x, mid+1, stop)
  } else {
    // don't blow up if x is not found
    return null
  }
}
```

```javascript
function mergeSort (xs) {
  if (xs.length <= 1) {
    // base case, an array of size 0 or 1 is sorted
    return xs;
  }
  const mid = Math.floor(xs.length / 2)

  // Divide the array
  const left = mergeSort(xs.slice(0, mid))
  const right = mergeSort(xs.slice(mid, xs.length))

  // Merge the sorted halves
  return _merge(left, right)
}

function _merge (xs, ys) {
  var result = [];
  while (xs.length && ys.length) {
    result.push(xs[0] < ys[0] ? xs.shift() : ys.shift())
  }
  return result.concat(xs.length ? xs : ys)
}
```

```javascript
function bubbleSort (xs) {
  // Sweep the array enough times to ensure everything is sorted
  for (let i = 0; i < xs.length; i++) {
    // Sweep through the array sorting as we go
    for (let j = 0; j < xs.length; j++) {
      // Swap adjacent items if they aren't sorted
      if (xs[j] > xs[j + 1]) {
        let tmp = xs[j]
        xs[j] = xs[j + 1]
        xs[j + 1] = tmp
      }
    }
  }
  return xs
}
```

```javascript
function fibonacci (num) {
  // base case
  if (num <= 1) {
    return num
  }

  // run fibonacci to figure out the previous two numbers to add
  return fibonacci(num - 1) + fibonacci (num - 2)
}
```
