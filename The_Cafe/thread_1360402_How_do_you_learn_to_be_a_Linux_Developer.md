---
title: "How do you learn to be a Linux Developer?"
date: 2009-12-20
forum: The Cafe
---

### Post by kevinwmiller on 2009-12-20
I was wondering how you learn to be a Linux Developer? Where do you start, if you want to learn more? Short of purchasing expensive books.

Say if you wanted to get involved in the Linux Open Source community, and someday develop, where would you begin?

I figure this might be a good topic.

---

### Post by &#32 Greg on 2009-12-20
Look at the source code, learn C, bug track for your favourite projects (run dev versions).

---

### Post by kevinwmiller on 2009-12-20
Well, I thought about buying the K&R C book.  Trying to learn programming for the first time.  I am also enrolled in school for a bachelors in IT - Software Architecture, starting in January.

I just have this desire to get started now. lol.  

I think I find myself more and more interested in Linux, and wanting to learn as much as I can about that.

---

### Post by Xbehave on 2009-12-20
I'd go with find an itch and scratch it, assuming you mean linux generally and not just the kernel, just find and itch and start writing a program to solve it. IMHO it's esaier to write a new program (but following standards) than it is to jump in and try and contribute to another projects. The easiest language for simple projects is probably python, but if you are looking to contribute to other projects you will probably need to learn C/C++ as that is what most projects use (firefox,kernel,mplayer,kde,etc).

Disclaimer: I'm not a Linux developer but i have scratched a few itches and will hopefully end up becoming one, but i  have to learn C/C++ to help with the projects I'm interested in.

If you are interested in learning to program 
[http://www.reddit.com/r/carlhprogramming/](http://www.reddit.com/r/carlhprogramming/) may help
I'm following some MIT openCourseware lectures too, but I find that with higher level languages you can do a lot of stuff without an understanding of the theoretical side though (i.e no need to learn the difference between merge sort and selection sort, when you can just call sort and assume the python developers are smart and they are timsort FTW)

---

### Post by kevinwmiller on 2009-12-20
I went to, and bookmarked all of those links.

Thanks for your response, I'm trying to find books and online resources to get started.  I would like to dedicate my free time to learning all of this.

---

### Post by &#32 Greg on 2009-12-20
The K & R is an excellent resource for C.

---

### Post by mdmarmer on 2009-12-21
What's a K & R ??

Mike

OK -- it's in wikipedia [http://en.wikipedia.org/wiki/The_C_Programming_Language_(book](http://en.wikipedia.org/wiki/The_C_Programming_Language_(book))

---

### Post by yester64 on 2009-12-21
> **  Greg said:**
> Look at the source code, learn C, bug track for your favourite projects (run dev versions).

I personally would suggest to try first a script language. C can be very overwhelming.
I used to code a little in Arexx (does that get used still?) and Pearl seems nice too. Altough Pyhton is the next hot one. Thats were i will dig in a little.

---

### Post by &#32 Greg on 2009-12-21
> **yester64 said:**
> I personally would suggest to try first a script language. C can be very overwhelming.
I used to code a little in Arexx (does that get used still?) and Pearl seems nice too. Altough Pyhton is the next hot one. Thats were i will dig in a little.

C isn't completely esoteric or anything. Scripting languages are a bit easier to start with, but concepts are concepts, and chances are in the open source world the programs that are best observed are written in C.

---

### Post by macogw on 2009-12-21
Ah, but C will give you a better understanding of the system.  Really, I'm quite glad that my school required that I learn Assembly and about how hardware is put together.  You can't write efficient code if all you know is Python.  How would you optimize?

---

### Post by Bodsda on 2009-12-21
My first thoughts as to becoming a Linux developer would definately be to help out other projects. You don't have to be a C guru or a python genius to help out and some of the projects will offer mentoring.

Fiddle around with a few languages like C, C++, Python, Perl, PHP, Ruby and see which one takes your fancy. Then delve deeper and see if any programs you use are written in this language. From there, you can contact the team and ask if there is anything you can do to help. 

Being a developer isnt a title you can get from a man behind a dodgy van; like forestpiskie :), you would need to work hard to get yourself noticed, but don't do it for a title or publicity, do it because you enjoy it.

