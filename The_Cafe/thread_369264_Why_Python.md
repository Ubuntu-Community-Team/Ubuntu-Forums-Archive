---
title: "Why Python?"
date: 2007-02-24
forum: The Cafe
---

### Post by liviubero on 2007-02-24
Hello,
I am new to Ubuntu and Linux, but got excited about this project and thinking to replace completely Windows with Ubuntu. Actually, I use Windows only for a few application with which I am already used (like Dreamweaver for its css and php support).
I bought myself the official Ubuntu book and I like it. I like the whole idea. Actually I love it.
I just read there in chapter 1.3.2 about the project's "concentration on Python as the only programming language with which the whole system can be build up and extended" (I have it in German, so perhaps my English translation isn't the best one).

My wish now is to start learning to program. (Hopefully I will be accepted in the Softwaretechnik University in Stuttgart and thus become a diplomed programmer).  I learn right now PHP and I wanted also to start learning a programing language (not a server side one), so that I can write desktop and network applications. In this order, I was thinking about Java.
But now, I read in the Ubuntu official book about Python. And before starting to learn Python, I have a few questions. I cannot just start learning anything. The time I have doesn't leave me to just play around with things. So I have to be very practical. That is, I have to decide myself to begin with only one programing language and when I can master it, then try others. 
My question is:
Why Python?
What makes it to the "only programing language" (as the book tells)?

.... I hope that my English is understandable.

---

### Post by ssam on 2007-02-24
most of the software in ubuntu is written in C/C++ (eg the kernel, gnome, firefox etc). python is used for some of the ubuntu specific tools like ubiquity (the GUI installer).

Java has never been included in ubuntu by default for licencing reasons (the licencing is currently being changed, so this may change in the future).

Python is installed by default, along with all the python libraries need to build GUI applications.

