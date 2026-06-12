---
title: "Installing Visual C++ with wine?"
date: 2011-05-27
forum: Wine
---

### Post by emiller12345 on 2011-05-27
I've got an interesting problem I'd like to propose.  I've love to install Visual C++ Studio Express 2010 (which is free {no cost}, but is not free {closed source}) on my ubuntu with wine.  I've downloaded the VS2010Express1.iso which is the installer, but will not install because of the .NET 4.0 framework.  Does anyone have a walk-through or howto on how to do this?  I could care less right now about the actual IDE, if I can start by compiling and testing from the command line in wine.

---

### Post by doas777 on 2011-05-27
I think you will find that visual studio and the assocaited runtimes are too complicated for wine. 

the Wine AppDB has .net 4 framework rated as "Garbage" so probably not an option. [http://appdb.winehq.org/objectManager.php?sClass=version&iId=17886](http://appdb.winehq.org/objectManager.php?sClass=version&iId=17886)

if you are wanting to do cli compiles anyway, why not use mono/mono-develop for a linux friendly implementation of c#?

---

### Post by emiller12345 on 2011-05-27
I'll look into mono.  I was looking for something to allow me to do cross-compiling other's win32 cpp code. A lot of code won't compile with mingw32.

---

### Post by psusi on 2011-05-27
IIRC, doing so violates the license agreement.  I seem to remember it stipulating that you use it on windows to develop software for windows.

---

### Post by Ran222 on 2011-06-02
Hello,

What is working:

I have visual C++ 6.0 (yes, the old one) and it works
ok on ubuntu koala 9.04.
I need VC++, so I use 9.04.
Never did try programming in directx but opengl for instance is compiling and running ok.
I did try ubuntu 10.4..... and newer,  it works but not ok, restarts ubuntu, graphics missing....

Greetings,

Ran222

---

### Post by bobwyajnr on 2011-06-02
> **Ran222 said:**
> Hello,

What is working: ...

[B]
Stop, right there!! Fin! Thread HIJACK detected![/B] :popcorn:


@**emiller12345**

RE Visual Studio is definitely a VirtualBox job and will be for a long time... All the .net/mono stuff is quite 'evil' from what I gather...

I am still investigating native Linux IDE's so I cannot comment too much on them.

Currently I am using [CodeBlocks]("http://www.codeblocks.org/") - which is OK. I've been using it to teach myself a bit about the Boost libraries and Gtk programming. Nothing to right home about... But it does the job!

Bob

P.S. **Ran222**, get it together and start a new thread please...

---

