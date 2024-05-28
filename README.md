# Bird Watcher

Welcome to Bird Watcher.
If you get stuck on the exercise, check it out at the bottom of each instruction in the helps section, but try and solve it without using those first :)

## Introduction

## Arrays

In C#, data structures that can hold zero or more elements are known as _collections_. An **array** is a collection that has a fixed size/length and whose elements must all be of the same type. Elements can be assigned to an array or retrieved from it using an index. C# arrays are zero-based, meaning that the first element's index is always zero:

```csharp
// Declare array with explicit size (size is 2)
int[] twoInts = new int[2];

// Assign second element by index
twoInts[1] = 8;

// Retrieve the second element by index
twoInts[1] == 8; // => true
```

Arrays can also be defined using a shortcut notation that allows you to both create the array and set its value. As the compiler can now tell how many elements the array will have, the length can be omitted:

```csharp
// Three equivalent ways to declare and initialize an array (size is 3)
int[] threeIntsV1 = new int[] { 4, 9, 7 };
int[] threeIntsV2 = new[] { 4, 9, 7 };
int[] threeIntsV3 = { 4, 9, 7 };
```

Arrays can be manipulated by either calling an array instance's methods or properties, or by using the static methods defined in the `Array` class.

## For Loops

A `for` loop allows one to repeatedly execute code in a loop until a condition is met.

```csharp
for (int i = 0; i < 5; i++)
{
    System.Console.Write(i);
}

// => 01234
```

A `for` loop consists of four parts:

1. The initializer: executed once before entering the loop. Usually used to define variables used within the loop.
2. The condition: executed before each loop iteration. The loop continues to execute while this evaluates to `true`.
3. The iterator: execute after each loop iteration. Usually used to modify (often: increment/decrement) the loop variable(s).
4. The body: the code that gets executed each loop iteration.

## Foreach Loops

The fact that an array is also a _collection_ means that, besides accessing values by index, you can iterate over _all_ its values using a `foreach` loop:

```csharp
char[] vowels = new [] { 'a', 'e', 'i', 'o', 'u' };

foreach (char vowel in vowels)
{
    // Output the vowel
    System.Console.Write(vowel);
}

// => aeiou
```

## Running the tests
If you use Rider or Visual Studio, you can run the tests by opening the solution file and right clicking on the test file and selecting "Run" or "Run Unit Tests".

If you use visual studio code you must run the command `dotnet test` from the exercise directory.

## Instructions

You're an avid bird watcher that keeps track of how many birds have visited your garden in the last seven days.

You have six tasks, all dealing with the numbers of birds that visited your garden.

## 1. Check what the counts were last week

For comparison purposes, you always keep a copy of last week's counts nearby, which were: 0, 2, 5, 3, 7, 8 and 4. Implement the (_static_) `BirdCount.LastWeek()` method that returns last week's counts:

```csharp
BirdCount.LastWeek();
// => [0, 2, 5, 3, 7, 8, 4]
```
<details>
  <summary>Helps</summary>
  <ul>
<li>As this method does _not_ depend on the current week's count, it is defined as a  <a href="https://www.oreilly.com/library/view/programming-c/0596001177/ch04s03.html">`static` method</a>.</li>  
<li> There are <a href="https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/arrays#single-dimensional-arrays">several ways to define an array</a></li></ul>
</details>

## 2. Check how many birds visited today

Implement the `BirdCount.Today()` method to return how many birds visited your garden today. The bird counts are ordered by day, with the first element being the count of the oldest day, and the last element being today's count.

```csharp
int[] birdsPerDay = { 2, 5, 0, 7, 4, 1 };
var birdCount = new BirdCount(birdsPerDay);
birdCount.Today();
// => 1
```
<details>
  <summary>Helps</summary>
  <ul>
<li>Remember that the counts are ordered by day from oldest to most recent, with the last element representing today.</li>  
<li>Accessing the last element can be done either by using its (fixed) index (remember to start counting from zero) or by calculating its index using the <a href="https://learn.microsoft.com/en-us/dotnet/api/system.array.length?view=net-8.0">array's size</a>/li></ul>
</details>