Python is easy to learn (try the free book at [http://www.ibiblio.org/obp/thinkCSpy/](http://www.ibiblio.org/obp/thinkCSpy/) ). It is very portable. It has lots of useful libraries.

---

### Post by My Lost Shadow on 2007-02-24
I think Python was chosen because of it's automatic memory management, easy reading code, there are less syntactic exceptions and less boilerplate than in C for example.

Also, it is a multi-paradigm programming language which means that you can use object orientation and structured programming, functional programming and even aspect-orientated programming. It even has a feature which binds method and variable names during program execution.

---

### Post by Starchild on 2007-02-24
[Why Python?]("http://www.python.org/about/success/esr/")

---

### Post by hotani on 2007-02-24
Read the above for why Python is worth learning. Then [read this book](http://www.greenteapress.com/thinkpython/html/) for a great intro to the basics of Python as well as object oriented design in general. I learned python on my own via that book, and worked all the examples and problems. It is a great no-bs guide to the language.

---

### Post by DrainBead on 2007-02-24
Python, Perl, C and C++ is all you need to know to get involved in FOSS.

Python is nice but Perl is nicer, C is better for most anything and C++ is king in KDE.

---

### Post by liviubero on 2007-02-25
FOSS=?
Why is Java not on the list?
As I read, Java was developed from C++ because this one had not sufficient power.

I am just trying to find out with what should I begin my learning.

hotani: your link is dead (at least now, when I'm trying to open it).

---

### Post by graabein on 2007-02-25
FOSS = Free and open source software ([wikipedia]("http://en.wikipedia.org/wiki/FOSS")).

I want to learn Python (and Perl) also. I know C/C++ and some Java but mostly Visual Basic and C# ASP.NET because that's what we use where I work.

---

### Post by hotani on 2007-02-25
> **liviubero said:**
> 
hotani: your link is dead (at least now, when I'm trying to open it).

hmmm, works ok from here. [Here is the same book](http://www.ibiblio.org/obp/thinkCSpy/) at a different site. The title is "How to Think Like a Computer Scientist" by Allen B. Downey, Jeffrey Elkner and Chris Meyers.

---

### Post by pirothezero on 2007-02-25
> **liviubero said:**
> FOSS=?
Why is Java not on the list?
As I read, Java was developed from C++ because this one had not sufficient power.

This probably has to do with having to use the jvm for java. I am new to the linux world when it comes to what the masses use, but I wouldn't be surprised to learn if most linux users don't like having java on their systems just like a lot of windows people. Then again there is no utorrent in linux, and imo azureus comes 2nd so maybe thats how it is for most people. 

But like what was mentioned earlier the licensing issues become since one has to install java going out of their way if they have applications they want to use with java, with c++ and python they just work. Don't get me wrong though I love java and consider it to be a great language and I code in it almost every day but I believe it comes down to a convience factor in the end user whether they will use it or not. Example being not sure in linux but people stay away from azureus because its blotted and runs on 'slowass' java so they opt for utorrent.

---

### Post by SunnyRabbiera on 2007-02-25
Python is good and simplistic, but it will certainly have some compition from java now its practically FOSS

---

### Post by liviubero on 2007-02-26
hotani: the link is ok now. I have that book and started to read it. Thanks.

I found out that I have installed Python 2.4 on my mashine. In add/remove applications panel there is an option for installing Python 2.5.
Should I uninstall the 2.4 version first, or install direct 2.5?

And what Python editor would you recomend from that list?

---

### Post by ssam on 2007-02-26
stick with python 2.4. the differences between 2.4 and 2.5 are not really noticeble unless you are doing very advanced things (like writing libraries). all most all python programs will work the same on 2.3, 2.4 or 2.5. however the version of 2.5 in edgy does not have as many libraries as 2.4.

feisty will have 2.5 by default.

---

### Post by liviubero on 2007-02-26
OK.
And a Python editor?
I have in the Add/Remove Panel a lot of Python editors.
Until now I, in order to write the examples from that Book ("Think like a ...), I used a text editor, Gedit.

---

### Post by Tomosaur on 2007-02-26
I personally like Scite. It's not an IDE, but it's lightweight, quick loading, and has syntax highlighting. I think you CAN make it into an IDE, with code completion and compilation and such, but I've never bothered. I use JEdit for my IDE requirements. It looks ugly but it's got tons of useful features.

---

### Post by reacocard on 2007-02-26
I like geany. Clean, simple, fast. It's in Ubuntu's repos too:
```
sudo apt-get install geany
```
or you can get a more recent version from my repo: [http://syzygy42.tuxfamily.org/dists/edgy/universe/](http://syzygy42.tuxfamily.org/dists/edgy/universe/)

---

### Post by EdThaSlayer on 2007-02-26
> **reacocard said:**
> I like geany. Clean, simple, fast. It's in Ubuntu's repos too:
```
sudo apt-get install geany
```
or you can get a more recent version from my repo: [http://syzygy42.tuxfamily.org/dists/edgy/universe/](http://syzygy42.tuxfamily.org/dists/edgy/universe/)

If you want to get used to an IDE environment use the one that comes with Python which is called IDLE. I used that before I started using Geany. If your already an experienced programmer then just skip and use Geany. For beginner reading you should try getting the book [URL="www.byteofpython.info"]ByteOfPython
[/URL].

---

### Post by G Morgan on 2007-02-26
Always considered C the best language to learn in*, then Java. Python hides you from too many things to be considered a solid introduction to programming and then the more advanced languages tend to daunt people from going further (which is why we have so much VB6 junk on the planet).

I'd avoid C++ like the plague, it has it's uses but syntactically is a pig and really needs replacing with a more sane specification. It's what happens when you try to be all things to all people and almost succeed.

Really programming is all about concepts, you will not be able and should not try to memorise an entire language specification. Instead focus on a paradigm. When you know object oriented programming (OOP) then Smalltalk, Java or C++ are all the same bar a few minor oddities or brain crashes. So with OOP focus on why we have objects and what they are supposed to do and look like and don't get too bogged down in specifics. Same goes for procedural, functional, logic programming or relational. Python being multi-paradigm can blur these lines but focusing on the OOP aspects will probably put you in the best stead for the future (even if OOP is becoming less of an absolute with things like functional getting more brain time).

*and it is very very simple despite claims to the contrary. What's hard is debugging huge programs in it. For introducing you to control structures, variables, decisions and the other entities that make the basis of programming it is great. Just don't go beyond that with it, when you have learned the basics move up to something like Java which introduces a few more concepts.

---

### Post by liviubero on 2007-02-26
Wow, thanks, G Morgan.
I played a little with Java, but not really deeped in. What I studied more in depth is Php and I observed the simplicity of Python, comparing it with php.
Actually, I just want to learn something good, something with which I can start create in a fast and funny way applications and that's it. Right now my activity won't let me study in depth any complicated language.
I understand what you say about C. I agree. I myself rejected for instance any tool for web design, preferring to work in html with Notepad. Just when I had to do things fast, I choose a wysiwyg tool.

But now I would leave Java and C for later, when (if) I go to University.

---

### Post by G Morgan on 2007-02-26
Also I'd stick with just a text editor and the CLI to begin with. It's always worth seeing everything in pure code rather than trying to automate too much when you are trying to learn. I think Gedit will have syntax highlighting for Python but if it doesn't I'm almost certain that something like KATE will.

---

### Post by liviubero on 2007-02-26
Indeed Gedit has syntax highlight.
It is ok. Actually I use Gedit, but I just wanted to know for the future.
Thanks for replying.

---

### Post by hotani on 2007-02-26
I've been using Bluefish, but most of what I work on is web-based. Still, it makes a fairly good python editor, and having the tree view is nice.

---

### Post by jincast90 on 2007-02-26
I am learning C, and I can confirm there is syntax highlighting for Gedit, when programming in C.

---

### Post by liviubero on 2007-02-26
I am also curious why people choose Python after all.
Just because it seems simple to use? That it has no such tormenting syntax rules? That you can just write

[COLOR="Indigo"]text="Whatever"
print text
[/COLOR]
instead of

[COLOR="DarkOrange"]<?php[/COLOR]
 [COLOR="DarkOrange"]$[/COLOR][COLOR="Indigo"]text="Whatever"[/COLOR][COLOR="DarkOrange"];[/COLOR]
[COLOR="Indigo"]echo[/COLOR] [COLOR="DarkOrange"]$[/COLOR][COLOR="Indigo"]text[/COLOR][COLOR="DarkOrange"];
?>[/COLOR]

I mean, what makes it so attractive that it was declared in the official Ubuntu book the only programming language on which the project concentrate itself when it comes to development?

---

### Post by Sentinel83 on 2007-02-26
If you are asking which language - I would think that Java would be a better language to concentrate on, strictly because of its cross-platform abilities.  Unless you know you will want a job programming only in Unix/Linux, Java will enable you to learn the language and apply the programs to most OSs (and its close to C, so that helps there too)

Just my two cents.

---

### Post by 23meg on 2007-02-26
> **liviubero said:**
> Indeed Gedit has syntax highlight.
It is ok. Actually I use Gedit, but I just wanted to know for the future.
Thanks for replying.

Its plugins, which it seems aren't very widely known of, also come in handy; especially code comment, embedded terminal and Python console.

---

### Post by G Morgan on 2007-02-26
> **Sentinel83 said:**
> If you are asking which language - I would think that Java would be a better language to concentrate on, strictly because of its cross-platform abilities.  Unless you know you will want a job programming only in Unix/Linux, Java will enable you to learn the language and apply the programs to most OSs (and its close to C, so that helps there too)

Just my two cents.

Unix is the biggest target for Java in the server room. Companies are finally starting to learn and are taking portable code rather than running obscure code dependant on some PDP-11 instruction.

---

### Post by liviubero on 2007-02-26
> **Sentinel83 said:**
> I would think that Java would be a better language to concentrate on, strictly because of its cross-platform abilities.  Unless you know you will want a job programming only in Unix/Linux, Java will enable you to learn the language and apply the programs to most OSs (and its close to C, so that helps there too)

Isn't Python cross-platform?
I think it does.
I mean, I've seen cool tutorials for Windows.

---

### Post by reacocard on 2007-02-26
> **liviubero said:**
> Isn't Python cross-platform?
I think it does.
I mean, I've seen cool tutorials for Windows.

It is indeed. Java simply has wider acceptance/use.

---

### Post by liviubero on 2007-02-27
> **reacocard said:**
> It is indeed. Java simply has wider acceptance/use.

Why?
I also tried a few months ago to learn something about Java and I found it cool, but I find that with Python I learn much faster.
Why is this obsession with Java?
What can Java do and Python not?

Could be Python scripts be compiled so that they work not only on a system with Python installed on it? That is without the interpreter?
Are there any ways to compile for instance this script:
[COLOR="Orange"]print "Hello, nobody"[/COLOR]
to a .exe file, for instance?

---

### Post by Tuna-Fish on 2007-02-27
> **liviubero said:**
> I am also curious why people choose Python after all.
Just because it seems simple to use? That it has no such tormenting syntax rules? That you can just write

[COLOR="Indigo"]text="Whatever"
print text
[/COLOR]
instead of

[COLOR="DarkOrange"]<?php[/COLOR]
 [COLOR="DarkOrange"]$[/COLOR][COLOR="Indigo"]text="Whatever"[/COLOR][COLOR="DarkOrange"];[/COLOR]
[COLOR="Indigo"]echo[/COLOR] [COLOR="DarkOrange"]$[/COLOR][COLOR="Indigo"]text[/COLOR][COLOR="DarkOrange"];
?>[/COLOR]

I mean, what makes it so attractive that it was declared in the official Ubuntu book the only programming language on which the project concentrate itself when it comes to development?

The syntax doesn't really matter at all. Curly braces or no curly braces doesn't do a difference. Python happens to have a very good set of libraries and it is generally fast to write working code in python. The reason python is the primary language for ubuntu is very likely not so much about python being better than the rest but about that when you do it all in one language it is easier to maintain.


> **liviubero said:**
> Why?
I also tried a few months ago to learn something about Java and I found it cool, but I find that with Python I learn much faster.
Why is this obsession with Java?
What can Java do and Python not?
For example some implementation of java can be found on pretty much all modern cellphones, so if you are coding for cellphones, using java is a must. 

Basically, learning a new programming language can be compared to learning a new real language while learning to program can be compared to learning to speak. Essentially, once you can program in python, you also can program in java, all it takes there is that you learn a new syntax which is a LOT easier than learning to program in the first place. So if you get python easier, just use python for now, and then some time later code something in java.

> 
Could be Python scripts be compiled so that they work not only on a system with Python installed on it? That is without the interpreter?
Are there any ways to compile for instance this script:
[COLOR="Orange"]print "Hello, nobody"[/COLOR]
to a .exe file, for instance?


Yes, python can be packaged in a self-contained executable, using, for eample, one of the following:
[http://www.py2exe.org/](http://www.py2exe.org/)
[http://pyinstaller.python-hosting.com/](http://pyinstaller.python-hosting.com/)
[http://svn.pythonmac.org/py2app/py2app/trunk/doc/index.html](http://svn.pythonmac.org/py2app/py2app/trunk/doc/index.html)

---

### Post by G Morgan on 2007-02-27
Java is semi compiled which means it has the run anywhere benefits of interpretation but runs quite close to native efficiency these days (normally where there are problems is where somebody uses unmanaged code via JNI and doesn't clean up properly after themselves. Perfect example being SWT with Azureus). In any case Java is much more efficient.

Java is also more expressive than Python.

Python will be faster to develop in for simpler apps but Java would come more into it's own as complexity increases.

---

### Post by hotani on 2007-02-27
semi-related question: Any of you worked with [Jython](http://jython.org)?

We are setting up a portal at work and its interface is java. However, the programmer who will be maintaining it, as well as myself who will most likely be a backup, are python programmers. We are considering trying out Jython to have a familiar environment to work with.

Granted, it is always good to learn a new language, yada yada, but we're curious about Jython and if code written with it can be as powerful as using straight java.

---

### Post by liviubero on 2007-03-23
> **Tuna-Fish said:**
> Yes, python can be packaged in a self-contained executable, using, for eample, one of the following:
[http://www.py2exe.org/](http://www.py2exe.org/)
[http://pyinstaller.python-hosting.com/](http://pyinstaller.python-hosting.com/)
[http://svn.pythonmac.org/py2app/py2app/trunk/doc/index.html](http://svn.pythonmac.org/py2app/py2app/trunk/doc/index.html)

Well, I searched for pyinstaller in Synaptic and didn't find it, also didn't find py2exe.
Are there any other applets which could do the job?
Or, how could I install pyinstaller for instance, without Synaptic?

---

### Post by DoctorMO on 2007-03-23
You want to package the exe for a python program by targeting it from another platform such a linux?

I use the normal distutils, set up a package information and use ./setup.py bdist/bdist_rpm etc to create the various installers.

---

### Post by liviubero on 2007-03-24
> **DoctorMO said:**
> You want to package the exe for a python program by targeting it from another platform such a linux?

I use the normal distutils, set up a package information and use ./setup.py bdist/bdist_rpm etc to create the various installers.

You lost me.
I just want to package my Python programmes without having to use PyInstaller from within Windows. So I downloaded the PyInstaller for Linux, because I didn't find it with Synaptic and didn't knew any other utility for packaging Python programmes, and then I didn't knew how to use it. I am really a newbie with Linux.
What is this: "./setup.py bdist/bdist_rpm etc" ?
If I could package the .py files in .exe files with some sort of Ubuntu command, then I would gladly want to know it.

I just want to avoid using Windows anymore and have no idea about how to install anything without Synaptic.
Or maybe there is some application available with Synaptic which could do the same job as PyInstaller?

---

### Post by DoctorMO on 2007-03-24
right yes, you want to install existing python applications... if they use distutils you will see a setup.py file. run sudo ./setup.py install to install that application or module.

---

### Post by liviubero on 2007-03-24
....................
NO.
I wrote a Python application.
This application is a python file. This python file (.py) cannot be run without the Python software installed. If I want to use the application I wrote on a computer which doesn't have Python installed, the I have to transform my .py file into an .exe one.
In this order I searched for an application which could do this. I haven't found anything with Synaptic (or perhaps I didn't searched the right thing) and didn't found anything. This is why I wanted to use the PyInstaller, but I have idea how to install it in Ubuntu-Linux.
I don't have any Python programmes to install. Such programmes I haven't wrote.

---

### Post by reacocard on 2007-03-24
> **liviubero said:**
> You lost me.
I just want to package my Python programmes without having to use PyInstaller from within Windows. So I downloaded the PyInstaller for Linux, because I didn't find it with Synaptic and didn't knew any other utility for packaging Python programmes, and then I didn't knew how to use it. I am really a newbie with Linux.
What is this: "./setup.py bdist/bdist_rpm etc" ?
If I could package the .py files in .exe files with some sort of Ubuntu command, then I would gladly want to know it.

I just want to avoid using Windows anymore and have no idea about how to install anything without Synaptic.
Or maybe there is some application available with Synaptic which could do the same job as PyInstaller?

I don't think this is possible. I think you HAVE to build the exe under windows, so that the necessary libraries and such can be bundled into it. You could probably run the windows version of pyinstaller under wine, but I don't think there's any linux-native way to build a windows executable.

Also, I just took a stab at installing pyinstaller under linux, and I'm lost. It uses some weird install method that I can't figure out. I've compiled plenty of programs under linux before, but this one has me stumped.

---

### Post by liviubero on 2007-03-24
Ok,
Thank you. So there is no method for building .exe files under Linux except for this impossible programme. And I don't want right now to try my brains out with installing PyInstaller under Linux.
I will try PyInstaller under Windows.
Thanks.

---

### Post by SavantEdge on 2007-03-25
Well, if you're writing your applications for Linux, then you're not going to need PyInstaller.
PyInstaller will be useful when you're trying to distribute your applications.

---

### Post by liviubero on 2007-03-25
I do want to distribute my applications.
I just used PyInstaller under Windows and it works. Now I have to figure out how to use it under Linux.

---

### Post by reacocard on 2007-03-25
> **liviubero said:**
> I do want to distribute my applications.
I just used PyInstaller under Windows and it works. Now I have to figure out how to use it under Linux.

Under linux, you'll use a different method. For python, that usually means writing either a setup.py or a Makefile, then making a tarball of that and the source code. Beyond that, you could also package it into deb or rpm files, for easy installation on other systems, but those are harder to make than just a straight tarball. Feel free to contact me with any questions about packaging your program for linux (not windows ;) ).

---

