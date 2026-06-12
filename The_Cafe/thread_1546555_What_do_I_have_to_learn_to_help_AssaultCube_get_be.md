---
title: "What do I have to learn to help AssaultCube get better?"
date: 2010-08-05
forum: The Cafe
---

### Post by TheNerdAL on 2010-08-05
So me and my friend want to help the open source community by trying to improve the open source game called AssaultCube which is for Mac, Windows and Linux. What would we need to learn to improve it? And how would we do it? Thanks!

---

### Post by Tahakki on 2010-08-05
Learn C++ and OpenGL would be a good start.

---

### Post by TheNerdAL on 2010-08-05
> **Tahakki said:**
> Learn C++ and OpenGL would be a good start.

Got it. I shall get some books about that or is there a place where I can learn it?

---

### Post by forrestcupp on 2010-08-05
Just do a google search for C++ tutorials and OpenGL tutorials.  There are tons of them out there that are helpful.

Just know that you are in for a long haul, especially if you have no programming background.  Don't think that you will actually be working on AssaultCube any time soon, or even anything remotely that complicated.  You're going to have to take about a million baby steps before you're ready for that.

But you can do it if you stick to it.

---

### Post by ve4cib on 2010-08-05
Do you have any programming experience already?  If so, what languages have you used?

Learning the languages and libraries is just part of what you need.  Learning about algorithms is another major part of being a good programmer and often makes the difference between contributing "code" and "good code."  Learning how a computer "thinks" and being able to break complex tasks into small, concise operations that a computer can do quickly is ultimately what a programmer does.  Know how data flows from one place to another is very important (especially in games where operations are often done in parallel with each other; you can start task A and B at the same time, but you might not be able to start task C until A and B are half-finished, and you might even need the results from C before B can finish).

I can't think of any good places to learn about algorithms, short of school.  Most textbooks/websites and tutorials will have some basic examples, and good ones will usually go into more detail.

---

### Post by TheNerdAL on 2010-08-05
> **ve4cib said:**
> Do you have any programming experience already?  If so, what languages have you used?

Learning the languages and libraries is just part of what you need.  Learning about algorithms is another major part of being a good programmer and often makes the difference between contributing "code" and "good code."  Learning how a computer "thinks" and being able to break complex tasks into small, concise operations that a computer can do quickly is ultimately what a programmer does.  Know how data flows from one place to another is very important (especially in games where operations are often done in parallel with each other; you can start task A and B at the same time, but you might not be able to start task C until A and B are half-finished, and you might even need the results from C before B can finish).

I can't think of any good places to learn about algorithms, short of school.  Most textbooks/websites and tutorials will have some basic examples, and good ones will usually go into more detail.

I have no experience. ):

---

### Post by Tahakki on 2010-08-05
I wouldn't worry about algorithms just yet. How about learning Python and GTK, then possibly GStreamer? These are all far easier than C++/OpenGL, and actually can be used very easily to contribute to Ubuntu itself.

[http://diveintopython.org/toc/index.html](http://diveintopython.org/toc/index.html)

---

### Post by ve4cib on 2010-08-05
> **TheNerdAL said:**
> I have no experience. ):

If you've got no experience then definitely start off by learning the languages and libraries.  Algorithms are the last thing to learn; if you can't write code at all then spending hours studying algorithms will only waste your time and frustrate you.

This URL is a must-have bookmark if you do any C++ coding (and even some C).  It's *the* reference for the standard libraries.

[http://www.cplusplus.com/reference/](http://www.cplusplus.com/reference/)

There are also some tutorials and forums on that website that might help you out getting started.  In terms of some packages to install, you'll want G++ for sure (that's the GNU C++ Compiler).  Any standard text-editor (Geany, Gedit, Kate, etc...) will work fine for writing code, and then you compile using the terminal.

```
$ sudo apt-get install g++
```

Finally, if you want to be really ambitious, you can get the source code for AssaultCube and take a look at it.

```
$ apt-get source assaultcube
```

If you're new to the world of code a lot of it will probably no sense at all, but it'll give you an idea of how the files and folders are structured.  You can even try just checking out the source and compiling it to see if you can get that to work.

---

