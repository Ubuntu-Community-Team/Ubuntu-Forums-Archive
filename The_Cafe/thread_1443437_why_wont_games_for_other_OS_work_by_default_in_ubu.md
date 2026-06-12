---
title: "why wont games for other OS work by default in ubuntu"
date: 2010-03-31
forum: The Cafe
---

### Post by tooatw on 2010-03-31
i am not expecting a "because it is made for another one" 
i am expecting an answer from a programmer's point of view
i mean if i do something in c or c++ or java or whatever when i compile it in windows i get something that will run in windows and if i compile it in linux it will work for linux
so why wont they work in different os'?

---

### Post by dabby_yo on 2010-03-31
DirectX vs OpenGL?

---

### Post by Crunchy the Headcrab on 2010-03-31
That's not entirely true.  Those game require tools that only work on certain platforms.  For example most Windows games use DirectX, some Microsoft API's that are not licensed to run on anything other than Windows (surprise surprise).  The reason why people have allowed this to happen is largely in part to the amount of market share that Windows has.  If you're going to make games for the most lucrative OS, then you're going to use the best tools available for you to do that on that OS, which in this case aren't available on the other OS's.

---

### Post by k33bz on 2010-03-31
what dabby_yo said as well as the file structure and different languages. DOS vs Unix

---

### Post by tooatw on 2010-03-31
of course!
they use 3rd party software 
i always thought they were independent

---

### Post by dabby_yo on 2010-03-31
> **tooatw said:**
> of course!
they use 3rd party software 
i always thought they were independent

If you're a PC gamer, how could you *not* know the difference between DirectX and OpenGL?

---

### Post by fatality_uk on 2010-03-31
It's down to the way the game creates & accesses the GUI. If you create a text based C application, it will run on virtually all OS's. But as said, DirectX is Microsoft's default 3D API set. Now changing the 3D-API isn't massively difficult, but as Linux, OS X's market share is combined less than 10%, it's not very cost effective to port the code as it would take a good few months to port to OpenGL from DirectX. As the vast majority of the market is for Windows gaming.

---

### Post by Chronon on 2010-03-31
Java can work on any platform for which a Java Virtual Machine has been implemented.  Thus the whole "code once run anywhere" mantra.

Compiled languages get converted directly to machine language for a given architecture.  I suspect that the main reason that a compiled binary for x86 only runs on a certain OS is because it contains functions that are specific to the OS it is meant to run on.  I believe that a binary for x86 will run on any such chip, it just won't properly interact with an arbitrary kernel.  However, it's possible (at least in principle) to simply use a bootloader to execute individual binaries rather than use a complete operating system.

I am not an expert in this, so I welcome corrections.

---

### Post by cguy on 2010-03-31
When you compile some code, the resulting program is not understandable by the processor, but by the operating system. It's the OS who then talks with the CPU telling it what to do.
It's not the libraries which are used which make the difference.

---

### Post by Chronon on 2010-03-31
> **cguy said:**
> When you compile some code, the resulting program is not understandable by the processor, but by the operating system. It's the OS who then talks with the CPU telling it what to do.
It's not the libraries which are used which make the difference.
It is possible to compile a binary that is understandable by the processor (this is basically a firmware).  Your comment does seem to crack the whole nut of this whole question, though.  Software doesn't talk to the hardware directly.  It makes calls to the kernel.  A binary that talks directly to the hardware is really a firmware and not software.

---

### Post by lisati on 2010-03-31
> **cguy said:**
> When you compile some code, the resulting program is not understandable by the processor, but by the operating system. It's the OS who then talks with the CPU telling it what to do.
It's not the libraries which are used which make the difference.

It's not so much that the processor can't understand the compiled program, but that the "behinds the scenes" stuff (system calls etc.) is usually different. Assuming, of course, that it's compiled for an OS that runs on the same kind of processor.

---

### Post by tooatw on 2010-03-31
> **dabby_yo said:**
> If you're a PC gamer, how could you *not* know the difference between DirectX and OpenGL?

i'm not much of a gamer, just out of curiosity

---

### Post by iRiUX on 2010-03-31
There are layers of communication. The Application/Game communicates with the operating system and the operating system communicates with the hardware. The problem is, the Windows (e.g.) App/Game will talk to the Linux OS as if its a Windows OS and the Linux OS will be like: wtf dude, are you stoned or something?! The following is based on a real event:

The windows Game is like: hey man...  I want you to let me to use recipes.exe (program he needs to make pancakes)...
and the Linux OS will like: wtf is this recipes.exe ****?... U smoking crack?... ******* moron.
Windows Game: wtf dude, im waiting, gimme access to recipes.exe
Linux OS: No crackers allowed, get the **** out of here.
Windows Game: ERROR

---

### Post by pirlo89 on 2010-03-31
> **iriux said:**
>  the following is based on a real event:

The windows game is like: Hey man...  I want you to let me to use recipes.exe (program he needs to make pancakes)...
And the linux os will like: Wtf is this recipes.exe ****?... U smoking crack?... ******* moron.
Windows game: Wtf dude, im waiting, gimme access to recipes.exe
linux os: No crackers allowed, get the **** out of here.
Windows game: Error

lol :p

---

### Post by forrestcupp on 2010-03-31
> **tooatw said:**
> 
i mean if i do something in c or c++ or java or whatever when i compile it in windows i get something that will run in windows and if i compile it in linux it will work for linux


In C and C++, what you just said isn't even close to being true.  It's true for very simple command line-based programs, but that's about all.  Most Windows programs are going to be programmed in C using either WinAPI or DirectX.  Try taking that code and compiling it in Linux; you won't get very far.

There are toolkits and engines, like wxWidgets and Ogre3D, where you can program GUIs and 3D games, and it will be compilable on Windows and Linux with the same code.  So it *is* possible.  But the truth is like other people said; Linux is a very, very small market share, and most programmers just don't care.

But it's definitely not true that you can just take any random code and it will compile on any OS.

---

### Post by sandyd on 2010-03-31
perhaps direct2d, which was recently added to ati's drivers will make games on linux more popular. but then again, I would prefer to have direct3d instead... which we will likely get in the future... hopefully in my lifetime.

---

### Post by madjr on 2010-03-31
@tooatw

well i believe a simpler example would be to take um something like firefox

take the linux version and take the windows version (in wine)

there will be differences that will make 1 virtually unusable in the other even if you get to compile the code

some games can be a lot more complex, api and driver dependent, etc

wine is prove that 2 OSs can live side by side, but reverse engineering is H.A.R.D, it's awesome what they accomplished so far

in the meantime we can only BATTLE IT OUT (like apple and Android are doing), they will soon be just as big as the PC as a gaming platform. a win for *Nix

devs have embraced OpenGL and other open standards, in many fronts, like never before

Mobile and desktop will eventually fuse (check [nvidia tegra presentation]("http://www.youtube.com/watch?v=mlOTcs-effU")), making Android a Big dominant OS and open lots of doors for all linux and kernel, even merge normal linux projects with android compatibility

a Big SWIFT Kick to MSFT's dominance, that they didnt see coming

---

### Post by whiskeylover on 2010-03-31
If you wrote code that is strictly ANSI ISO C/C++ compliant, then it should compile on all platforms. Sadly, if you want your game to be even a least bit enjoyable, you'd have to link to libraries that are platform dependant (graphics/audio/filesystem/whatever) or write everything from scratch.

---

### Post by Warpnow on 2010-03-31
The short answer is that the pre-requisites cannot be satisfied due to a closed source, windows only component somewhere in the hierarchy.

---

