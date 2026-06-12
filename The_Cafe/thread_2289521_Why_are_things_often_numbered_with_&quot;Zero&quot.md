---
title: "Why are things often numbered with &quot;Zero&quot; first?"
date: 2015-08-04
forum: The Cafe
---

### Post by mikodo on 2015-08-04
I guess it is a math/computer thing. I have never studied either in secondary school.

Examples.

I have a quad-core CPU.

Numbers in xfce4-sensors are:

Core 0
Core 1
Core 2
Core 3

My hard drive, if I remember properly, always list the first partition as Zero.

I'm sure I've seen other examples but, you get the idea.

Why is this?  :)

---

### Post by QIII on 2015-08-04
Because we Math/computer geeks like to make things confusing so we look smart.

The reason is the notion of an index.  Indexes start at zero.  When you "index" something, you are making sure your measurement or what have you starts at 0.

If you want to read the first line in a file, you have to start at the 0th position to read through and capture the entire line.

You start at the start or you miss the first thing.

---

### Post by monkeybrain20122 on 2015-08-04
Because the set of natural numbers starts with 0 mathematically and "nothing" seems more natural as a start than "one" philosophically. :)

---

### Post by mikodo on 2015-08-04
Thanks folks.

I remember the imbecile grade 9 math teacher we had, early in the year wasting a large part of a class, having each of we students in the class in turn, try to count to ten. Not knowing any better, we all counted I through 10. He gleefully told each one of us we were wrong. (small things amuse small minds). Then, he introduced zero, and let us guess what negative numbers were. We had no idea, what they were of course. 

A few years later, my younger sister was incessantly teased by this guy because she had gone to private school, until grade 12. She had the smarts enough tell our dad. As my sister tells it, dad was out of the house like a shot. The teacher never teased my sister again.  :)

Why, I remember all this now, after 45 years, I'll never know.

---

### Post by tgalati4 on 2015-08-04
A two-digit binary number is used to enumerate the CPU's:

00  Core Number 0
01  Core Number 1
10  Core Number 2
11  Core Number 3

Binary is represented as 2^1+2^0

So

0^1 + 0^0 = 0
0^1 + 2^0 = 1
2^1 + 0^1 = 2
2^1 ^ 2^0 = 3

Such counting schemes start with 0.

---

### Post by mikodo on 2015-08-05
Hey.

Two digit binary counting.

Instead of "ten" digit decimal counting.

You sent me on a journey of internet searches.

Thanks.

---

### Post by Skaperen on 2015-08-05
because geeks just can't stand it when the last number in binary gets wider.

---

### Post by lisati on 2015-08-05
Sometimes it's just easier to start with zero. When you're about to go buying your groceries, you start with nothing in your shopping cart, and the bill grows as the adventure in the supermarket happens.

---

### Post by Bucky Ball on 2015-08-05
If you ask a computer programmer how many kids they have and they say one, you know they have two because programmers count from zero. ;)

---

### Post by mikodo on 2015-08-05
Same for wives/husbands?

---

### Post by Bucky Ball on 2015-08-05
> **mikodo said:**
> Same for wives/husbands?

Yea, I have zero wives/husbands, as in, I am married. :)

---

### Post by QIII on 2015-08-05
So does that explain why Mathematicians who develop software have zero lives?

---

### Post by SantaFe on 2015-08-05
If Geeks love Zero so much, why don't they like to use it in version numbers?  Like I'm on MATE 1.8.2, but the next update is MATE 1.10.  Why isn't the current version 1.082? :D

And yes, I know 8 comes before 10, but I don't know how many people I've ran into that aren't confused by the numbering system. ;)

---

### Post by Bucky Ball on 2015-08-05
> **SantaFe said:**
> If Geeks love Zero so much, why don't they like to use it in version numbers?  Like I'm on MATE 1.8.2, but the next update is MATE 1.10.  Why isn't the current version 1.082? :D

Because that's not how it works. 1.8.2 would actually be 0.7.1 because 1 is a mathematician's 0 (zero is considered a digit?). ;)

