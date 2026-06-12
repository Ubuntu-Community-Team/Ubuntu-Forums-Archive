---
title: "beginning programming"
date: 2009-07-30
forum: The Cafe
---

### Post by nathang1392 on 2009-07-30
im interested in beginning to learn how to program under ubuntu. im not completely sure on what language i want to use, most likely c++ or python. i was wondering if anyone knew of any books that were specific to programming in ubuntu that i could download for free.

---

### Post by Delever on 2009-07-30
> **nathang1392 said:**
> im interested in beginning to learn how to program under ubuntu. im not completely sure on what language i want to use, most likely c++ or python. i was wondering if anyone knew of any books that were specific to programming in ubuntu that i could download for free.

First of all, there is [Programming Talk]("http://ubuntuforums.org/forumdisplay.php?f=39") subforum.

It depends how much you already know. Most of the stuff is the same, however deployment is very different.

---

### Post by nathang1392 on 2009-07-30
well i know some basic programming concepts that i learned in a class at school, but these involved neither popular languages or ubuntu.

---

### Post by Grant A. on 2009-07-30
C++ is a bloated monster, and inexperienced coding in it often results in spaghetti code. The founder of the Linux kernel, Linus Torvalds, was very vocal about his disgust of it [here]("http://lwn.net/Articles/249460/").

The best language above all for a beginner is Python. The best book, imho, to learn it is [Python Programming for the Absolute Beginner by Michael Dawson.]("http://www.amazon.com/Python-Programming-Absolute-Beginner-Michael/dp/1598631128/ref=sr_1_1?ie=UTF8&s=books&qid=1248988895&sr=8-1").

Please note that the book deals with Python 2.6, but it can be easily adapted to Python 3.0. Just make these changes:

**2.6**: print " "
**3**: print(" ")

**2.6**: raw_input(" ")
**3**: input(" ")

There are more changes, but you can find them on the Python website if you need to know them. Good luck!

---

### Post by Delever on 2009-07-30
Search for tutorials. Follow them. If you don't know something, search. Imagine that there are thousands of other people learning programming and posting in various forums. Therefore, for almost any problem you encounter there is post in some forum with answer. Learn to use google to get those answers.

Also, I have sent you PM on how to compile simple programs in different languages, so you can overview all of them.

Good luck.

---

### Post by samalex on 2009-07-30
Hi,

I recommend either Qt or Mono, though by saying the latter I've probably sparked a flame war (sorry if so).

Qt was bought by Nokia not long ago from TrollTech (or did they buy TrollTech, can't remember).  Qt Creator is good and very intuitive to help create simple or complex Apps.  

For the same reasons I also suggest Mono because MonoDevelop is solid and works great.

Qt is more on the FOSS side so it's more standard, but Mono uses C# which is a Microsoft creation.  Another reason I suggest Mono is because of the huge resources out there for C#, which most translate well into Mono from the Microsoft world.

And also both frameworks are cross platform, so code you write on one can be compiled on Linux, OSX, and Windows, which is always nice :)

Again, others might not agree with my suggestion, but it's just my opinion.  

Sam

---

### Post by starcannon on 2009-07-30
> **nathang1392 said:**
> im interested in beginning to learn how to program under ubuntu. im not completely sure on what language i want to use, most likely c++ or python. i was wondering if anyone knew of any books that were specific to programming in ubuntu that i could download for free.


All the guru's I have talked to say, "start with C". So, I of course started with python lol.

Choose one and stick with it till you "get it". The reasoning for starting with C has been explained as "if you know C, then everything else will just make sense".

GL and HF

---

### Post by Sxeptomaniac on 2009-07-30
There are some rather nice online resources for Ruby.  You may or may not want a book to get into the deeper stuff later, if you decide to go this route, but they can be a good start for deciding if Ruby's something you want to get into.

