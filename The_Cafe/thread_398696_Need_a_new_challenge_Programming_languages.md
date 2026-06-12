---
title: "Need a new challenge? Programming languages"
date: 2007-04-01
forum: The Cafe
---

### Post by ade234uk on 2007-04-01
I need a new challenge. I have got Ubuntu sitting here doing nothing. I am interested in creating applications to use in Ubuntu. Where do I start? What do you use.

I have seen three or four I am possibly interested in learning. Finding the right one is important. I am quite interested in Mono due to it being able to run on other platforms. But then Python looks quite interesting as well?

Mono
Python
GCC

---

### Post by thelinuxguy on 2007-04-01
> **ade234uk said:**
> I need a new challenge. I have got Ubuntu sitting here doing nothing. I am interested in creating applications to use in Ubuntu. Where do I start? What do you use.

I have seen three or four I am possibly interested in learning. Finding the right one is important. I am quite interested in Mono due to it being able to run on other platforms. But then Python looks quite interesting as well?

Mono
Python
GCC

I wanted an application that sits on my desktop, in a corner, and displays a word and its meaning for improving my vocabulary. There is an applet named "Gnome Word of the Day" but it just displays the word on the Gnome panel and I have to click it to see the meaning. I wanted something similar but with some more functionality such as
[LIST=1]
[*]the word should change when I click it (maybe with small next/previous buttons at either end
[*]it should be on the desktop and I can drag it around
[*]it should allow me to specify input files in a specific format to pull words from rather than connecting to one of the online dictionaries so that I can use it offline as well
[*]an import functionality from existing apps would be nice
[/LIST]

I am not aware if such an app already exists or if Gnome WOTD applet already provides these. But how is it for a programming task? The language/tools to use for this is your choice.

---

### Post by macogw on 2007-04-01
Python is cross-platform as well.  Also, GCC isn't a  it's a C compiler.  Again, cross-platform.  Python is one of the easiest languages to learn, and it's used in Ubuntu a lot.  C is used in a lot of GNOME stuff because Glade (a program to design GNOME interfaces) outputs C.

---

### Post by Luggy on 2007-04-01
Pttth, you wusses and your compilers.
Be a man an write straight machine code!

---

### Post by macogw on 2007-04-01
> **Luggy said:**
> Pttth, you wusses and your compilers.
Be a man an write straight machine code!

0x4E 0x6F

---

### Post by rolando2424 on 2007-04-01
> **macogw said:**
> 0x4E 0x6F

01011100 10111010

---

### Post by DoctorMO on 2007-04-01
be a real man and control the electrons with heavy magnets near the cpu.

---

### Post by IYY on 2007-04-01
If you've never programmed before, Python+GTK would probably be the best option.

---

### Post by macogw on 2007-04-01
> **rolando2424 said:**
> 01011100 10111010

V º ? What?

---

### Post by Compucore on 2007-04-01
Myself I would go with C++. I had started in the late 80's early 90's with GWbasic, THen crossed over to Pascal on a Vax VMS then to Turbo Pascal and went to C++ later on in the good old DOS days, Then over to windows. C++ seems more viable to me over here. Since you can cross platform to what ever platform you want to use or work with. C++ is mor or less a standard for linux/unis based systsems. And since your going to be working in an IDE environment it would be easier. Since your using a gui interface for he frontend and the back end is just some source code for programming in general.

Compucore

---

### Post by Nils Olav on 2007-04-01
> **DoctorMO said:**
> be a real man and control the electrons with heavy magnets near the cpu.

:lol:

---

### Post by ynnhoj on 2007-04-01
> **IYY said:**
> If you've never programmed before, Python+GTK would probably be the best option.i agree--i think python is a great place to start.  gui programming can be a pain (not that it's terribly difficult, it just seems like such a chore) so don't let that take the wind out of your sails when you get to it :)  that being said, pygtk actually isn't all that bad..

---

### Post by ssam on 2007-04-01
there is lots of info in the programming section of the forum. start with [http://ubuntuforums.org/showthread.php?t=333867](http://ubuntuforums.org/showthread.php?t=333867)

---

### Post by reacocard on 2007-04-01
> **ynnhoj said:**
> i agree--i think python is a great place to start.  gui programming can be a pain (not that it's terribly difficult, it just seems like such a chore) so don't let that take the wind out of your sails when you get to it :)  that being said, pygtk actually isn't all that bad..

I 3rd(?) that. I only recently started programming myself (end of last year) and I found Python to be both easy to use and very powerful. I also tried C++ for a bit but it gave me too many headaches, I'll probably try it again or C after I get better with Python. You can load C modules into Python, so that might be a nice way to transition.

As for pyGTK, use Glade. *Much* easier than writing the whole thing out by hand.

Also, for a nice, basic IDE, I recommend geany. It's in the repos.

---

### Post by ynnhoj on 2007-04-01
> **reacocard said:**
> I also tried C++ for a bit but it gave me too many headaches, I'll probably try it again or C after I get better with Python.i think you'd be best off learning the basics of c programming before you get into c++.  all it takes is a few good books and (in some cases) some patience.  after all, quite a bit of your python knowledge is transferrable, so for some things it's just a matter of learning the c/c++ syntax (ifs, loops, classes, try & catch, etc.).  of course, some things will be new to you (dynamic memory allocation, all the silly things you can do with pointers and pointer arithmetic, etc.) but you can learn it all in time.

---

### Post by plb on 2007-04-01
Python

---

### Post by RandomJoe on 2007-04-01
Another vote for Python!  Especially if you aren't going to be able to dedicate a LOT of time to the task of learning.

I tried for years to get the hang of C/C++, but I always find I can get so far before other things divert my time and by the time I get back to it I feel like I'm starting over.  Python has just clicked with me, and even though I've already had a couple of stints where I didn't look at any code for a couple of months or more, it's been _easy_ to pick back up where I left off.

That said, I have kept enough of the C knowledge that I know what I'm looking at.  I just can't write something from scratch and even hope for it to compile! :)

---

### Post by macogw on 2007-04-01
> **RandomJoe said:**
> Another vote for Python!  Especially if you aren't going to be able to dedicate a LOT of time to the task of learning.

I tried for years to get the hang of C/C++, but I always find I can get so far before other things divert my time and by the time I get back to it I feel like I'm starting over.  Python has just clicked with me, and even though I've already had a couple of stints where I didn't look at any code for a couple of months or more, it's been _easy_ to pick back up where I left off.


That's probably because it's executable pseudocode.

---

