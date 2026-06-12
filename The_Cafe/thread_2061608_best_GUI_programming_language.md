---
title: "best GUI programming language ?"
date: 2012-09-23
forum: The Cafe
---

### Post by raja.genupula on 2012-09-23
Whats the best GUI programming language ?? 

I need it for scripts and databases . One more thing is it should be light and more featured .

---

### Post by HermanAB on 2012-09-23
Perl of course.  It does everything.

---

### Post by ki4jgt on 2012-09-23
> **HermanAB said:**
> Perl of course.  It does everything.

How easy is Pearl. I've been looking for a Linux replacement to BASIC. I thought I would find it with Python but it's just too function driven when it comes to GUIs. I don't mind a good function where terminals are concerned but throw in GUI functions and I get headaches :(

---

### Post by Lars Noodén on 2012-09-23
Another vote for perl here.  It's very easy to learn and very, very flexible to write in.  There are APIs for your databases, too.  It's all in [CPAN](http://www.cpan.org/modules/) and most of CPAN is already in the repositories.

---

### Post by raja.genupula on 2012-09-23
Thank you Friends and one more thing  is any more suggestion to have a start with perl ? 

may i know what we can do only with perl ?

---

### Post by Lars Noodén on 2012-09-23
Here are some resources for starting with Perl:
[http://www.perl.org/books/beginning-perl/](http://www.perl.org/books/beginning-perl/)
[http://learn.perl.org/](http://learn.perl.org/)

There is a lot of online documentation already on your system.  If you enter [man perl](http://manpages.ubuntu.com/manpages/precise/en/man1/perl.1.html) and scroll down a little, it will point at these resources.

If you start to get into perl, then a good investment is the "[camel book](http://shop.oreilly.com/product/9780596000271.do)"

I'm not sure there is anything unique to perl these days.  It's pattern matching capabilities have largely spread to other languages as 'PCRE'  CPAN is still formidable though PHP is starting to catch up.

---

### Post by HermanAB on 2012-09-23
I found Perl to be super easy when using a C-like syntax and a total mess when trying to use its Object Oriented syntax, TIMTOWTDI.

---

### Post by Lucradia on 2012-09-23
Python

---

### Post by Lars Noodén on 2012-09-23
> **HermanAB said:**
> I found Perl to be super easy when using a C-like syntax and a total mess when trying to use its Object Oriented syntax, TIMTOWTDI.

"there's more than one way to do it" (tm)  ;)

But +1 for the C-like syntax.  Perl, when done right, is quite readable.  It's a fun language.

---

### Post by Majorix on 2012-09-23
Why not Ruby?

---

### Post by Primefalcon on 2012-09-23
I say python

---

### Post by MG&amp;TL on 2012-09-23
> **Primefalcon said:**
> I say python

Yup, I'd go with that too. You could argue that almost any major language is 'the best'. 

If you wanted a compiled language, I'd choose C++ (probably with Qt) or C (probably with GTK+).

---

### Post by Primefalcon on 2012-09-24
my favs all up

are bash (real quick and easy)

python (for guis or more complex stuff)

c++ (when I want speed)

web programing comes down to php, javascript and xml mostly

---

### Post by forrestcupp on 2012-09-24
> **Primefalcon said:**
> I say python

> **MG&TL said:**
> Yup, I'd go with that too. You could argue that almost any major language is 'the best'. 

If you wanted a compiled language, I'd choose C++ (probably with Qt) or C (probably with GTK+).

> **Primefalcon said:**
> 
python (for guis or more complex stuff)

Why python? Python doesn't have any api for GUI stuff at all. You have to use a 3rd party toolkit, which is usually a wrapper of something created for C/C++. So you might as well just do it natively with C/C++.

If you're using Windows, I'd probably say C#.

---

### Post by vexorian on 2012-09-24
C/C++ doesn't have any API for GUI either. The only standard C++ libraries are things like the STL and maybe part of Boost in the newest spec. All the stuff you would use for GUI in the Cs is third party.

It makes sense that python uses wrappers. This way those core things like graphics and GUI will have C-like performance. If these libraries were implemented in python, all python apps would be extremely slow.

---
It does not pay to be obssessed with using "the best" language. Tell you the truth whether or not you are using the best language or one of the best languages is quite irrelevant in the end of things. It is more important to be good at whathever language you are using and to have a compatible mindset with it. And also to know how to write manteinable code. No user is going to award you bonus points for using "the best" language.

Edit: Oh, and something can't be light and feature rich at the same time.

But C# should rot in hell.

---

### Post by forrestcupp on 2012-09-24
> **vexorian said:**
> C/C++ doesn't have any API for GUI either. The only standard C++ libraries are things like the STL and maybe part of Boost in the newest spec. All the stuff you would use for GUI in the Cs is third party.
I know. But my point is that most of the big 3rd party libraries and toolkits were written for C/C++. Python has to use wrappers, which are basically hacked ports. In my opinion, it's better to program in the language the the library or toolkit was written for. I've used both PyGTK and GTK+ with C++, like it was made for. They both work, but I think it's better to use what it was made for.

The good thing about Python is that other than for the GUI, its standard library is very extensive. I think Python is awesome. The only reason I brought this up is because he specifically asked for a good GUI programming language, and in my opinion, Python is not the best for GUI. I still stand by C# if the OP happens to be using Windows.

---

### Post by BrokenKingpin on 2012-09-24
I would say Python.

My personal preference would be C#, but with all the mono hate in the Linux community I would even bother trying to recommend it.

---

### Post by jrog on 2012-09-24
> **forrestcupp said:**
> Why python?
On Ubuntu at least, I think Python is the officially preferred language for applications. One reason is that they have set up the 'quickly' tool to use Python. This makes it *extremely* easy to get started on a GUI application without having to do much of anything; easier than with any other languages, AFAIK.

---

### Post by |{urse on 2012-09-24
A vote for perl or C++ here.

---

### Post by jrog on 2012-09-24
I'm actually surprised by all of the Perl recommendations here; didn't know that it was still this popular (what with Ruby and Python being all the rage these days) or that it was that effective as a GUI language. 

Personally, I just find Perl code so ugly that it makes me unhappy to use it (obviously, that's purely idiosyncratic). I love C/C++, though, so it's not an aversion to curly braces.

---

### Post by BrokenKingpin on 2012-09-24
> **jrog said:**
> I'm actually surprised by all of the Perl recommendations here; didn't know that it was still this popular (what with Ruby and Python being all the rage these days) or that it was that effective as a GUI language. 

Same here. I have been a professional programmer for years and have not come crossed it, or have even seen a job posting requiring it as a skill. Not that it really means anything, but you never really hear people talking about perl. Python and many other languages seem way more popular. Even on the two programming forums I belong to the perl sub-forums don't see much activity.

---

### Post by MG&amp;TL on 2012-09-24
> **BrokenKingpin said:**
> Same here. I have been a professional programmer for years and have not come crossed it, or even heard of a company that uses it for anything. Not that it really means anything, but you never really hear people talking about perl. Python and many other languages seem way more popular.

All the perl programmers are quietly typing cool stuff out in cellars somewhere. :lol:

I agree with forestcupp, but since the OP *seemed* (maybe not?) to want an interpreted language, I went with python.

---

### Post by forrestcupp on 2012-09-24
> **jrog said:**
> On Ubuntu at least, I think Python is the officially preferred language for applications. One reason is that they have set up the 'quickly' tool to use Python. This makes it *extremely* easy to get started on a GUI application without having to do much of anything; easier than with any other languages, AFAIK.

Interesting. I've never heard of quickly. So basicly, it just sets up a simple default app using PyGTK that can be tweaked in Glade. If you're going to be using Glade anyway, why do we really need quickly?

But that brings up a good point that using PyGTK in Python with the Glade GUI editor is probably the easiest way to create a GUI app in Linux. It's not necessarily my favorite method, but it probably is the easiest. That, mixed with Python's huge standard library might make it a good choice.

---

### Post by Primefalcon on 2012-09-24
> **forrestcupp said:**
> Why python? Python doesn't have any api for GUI stuff at all. You have to use a 3rd party toolkit, which is usually a wrapper of something created for C/C++. So you might as well just do it natively with C/C++.
not really python is very easy to use... plus though those toolkits may have been written in c++, a lot of the widgets such as such as wxWidgets, pyGTK_ has already been mentioned and such are very very easy to use....

And while c++ apps may be faster than python, python is a lot faster to do the core programming in

---

### Post by MG&amp;TL on 2012-09-24
> **forrestcupp said:**
> Interesting. I've never heard of quickly. So basicly, it just sets up a simple default app using PyGTK that can be tweaked in Glade. If you're going to be using Glade anyway, why do we really need quickly?


OT:
<rant>
You've nailed it on the head there. Not only is it slightly pointless, it also has a lot of boilerplate code that breaks if you don't use the default setup.

About the only good thing about it is that it will package it for you. Which is probably the thing I hate most about Ubuntu development.
</rant>

---

### Post by amboxer21 on 2012-09-25
Depends on the programming language you want to use and what DE your aiming for. Like the GTK toolkit is great for c programmers. It is written in C itself. Though the toolkit is heavy and depends on X window. Where as QT can run off hardware. Then again GTK can run off of a framebuffer and therefore will not need x window to run. GTK is aimed at gnome where as QT is aimed at KDE. GTK supports more languages. If your a C++ programmer use QT. Contrary to what people say about GTKMM, do not use it. It was not built with C++ in mind. QT is more for the OO programmer. These two toolkits would be your best bet. Do not use a perl UI toolkit if you want portability.

EDIT: IMHO, if your going to be writting GUI programs, why bother with an crutch like Glade that does a lot of the work for you? Use the command line. Glade adds a bunch of unnecessary garbage to the code anyway.

---

### Post by MG&amp;TL on 2012-09-25
> Like the GTK toolkit is great for c programmers. It is written in C itself.

Great. Doesn't mean nobody else can use it though.

>  Though the toolkit is heavy and depends on X window

Many toolkits are heavy. And GTK+ does not require X windows, it can use multiple backends. Hence why you can run it on windows, wayland (in recent releases), and even in a web browser.

> Where as QT can run off hardware

And GTK+ can't? Cairo is hardware-accelerated.

 > Then again GTK can run off of a framebuffer and therefore will not need x window to run.

How does running off a framebuffer remove a dependency on X? It doesn't have a lot to do with it AFAIK.

 > GTK is aimed at gnome where as QT is aimed at KDE.

To a limited extent, true. However, XFCE, LXDE, and many others all use GTK+. RazorQt uses Qt.

> If your a C++ programmer use QT. Contrary to what people say about GTKMM, do not use it. It was not built with C++ in mind.

Gtkmm was built as a C++ wrapper. In what way was it not built with C++ in mind? If you mean that GTK+ was not built with C++ in mind, then I agree with you. However, Gtkmm is a perfectly acceptable wrapper around a solid base.

> These two toolkits would be your best bet.

Why so? There are plenty of cross-platform stable GUI toolkits. Wxwidgets spring to mind.

> Do not use a perl UI toolkit if you want portability.

I don't know enough about this to comment properly, but it would apear that Perl runs on pretty much everything.

> EDIT: IMHO, if your going to be writting GUI programs, why bother with an crutch like Glade that does a lot of the work for you?

Doing work for you is not a bad thing. You'd prefer to write directly to screen with Xlib or whatever?

>  Use the command line

Er....what?

> Glade adds a bunch of unnecessary garbage to the code anyway. 

It looks like XML to me...previous versions had code generation, but that was designed to be minimal anyway, so I'm not really sure what you're on about.


Sorry to be so negative, but I'm not really sure where you're coming from. Hope you're not offended. :)

---

### Post by vexorian on 2012-09-25
OOP is merely one of many paradigms that works mildly correct in c++. It can work with C libraries just fine (better than most other languages).

---

### Post by mr john on 2012-09-25
If it's an alternative to visual basic for making GUI's then I would try GAMBAS. I'll probably get flamed for recommending a Visual Basic type language over a C type language, but whatever.


> 

sudo apt-get install gambas2
sudo gambas2



The reason why you start Gamabas with sudo is so that you can use the examples scripts that installed in non-writeable folders. Technically you could change the permissions of those files instead.

Alternatively, if you want to learn a language that is cross platform and used on over a billion devices then Java is pretty good. And once you learn java it's easy to learn other programming languages. I highly recommend the book "Java by Dissection". People used to say Java is slow but it's performance has increased greatly in many operating systems over the last few years. It can do desktop apps but it's also the number one language for mobile device and tablet applications.

---

### Post by josephmills on 2012-09-25
My list 

-C++/QT/Qt Quick 
-GO
-python

---

### Post by forrestcupp on 2012-09-26
> **MG&TL said:**
> Why so? There are plenty of cross-platform stable GUI toolkits. Wxwidgets spring to mind.wxWidgets is awesome. I've used it a lot in Windows because it's much easier than winAPI. But I'm pretty sure that in Linux, it uses GTK controls, doesn't it? If it uses GTK under the hood, I really don't think it's any easier to use than GTK+ or its wrappers. But then again, wxWidgets is probably better for cross-platform stuff than GTK+ is.


> **MG&TL said:**
> Doing work for you is not a bad thing. You'd prefer to write directly to screen with Xlib or whatever?
Personally, I prefer to not have things like Glade write my code for me. I have my own style of coding, and GUI editors, like Glade, *never* generate the code how I like it. That's why I'd rather just write it myself and use my head and trial & error for the positioning and settings of the controls. But I definitely see why people would want to use things like Glade, and I have used them myself for jobs I just wanted to get done real quick.

> **mr john said:**
> Alternatively, if you want to learn a language that is cross platform and used on over a billion devices then Java is pretty good. And once you learn java it's easy to learn other programming languages. I highly recommend the book "Java by Dissection". People used to say Java is slow but it's performance has increased greatly in many operating systems over the last few years. It can do desktop apps but it's also the number one language for mobile device and tablet applications.Java is an awesome, cross-platform language, and it's cool that it includes Swing for the GUI stuff. My only complaint it that its GUI implementations look like butt, and not native at all.

---

### Post by MG&amp;TL on 2012-09-26
> **forrestcupp said:**
> 
Personally, I prefer to not have things like Glade write my code for me. I have my own style of coding, and GUI editors, like Glade, *never* generate the code how I like it. 

That's the thing, it doesn't anymore. It **used** to, but now it produces an XML-like file that you can load with GtkBuilder. Which is:

a) Pretty cool.

b) Separates GUI design from implementation.

c) Means designers can work separately to programmers (at least in theory).

...so IMO it's a good thing. But I can see where you're coming from, the normal GUI code generation from IDEs (Visual Studio, I'm looking at you!) is horrible.

And Java does look 'like butt'. Which, I confess, is the reason I don't use it. My layout is bad to start with, if you add grey buttons on grey backgrounds with really weird borders....

---

### Post by jrog on 2012-09-26
+1 to "Java looks like butt" :D

---

### Post by forrestcupp on 2012-09-26
> **MG&TL said:**
> That's the thing, it doesn't anymore. It **used** to, but now it produces an XML-like file that you can load with GtkBuilder. Which is:

a) Pretty cool.

b) Separates GUI design from implementation.

