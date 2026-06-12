---
title: "Intro to programming: Pascal or Fortran?"
date: 2015-08-10
forum: The Cafe
---

### Post by haplorrhine on 2015-08-10
I guess this could have gone in Programming Talk, but I'm not actually programming anything.

I'm a beginning programmer, and I only know a little Bash and a little C++.  I'm interested in Linux security and web security, possibly learning more LAMP for employability's sake, but I'm a biology-oriented sciences student that excels in mathematics, and so I'm interested in scientific and statistical computing.  My school offers three different intro classes, one each for FORTRAN, BASIC, and PASCAL.  PASCAL seems to be recommended, but FORTRAN looks more appealing since it was made for scientific computing.  Can I have some more details about each?

---

### Post by buzzingrobot on 2015-08-10
Pascal was created as a teaching language, while Fortran was not. That may or may not mean much.  Wouldn't hurt to read a book or two about each and see which one feels like a better fit for you, if you have the choice of which language to use.  Remember, though, that algorithms are algorithms, independent of the language used to express them.  Ideally, you want a language that makes it easiest for you to express your ideas.

---

### Post by haplorrhine on 2015-08-10
I'm reading an interesting comparison of Fortran with C/C++.  [https://www.physicsforums.com/threads/why-is-fortran-so-fast.169974/](https://www.physicsforums.com/threads/why-is-fortran-so-fast.169974/)
It seems that Fortran does but a subset of what C++ does.  While Fortran is sort of pre-optimized, a skilled programmer can optimize C code even more because it's lower-level and closer to machine code.  In that case, maybe Pascal will teach me to optimize, and then I can just optimize my C.

May I ask why Pascal is superior as a teaching language?  I have done some programming myself, and i know the basic terminology.

---

### Post by montag dp on 2015-08-10
I have a good deal of experience with Fortran.  It is definitely easier to learn than C or C++, and it is nice for scientific computing because it has lots of intrinsic math functions and built-in support for multi-dimensional arrays (which are much more flexible and powerful than regular C/C++ pointer arrays), complex numbers, and "namelist" input which makes it really simple to read inputs from a text file with a specific format.  Hopefully the class teaches you the "new" Fortran 90 standard, and not the old Fortran 77 standard which is really outdated but still used in a lot of legacy codes.

I think you are right that the functionality of Fortran could be seen as a subset of what can be done in C/C++, if you recognize that many of the useful types (like arrays) aren't available in C/C++ unless you write your own class.  It does lack many functions of C and C++; most notably the fact that it is not object-oriented and you can't really write a GUI in Fortran.  (Actually, I've read that the latest standard does define an object oriented syntax, but I've never seen it used and also don't know if any compilers support it yet.)

I would definitely say it is a good first programming language for scientists and engineers. I don't know much about Pascal, though.

---

### Post by Bakerconspiracy on 2015-08-16
It is interesting that they are offering these languages as an introduction to programming. Fortran was around "pre-stack" meaning there was no function calling at one point of time (all the code was substituted in place) - everything including the variables were static. FORTRAN might be good to write something that executes extremely fast. The movement has been toward Matlab and R nowadays for big data. I've seen a ton of python floating around labs too.

My two cents is that if these classes are being offered by the biology / physics dept as intros, take a look at what the computer science / math dept has as an analog.

---

### Post by Wadim_Korneev on 2015-08-31
The fact that Fortran has been used for decades means there are huge libraries of Fortran code that would take years of recoding and debugging to convert to other languages. Another factor is that on some super-computers, more work has been done on adding extensions and optimizations to Fortran compilers on those computers versus other languages for those computers (a choice made because of legacy of Fortran).

---

### Post by sab7 on 2015-09-02
In my opinion, Pascal has many advantages over Fortran.
[LIST]
[*]Object-oriented Pascal programming is possible,
[*]You can use OpenGL, Vulkan in Pascal,
[*]Rapid Application Development (RADs) such as Lazarus,
[*]Smartphone cross-compilation.
[/LIST]

---

