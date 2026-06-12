---
title: "Weirdest bugs you have fixed?"
date: 2010-08-02
forum: The Cafe
---

### Post by Zorgoth on 2010-08-02
Today I spent a large amount of time wrestling with some Matlab code that worked only when debugging (which makes it awfully hard to track down the bug...).  There were all kinds of files being opened and closed and opportunities for matlab to do some kind of unsafe multithreading, but no, there did not lie the problem.  After about 2 and a half hours it was discovered that apparently 

x=[a,d*ceil(b)];

can be different than

c=ceil(b);
x=[a,d*c];

when running normally, but is the same when running with a breakpoint somewhere (which is very odd since this is an interpreted language).

Floating point errors never cease to amaze me.

So what is the strangest bug you have ever found?

---