Try Ruby in your browser (the tutorial is a bit odd, as it's by the same person as the next link):
[http://tryruby.hobix.com/](http://tryruby.hobix.com/)

"Why's Poignant Guide to Ruby" (possibly the strangest programming book currently in existence):
[http://poignantguide.net/ruby/](http://poignantguide.net/ruby/)

"Programming Ruby" (a more traditional free book on programming in Ruby):
[http://www.rubycentral.com/book/](http://www.rubycentral.com/book/)

---

### Post by Delever on 2009-07-30
To the OP: in the ocean of programming languages, stick with first one that works for you.

However, let me describe learning required shortly:

**Python**

When you start with command line, you need to know as much as you need to do. If you want to use functions, you only need to learn them when you need to use them. Same with other things.

When you want to do more (for example, making program with GTK interface), required knowledge increases, and tutorials require that you know at least basics of objective oriented (OO) programming.

How much you can do? Adjusting volume for audio in real time - no, python is too slow (you would use some C library to do that). Creating simple game, a program with buttons, doing that easily - yes. Also, python is easy to read, however, it has very powerful language features.

Portability: can run on all common platforms, provided that libraries you use can.

**C**

Again immediate results when you start with command line. However, every thing you do requires "intimate" instructions for CPU. The set of possible things you can do is small and easily learnable.

When you want to do more, you have to get clever. For example, Linux kernel is written with C, but that C is written in clever way to simulate objects with functions (which C lacks). They call it "fake OO".

How much you can do? Well, OS kernel - duh :). Must be clever, have lots of time to write redundant things. It is as fast as it can get.

Portability: well, since you can write OS in it, it can work even on that.

**C++**

It is extended C. But it is recommended to start learning C++ itself, not C. All C features are accessible from C, but C++ has bigger standard library, which should be used instead. When you start, you get immediate results but write more weird (at first) things. Also, to use standard library, you must learn OO programming very soon.

When you want to do more and have learned standard library and OO, you can do anything C can do but easier (well, maybe not writing kernel :)). However, you reach this point much more slowly, than, say, using Python.

How much you can do? Adjusting volume for realtime audio - of course. It is as fast as it gets, but easy enough WHEN learned. Very common use for high-performance applications like games.

Portability: if you select libraries you use carefully, it is fully portable, however, has some pains.

**C# or Java**
When you start, you write more "weird" things at first than with C++, C or python. Everything must be object oriented (OO) in these languages, therefore you write your functions inside objects. Very portable standart libraries (without interface stuff), but they also require OO knowledge.

When you want to do more these languages help a lot. Compiler for these languages check great deal of a program at compile time (more than C/C++/Python), so only nastier errors on runtime. Loved by business.

How much you can do? Any bigger toolkit has C# or Java interfaces, so you can use many libraries to do different things. Huge standard library which abstracts differences between platforms. They are fast languages if you are clever. Adjusting volume of real-time audio? Well, yeah, but it will consume lots of CPU, may skip, and you would use other library for that.

Portability: very little work to make program portable - simple ones run without modifications and with no recompiling.

**Other**

I have little knowledge about other languages, but:

Ruby - somewhat like python, claimed to be even easier
Pascal - nicer but more verbose C

---

### Post by nathang1392 on 2009-07-30
im thinking of using python since so many people recommended it. can anyone advise a book that is good for someone just starting out, free if possible.

---

### Post by Grant A. on 2009-07-30
> **nathang1392 said:**
> im thinking of using python since so many people recommended it. can anyone advise a book that is good for someone just starting out, free if possible.

I already said where.

It's only $20 USD. That's **very** cheap. Anything free you will find will assume that you already know another language, such as the Python tutorial on the Python website.

The book I suggested doesn't even require that you know how to program. It spells it all out for you, and uses real-world analogies to explain some concepts.

> **Grant A. said:**
> 
The best language above all for a beginner is Python. The best book, imho, to learn it is [Python Programming for the Absolute Beginner by Michael Dawson.]("http://www.amazon.com/Python-Programming-Absolute-Beginner-Michael/dp/1598631128/ref=sr_1_1?ie=UTF8&s=books&qid=1248988895&sr=8-1").

---

### Post by snova on 2009-07-30
> **nathang1392 said:**
> im thinking of using python since so many people recommended it. can anyone advise a book that is good for someone just starting out, free if possible.

A small suggestion: [Think Python]("http://www.greenteapress.com/thinkpython/thinkpython.html")

There are many, a quick [search]("http://www.google.com/search?q=python+tutorial") turns up a few.

---

### Post by Granito_man on 2009-07-30
There's a "Dive into Python" at repo's.

---

### Post by mynameinc on 2009-07-30
I started with Python.  Very good.

Also,
**[SIZE="7"]EMACS RULES VI DROOLS![/SIZE]**

Seriously, emacs is better for a beginner...

and everyone else! :)

---

### Post by MaxIBoy on 2009-07-30
+1 for Python. I've learned Python, C++, C, and BASH (in that order,) and I still prefer Python. It's simple, it's elegant, and you have vast libraries at your disposal to make common tasks easier. I find Python code, in its final form on the screen, is the closest to the way I think the program through when I'm planning how it will work. 

The problem with Python is performance, although you can easily integrate C or C++ components with it. Keep in mind that 95% of the time will be spent on 5% of the lines of code, which means that those few critical lines can be written in C, giving good performance without compromising the readability and convenience Python gives you for the rest of the code.

[This essay](http://www.linuxjournal.com/article/3882) by Eric S. Raymond is close to how I feel about it (minus the part where he talks about old languages like FORTRAN: That was all before my time.)

---

