---
title: "Question Regarding Python as a Development Language"
date: 2010-07-04
forum: The Cafe
---

### Post by GMU_DodgyHodgy on 2010-07-04
I know there have been arguments about the types of programming languages to use. Most of my experience is in Java/C++ and VB.

However, my son is in 6th grade taking his second computer science class and is learning the fundamentals of programming using Python.  His text book (required summer time course) is actually pretty good. I have been working with him and have been impressed with Python to be honest. Fairly clean, fast and pretty powerful.  

I wouldn't use it to make a server side enterprise application like I would with Java - but it looks like a great desktop development environment and it can bind to Java and C++ libraries.


My son really likes it and is excited learning with it.

Anyone have thoughts?

---

### Post by Bachstelze on 2010-07-04
> **GMU_DodgyHodgy said:**
> 
I wouldn't use it to make a server side enterprise application like I would with Java

Why not?

---

### Post by GMU_DodgyHodgy on 2010-07-04
> **Bachstelze said:**
> Why not?

Not sure - not aware of how to implement it in a server environment - do not know all of its classes like I do for Java.  Maybe I should qualify my statement to say because I am new to Python as a language.

---

### Post by Queue29 on 2010-07-04
> **GMU_DodgyHodgy said:**
>  Fairly clean, fast and pretty powerful.  


Clean and powerful, yes. Fast? Heeiilll no. 