c) Means designers can work separately to programmers (at least in theory).

...so IMO it's a good thing. In that case, I hate it even more. Android SDK does things the same way, and I hate it. I can definitely see the benefit in doing things that way, but I guess I'm stubborn and old school. I'll probably have to bite the bullet and give in to the Xml way of doing things, though.

> **MG&TL said:**
> But I can see where you're coming from, the normal GUI code generation from IDEs (Visual Studio, I'm looking at you!) is horrible.I'm looking at wxBuilder, too.

---

### Post by vexorian on 2012-09-26
> **jrog said:**
> +1 to "Java looks like butt" :D
There are GTK wrappers for Java just like there are GTK wrappers for most mainstream languages. Thus you can make native GTK apps that just happen to run their code in the Java VM.

You can also make SWING applications use GTK's color scheme too. The main problem with the latter approach is that the global menu won't work.

---

### Post by jrog on 2012-09-26
> **vexorian said:**
> There are GTK wrappers for Java just like there are GTK wrappers for most mainstream languages. Thus you can make native GTK apps that just happen to run their code in the Java VM.

You can also make SWING applications use GTK's color scheme too. The main problem with the latter approach is that the global menu won't work.
True; I was mostly just having fun, though the *native* look of Java applications really is ugly.

---

### Post by vexorian on 2012-09-26
But it is equally ugly in every platform. Which makes them good at that cross platform stuff.

