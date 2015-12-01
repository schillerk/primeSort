# primeSort
A few weeks ago, I was prepping for coding interviews and discovered countingSort. Unlike comparison sorts which are mathematically proven to have a lower bound of O(n*log(n)) time, countingSort is able to run in O(n) time using a frequency array and two linear passes.

As you might guess, there's a reason countingSort isn't usually taught in schools or implemented in real life. While it works great for some data sets (e.g. sorting years of experience), it doesn't even take pathological data to make both running time and memory use non-optimal.

There's a variant of countingSort called radixSort that works a lot better, but even here we run into problems with real world applications

To supplement these sorts, I'm happy to introduce primeSort: a technique that functions worse than both of them.

Here's how it works:

Download a list of primes and parse it into an array. Instantiate a integer with value 1, execute a linear pass through your input array, and each time you get to an element of value n, multiple your integer by n.

Now, run through your array of primes, stopping when you get to the index equal to the max value of your original input. Each time your integer is divisible by the prime at any given index, output the index.

And you're done!

To deal with duplicates, we simply replace the if statement in the code above with a while loop that checks for powers of any given prime.

So why does this work? According to the Fundamental Theorem of Arithmetic, also known as unique prime factorization, every integer can be factored into primes, and this factorization is unique. This means that when we multiple a bunch of primes together, we've created a kind of lossless compression. All the data is still there, and we have no problem pulling our original primes out again.

The real problem here is with the word compression. Even though this only requires a single variable, multiplying primes by each other means that the variable quickly grows to take up far more memory than the array used in countingSort.

Still, this is a neat application of the FTA, and could be a great way to surprise your examiner (or maybe just display your sense of humor) at your next coding interview.