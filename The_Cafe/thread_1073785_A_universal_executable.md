---
title: "A universal executable"
date: 2009-02-18
forum: The Cafe
---

### Post by dragos240 on 2009-02-18
Hello, i am frustrated at the fact that so many programers have to program something an export it into different formats for different os's. Is there a universal executable that any operating can run natively? If so would you use it?

---

### Post by insineratehymn on 2009-02-18
Well... there are a bunch of cross-platform languages. Take java for instance... anything you write in Java will(should) work on Mac like it work on Linux. Although you need a machine to run Java programs, the language is cross platform. There is a standard for cross-platform APIs, POSIX. Although any OS can wantoningly claim they are POSIX-compliant, it doesn't necessarily mean that they are.

Deep question, man.

---

### Post by kavon89 on 2009-02-18
Not really no. You'd need a layer or environment for the executable to run inside, then the environment would translate those calls and actions for the specific operating system (open a gui window, make buttons here and here etc) like in Java.

Technically one could make a program in assembly which should work on any x86 processors.

---

### Post by tom66 on 2009-02-18
The only cross platform compiled language I know is Java, but there are hundreds of interpreted languages, such as Python, Perl, PHP... And although not cross platform you can create a Windows executable and use Wine on Linux or Mac (through Darwine, I think), as long as it is a basic app and doesn't rely too much on obscure functions. Or using Cygwin you can get a Linux program working on Windows and possibly more (I'm not sure though).

---

### Post by MaxIBoy on 2009-02-18
> **dragos240 said:**
> Hello, i am frustrated at the fact that so many programers have to program something an export it into different formats for different os's. Is there a universal executable that any operating can run natively? If so would you use it?
Natively? No.


However, Java bytecode will run on any standards-compliant Java VM on any operating system, that's what Java has mostly been used for.

---

### Post by billgoldberg on 2009-02-18
**Is there a universal executable that any operating can run *natively?***

No