[http://shootout.alioth.debian.org/u32q/benchmark.php?test=all&lang=python3&lang2=javasteady](http://shootout.alioth.debian.org/u32q/benchmark.php?test=all&lang=python3&lang2=javasteady)

Fine for desktop applications? I say yes. Most programs are slowed down by waiting for user input anyway, so the speed of the language (interpreter, in Python's case) doesn't matter. However as a server side language, or for use in any sort of performance application, python does not belong.

---

### Post by mickie.kext on 2010-07-04
> **GMU_DodgyHodgy said:**
> I know there have been arguments about the types of programming languages to use. Most of my experience is in Java/C++ and VB.

However, my son is in 6th grade taking his second computer science class and is learning the fundamentals of programming using Python.  His text book (required summer time course) is actually pretty good. I have been working with him and have been impressed with Python to be honest. Fairly clean, fast and pretty powerful.  

I wouldn't use it to make a server side enterprise application like I would with Java - but it looks like a great desktop development environment and it can bind to Java and C++ libraries.


My son really likes it and is excited learning with it.

Anyone have thoughts?
Python is great for both server and desktop apps (althoug Java is better for server envoirment). For example, Launchpad (Ubuntu's bug tracker) is written in Python. Obviously, lots of desktop software is too. If you want to make server application, you might want to look at this neat [library]("https://storm.canonical.com/") for object-relational mapping. It is like Python equivalent to JBoss Hibernate.

---

### Post by Mr. Picklesworth on 2010-07-04
> **GMU_DodgyHodgy said:**
> ]I wouldn't use it to make a server side enterprise application like I would with Java - but it looks like a great desktop development environment and it can bind to Java and C++ libraries.

You may change your mind yet ;)
[http://www.djangoproject.com/](http://www.djangoproject.com/)

Okay, I suppose a web framework isn't _quite_ the same thing, but it can probably fit a lot of the time and Django is really modular. You can just take it's awesome ORM component, for example, and leave the rest.

I've been using Django for lots of stuff lately and it has been _awesome_!

> **Queue29 said:**
> Clean and powerful, yes. Fast? Heeiilll no. 

[http://shootout.alioth.debian.org/u32q/benchmark.php?test=all&lang=python3&lang2=javasteady](http://shootout.alioth.debian.org/u32q/benchmark.php?test=all&lang=python3&lang2=javasteady)

Fine for desktop applications? I say yes. Most programs are slowed down by waiting for user input anyway, so the speed of the language (interpreter, in Python's case) doesn't matter. However as a server side language, or for use in any sort of performance application, python does not belong.

I agree with you on both points. However, I think it's worth mentioning that a Python app is a lot *easier* to optimize than an app written in C. A Python app could have much better *perceived* performance by the developer bothering to implement stuff like multithreading, with a UI thread detached from everything else. In addition, since the basic types are pretty sophisticated and Python already does a lot of string processing, anything that needs a hash table probably already uses a hash table.
Python makes that kind of stuff really easy so peoples' heads don't explode. The very central, well maintained offline documentation helps a lot, too.


We do have [Vala]("http://live.gnome.org/Vala"), now &#8212; a compiled language with good support in Gnome that is actually nice to use &#8212; so there are a few more ways to obtain [the same level of coding bliss]("http://www.xkcd.com/353/") :)

---

### Post by JDShu on 2010-07-04
> **Queue29 said:**
> Clean and powerful, yes. Fast? Heeiilll no. 


While Python is clearly slower than C, comparing it to Java is much more complicated. The thing about Python is that for speed, you need to implement it so that you take advantage of the native C code. If you do, then it does very well.

---

### Post by igouy on 2010-07-04
> **Queue29 said:**
> Clean and powerful, yes. Fast? Heeiilll no. 

[http://shootout.alioth.debian.org/u32q/benchmark.php?test=all&lang=python3&lang2=javasteady](http://shootout.alioth.debian.org/u32q/benchmark.php?test=all&lang=python3&lang2=javasteady)

Fine for desktop applications? I say yes. Most programs are slowed down by waiting for user input anyway, so the speed of the language (interpreter, in Python's case) doesn't matter. However as a server side language, or for use in any sort of performance application, python does not belong.


The ordinary java -server comparison makes your basic point more effectively - 

[http://shootout.alioth.debian.org/u32q/benchmark.php?test=all&lang=python3&lang2=java](http://shootout.alioth.debian.org/u32q/benchmark.php?test=all&lang=python3&lang2=java)


As for server side languages, couldn't we just as easily say - most programs are slowed down by waiting for I/O, so the speed of the language (interpreter, in Python's case) doesn't matter?

For example - "It may seem paradoxical to use an interpreted language in a high-throughput environment, but we have found that the CPU time is rarely the limiting factor; the expressibility of the language means that most programs are small and spend most of their time in I/O and native run-time code."
[[COLOR="Blue"]Interpreting the Data: Parallel Analysis with Sawzall[/COLOR]]("http://labs.google.com/papers/sawzall.html"), page 27.

---

### Post by igouy on 2010-07-04
> **GMU_DodgyHodgy said:**
> Not sure - not aware of how to implement it in a server environment - do not know all of its classes like I do for Java.  Maybe I should qualify my statement to say because I am new to Python as a language.

Fair enough - you seem to be saying that you don't have the same confidence in your Python knowledge and skills as you do in your Java knowledge and skills, so in practice it would be less risky to do what you know best.

---

### Post by juancarlospaco on 2010-07-04
Make your Python App starting like that, and check the Speed of the App:

```

#!/usr/bin/env python
# -*- coding: utf-8 -*-
# License:      GPL v3
# Dependencies : sudo apt-get install python-psyco
#
try:
    import psyco  # Speed Up if avaliable
    psyco.full()
except ImportError:
    print(" ")
    print(" No PYTHON-PSYCO avaliable!, this application will run slower... ")
    print(" ")
    pass
#
# here continues the code...

```

[LIST]
[*]*Also i already enhaced Ubuntu Software Center speed by modifing the .py files with sudo*
[/LIST][SIZE="1"]
(can be done with Gwibber but the app is bugged anyways)
[/SIZE]

:)

---

### Post by igouy on 2010-07-04
> **juancarlospaco said:**
> Make your Python App starting like that, and check the Speed of the App

[[COLOR="Blue"]Psyco is the past[/COLOR]]("http://shootout.alioth.debian.org/gp4/benchmark.php?test=all&lang=psyco&lang2=python") - [[COLOR="Blue"]PyPy is the future[/COLOR]]("http://shootout.alioth.debian.org/u32/benchmark.php?test=all&lang=pypy&lang2=python").

---

### Post by GMU_DodgyHodgy on 2010-07-04
Thanks everyone for their feedback.  I have been doing the tutorials with my son and have found the language to be very ineresting. It reminds of Java in its younger years and it seems just very accessible.  

I am also more senior in my career and am more in project management and project design and not much day to day coding. 

Playing with it has intrigued me - I am now just doing it for fun and I do like it. 

From what others have posted here - it seems there is a lot more to Python than I originally thought.

I now have a Summer project!!

---

### Post by NightwishFan on 2010-07-04
I watched a video tutorial and learned how to code simple pygtk in 10 minutes. It is a great language. You might want to look at Canonical's "Quickly" too.
[http://en.wikipedia.org/wiki/Quickly_%28software%29](http://en.wikipedia.org/wiki/Quickly_%28software%29)

---

### Post by MaxIBoy on 2010-07-05
Python is an actively-developed and modern, yet still fully matured and fleshed-out programming language. In fact, Python has been around since 1991, making it four years older than Java.

Eric S. Raymond, who is a legendary programming expert (and one of the first people to propose the term "Open Source," incidentally,) recommends Python over Java as a first language:
> 1. Learn how to  program.

This, of course, is the fundamental  hacking skill.  If you don't know any computer languages, I recommend starting with Python.  It is cleanly designed, well documented, and relatively kind to beginners. Despite being a good first language, it is not just a toy; it is very powerful and flexible and well suited for large projects.  I have written a more detailed [evaluation of  Python]("http://www.linuxjournal.com/article.php?sid=3882").  Good [ tutorials]("http://docs.python.org/tut/tut.html") are available at the [Python web site]("http://docs.python.org/tutorial/").


I  used to recommend Java as a good language to learn early, but [this critique]("http://www.stsc.hill.af.mil/CrossTalk/2008/01/0801DewarSchonberg.html") has changed my mind (search for &#8220;The Pitfalls of Java as a First Programming Language&#8221; within it).  A  hacker cannot, as they devastatingly put it &#8220;approach problem-solving like a plumber in a hardware store&#8221;; you have to know what  the components actually *do*.  Now I  think it is probably best to learn C and Lisp first, then Java.
Python was my first language. I now know Lua (also great for a beginner,) Bash, and C with a decent degree of competence, but Python is the language I would choose for a new large-sized project. Lua might be slightly more elegant, but Python has a [massive amount of libraries](http://docs.python.org/library/index.html) (in the standard distribution or available separately) to help you build everything from email clients and web servers to 2D games and media players. It's a good language to start with, and a good useful language to know even if you are already a professional programmer. 


Regarding Python optimization:
[http://www.python.org/doc/essays/list2str.html](http://www.python.org/doc/essays/list2str.html)
It's an essay written by Python's inventor, Guido himself. Although it's a bit out of date in some of the specific details of the example being shown, it does show what mindset you need in order to make your Python code run fast.

---

### Post by smellyman on 2010-07-05
> **GMU_DodgyHodgy said:**
> 

However, my son is in 6th grade taking his second computer science class and is learning the fundamentals of programming using Python.


6th grade learning Python??? I was trying to wrap my head around circling a direct object in a sentence.

time to get out of IT fast.....

---

### Post by GMU_DodgyHodgy on 2010-07-05
> **smellyman said:**
> 6th grade learning Python??? I was trying to wrap my head around circling a direct object in a sentence.

time to get out of IT fast.....

Hah -he goes to a Catholic school that is pretty demanding.  He is just starting to cut his teeth during the Summer so when he goes back in the Fall he can have a leg up in understanding programming principles and focus on the concepts and best practices.  

It keeps him busy and behaving while it's raining or after swim team practice.

Personally, I like Python- learning it now makes me feel like I did when I first used Basic on my Commodore 64 or first took Turbo Pascal in my high school CS class.

---

### Post by MCVenom on 2010-07-05
I learned Visual Basic in fourth (possibly third) grade. Visual Basic 6. I believe VB.NET came out that same year, or a year before :P

Python's my first truly useful language, IMO. :lolflag:

---

### Post by juancarlospaco on 2010-07-05
> **igouy said:**
> [[COLOR="Blue"]Psyco is the past[/COLOR]]("http://shootout.alioth.debian.org/gp4/benchmark.php?test=all&lang=psyco&lang2=python") - [[COLOR="Blue"]PyPy is the future[/COLOR]]("http://shootout.alioth.debian.org/u32/benchmark.php?test=all&lang=pypy&lang2=python").

*The benchmarks are too old [I][SIZE="1"](Python 2.5)[/SIZE]*, the benchmark shows Psyco being faster.
Psyco depends on your configuration to become the fastest, and need perfect coding.[/I]

:s

---

### Post by cprofitt on 2010-07-05
> **GMU_DodgyHodgy said:**
> Hah -he goes to a Catholic school that is pretty demanding.  He is just starting to cut his teeth during the Summer so when he goes back in the Fall he can have a leg up in understanding programming principles and focus on the concepts and best practices.  

It keeps him busy and behaving while it's raining or after swim team practice.

Personally, I like Python- learning it now makes me feel like I did when I first used Basic on my Commodore 64 or first took Turbo Pascal in my high school CS class.


My daughter is just going in to 5th grade and I have been slowly teaching her Python. My son is not yet in 1st grade -- but he has some concepts down -- just have to get him to spell better before he can write code.

---

### Post by NightwishFan on 2010-07-05
Some may find learning code that early odd, but that is the best time to learn. He will grasp it quite swiftly that young, especially if you make it fun. Tell him I wish him good luck! :)

---

### Post by igouy on 2010-07-07
> **juancarlospaco said:**
> *The benchmarks are too old [I][SIZE="1"](Python 2.5)[/SIZE]*, the benchmark shows Psyco being faster.
Psyco depends on your configuration to become the fastest, and need perfect coding.[/I]

:s


"Psyco is a reasonably complete project. I will not continue to develop it beyond making sure it works with future versions of Python. My plans for 2006 are to port the techniques implemented in Psyco to PyPy." [[COLOR="Blue"]Psyco - Future plans[/COLOR]]("http://psyco.sourceforge.net/introduction.html")

Psyco is the past - PyPy is the future.

---

### Post by donkyhotay on 2010-07-07
> **smellyman said:**
> 6th grade learning Python??? I was trying to wrap my head around circling a direct object in a sentence.

time to get out of IT fast.....

Although I didn't understand most of it at the time I was reading/modifying source code when I was in 1st/2nd grade. I had a C64 and by messing around I learned how to read the source code of any program since everything there was scripted in basic. I got pretty good with it for awhile (especially around 6th grade) though of course I've moved on and hardly remember anything from back then. Although I do mess around with other languages from time to time, python is my current language of choice and is what I use in my own [projects](code.google.com/p/tether).

---

### Post by Shining Arcanine on 2010-07-07
> **GMU_DodgyHodgy said:**
> I know there have been arguments about the types of programming languages to use. Most of my experience is in Java/C++ and VB.

However, my son is in 6th grade taking his second computer science class and is learning the fundamentals of programming using Python.  His text book (required summer time course) is actually pretty good. I have been working with him and have been impressed with Python to be honest. Fairly clean, fast and pretty powerful.  

I wouldn't use it to make a server side enterprise application like I would with Java - but it looks like a great desktop development environment and it can bind to Java and C++ libraries.


My son really likes it and is excited learning with it.

Anyone have thoughts?
I heard that some Google employees do their programming in Python, so it should be possible to use it for whatever you want to do..

---