When it comes to dates, of course, it is used, as in, for instance, Ubuntu 14.04. 14=2014, 04=April, which would, in actuality, be 0414, meaning April 2014. :-k Must be getting late ... :)

---

### Post by Old_Grey_Wolf on 2015-08-05
Google search "positional notation". There is more meaning to 0 than you may think, and 10 isn't what you may think it is.

I have done programing in binary, octal, and hex over the decades; so. it comes naturally to me. :)

---

### Post by QIII on 2015-08-05
There are 10 types of people in the world:  those who understand binary and those who don't.

---

### Post by PJs Ronin on 2015-08-05
I seem to recall a TV program years ago that (in part) dealt with numbers and numbering.   From what I remember, the notion of a number, zero or 0, representing a property just like one or two, was not accepted by the ancients until it was developed in India (Google has a lot on this too).   Until that time, zero was at best just a place holder.   Interestingly, before zero was formally identified, Indian scholars also proposed a numbering system based on short and long dashes... binary anyone?

I've also heard a quotation along the lines "Math, the only true science.   Everything else is finger painting."

---

### Post by montag dp on 2015-08-06
Actually, in Fortran indices start with 1 instead of 0.  I don't know if there are any other programming languages that do it that way.  Well, actually Matlab does too, if you count that as a programming language, I think because it borrows its array library from Fortran.  IMO, starting with 1 is less confusing, because then the current index in the array is also the same as the number of elements you've counted.

---

### Post by mystics on 2015-08-07
> **montag dp said:**
> Actually, in Fortran indices start with 1 instead of 0.  I don't know if there are any other programming languages that do it that way.  Well, actually Matlab does too, if you count that as a programming language, I think because it borrows its array library from Fortran.

I've heard that Pascal also starts at 1. I can't confirm it personally, though, as I've never used the language.

> IMO, starting with 1 is less confusing, because then the current index in the array is also the same as the number of elements you've counted.

For me, I've been so heavily trained in programming to start counting at zero that it just comes naturally now. I have made arrays and vectors that started counting at 1 for whatever reason, and I always have to stop myself from starting the counting at 0 like I normally do.

---

### Post by portalhavoc on 2015-08-07
**Zero** divided by **Zero?** :P

---

### Post by pissedoffdude on 2015-08-08
Yeah, that was pretty weird in college too.  Classes in Philosophy/Logic always included 0 as a natural number and classes in the Math department always began the natural nums with 0.  From what I saw in logic there was a set of basic axions, where 0 was a natural number and by applying another axiom to success 0 you can generate s(0)=1, s(s(0))=2, and so on, and basically from these base set of axioms you can generate the set of natural numbers, rules of logic, and basically all the language of math.  Whereas math classes were like it doesn't matter, time to prove stuff.  Maybe it's because compy-sci people were more attuned to logic, so they just followed that standard?

---

### Post by Bucky Ball on 2015-08-08
I always figured that starting with 01 logically meant the very first number should be 00! Those brains, ey? :)

---

### Post by montag dp on 2015-08-09
> **mystics said:**
> For me, I've been so heavily trained in programming to start counting at zero that it just comes naturally now. I have made arrays and vectors that started counting at 1 for whatever reason, and I always have to stop myself from starting the counting at 0 like I normally do.Yeah, it's not a big deal or anything that you can't get used to, but it can be a little confusing at first.  For example, I think the python for loop syntax is a little confusing:

```
for i in range(idx1, idx2):
``` The last value of i will be idx2 - 1, not idx2.  I think this is because loops usually start at 0 in python (due to lists, arrays, etc. starting at 0), in which case idx2 is the number iterations in the loop.  I guess that's really just a python thing, though, and if you're writing a loop in C/C++ it's less confusing because you specifically say whether the last index is included, like this:

```
for ( i = idx1; i < idx2; i++ )
```

tldr: I guess it's not really very confusing, but still a little less intuitive than starting at 1.

---

