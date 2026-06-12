---
title: "Where to start, which programming language?"
date: 2009-10-20
forum: The Cafe
---

### Post by jonathanharker on 2009-10-20
Hi there,

I am about to start a research project about shape recognition.  As part of this project, I want to research different operating systems to determine which would be the most efficient at getting the job done.

I wouldn't say that I am a Microsoft fan boy, but I have little-to-no experience of Ubuntu or linux in general.  

My question is simple, what are the common programming tools/languages on Ubuntu?  Windows has Visual studio/delphi/python etc, what do people like to use to develop programs on Ubuntu?

Thanks for reading and (hopefully) responding.

---

### Post by OpenGuard on 2009-10-20
Python, Perl, Java, C/C++, etc. - actually, there are only 2 languages I haven't seen on Linux .. Visual Basic and Delphi.

---

### Post by NoaHall on 2009-10-20
The tools we use are "man" tools. Haha. No, I tend to use Geany for everything, which is basicly a text-editor with syntax colouring etc.
There's gambas for OOP programming, eclipse, code::blocks and blueJ.

The main languages tend to be Java, Python, and C.
The shell languages are Perl and bash/dash. 

I'd say for your project, you should go with Python/Java.

---

### Post by betrunkenaffe on 2009-10-20
Your project seems flawed. You'd have to produce it using the same code which works on all the OS you are using to eliminate coding based productivity variance. Also, would you really be determining which OS does it most efficiently or simply determining which is most efficient with your developped code (which is obviously not optimized for each platform)?

The variables seem extremely hard to eliminate from this equation.

On the programming languages, I like C++, widely available and fairly easy to cross program. There is also widgits for developping Linux based app GUIs much like Visual C++ Express.

I've never done a GUI in Linux so no expert on that, all my work has been on making the console stuff so someone else can GUI it :)

Quote: I'd say for your project, you should go with Python/Java. << Python would also be good. Not a fan of Java when comparing efficiency, you are already behind.

---

### Post by openfly on 2009-10-20
openframeworks or processing seem to be the preferred methods for easy shape recognition apps.

---

### Post by Xbehave on 2009-10-20
> **OpenGuard said:**
> I haven't seen on Linux .. Visual Basic and Delphi.
[delphi]("http://en.wikipedia.org/wiki/Kylix_%28software%29") (closed) and died circa 2006 (even wikipeida says it sucked, but it can be got running on recent distros)
[visual basic]("http://en.wikipedia.org/wiki/Mono_%28software%29"), only VB.net.

Now you've seen everything :P

> I am about to start a research project about shape recognition. As part of this project, I want to research different operating systems to determine which would be the most efficient at getting the job done.
1) Is this project going to be open source?
1a) If so, What license? there are a few similar projects you might be interested in.
1b) if not will it never be distributed?
2) What do you mean by efficient?
2a)If you mean computational efficiency then obviously hand crafted assembly is the fasted,then C,then C++,then Java,then python/perl,etc
2b)If you want ease of coding, then as this will probably be OO and complex, so you can drop C (unless your a sadist), if you plan on threading then drop python (It's the only language i know well but the global interpreter lock hurts threading), this leaves you with C++/C#,java and a few others to look at. You should note that similar projects tend to use java, it may be for a good reason or it may just be that is what they got their AI courses in, either way it's something to look into.

tl;dr use java

---

### Post by OpenGuard on 2009-10-20
> **Xbehave said:**
> [delphi]("http://en.wikipedia.org/wiki/Kylix_%28software%29") (closed) and died circa 2006 (even wikipeida says it sucked, but it can be got running on recent distros)
[visual basic]("http://en.wikipedia.org/wiki/Mono_%28software%29"), only VB.net.

Now you've seen everything :P


I thought Mono was just for C# :rolleyes: Live and learn!
Anyway, thanks for the link to Kylix .. will give it a read a bit later on today.

---

### Post by betrunkenaffe on 2009-10-20
> **Xbehave said:**
> 
 if you plan on threading then drop python (It's the only language i know well but the global interpreter lock hurts threading),

Heard about stack less python a while back, it's supposed to be developed for threading. Assumed there was Linux implementation, no?

---

### Post by Dragonbite on 2009-10-20
> **OpenGuard said:**
> Python, Perl, Java, C/C++, etc. - actually, there are only 2 languages I haven't seen on Linux .. Visual Basic and Delphi.

Visual Basic is also from [[COLOR="Blue"]Gambas[/COLOR]]("http://gambasrad.org/") which has done a pretty good job of VB 6 (classic) syntax.

Mono is alright for VB.NET, but Monodevelop does not include a GUI builder for VB.NET, but it does for C#.

For VB.NET there is also KBasic, though it is a slightly modified VB.NET. For more transferable VB.NET I would use Mono which can be developed in Monodevelop or you can use Visual Studio and use MOMA to test that the code is Mono compatible (and where it fails so you can fix it).

---

### Post by jonathanharker on 2009-10-20
> **Xbehave said:**
> []("http://en.wikipedia.org/wiki/Kylix_%28software%29")

1) Is this project going to be open source?
1a) If so, What license? there are a few similar projects you might be interested in.
1b) if not will it never be distributed?
2) What do you mean by efficient?
2a)If you mean computational efficiency then obviously hand crafted assembly is the fasted,then C,then C++,then Java,then python/perl,etc
2b)If you want ease of coding, then as this will probably be OO and complex, so you can drop C (unless your a sadist), if you plan on threading then drop python (It's the only language i know well but the global interpreter lock hurts threading), this leaves you with C++/C#,java and a few others to look at. You should note that similar projects tend to use java, it may be for a good reason or it may just be that is what they got their AI courses in, either way it's something to look into.

tl;dr use java

1) The project will be open source, although this project will lean more towards research than actual programming
1a) Probably [GNU General Public License (GPL)]("http://www.opensource.org/licenses/gpl-2.0.php")
1b) it will be distributed, to help anybody else who may be doing something similar
2) By efficiency, I mean I want to keep overheads to a minimum.  I wrote a simple program in c# to look at pixel patterns on a 350x350 black and white image.  Its fair to say that I am resonably competent with C# and write quite efficent code.  However, i found it was achieving a mere 2-3 frames per second.  I would like it to be at least 10 frames per second.