---

### Post by MaxIBoy on 2009-12-21
Start out with Python. If you start out with C, you fall under the impression that programming is all about micromanaging your code, which is not true at all. 99% of all software these days is limited by how fast the user can type and click, not by the speed of the code itself. That being said, C is a good language to know. There are a few situations where it is appropriate to use, and a lot of existing open-source projects are written in C.

This is a great book on Unix development, full text available free on the Internet:
[http://www.faqs.org/docs/artu/](http://www.faqs.org/docs/artu/)


It's good to start out helping out other projects instead of starting your own. Find some bug that drives you nuts, and fix it. Add some new useful feature. Most developers are more likely to accept bug reports and feature requests if they happen to be accompanied by patches.

---

### Post by Flarkis on 2009-12-23
I would personally suggest C as a starting language. Although it is not the most user friendly you quickly learn the fundamentals of programming and avoid picking up some of the bad habits associated with 'n00b' languages (i do not consider python to be one of these though). I might also suggest java, it is quickly becoming a more and more popular language due to its portability. It also has a very rich standard library and includes everything you would need for most basic programs.

---

### Post by Frak on 2009-12-23
I strongly suggest you learn Ruby or Python first. C is great, it really is. It's very simple, and is very powerful, but it will throw you around like a ragdoll if you don't know what's going on. If you're going to school, and they offer C courses, take that, but learning C on your own is like creating the empire state building in CAD, with no knowledge of CAD.

Oh, and K&R assumes you already know how to program. It's an explanation guide, not a learn to program guide. In fact, this is an AMAZING book to learn programming with: [http://www.pragprog.com/titles/ltp2/learn-to-program-2nd-edition](http://www.pragprog.com/titles/ltp2/learn-to-program-2nd-edition)

---

### Post by yester64 on 2009-12-23
Whats your take on Vala?

---

### Post by DeadSuperHero on 2009-12-23
How do you learn to be a linux developer?

You just do. It can be through a number of methods, through any language really. Some developers stick to games because they prefer it, others learn advanced high and low-level languages to make changes to the core distribution they work on. It really depends.

The beauty of this is that the potential for what you can do with it is essentially limitless.

---

### Post by Frak on 2009-12-23
> **yester64 said:**
> Whats your take on Vala?
I like Vala.

---

### Post by yester64 on 2009-12-23
> **Frak said:**
> I like Vala.

:P

The reason i ask is, i recently downloaded an imageorganizer which written in Vala. Did not have any depentecies.
The program is Shotwell.
I will take a look into this. It made me curious.

---

### Post by bodhi.zazen on 2009-12-23
Many routes to becoming a developer. 

[https://wiki.ubuntu.com/MOTU](https://wiki.ubuntu.com/MOTU)

[https://wiki.ubuntu.com/MOTU/GettingStarted](https://wiki.ubuntu.com/MOTU/GettingStarted)

[https://wiki.ubuntu.com/UbuntuDevelopers](https://wiki.ubuntu.com/UbuntuDevelopers)

---

### Post by Frak on 2009-12-23
> **bodhi.zazen said:**
> Many routes to becoming a developer. 

[https://wiki.ubuntu.com/MOTU](https://wiki.ubuntu.com/MOTU)

[https://wiki.ubuntu.com/MOTU/GettingStarted](https://wiki.ubuntu.com/MOTU/GettingStarted)

[https://wiki.ubuntu.com/UbuntuDevelopers](https://wiki.ubuntu.com/UbuntuDevelopers)
If you don't know how to program in the first place, those venues are meaningless.

---

### Post by bodhi.zazen on 2009-12-23
> **Frak said:**
> If you don't know how to program in the first place, those venues are meaningless.

Perhaps to you, but you forget we are a community, and programming is not required to learn packaging. In addition, the MOTU has a mentoring program as well.

Sending someone off to learn language C or Python or what not does not really teach one to integrate into the community of developers or become involved in a (upstream) project.

---

### Post by wsonar on 2009-12-23
Forgive me I didn't read whole thread

(only my opinion)

Learn c/c++
study LPI cert or equilivent linux administration knowledge

learn shell scripting

learn apache,mysql,php
learn python,perl

learn wxWidgets and or QT

---

### Post by wsonar on 2009-12-23
> **kevinwmiller said:**
> Well, I thought about buying the K&R C book.  Trying to learn programming for the first time.  I am also enrolled in school for a bachelors in IT - Software Architecture, starting in January.


I recommend the traditional Bachelors of Computer Science that's what I'm working on.


It's what I found most software development jobs seek

---

### Post by wsonar on 2009-12-23
> **kevinwmiller said:**
> I went to, and bookmarked all of those links.

Thanks for your response, I'm trying to find books and online resources to get started.  I would like to dedicate my free time to learning all of this.


I had the teach yourself c++ for linux in 21 days I think it was pretty good.

I just aced my comp science I and it was helpfull that I had already taught myself some c++

---

### Post by 23meg on 2009-12-23
> **Frak said:**
> If you don't know how to program in the first place, those venues are meaningless.

Not at all. Packaging != Programming, even though some programming skills do transfer positively to packaging.

---

### Post by Frak on 2009-12-23
> **bodhi.zazen said:**
> Perhaps to you, but you forget we are a community, and programming is not required to learn packaging. In addition, the MOTU has a mentoring program as well.

Sending someone off to learn language C or Python or what not does not really teach one to integrate into the community of developers or become involved in a (upstream) project.

> **23meg said:**
> Not at all. Packaging != Programming, even though some programming skills do transfer positively to packaging.

He wants to learn how to program. MOTU is not what he wants. Now, if you want to add in the "contributing the community", you missed quite a few links bodhi. You need to include documentation/bug tracking/etc as well.

---

### Post by Mr. Picklesworth on 2009-12-23
> **Frak said:**
> I like Vala.

Excellent, another one! Vala is simply beautiful :)
Here's a nice thing for anyone who has learned Java: [http://live.gnome.org/Vala/ValaForJavaProgrammers](http://live.gnome.org/Vala/ValaForJavaProgrammers)

The thing I love most about it is all the Java / C# stuff it manages to do while becoming entirely normal compiled C code. This is pushing the power of the GObject library to its potential, where in the past it has really been underutilized. (For good reason; if that thing was fully utilized in plain C, nothing would get done).

Fast, easy, beautiful and powerful. Someone just needs to make Ogre bindings for it and I will be set.

I think it's a language that deserves a lot of push going forwards, and while it's still pretty new I highly recommend it.

---

### Post by Frak on 2009-12-23
> **Mr. Picklesworth said:**
> Excellent, another one! Vala is simply beautiful :)
Here's a nice thing for anyone who has learned Java: [http://live.gnome.org/Vala/ValaForJavaProgrammers](http://live.gnome.org/Vala/ValaForJavaProgrammers)

The thing I love most about it is all the Java / C# stuff it manages to do while becoming entirely normal compiled C code. This is pushing the power of the GObject library to its potential, where in the past it has really been underutilized.

Fast, easy, beautiful and powerful. Someone just needs to make Ogre bindings for it.
It take the ugly GObject and makes it clean.

---

### Post by phrostbyte on 2009-12-23
Oh god there is so many ways to program for Linux it's overwhelming. 

- Dozens of languages
- Many approaches to similar problems
- Many possible problems to tackle

First you want to define what you want to do? Make a video game? Work in kernel mode? GUI apps; GTK? Qt? FLTK? Xlib? :D Or maybe console apps (ncurses/std)? How about high algorithmic stuff like natural language processing? :)

Then you want to define what language you want to use, although the choice of problem may facilitate a specific language (although don't be sure about this!) :)

Do you want to learn how to program? Well start off small. Here is an app (Python) that might help. Try to run it, try to modify it. :)

[http://ubuntuforums.org/showthread.php?t=1237842](http://ubuntuforums.org/showthread.php?t=1237842)

Good luck!

---

### Post by 23meg on 2009-12-23
> **Frak said:**
> He wants to learn how to program. MOTU is not what he wants. 

I'm not sure the OP knows precisely what he/she wants (not that there's anything wrong with that), as indicated by the mismatch between "Linux developer" in the title and the content of the original post, which indicates that he/she isn't specifically interested in becoming a kernel developer. In any case, the original post goes (emphasis mine):

> Say if you wanted to **get involved** in the Linux Open Source community, **and someday develop**, where would you begin?

If the priorities are to get involved *now*, "test the water" with packaging and maintenance, and then maybe dive in fully someday, MOTU is a good place to be.

---

### Post by kevinwmiller on 2009-12-24
I suppose I don't really know what I meant by my original post/thread creation.  I do want to learn to program someday, that is for sure.  I don't know exactly how to go about it, or if I will be any good at it etc.

I also know that I want to become involved in the community in the future.  I would like to learn as much as I can.  So, MOTU, after looking at it, does look like a pretty good start with that.
 
I apologize for not fully understanding what "Linux Developer" meant.  I didn't mean to belittle the title, or show it any disrespect.  I suppose I just didn't know how to communicate properly what I meant, and chose that title.

On the BS in Computer Science issue.  I don't have that option in my area, so I chose what I could find, which was BS in IT - Emphasis in Software Architecture.  In all seriousness, I barely know what that even means.

I'm just trying to take the steps that I can find, to get to where I want to be someday, and that is knowledgeable, useful, and employed doing something I enjoy.

I appreciate all the posts, and have read each and every one of them.  I will pursue all of the advise given.

In the mean time, I think I will check out those MOTU links.

Thanks, guys!

---

### Post by kevinwmiller on 2009-12-24
Oh, and thanks to Macogw!  I click on your ZaReason button, and I just found the coolest computer shop around! 

I'm probably going to buy a new system from them in March.  

Thanks for the site!

---

### Post by julianb on 2009-12-25
one possible approach is for you to take a really simple app (like leafpad or Pong) and try to re-create it. then change it so that it suits your preferences more.

another thing you could do is try out a bunch of different linux distributions and try to make them all suit your preferences. this will probably involve learning a lot about using the bash terminal and about different programs (wicd vs network manager, lxde vs xfce, etc). You'll find that some programs are "almost just right but i just wish it would do ____" and when that happens, you've a great chance to learn a new programming skill.

There's a shift in programming and you have the opportunity to be ahead of (or behind) the curve on this one: 

people really like it when apps work remotely: an app that runs in a web browser can be run on any platform (linux/windows/mac) and can be run from any location, and can also be run off your hard drive. old-style apps just don't give you that choice.

---

### Post by kevinwmiller on 2009-12-25
Maybe I could make the square ball in pong, round.

---

### Post by ashmew2 on 2009-12-26
I find myself at the same point , i started with C++ , recently wrotea very rough Snake game...I am also a beginner , but i try to improvise everyday and i think thats the important thing to do ...I want to develop applications which others could use and enjoy but it aint that easy , but you have to start somewhere,sometime...The more you think about it , the less you will do....I mean , just dont consider options , choose one and dive into it...Pick out something , like C++/Lisp/C/Java anything , just take it up , google tutorials and keep learning...I think programming is about writing algorithms , not syntax...If you like to solve puzzles/challenges, im pretty sure there's a programmer in you already ;)

Just dont let it suffocate inside you..

Pick a language and get to work , if you ever get stuck , just post questions , i am pretty sure the programming Gurus will help you ;)

Oh and , I almost fully agree with post # 33 :D

---

### Post by phrostbyte on 2009-12-26
For learning programming and also a bit of packaging you can do:

```

apt-get source package

```

(no sudo)

A good starting example would be hello. 

hello is a simple program which basically just displays "Hello world!" to the std output.

```

apt-get source hello

```

This downloads the source for the package "hello" in your working directory. It's just a bunch of files. The ones in the debian/ directory control package installation and metadata. The other directory is the program's actual source code (in this case it's C code).

You can then modify the source, and build a binary deb with.

```

dpkg-builddeb

```

---