---

### Post by MG&amp;TL on 2012-09-26
> **vexorian said:**
> But it is equally ugly in every platform. Which makes them good at that cross platform stuff.

I am **so** quoting that next time this comes up. :)

---

### Post by rg4w on 2012-09-26
> **ki4jgt said:**
> I've been looking for a Linux replacement to BASIC.
Have you considered RealBasic?

I believe they have an IDE for Linux along with their Mac and Win versions, and while it's proprietary it has a good reputation.

Another GUI IDE I very much enjoy is LiveCode, from runrev.com.  Very unusual language, but I also find it unusually productive to work with.

---

### Post by josephmills on 2012-09-26
This is a top 20 list,Of the many reasons Why I think that qml is the future 
QML(qt-quick)

1) The IDE is top notch (qt creator)

2) The coding is super super simple

3) It can use C++, javascript, xml , html5 

4) There is a Plug-in for Gimp This cuts down on design ten fold
[http://www.youtube.com/watch?v=AzYKHbRWI2o](http://www.youtube.com/watch?v=AzYKHbRWI2o)

5) The Documentation that is under the help section is the best that there is out there

6) There are examples everywhere

7) you dont have to be crazy smart to learn qml

8) opengles and opengl are great and making and qt-quick2 has both  and rendering is super easy
[http://www.youtube.com/watch?v=SMRln8FJvKc](http://www.youtube.com/watch?v=SMRln8FJvKc)
[http://www.youtube.com/watch?v=P4kv-AoAJ-Q](http://www.youtube.com/watch?v=P4kv-AoAJ-Q) 

9) States and Transtions are just about as simple as 1,2,3 in Qt-quick 
[http://www.youtube.com/watch?v=UjjIk4e_6Q4](http://www.youtube.com/watch?v=UjjIk4e_6Q4)

10) qt3d is included and super super easy 
[http://www.youtube.com/watch?v=VvQ_NHKtHwE](http://www.youtube.com/watch?v=VvQ_NHKtHwE) 

11) QT-quick works on 
windows 
mac 
linux 
arm (yes pi)
embedded linux 
MeeGo/Harmattan/SDK

12) Integration of any version control, 
GIT 
BZR
Mircurial
Subversion 
Perforce 
CVS