Do you say Java just because its easy to write and because its cross-OS compatible.  Or because there are legimate benefits to developing in it.

---

### Post by Dragonbite on 2009-10-20
> **jonathanharker said:**
> 2) By efficiency, I mean I want to keep overheads to a minimum.  I wrote a simple program in c# to look at pixel patterns on a 350x350 black and white image.  Its fair to say that I am resonably competent with C# and write quite efficent code.  However, i found it was achieving a mere 2-3 frames per second.  I would like it to be at least 10 frames per second.

If you are already experienced with C#, then I would lean towards Mono since it will use this knowledge, be cross platform (there's even a Mac version of Mono) and you can fall back to Visual Studio if necessary.

---

### Post by Warpnow on 2009-10-20
> **jonathanharker said:**
> Hi there,

I am about to start a research project about shape recognition.  As part of this project, I want to research different operating systems to determine which would be the most efficient at getting the job done.

I wouldn't say that I am a Microsoft fan boy, but I have little-to-no experience of Ubuntu or linux in general.  

My question is simple, what are the common programming tools/languages on Ubuntu?  Windows has Visual studio/delphi/python etc, what do people like to use to develop programs on Ubuntu?

Thanks for reading and (hopefully) responding.

Compile something in gcc then in visual c and I think it will be apparent which is faster.

---

### Post by Daveski on 2009-10-20
> **jonathanharker said:**
> 1)
2) By efficiency, I mean I want to keep overheads to a minimum.  I wrote a simple program in c# to look at pixel patterns on a 350x350 black and white image.  Its fair to say that I am resonably competent with C# and write quite efficent code.  However, i found it was achieving a mere 2-3 frames per second.  I would like it to be at least 10 frames per second.


I suspect speed is important, so you may have to steer clear of interpreted or intermediate languages. Cross platform and standard, with the speed you need, probably c/c++ is the best option.

---

### Post by rajcan on 2009-10-20
I'd go with python personally. I'm not a fan of the language but it is used a lot for programming nowadays. After you get the idea of programming and OO, probably move onto c or c++. I wouldn't start there cause pointers will kill you. And whatever you do, don't start with a BASIC dialect. You'll get used to that, move onto other languages, and be confused to no end.

---

### Post by sloggerkhan on 2009-10-20
Python or C would be my thoughts.

It'll be a lot harder to start with c than python most likely.

And pointers aren't the devil everyone makes them out to be. They make sense and pretty straightforward in simple uses. It's when people start going crazy with them and do stuff like ***blagh[][] and there's no documentation on what the hell it is that they get irritating.

---

### Post by markbuntu on 2009-10-20
If you learn c/c++ then you will have a solid foundation for programming in any other language and you can always make something in c/c++ to do the things the other languages do too slowly or not at all.

---

