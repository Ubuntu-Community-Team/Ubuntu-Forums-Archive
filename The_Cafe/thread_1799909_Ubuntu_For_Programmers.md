---
title: "Ubuntu For Programmers"
date: 2011-07-08
forum: The Cafe
---

### Post by raja.genupula on 2011-07-08
we have many types of Ubuntu. What if we have a Ubuntu only for programmers and developers . i mean with  programming languages, database's ,IDE's and packaging tools.

---

### Post by ki4jgt on 2011-07-08
You may have something, or you may not. Personally, I wouldn't use. For some reason I have a problem going with anything that's not Ubuntu official release. It's not b/c I'm afraid of security (which I am a little) but b/c I'm a person who likes using the original and customizing it to my own specifications. I also wouldn't use if it was completely programmer centric b/c Ubuntu is a little bit of this, and a little bit of that. Listening to music, watching Youtube, playing games they all inspire me to think differently when I program. They get my mojo started. Not to mention, most programmers need certain things which are related to the current programming project they're doing. There's no way of knowing what they need. What would truly be interesting though would be, if you developed a script, which allowed the user to choose their programming language of choice, and you installed the most popular/best all around applications used for that particular language.

So:

Choose a language:
a: C/C++
b: Java
c: Python
d:
e:

choice: B
. . . Installing Java packages


Of course this is all my (Humble) opinion. It doesn't set the user up thinking they have all they need and then force them to need more, if the support they need isn't there, in other words they know what support is available to them on their system. It allows them to use their system for other things (besides programming), it allows users who have never programmed to know what tools are popular and what tools just altogether stink.

I could see it as a script, but not as an OS sorry, I just don't see it. I could be totally wrong on this, so I'm not putting you down or anything. If you see a need for it, build it, but, with all the packages you have at your disposal in the repos. I would just build a script.

---

### Post by raja.genupula on 2011-07-08
i had used Ubuntu without internet upto 18months .i installed nothing and programmed nothing . for everything i had used windows (java , IDE's).what if we provide, i am sure it will be useful.

---

### Post by BrokenKingpin on 2011-07-08
I am sure most programmers (including myself) would prefer just to install what they need. If you just try and cover off all types of development and languages, you will just end up with a bloated system with the developer only using the one IDE. It is just easier for the programmer to take 2 mins and apt-get the the IDE and tools they need for the job.

---

### Post by juancarlospaco on 2011-07-08
Vim and Python already come built-in...  :P

---

### Post by IWantFroyo on 2011-07-08
I would prefer just using normal Ubuntu. Along with my programming stuff, I use my computer for daily use too. Also, I want to choose my own tools. I just use Kate or Gedit, anyways.

---

### Post by unknownPoster on 2011-07-08
There are distributions that allow you to install the development packages during your initial install. 

Arch, Fedora, CentOS and RedHat are some examples. 

But as someone else said, covering all development environment situations would be near impossible. 

For web development, you'd need to provide the LAMP stack.
Java would need the runtime environments and jdks installed.
C and C++ would need the compilers and debugging tools installed (gdb, valgrind, etc.)
And that's not including the less known, but still used languages like Haskell and LISP.

Then you get into what libraries and toolkits to install on top of the individual language support. How do you decide which of these to install GTK, QT, tkinter, SDL, pygame, etc?

Then you get into IDEs and editors. Eclipse, Netbeans, vim, emacs, geany, nano, kate, gedit, joe, etc, are all potential options.

Ultimately, programmers typically aren't new users, so they'll know what and how to install packages for their needs.

---

### Post by jrothwell97 on 2011-07-08
Ubuntu for Programmers would be like a toolbox for people who want to use screwdrivers.

Make of that what you will.

---

### Post by Bandit on 2011-07-08
sudo apt-get install build-essential 

/thread.. :)

---

### Post by lisati on 2011-07-08
For myself, if I were to get back to programming more regularly, I'd probably use one of the existing flavours of Ubuntu, and install what I need there, particularly if my project is something that I'd want to share with others.

---

### Post by Bandit on 2011-07-08
> **lisati said:**
> For myself, if I were to get back to programming more regularly, I'd probably use one of the existing flavours of Ubuntu, and install what I need there, particularly if my project is something that I'd want to share with others.

Thats pretty much what I like to do, besides if I bother to write something for Ubuntu, I want to make sure its totally compatible. Surest way to do this is the write it on the desktop your writing it for.

---

### Post by pafoo on 2011-07-08
I think as a programer its a decent idea. Think instead a distro with less visual fluff  (no offense), less of everything that takes alot of resources. What if I want a distro that can easily be installed on my old pentium2-4, that would be great to create multiple desktop's/servers with minimal requirements for testing. The closer the Distro gets to user friendly the less tech friendly it gets! Everyone remembers how windows first started as a shell for unix/dos =)

Think instead distro with a ton of tools, a distro with high availability, clarity and minimal impact. A better term would be a "development" distro. Example, why window's created powershell to get windows back to a "development" style environment because developers do not need fluff, we need usability, scalability and access!

---

### Post by Random_Dude on 2011-07-08
> **BrokenKingpin said:**
> I am sure most programmers (including myself) would prefer just to install what they need. If you just try and cover off all types of development and languages, you will just end up with a bloated system with the developer only using the one IDE. It is just easier for the programmer to take 2 mins and apt-get the the IDE and tools they need for the job.

+1
I think programmers prefer to customize what they need, which is more than covered by existing distros, imho.

---

### Post by diesch on 2011-07-08
> **pafoo said:**
> I think as a programer its a decent idea. Think instead a distro with less visual fluff  (no offense), less of everything that takes alot of resources. What if I want a distro that can easily be installed on my old pentium2-4, that would be great to create multiple desktop's/servers with minimal requirements for testing

For testing you usually need a system that is as much like your target users system as possible. And usually it's much ore convenient to use a virtual system than real hardware to that up some testing systems.

There are of course good reasons why one wants to have a distro that runs on a low spec system. But that isn't specific to programmers.

---

### Post by 8_Bit on 2011-07-09
Simpler solution. Make a meta-package that contains all development packages as dependencies. Gcc, Java SDK, Codeblocks, and others all in one metapackage. Problem solved. We need LESS distributions, LESS derivatives, please! Start trying to cooperate and work together with each other instead of splitting off endlessly! It is doing the community no good.

---

### Post by WinterMadness on 2011-07-09
its not necessary, we have ubuntu, just download the things you want.

---