(to others, java isn't install OOTB)

**If so would you use it?**

I guess so.

---

### Post by dspari1 on 2009-02-18
> **dragos240 said:**
> Hello, i am frustrated at the fact that so many programers have to program something an export it into different formats for different os's. Is there a universal executable that any operating can run natively? If so would you use it?

JAR files are universal executables. Those are programs written in Java.

---

### Post by Npl on 2009-02-18
> **dspari1 said:**
> JAR files are universal executables. Those are programs written in Java.Java Programms are as portable as Gameboy Games written in Assembler. They need Emulators to run at all and so far the amount of Platforms which have an Gameboy-Emulator >> the amount of platforms that have an Java-Emulator.

---

### Post by klange on 2009-02-18
> **dspari1 said:**
> JAR files are universal executables. Those are programs written in Java.

JAR files are archives. They aren't even executable files to begin with - they simply contain executable Java class files.

And then you still need Java.

And your Java version needs to be compatible.

The closest we have to a real cross-platform universal executable format is CLI-form EXEs (Mono and what not): You can run them on Windows, Linux, Mac, hacked iPhones, Android phones, etc. etc.

---

### Post by Kvark on 2009-02-18
> **kavon89 said:**
> Technically one could make a program in assembly which should work on any x86 processors.
Unix like kernels won't execute EXE files and Windows won't execute ELF files. How do you make one file that both will execute?

If you solve that problem then you can hypothetically run a program without dependencies on both platforms because as you say x86 machine code is the same regardless of OS. Such a program would be useless though as it can't access files or do anything else without calling a library or the kernel. I guess you could perhaps make an executable that contains both a version that depends on Windows components and a Unix version, that when executed attempts kernel calls and chooses version depending on which kernel's calls work.

Or in the real world you could just use Java, Mono or another cross platform technology instead of strictly native executables.

---

### Post by kavon89 on 2009-02-18
> **Kvark said:**
> Unix like kernels won't execute EXE files and Windows won't execute ELF files. How do you make one file that both will execute?

If you solve that problem then you can hypothetically run a program without dependencies on both platforms because as you say x86 machine code is the same regardless of OS. Such a program would be useless though as it can't access files or do anything else without calling a library or the kernel. I guess you could perhaps make an executable that contains both a version that depends on Windows components and a Unix version, that when executed attempts kernel calls and chooses version depending on which kernel's calls work.

Or in the real world you could just use Java, Mono or another cross platform technology instead of strictly native executables.

Yea I was thinking that the program would have to have no dependencies on the machine's operating system and be pretty useless, but it should be able to do hello world and adding predefined numbers etc.

---

### Post by forrestcupp on 2009-02-18
> **tom66 said:**
> The only cross platform compiled language I know is Java,

I wouldn't call bytecode truly compiled.  It's better than interpreted, but not really compiled.  I don't think it would be possible to truly compile any language to machine code that would work on multiple OS's.

But if there were some universal thing that didn't have to be compiled, I wouldn't use it.  You would have to assume that people would have that specific run time module installed in order to run your program.  Also, it wouldn't be nearly as fast as compiled code.  Those are the reasons I quit programming in .Net a long time ago.

The best we can do is program in C++ with something like wxWidgets where you can have one set of code, and just compile that code on multiple platforms.

And in my opinion, most Java apps look like crud.

---

### Post by [h2o] on 2009-02-18
I don't think the format of the executable is the problem. The different inner workings of the operating system (system calls, to name one thing), libraries, etc is the real problem.

---

### Post by maybeway36 on 2009-02-18
You could write it for DOS and stick it on a boot CD, but then you'd need drivers.
There's also wine for Linux/BSD/Mac and the Linux compatibility layer for FreeBSD.

---

### Post by [h2o] on 2009-02-18
> **forrestcupp said:**
> But if there were some universal thing that didn't have to be compiled, I wouldn't use it.  You would have to assume that people would have that specific run time module installed in order to run your program.  Also, it wouldn't be nearly as fast as compiled code.  Those are the reasons I quit programming in .Net a long time ago.
Speed might be an issue, but most times it will probably not be noticable. A computer is idle most of the time anyway.
And the problem with "run time modules" is not very big either. Let's say I write a program for Python 2.3 or 2.4. Then I am almost 100% certain to be able to run it on any decently recent Linux installation. Unless I use a non-standard library, but then that goes for any other program regardless of language.

---

### Post by dragos240 on 2009-02-18
I mean, what i'm thinking of is an executable that is universally recognised by the maker of the operating system. What i feel makes programs different in format and how their made is that no universal agreement on one format is made. For example, if Linus Torvalds, and all the other linux people, Bill Gates, Steve Jobs, could agree on one format and program something within each operating system that enables that format to read, it would be a heck lot easier, also we could make something that detects the OS and runs specific tasks for that specific os, then it would work. Java is universal if you have the latest version installed, just like flash. My idea is the first one, each computer operating system designer could work together to form one format, and tweak their OS'es to interperate the code differently so that the operating system could understand it. What do you think, if this happened of course.

---

### Post by smartboyathome on 2009-02-18
> **dragos240 said:**
> I mean, what i'm thinking of is an executable that is universally recognised by the maker of the operating system. What i feel makes programs different in format and how their made is that no universal agreement on one format is made. For example, if Linus Torvalds, and all the other linux people, Bill Gates, Steve Jobs, could agree on one format and program something within each operating system that enables that format to read, it would be a heck lot easier, also we could make something that detects the OS and runs specific tasks for that specific os, then it would work. Java is universal if you have the latest version installed, just like flash. My idea is the first one, each computer operating system designer could work together to form one format, and tweak their OS'es to interperate the code differently so that the operating system could understand it. What do you think, if this happened of course.

But then why would people run Windows? If this truely happened, then Microsoft would lose a huge edge because people could then run the programs on any operating system.

---

### Post by phrostbyte on 2009-02-18
> **smartboyathome said:**
> But then why would people run Windows? If this truely happened, then Microsoft would lose a huge edge because people could then run the programs on any operating system.

++

You basically described Microsoft's business model.

---

### Post by dragos240 on 2009-02-18
> **smartboyathome said:**
> But then why would people run Windows? If this truely happened, then Microsoft would lose a huge edge because people could then run the programs on any operating system.

People that don't know what linux is and uses whatever is at best buy or target. Honestly, it's not compatibility that makes linux not for the average user, it's because the average user knows basicly squat, this is where microsoft comes in :p.

---

### Post by directhex on 2009-02-18
Linux can be taught foreign binary formats, to allow direct execution of .exe or .jar (or other) non-ELF files

Generally though, you either use a format with an interpreter/VM/JIT like Python or C#, and mandate the required framework as a prerequisite, or you pick an existing "native" format & push it as the right choice for others (e.g. trying to convince MS to use ELF for Windows binaries)

---

### Post by forrestcupp on 2009-02-19
> **'[h2o] said:**
> Speed might be an issue, but most times it will probably not be noticable. A computer is idle most of the time anyway.
Speed can be a major issue.  Python is great, but it can't power a fast paced 3D game.  The only thing you can use Python for in that situation is as the scripting language to power a 3D/Game engine which is compiled specifically for a certain OS.  So you end up back in the same boat.  I agree with you about simple apps, but we need to run a lot more than just simple apps, and that's where you find the big difference.

> **'[h2o] said:**
> And the problem with "run time modules" is not very big either. Let's say I write a program for Python 2.3 or 2.4. Then I am almost 100% certain to be able to run it on any decently recent Linux installation. Unless I use a non-standard library, but then that goes for any other program regardless of language.
Sure, you can be almost 100% certain that any recent *Linux* installation can run it, but the whole point of this thread is to be cross platform.  I don't know very many Windows users who have Python installed.  The standard framework used in the Windows world is .Net, and too many Linux users whine about Mono.

> **phrostbyte said:**
> ++

You basically described Microsoft's business model.
He basically described *every* money making corporation's business model.

---

### Post by Armor Nick on 2009-02-19
Although it's not really the answer to this question, I think it's best to program with portable libraries and compile on every necessary platform. It has the advantage of speed, and it isn't hard to distribut libraries with your application.

---

### Post by [h2o] on 2009-02-19
> **forrestcupp said:**
> Speed can be a major issue.  Python is great, but it can't power a fast paced 3D game.  The only thing you can use Python for in that situation is as the scripting language to power a 3D/Game engine which is compiled specifically for a certain OS.  So you end up back in the same boat.  I agree with you about simple apps, but we need to run a lot more than just simple apps, and that's where you find the big difference.
3D games are part of the category "really computationally heavy applications". Most applications are not in that category. Python is definately suitable for more than "simple apps", but maybe not the ideal choice for real-time-applications or extreme number crunching.

---

### Post by MaxIBoy on 2009-02-19
I'm just waiting for psyco or something similar to become the standard interpreter. 

As a matter of fact, python+psyco+pygame is capable of powering a fully 3D game (as evidenced by a few personal projects I'm working on that I haven't finished yet.) Sure, you're not going to write the next Crysis. Writing the next Quake II, though, wouldn't be a problem.

---

### Post by directhex on 2009-02-19
How about HTML+JS as the "universal executable"?

---

### Post by dragos240 on 2009-02-19
> **directhex said:**
> How about HTML+JS as the "universal executable"?

HTML and javascript? That really couldn't do much.

---

### Post by phrostbyte on 2009-02-19
Right now I have a program called JFLAP, it designs automata. JFLAP is distributed as a single binary (with a .jar extension) but it can run on Windows, Ubuntu, and probably 100 other places. So this can be considered a universal executable (it's Java).

---

### Post by directhex on 2009-02-19
> **dragos240 said:**
> HTML and javascript? That really couldn't do much.

The problem with "universal" anything is the lowest common denominator factor.

And the early iPhone SDK was all about AJAX. Aren't the "universal applications" the ones which any web browser on any OS can display?

---

### Post by jpkotta on 2009-02-19
> **dragos240 said:**
> I mean, what i'm thinking of is an executable that is universally recognised by the maker of the operating system. What i feel makes programs different in format and how their made is that no universal agreement on one format is made. For example, if Linus Torvalds, and all the other linux people, Bill Gates, Steve Jobs, could agree on one format and program something within each operating system that enables that format to read, it would be a heck lot easier, also we could make something that detects the OS and runs specific tasks for that specific os, then it would work. Java is universal if you have the latest version installed, just like flash. My idea is the first one, each computer operating system designer could work together to form one format, and tweak their OS'es to interperate the code differently so that the operating system could understand it. What do you think, if this happened of course.

The whole notion of a universal executable is flawed.  The hard part isn't compiling/packaging/installing the compiled program.  The hard part of making a portable program is accounting for the differences of the platforms.  Once you've done that, it is trivial to automatically generate the binaries for the platforms you support.

Consider this:  I could define a format that contained binaries from multiple platforms, and when I "executed" it, a small runtime would extract the binary for my platform and launch it normally.  This clearly doesn't make anything easier, other than you download a platform independent file that's larger than it needs to be.

---

### Post by forrestcupp on 2009-02-21
> **MaxIBoy said:**
> I'm just waiting for psyco or something similar to become the standard interpreter. 

As a matter of fact, python+psyco+pygame is capable of powering a fully 3D game (as evidenced by a few personal projects I'm working on that I haven't finished yet.) Sure, you're not going to write the next Crysis. Writing the next Quake II, though, wouldn't be a problem.

Psyco is pretty interesting.  I've never heard of that before.  Thanks for pointing that out.  

But the thing is that Psyco and Pygame are both written in C and/or Assembly.  So you're basically just back to using Python as a scripting language to run something more powerful that has been compiled.  And then we're back to the argument that not very many Windows users have Python installed, so I know even less have Pygame working on their computers.

Also, I've never seen a 3D project using pygame.  Do they exist?  I've only seen 2D games made from pygame.

---

### Post by LinuxGuy1234 on 2009-02-21
> **dragos240 said:**
> Hello, i am frustrated at the fact that so many programers have to program something an export it into different formats for different os's. Is there a universal executable that any operating can run natively? If so would you use it?

Java, Python, Perl, PHP and other *computer-interpreted* languages are 100% cross-platform. The *compiler-interpreted* languages, like C, C++ and Fortran, are not.

The only "universal compiler-interpreted" binaries are that of Mac OS X's Universal Binaries, which can run on Apple Macs with *either* a x86 processor or a PowerPC processor.

---

### Post by aaaantoine on 2009-02-21
> **forrestcupp said:**
> And then we're back to the argument that not very many Windows users have Python installed, so I know even less have Pygame working on their computers.

Python developers who create Windows install packages would then be wise to include the Python runtime libraries, same as just about every Windows game includes a Direct X installation package.

---

