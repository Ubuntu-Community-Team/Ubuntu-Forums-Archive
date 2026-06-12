---
title: "Easiest to impliment high performance code"
date: 2009-04-10
forum: The Cafe
---

### Post by xir_ on 2009-04-10
Ok so i can 'code' in perl, understand python and modify Fortran but each of these have their drawbacks. I'm about to start a theoretical chemsitry Phd in the summer and i will be writing my own high performance code for the first time.


Nearly all the code in chemistry is fortran 77 and 98, I want to look beyond this and try to create new code using a more modern language. what would you suggest as a good starting point? 

All my work will be done in linux (ubuntu of course) I was thinking of C or C++ with python graphical front ends.

Do any of you guys have some suggestion on which might be the best? Or any scientist out there with their own experiences?


I'm really looking forward to getting my teeth into my first Linux code and hopefully from there i can start to contribute to the overall code base of some open source projects.

---

### Post by wicky_ts on 2009-04-10
It depends on your need. In my case I have to handle hell lot of vectors and matrices and get in to trouble when doing it with C. If you have the same thing better to use C++. It can cope with these things well and have lot of good libraries for that. 
I have no experience with python.

---

### Post by xir_ on 2009-04-10
> **wicky_ts said:**
> It depends on your need. In my case I have to handle hell lot of vectors and matrices and get in to trouble when doing it with C. If you have the same thing better to use C++. It can cope with these things well and have lot of good libraries for that. 
I have no experience with python.

cheers for the reply 


I will be having to do a lot of matrix work as matrix maths is a beautiful way of representing quantum systems. I think the physics dept in my uni does C++ courses so i will probably give learning it a try.

My understanding is that python has a graphical library which makes it easy to create a front ends in GTK.

---

### Post by MaxIBoy on 2009-04-10
Python is amazing, and I love it to death, but it's not a high-performance language. Performance can be improved 20-fold using Psyco (a just-in-time interpreter for Python,) but a compiled language will almost always be faster.

C is faster than C++ by a small margin, but C++ has a lot of features missing in C.

---

### Post by xir_ on 2009-04-10
> **MaxIBoy said:**
> Python is amazing, and I love it to death, but it's not a high-performance language. Performance can be improved 20-fold using Psyco (a just-in-time interpreter for Python,) but a compiled language will almost always be faster.

C is faster than C++ by a small margin, but C++ has a lot of features missing in C.

I was thinking of switching from perl scripting to python because of it graphical abilities, unfortunately again its used more in the scientific community than python for legacy reasons.


Is C++ easier to code in that C, I know that its object orientated, but i'm not sure what that really means, so for the moment its all about the speed of coding and performance.

I take it though that C++ is slightly more feature right than Fortran.


Would there be anything stopping me from codding C++ as close to Fortran 77 style, more so that my supervisors will be able to understand the code?

---

### Post by MaxIBoy on 2009-04-10
Reminds me of the old quote, "A sufficiently determined Real Programmer can write Fortran in any language." 

Idealized: [http://www.pbm.com/~lindahl/real.programmers.html](http://www.pbm.com/~lindahl/real.programmers.html)
Real life: [http://catb.org/jargon/html/R/Real-Programmer.html](http://catb.org/jargon/html/R/Real-Programmer.html)



Write C++ in C++, not Fortran. Also, read this:
[http://www.catb.org/~esr/writings/taoup/html/](http://www.catb.org/~esr/writings/taoup/html/)



Finally in response to your question: [http://en.wikipedia.org/wiki/Object-oriented_programming](http://en.wikipedia.org/wiki/Object-oriented_programming)

---

### Post by happysmileman on 2009-04-10
C++ is basically a superset of C, so any valid C code is also valid C++ code (with very few exceptions). So really there's no reason to use C over C++ IMO, since anything you can do in C can be done the exact same way in C++ if you choose, but not the other way around.

As for using Python front-ends, I don't really see the point, you'll still be using all the same functions and classes, so might as well just do them in whichever language you choose.
There are graphical designers for both GTK and Qt, so you can just design the interface drag and drop if you choose, and then it's probably easier to assign the buttons to the tasks and stuff if you DON'T use a different langauge.

---

### Post by wicky_ts on 2009-04-10
"Write C++ in C++, not Fortran."
++1

This is the most important. do not try to write a fortran program in C++. If you are manupilating matrices and worried about speed, first thing to do is sitdown and think how to avoid as much as possible number crunching operations like inverting a matrix, getting LU decomposition, matrix matrix multiplications, use of full matrices ...etc. These things going to test your cpu power to its maximum edge. If you can avoid these things, even befoure writing the program u are sure it is n^2 times faster, and that is alot.

I am extreamly sure that C++ code is much more easy to understand than a fortran code.

---

