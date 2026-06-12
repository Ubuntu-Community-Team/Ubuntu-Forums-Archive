---
title: "[SOLVED] What compiler uses Apple"
date: 2008-10-24
forum: The Cafe
---

### Post by cl333r on 2008-10-24
Hi,
I was wondering what compiler uses Apple for their C/C++ apps. I googled but couldn't find any answer.

---

### Post by LaRoza on 2008-10-24
[http://developer.apple.com/tools/xcode/](http://developer.apple.com/tools/xcode/)

([http://laroza77.wikidot.com/c](http://laroza77.wikidot.com/c))

---

### Post by jespdj on 2008-10-24
As far as I know, Mac OS X and most applications for that OS are not written in C or C++, but in [Objective-C](http://en.wikipedia.org/wiki/Objective-C), which is a programming language that looks like C but has object oriented capabilities added.

---

### Post by LaRoza on 2008-10-24
> **jespdj said:**
> As far as I know, Mac OS X and most applications for that OS are not written in C or C++, but in [Objective-C](http://en.wikipedia.org/wiki/Objective-C), which is a programming language that looks like C but has object oriented capabilities added.

True, but not relevant.

The OP asked about two languages, not that one. Objective-C is also a strict super set of C, so valid C code is valid Objective-C code.

---

### Post by joninkrakow on 2008-10-24
> **cl333r said:**
> Hi,
I was wondering what compiler uses Apple for their C/C++ apps. I googled but couldn't find any answer.

Well, I've compiled a few X11 and commandline apps in OSX, and had to install X-tools to do so, but compiling used GCC 4.0.something when I did it. I have heard that gcc is also used for compiling Quartz apps, but I can't speak authoritatively on that. I only know that gcc is used for X11 and commandline apps. 

-Jon

---

### Post by cl333r on 2008-10-24
From the LaRoza's link:
> ...and the powerful GCC compiler capable of targeting Intel and PowerPC regardless of host platform.
looks like they're using gcc as well. Thanks all, now I got a clue.
offtopic: Micro$oft must also be using gcc internally :)

---

### Post by forrestcupp on 2008-10-24
> **cl333r said:**
> Micro$oft must also be using gcc internally :)

No, they're not, but you can use gcc to compile Windows programs.

---