## 3. Increment today's count

Implement the `BirdCount.IncrementTodaysCount()` method to increment today's count:

```csharp
int[] birdsPerDay = { 2, 5, 0, 7, 4, 1 };
var birdCount = new BirdCount(birdsPerDay);
birdCount.IncrementTodaysCount();
birdCount.Today();
// => 2
```
<details>
  <summary>Helps</summary>
  <ul>
<li>Remember that the counts are ordered by day from oldest to most recent, with the last element representing today.</li>  
<li>You can use the <a href="https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/proposals/csharp-8.0/ranges#systemindex">Range</a>  to solve this exercise./li></ul>
</details>


## 4. Check if there was a day with no visiting birds

Implement the `BirdCount.HasDayWithoutBirds()` method that returns `true` if there was a day at which zero birds visited the garden; otherwise, return `false`:

```csharp
int[] birdsPerDay = { 2, 5, 0, 7, 4, 1 };
var birdCount = new BirdCount(birdsPerDay);
birdCount.HasDayWithoutBirds();
// => true
```
<details>
  <summary>Helps</summary>
  <ul> 
<li>If you have done it with ^ you only have to add after the array/li></ul>
</details>

<details>
  <summary>Helps Refactor</summary>
  <ul>
<li>You can use <a href="https://learn.microsoft.com/es-es/dotnet/api/system.array.indexof?view=net-8.0">Array.IndexOf</a>.</li>  
</ul>
</details>

## 5. Calculate the number of visiting birds for the first number of days

Implement the `BirdCount.CountForFirstDays()` method that returns the number of birds that have visited your garden from the start of the week, but limit the count to the specified number of days from the start of the week.

```csharp
int[] birdsPerDay = { 2, 5, 0, 7, 4, 1 };
var birdCount = new BirdCount(birdsPerDay);
birdCount.CountForFirstDays(4);
// => 14
```

<details>
  <summary>Helps</summary>
  <ul> 
<li>A variable can be used to hold the count for the number of visiting birds.</li>
<li>The array can be iterated over using a <a href="https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/statements/iteration-statements">for loop </a></li>
<li>The variable can be updated inside the loop.</li>
<li>Remember: arrays are indexed from `0`.</li>
</ul>
</details>

<details>
  <summary>Helps Refactor</summary>
  <ul>
<li>You can use <a href="https://learn.microsoft.com/es-es/dotnet/api/system.math.min?view=net-8.0">Math.Min</a> and <a href="https://learn.microsoft.com/es-es/dotnet/api/system.linq.enumerable.sum?view=net-8.0">Sum</a></li>  
</ul>
</details>

## 6. Calculate the number of busy days

Some days are busier that others. A busy day is one where five or more birds have visited your garden.
Implement the `BirdCount.BusyDays()` method to return the number of busy days:

```csharp
int[] birdsPerDay = { 2, 5, 0, 7, 4, 1 };
var birdCount = new BirdCount(birdsPerDay);
birdCount.BusyDays();
// => 2
```

<details>
  <summary>Helps</summary>
  <ul> 
<li>A variable can be used to hold the number of busy days.</li>
<li>The array can be iterated over using a <a href="https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/statements/iteration-statements">for loop </a></li>
<li>The variable can be updated inside the loop.</li>
<li>A <a href="https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/statements/selection-statements">conditional statement</a> can be used inside the loop.</li>
</ul>
</details>

<details>
  <summary>Helps Refactor</summary>
  <ul>
<li>You can use <a href="https://learn.microsoft.com/es-es/dotnet/api/system.array.findall?view=net-8.0">Array.FindAll</a></li>  
</ul>
</details>

## 7. Refactor the code
Now that you have the exercises done, refactor the code with other alternatives within the c# language.

You can find help in the Helps Refacto section, after Helps.


## Source

### Created by

- @ErikSchierboom

### Contributed to by

- @yzAlvin