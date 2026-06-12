---
title: "Ideas for C++ &quot;contest&quot;"
date: 2012-02-22
forum: The Cafe
---

### Post by CoffeeRain on 2012-02-22
Hey! Do you have ideas for a sort of contest in C++? My friend started taking C++ and is into it, so I figured we could see who could do something in the least amount of lines or something like that. Do you have any ideas for what we could do or if the least amount of lines is not a good idea? Thanks!

---

### Post by |{urse on 2012-02-22
Definitely least amount of lines :) at least that's awarding elegance and simplicity.

For intermediate entrants some sort of project using a large 4d array with both constants and variables would be challenging and fun. If you wanted to kick things up a notch you could add that the array needs to show correct data both by value and reference and needs to be dynamically allocated AND must pass a memory leak check with valgrind or some similar program.

---

### Post by Simian Man on 2012-02-22
Least number of lines is a terrible goal for any programmer.  Sometimes a more elegant solution is shorter, but more often a shorter program expresses a simpler, but less efficient algorithm.  It would also encourage cryptic, undocumented code in order to reduce length.

A better goal is to see who can solve the problem in the shortest amount of time.  Google "acm programming contest problems" for links to problems used in programming competitions.  These often come with input sets and the correct output.  Sometimes they often include sample solutions.  You can also look at [Project Euler]("http://projecteuler.net/") which is a set of mathematical programming problems.  I don't know how math savvy you and your friends are though.

---

### Post by Tony Flury on 2012-02-22
> **Simian Man said:**
> Least number of lines is a terrible goal for any programmer.  Sometimes a more elegant solution is shorter, but more often a shorter program expresses a simpler, but less efficient algorithm.  It would also encourage cryptic, undocumented code in order to reduce length.

A better goal is to see who can solve the problem in the shortest amount of time.  Google "acm programming contest problems" for links to problems used in programming competitions.  These often come with input sets and the correct output.  Sometimes they often include sample solutions.  You can also look at [Project Euler]("http://projecteuler.net/") which is a set of mathematical programming problems.  I don't know how math savvy you and your friends are though.

COmpletely agree - code line count is an appalling measure of effectiveness. You should be measuring something like : 
[LIST]
[*]Least CPU time to execute against a known input.
[*]Quickest elapsed run time
[*]Least Disk I/O
[*]smallest memory footprint
[/LIST]
All of those are real live issues you will face every day as a developer

---

### Post by JDShu on 2012-02-22
Readability: Give it to a bunch of judges and measure the [WTFs/minute]("http://www.osnews.com/story/19266/WTFs_m"). ;)

---