13) IMHO qtcreator has the best syntax highlighting and snippets out there for a IDE You can also add anything from kate for like make or python or css highlighting 

14) It is under the lgpl 

15) Having valgrind to look for mem holes is great esp when it is in the IDE itsself

16) declarative views
[http://qt-project.org/doc/qt-4.8/qdeclarativeexamples.html](http://qt-project.org/doc/qt-4.8/qdeclarativeexamples.html)

17) sql in programs 
[http://qt-project.org/doc/qt-4.8/declarative-sqllocalstorage.html](http://qt-project.org/doc/qt-4.8/declarative-sqllocalstorage.html)

18) It is in Ubuntu software Center (IDE and libs)

19) C++ plugins 
[http://qt-project.org/doc/qt-4.8/declarative-cppextensions-plugins.html](http://qt-project.org/doc/qt-4.8/declarative-cppextensions-plugins.html)

20) It is just so dang easy

---

### Post by Sslaxx on 2012-09-26
> **rg4w said:**
> Have you considered RealBasic?

I believe they have an IDE for Linux along with their Mac and Win versions, and while it's proprietary it has a good reputation.

Another GUI IDE I very much enjoy is LiveCode, from runrev.com.  Very unusual language, but I also find it unusually productive to work with.
Another BASIC out there is FreeBASIC. No IDE, but it's a fully-functional, open source BASIC compiler. [http://www.freebasic.net/](http://www.freebasic.net/)

---

