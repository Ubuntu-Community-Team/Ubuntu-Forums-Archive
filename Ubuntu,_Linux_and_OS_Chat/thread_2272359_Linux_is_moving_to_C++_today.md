---
title: "Linux is moving to C++ today?"
date: 2015-04-06
forum: Ubuntu, Linux and OS Chat
---

### Post by flaymond on 2015-04-06
Hello folks of the great Ubuntu forums. While browsing Internet and searching for random stuff about Linux, I found this article. [http://petereisentraut.blogspot.com/2013/05/moving-to-c.html](http://petereisentraut.blogspot.com/2013/05/moving-to-c.html).

I kinda shocked even the gcc compiler is moving to use (already did) C++ as the implementation language. [https://gcc.gnu.org/gcc-4.8/changes.html](https://gcc.gnu.org/gcc-4.8/changes.html)

A lot of GUI's today that made in GTK (C) mostly are moving toward to Qt(C++). (I know this issue is about Gnome 3  look and Qt GPL license, not about the language, but it still impact the ANSI C or Standard C).

From first time I'm using Linux, I attracted to ANSI C because it's somehow is the standard identity for Unix-like system. In your opinion, will C still remain as the standard programming language for Linux?

Thanks for opinions and knowledges you shared. :KS

---

### Post by Skaperen on 2015-04-06
just wait for it to move to Python

---

### Post by Skaperen on 2015-04-06
i can hack C++, too, so i'm not worried.  just glad they didn't move to C# or Java.

---

### Post by ian-weisser on 2015-04-06
Lots of different languages want to be the Flavor Of The Week.
Today it's QML/C++
Last year it was Go
Year before that it was Python
Year before that it was Vala
Next year it will be something different...or something recycled.

Originally, C was a sensible choice of language for the source code of the stdlibs.
There is no particular reason C _must_ remain the language for that source code.
There is also no compelling reason at this time to change/rewrite that source to a different language.

---

### Post by Elfy on 2015-04-06
When you found this article - did you then go looking for up to date information on it ? 

It might possibly have been mentioned here 2 years ago ...

*Thread moved to **Ubuntu, Linux and OS Chat**.*

---

### Post by alex361 on 2015-04-06
rumors mate most information out there are inaccurate i cant see something like that to happen anytime soon

---

### Post by Icarus315 on 2015-04-09
The presupposition that "Linux" is moving to C++ is false.  "Linux" is a kernel and is written in C and is going to stay that way.  C is "portable assembly language" and matches the domain of low level systems implementation very well.  It would be fool-hardy to implement the Linux kernel in C++.  Now, GCC - the compiler, as stated in your own links is now implemented in C++.  So what.  The compiler is a program that takes source code and produces object code which is linked into executables.  The source code, and resulting object code, is written in any language that GCC supports.  GCC, the program, that is doing the compilation is written in C++.  NOT the source code and object code it takes as input and produces resulting output from.

---

### Post by flaymond on 2015-04-09
I hope the Linux will stay in C though, I want to learn the kernel before it use other approach...thanks for the opinions and information you share. :D

---

### Post by Icarus315 on 2015-04-09
Linus Torvalds, the original author and benevolent dictator for life of Linux, had: [This](http://lwn.net/Articles/249460/) to say about the subject of C++.  C gets a mention for low level systems but mainly the post is talking about another project Linus Torvalds wrote called "git" and why it is not written in C++.  When you are working at low levels of the machine, close to the hardware, C really is one of the best languages to use.  C, by its design, mirrors solutions that match very well to the problems at that level.  If you used a higher level language like C++ then the solutions that language provides do not mirror as well the problems you are facing.  You do things differently in different languages and some languages are better at certain things than other languages.  If that wasn't true then there would be just a single computer language that was used for everything.

---

