---
title: "Help me chose a programming language and IDE"
date: 2011-12-07
forum: The Cafe
---

### Post by kio_http on 2011-12-07
I want to start developing GUI applications for Ubuntu and maybe later have database functionality to. 

I would prefer using QT but don't mind GTK as well.
I have quite a lot of experience in Vb.net on Windows.

Essentially I was something that does not necessarily have a vb.net like syntax (although I would like that) but works in a similar manner. The language should have an IDE available that is easy like Visual Studio 2010. I want functionality like intellisense and interoperability between the GUI designer and code view. E.g clicking a button in designer automatically creates the code for a click event.

The language should not be too complicated to learn (I like the way that you don't have to really bother about memory allocation etc with vb.net) and should have a good amount of easy to follow tutorials books and examples.

The key thing here is the designer/ code functionality being similar to Visual Studio. In visual studio I learnt how to write GUI apps before CLI ones.

Also another question, if I learn visual C++ on Windows using Microsoft's tutorials will I be able to easily learn QML and work with qtcreator?

---

### Post by forrestcupp on 2011-12-07
> **kio_http said:**
> 
Also another question, if I learn visual C++ on Windows using Microsoft's tutorials will I be able to easily learn QML and work with qtcreator?

It sounds like you already answered part of your question. You should learn C++ and use the IDE that comes with Qt, called Qt Creator.

C++ with winAPI tutorials are going to be completely different than learning to program in C++ with Qt. I mean *completely* different. Don't waste your time. 

The good news is that Qt is *way* easier to learn that winAPI. You need to find some online tutorials for plain ol' C++ for the console first. [Here is a decent one](http://www.cplusplus.com/doc/tutorial/) you could check out. I know it's tedious, and not what you want to be doing, but you have to learn the basics of C++ before you can just start programming a GUI. After you start getting that down, then you can find some tutorials for Qt. When you get to that point, things will start to get more fun, but you have to lay the groundwork first.

C++ is much different than VB. But having VB background will help you a lot more than not having any background at all. Have fun.

Also, you can program Qt in Windows using Qt Creator. So you should be able to learn it in Windows and carry it over to Linux. You just need to recompile your apps for each platform.

---

### Post by Bodsda on 2011-12-07
Microsoft continues to teach new developers bad habits and laziness... *sigh*

---

### Post by F.G. on 2011-12-07
> **forrestcupp said:**
> It sounds like you already answered part of your question. You should learn C++ and use the IDE that comes with Qt, called Qt Creator.

C++ with winAPI tutorials are going to be completely different than learning to program in C++ with Qt. I mean *completely* different. Don't waste your time. 

The good news is that Qt is *way* easier to learn that winAPI. You need to find some online tutorials for plain ol' C++ for the console first. [Here is a decent one](http://www.cplusplus.com/doc/tutorial/) you could check out. I know it's tedious, and not what you want to be doing, but you have to learn the basics of C++ before you can just start programming a GUI. After you start getting that down, then you can find some tutorials for Qt. When you get to that point, things will start to get more fun, but you have to lay the groundwork first.

C++ is much different than VB. But having VB background will help you a lot more than not having any background at all. Have fun.

Also, you can program Qt in Windows using Qt Creator. So you should be able to learn it in Windows and carry it over to Linux. You just need to recompile your apps for each platform.
i agree with forrestcupp, QTCreator is pretty straight forward and easy to use. also i think qt generally requires less code than gtk. c++ is a big language to learn, but a pretty good way to learn about programming. 

another choice could be python and qt4, using the pyqt4 module, although then you don't get the easy to use QT Creator so that's probably not for you (although python is quite a fun and easy language to learn). recently i've been learning some TCL/TK, which is a cross-platform programming language/framework, which uses the native look of the OS, you can make a 'hello world' GUI application in about three or four lines of code.  this seems to be a bit of an obscure language though. anyhow, I digress...

i'd definitely have a go at C++ and QTCreator (learning c++ alone will be pretty helpful).

---

### Post by trivialpackets on 2011-12-07
I would take a few moments to check out [http://developer.ubuntu.com/](http://developer.ubuntu.com/), python and quickly.  Pretty neat environment and development flow.

---

### Post by forrestcupp on 2011-12-07
> **Bodsda said:**
> Microsoft continues to teach new developers bad habits and laziness... *sigh*

We need you to give us the code to your Try() function. ;)

---

### Post by kio_http on 2011-12-07
> **forrestcupp said:**
> It sounds like you already answered part of your question. You should learn C++ and use the IDE that comes with Qt, called Qt Creator.

C++ with winAPI tutorials are going to be completely different than learning to program in C++ with Qt. I mean *completely* different. Don't waste your time. 

The good news is that Qt is *way* easier to learn that winAPI. You need to find some online tutorials for plain ol' C++ for the console first. [Here is a decent one](http://www.cplusplus.com/doc/tutorial/) you could check out. I know it's tedious, and not what you want to be doing, but you have to learn the basics of C++ before you can just start programming a GUI. After you start getting that down, then you can find some tutorials for Qt. When you get to that point, things will start to get more fun, but you have to lay the groundwork first.

C++ is much different than VB. But having VB background will help you a lot more than not having any background at all. Have fun.

Also, you can program Qt in Windows using Qt Creator. So you should be able to learn it in Windows and carry it over to Linux. You just need to recompile your apps for each platform.

I do use Win API sometimes also I know C# but don't regularly use it. How is monodevelop for C# and vb.net?

---

### Post by jjex22 on 2011-12-07
> **forrestcupp said:**
> [Here is a decent one](http://www.cplusplus.com/doc/tutorial/) you could check out. I know it's tedious, and not what you want to be doing, but you have to learn the basics of C++ before you can just start programming a GUI. After you start getting that down, then you can find some tutorials for Qt. When you get to that point, things will start to get more fun, but you have to lay the groundwork first.

C++ is much different than VB. But having VB background will help you a lot more than not having any background at all. Have fun.


I'm really new to coding - I've been hobby-ing it since summer, so I don't have the experience of the other guys, but I took their advice and started with C++, so from a noob's, perspective, forrestcupp is spot on - I've been using [cplusplus.com]("http://www.cplusplus.com") as forrestcupp suggests, as well as [cprogramming.com]("http://www.cprogramming.com/") and [learncpp.com]("http://www.learncpp.com/") together - switching from one to the other - I find both the repetition and the fact that they explain things in different ways really helps!

If I had to pick one, it'd be cprogramming, becuause of the end of unit quizes, but learncpp is definately the kindest to the utter noob! 

You obviously have a lot more experience than I do (I used BASIC on the C64 when I was a little person!) but if you are new to c and c++, these may really help :)

---

### Post by Dragonbite on 2011-12-07
> **eric.proctor said:**
> I would take a few moments to check out [http://developer.ubuntu.com/](http://developer.ubuntu.com/), python and quickly.  Pretty neat environment and development flow.

Wow, that looks pretty cool!  Thanks for the link!

---

### Post by lykwydchykyn on 2011-12-07
You can try kdevelop, I think it supports languages other than c++ and has tools for developing KDE applications.

If you want to go the PyQT route there's Eric; it has many of the features you mentioned, though IMO the interface is a disaster.  

Personally, after trying a lot of IDE, I ended up just using Emacs and hand-coding the GUIs (using PyQT).  It ultimately less work IMO, especially with PyQT (other languages/toolkits maybe not, I don't know). YMMV.

---

### Post by forrestcupp on 2011-12-07
> **kio_http said:**
> I do use Win API sometimes also I know C# but don't regularly use it. How is monodevelop for C# and vb.net?

Monodevelop is better for C# than it is for VB. You can't use the form designer with VB.

If you've actually used WinAPI, then you must already know C because that's the language it uses. 

Are you thinking of WinAPI, or are you thinking of .Net, which is a different thing? If you really know WinAPI, then you've programmed in C and you shouldn't have much problem learning C++. The only difference is learning object oriented programming.

---

### Post by F.G. on 2011-12-07
eric.proctor that does look pretty cool and a really good initiative. 

> **forrestcupp said:**
> We need you to give us the code to your Try() function. ;)
hey, so i know that this is off topic, but i was wondering about Bohsda's little code snippet:
```
while(!(succeed = Try()));
```
surely this will work only if Try() returns a boolean (otherwise it would almost always evaluate everything to !(true), and 'true' would be assigned to 'succeed' each iteraton). BUT, if this is the intention then wouldn't:
```
while(!(Try()));
```
work just as well? (just not assign anything to succeed). or alternatively we could have:
```
while(!(succeed == Try()));
```
where the bottoming out condition from Try() and 'succeed' could be anything?
i mean presumably to reflect the sentiment you don't really want 'succeed' to be modified by the output of Try(). unless your willing to change your standards of success.

sorry again for going off topic. also i would recommend (as well as online stuff), if you like books: "schuam's outline of programming with C++".

---

### Post by boazjones on 2011-12-07
C++ - n'est-ce pas?

---

### Post by juancarlospaco on 2011-12-07
I think theres no 1 answer to this question.

Anyways, if it useful to you, i choose...
For language: [http://python.org](http://python.org)
For Development IDE i use: [http://ninja-ide.org](http://ninja-ide.org)
For GUI i use HTML5: [http://www.html5rocks.com](http://www.html5rocks.com)
QML now also renders on-the-fly to HTML5 too: [https://gitorious.org/qmlweb/pages/Home](https://gitorious.org/qmlweb/pages/Home)
If you want a WYSIWIG IDE Point'n'Click RAD: [http://maqetta.org/](http://maqetta.org/)

I think theres no better GUI than HTML5, looks amazing on any device/os/whatever,
because you dont even need to know Programming, you cant program on HTML5,
its just a markup, like writing into a Wiki, or writing an XML, it always Display.

For Heavy Processing on Backend i use:
[http://bottlepy.org](http://bottlepy.org) or [https://www.djangoproject.com](https://www.djangoproject.com)

How a GUI looks like on HTML5 ...?, see yourself

[IMG]https://lh3.googleusercontent.com/-iuYUxz0FQb4/TsmIwOTSoTI/AAAAAAAAA0s/FCunGAzO6mo/s640/nethelper3.jpg[/IMG]

[IMG]https://lh3.googleusercontent.com/-45KQMrz-rvQ/TsazwakNkUI/AAAAAAAAA0I/Spv6BJtA0tY/s640/imgappalone.jpg[/IMG]

They are Real working apps, no Mockup, no Gimp :)

---

### Post by Bodsda on 2011-12-07
> **F.G. said:**
> eric.proctor that does look pretty cool and a really good initiative. 


hey, so i know that this is off topic, but i was wondering about Bohsda's little code snippet:
```
while(!(succeed = Try()));
```surely this will work only if Try() returns a boolean (otherwise it would almost always evaluate everything to !(true), and 'true' would be assigned to 'succeed' each iteraton). BUT, if this is the intention then wouldn't:
```
while(!(Try()));
```work just as well? (just not assign anything to succeed). or alternatively we could have:
```
while(!(succeed == Try()));
```where the bottoming out condition from Try() and 'succeed' could be anything?
i mean presumably to reflect the sentiment you don't really want 'succeed' to be modified by the output of Try(). unless your willing to change your standards of success.

sorry again for going off topic. also i would recommend (as well as online stuff), if you like books: "schuam's outline of programming with C++".

Yes, you could code the loop condition 3 ways and get the same result. The reason it is how it is is down to what part gets evaluated.

In my version, it is evaluating the value of succeed (To see if I have succeeded)
In the second version it is evaluating the return Value of Try  (To see how well I tried???)
In the third it is evaluating if the return value of Try equals a predetermined value of succeed (To see if I achieved what I expected???)

Only the first one makes sense when you read it as english.

Bodsda

---

### Post by forrestcupp on 2011-12-07
> **F.G. said:**
> 
hey, so i know that this is off topic, but i was wondering about Bohsda's little code snippet:
```
while(!(succeed = Try()));
```
surely this will work only if Try() returns a boolean (otherwise it would almost always evaluate everything to !(true), and 'true' would be assigned to 'succeed' each iteraton). BUT, if this is the intention then wouldn't:
```
while(!(Try()));
```
work just as well? (just not assign anything to succeed). or alternatively we could have:
```
while(!(succeed == Try()));
```
where the bottoming out condition from Try() and 'succeed' could be anything?
i mean presumably to reflect the sentiment you don't really want 'succeed' to be modified by the output of Try(). unless your willing to change your standards of success.

If you leave succeed out, you lose the whole joke of making code out of the saying "If at first you don't succeed, try, try again." ;)

The way he has it assumes that **succeed** is a bool variable and Try() returns a bool. So you're filling **succeed** with the return value of Try() and testing whether **succeed** is true or false. If it is false, then keep filling it with Try() and testing until it is true.

If you use !(succeed == Try()), then succeed never changes. You're just comparing whatever the current value of **succeed** is to the return value of Try(), and if **succeed** happens to not be equal to the return value of Try(), then you're stuck in an endless loop.

---

### Post by BrokenKingpin on 2011-12-07
> **kio_http said:**
> 
I would prefer using QT but don't mind GTK as well.
I have quite a lot of experience in Vb.net on Windows.

MonoDevelop with C# .Net (or event VB .Net I think). With the mono develop IDE you get a build in GTK designer, which makes it very easy to create GTK applications. If you are coming from VB.Net and Visual Studio you will feel right at home (the solution files are compatible between the two IDEs as well).

With Monodevelop I have written C# GTK applications that work on both windows and Linux without issues. It is great for .Net developers migrating to Linux.

---

### Post by F.G. on 2011-12-07
I see! you're evaluating if 'success' is true, which is determined (assigned to) by each 'Try()' (and then you keep trying if it isn't). i wonder if i could stick this into my own code and recompile myself.

sorry for derailing your thread, kio_http.

---

### Post by forrestcupp on 2011-12-07
> **F.G. said:**
> I see! you're evaluating if 'success' is true, which is determined (assigned to) by each 'Try()' (and then you keep trying if it isn't). i wonder if i could stick this into my own code and recompile myself.

sorry for derailing your thread, kio_http.

Very good, Grasshopper! :)

You could put it in your own code, but you'd have to come up with code to put into the Try() function that would eventually return true. ;)

---

### Post by F.G. on 2011-12-07
> **forrestcupp said:**
> Very good, Grasshopper! :)

You could put it in your own code, but you'd have to come up with code to put into the Try() function that would eventually return true. ;)
you mean a life goal, a spiritual ideal, a professional objective?
i guess even if it doesn't return true at least i could say i Try()ed.

---

### Post by juancarlospaco on 2011-12-07
```

from Trollib import OffTopic
OffTopic.stop()
```

---

### Post by Majorix on 2011-12-07
I too have written quite a lot of code on Visual Studio, using C# mainly. After switching to Linux I found Netbeans to be the IDE most resembling VS. With Netbeans you can create Java applications (with a GUI, if necessary) pretty much like the way you did on VS. For the language of choice, I suggest Java, which works perfectly with Netbeans, and you will soon be creating applications that can be executed on all major operating systems.

---

### Post by forrestcupp on 2011-12-07
> **Majorix said:**
> I too have written quite a lot of code on Visual Studio, using C# mainly. After switching to Linux I found Netbeans to be the IDE most resembling VS. With Netbeans you can create Java applications (with a GUI, if necessary) pretty much like the way you did on VS. For the language of choice, I suggest Java, which works perfectly with Netbeans, and you will soon be creating applications that can be executed on all major operating systems.

The only problem with Java and Swing is that the GUI looks like butt.

---

### Post by directhex on 2011-12-08
> **forrestcupp said:**
> The only problem with Java and Swing is that the GUI looks like butt.

and eats **ALL** the RAM

---

### Post by BrokenKingpin on 2011-12-08
> **Majorix said:**
> I too have written quite a lot of code on Visual Studio, using C# mainly. After switching to Linux I found Netbeans to be the IDE most resembling VS. With Netbeans you can create Java applications (with a GUI, if necessary) pretty much like the way you did on VS. For the language of choice, I suggest Java, which works perfectly with Netbeans, and you will soon be creating applications that can be executed on all major operating systems.
Netbeans is a good IDE, but if you were a C# developer why not use MonoDevelop (which is very similar to VS as I already stated), and you can still code in c#?

---

### Post by bharatchhajer on 2011-12-12
I would suggest Java programming Language, Since it is easy compared to C++ which has some difficult concepts like pointers. Which ever lanugage you use C++, Java or Python, they are all Object Oriented Programming Languages. There is good pictorial and text explanation of Object Oriented Programming Concept in Java at [http://www.javasprint.com/java_training_tutorial_blog/object_oriented_programming_oops.htm](http://www.javasprint.com/java_training_tutorial_blog/object_oriented_programming_oops.htm) . Its an explanation with example. There are two diagrams to explain the same in pictures.

---

### Post by kostkon on 2011-12-17
> **kio_http said:**
> I want to start developing GUI applications for Ubuntu and maybe later have database functionality to. 

I would prefer using QT but don't mind GTK as well.
I have quite a lot of experience in Vb.net on Windows.

Essentially I was something that does not necessarily have a vb.net like syntax (although I would like that) but works in a similar manner. The language should have an IDE available that is easy like Visual Studio 2010. I want functionality like intellisense and interoperability between the GUI designer and code view. E.g clicking a button in designer automatically creates the code for a click event.

The language should not be too complicated to learn (I like the way that you don't have to really bother about memory allocation etc with vb.net) and should have a good amount of easy to follow tutorials books and examples.

The key thing here is the designer/ code functionality being similar to Visual Studio. In visual studio I learnt how to write GUI apps before CLI ones.

Also another question, if I learn visual C++ on Windows using Microsoft's tutorials will I be able to easily learn QML and work with qtcreator?
[Gambas]("http://gambas.sourceforge.net/")??

---

### Post by ViperChief on 2011-12-19
> **Bodsda said:**
> Microsoft continues to teach new developers bad habits and laziness... *sigh*

Out of curiosity, how is Microsoft teaching anyone anything here? A student of any language can learn bad habits from any teacher or on their own. A student learning C++ while using Linux could learn bad habits, as well. If you're talking about the things that VS brings to the table, this is still an unfair generalization. VS and other IDE's bring a lot to the table, helping programmers to do their job more efficiently. While I have learned by starting off with console applications, I'm not going to judge someone's ability based on what language they started with or what way they learned (i.e. VS vs CLI & gcc). 

The fact is that someone who starts off with VB or C# using Visual Studio can be just as good, if not better, than someone who started with C in vim. To say otherwise is to assume things that you don't know and just make you look stupid.

Now, having said that, perhaps that's not what you meant. But, I have seen that sentiment many times, so I figured I would just address it. This attitude that you can't be a good programmer if you learn with an IDE or have VB as your first language is a stupid generalization and is unfair to the many good programmers who started off that way. Besides, not everyone wants to sit there writing code starting at vim and like that tools such as Intellisense can help them be more efficient. I know a very good electrical engineer who likes using VB when he can because he feels that it's a lot more efficient and then uses C or C++ when he needs low-level. 

tl;dr: Sitting there bad-mouthing MS over something they have no control over (quality of programmers) makes no sense.

---

### Post by Dragonbite on 2011-12-19
I think he means that the programming languages or IDE can allow people to do things, like not have to worry about case, and that if they move to another, more strict language they will have to re-learn that.

That's my guess. There are other examples but I just can't think of them right now.

---

### Post by ViperChief on 2011-12-19
> **Dragonbite said:**
> I think he means that the programming languages or IDE can allow people to do things, like not have to worry about case, and that if they move to another, more strict language they will have to re-learn that.

That's my guess. There are other examples but I just can't think of them right now.

Wouldn't that be like blaming a word processor for a person's inability to spell or use proper grammar since the program fixes so much?

---

### Post by KiwiNZ on 2011-12-19
> **Bodsda said:**
> Microsoft continues to teach new developers bad habits and laziness... *sigh*

Developers develop bad habits and laziness due to their poor best practices, bad work ethics and lack of professionalism.

Are you going to blame Ford or GM for bad drivers?

---

### Post by Dragonbite on 2011-12-19
> **ViperChief said:**
> Wouldn't that be like blaming a word processor for a person's inability to spell or use proper grammar since the program fixes so much?

Not blaming the word processor, rather auto-correcting spelling. Where if you make a common spelling mistake, it automatically changes the spelling to what it correctly should be (as correct as spell check can be that is ;) ).

Like if you type "hsi" it automatically changes it to "his" for example.  Handy for typing letters, but you never really learn the proper spelling that way.

When I find the red squigly line while typing a forum post, I try and figure out the correct spelling on my own before using it's suggestions.  This way it helps me learn the proper spelling a little bit more.

---

