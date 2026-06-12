---
title: "Fortran or Pascal -- Anyone use these?"
date: 2009-07-07
forum: The Cafe
---

### Post by kevdog on 2009-07-07
Does anyone still program in Fortran or Pascal.  These in addition to qbasic were the first languages I learned.  A dinosaur I know!

---

### Post by wojox on 2009-07-07
I have a buddy who's an engineer and he uses Fortran all the time.
I prefer OOP. When I start a fire I use a lighter over rubbing two sticks together. :p

---

### Post by cmay on 2009-07-07
yes there is. here is a link to someone who wants tohire a pascal programmer. 
[http://www.itjobswatch.co.uk/jobs/uk/pascal.do](http://www.itjobswatch.co.uk/jobs/uk/pascal.do)

the most downloaded  freeware application for windows was at a time devcpp that is coded in borlands delfhi pascal but its not developed anymore. and delfhi ius discontinued as far as i know. 

i started with pascal as the first language i could relate to. i did learn some  of it then i got sick and was in hospital for a long time before i got out and then i did not pick up programming before two years after i think it was. 

i still think hogh of pascal even that i forgot all about it. (it is turbo pascal 7.0 i am thinking about when i hear the word  pascal)

---

### Post by Pogeymanz on 2009-07-07
I know a lot of physicists and engineers that use Fortran. I'm a C++ guy, myself.

---

### Post by Daisuke_Aramaki on 2009-07-07
Fortran is still the predominant programming language that i use. Primarily use it to develop and simulate mathematical models.

---

### Post by kevdog on 2009-07-07
Why Fortran and not a more modern language?  What scientific advantages does it provide in the scientific arena?

---

### Post by 4th guy on 2009-07-08
Some local schools are still teaching Pascal.

---

### Post by Lateforgym on 2009-07-08
I know that Fortan is still out there at some major blue chip companies, but its mostly on legacy projects or research stuff.

You programmers have it tough. As soon as one language is the higher paying one, all the boneheads jump on it, then within a few years the market is saturated. Repeat process......

---

### Post by Gizenshya on 2009-07-08
> **kevdog said:**
> Why Fortran and not a more modern language?  What scientific advantages does it provide in the scientific arena?

Why not?  The professors have been using it for ages, and they would rather not re-invent the wheel every couple years with new programming languages that do the exact same thing as the ones before it.

It does everything they need it to... albeit maybe not as efficiently.  Unless it requires weeks of rented super-computer time, I don't see efficiency being a problem.

---

### Post by Simian Man on 2009-07-08
> **kevdog said:**
> Why Fortran and not a more modern language?  What scientific advantages does it provide in the scientific arena?

Well it has one major advantage over C, no pointers.  Pointers kill the compilers ability to optimize code because it can never assume that a value won't be changed by another pointer.

Most languages other than Fortran and C focus on delivering higher level constructs that aren't needed for scientific programming and just add overhead.

So Fortran really is a good language for scietific computing, it's not *entirely* because old guys won't give it up.

---

### Post by HavocXphere on 2009-07-08
Pascal probably not. Delphi does seem to be used by some businesses & schools though.

---

### Post by tjoff on 2009-07-08
I use Fortran in my daily work as a mechanical engineering Ph.D. candidate.
When it comes to high performance computing, Fortran and c (c++ is on its way) are still most widely used. I see several reasons for this.

1. Legacy code. Many software projects are developed and maintained over decades. Fortran has been around for 50+ years, and many existing codes and libraries are thouroughly validated and tested, which is extremely important. 
2. Parallization. When coding for parallel architectures, there are two main de facto standards, OpenMP and MPI. Presently these are only implemented natively under Fortran and C.
3. Compilers. High performace computing depends highly on compiler optimization of the runtime of the executable. The more high-level a language gets, the more difficult/impossible it gets to have the same level of compiler optimization. Optimizing compilers like for-loops, they don't like complicated class hierarchies. 

Lastly you should use the tool that fits the task. 
For number crunching Fortran is a excellent tool. 
I would never attempt to do serious GUI programming in Fortran, just as I would never attempt to do number crunching with something like Java.

---

### Post by kevdog on 2009-07-08
How do pointer prevent compiler optimization?  Pointers have been used in C for as long as I can remember.  In fact I can't really fathom doing complex programming without pointers.  Maybe thats an indication of how bad of programmer I am.

---

### Post by Gilabuugs on 2009-07-08
All the physics professors I know use fortran and a bunch of the engineers too.

---

### Post by tjoff on 2009-07-08
> **kevdog said:**
> How do pointer prevent compiler optimization?  

[http://en.wikipedia.org/wiki/Aliasing_(computing)#Conflicts_with_optimization](http://en.wikipedia.org/wiki/Aliasing_(computing)#Conflicts_with_optimization)

---

