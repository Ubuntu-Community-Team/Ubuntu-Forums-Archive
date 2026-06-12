---
title: "SDL app crashing; free being called on invalid pointer"
date: 2021-05-01
forum: Ubuntu Application Development
---

### Post by James_Lehman on 2021-05-01
Hello everyone.

I've been developing an SDL or SDL2 app called LaserBoy for many years on Ubuntu with no major issues, but now, all of a sudden, it's crashing. I don't know much about gdb, but I have found some stuff online and I can get it to save a core dump and use gdb to do a back trace. The app crashes in all kinds of different places but it all seems to lead back to malloc.c and free being called on an invalid pointer. So first I thought this was some new bug I had introduced into the code. Then I compiled a much older version of LaserBoy and it does the same thing. I have an AMD 8 core CPU and 24GB of ram in the form of 2x4GB and 2X16GB The 2x16GB says each stick is 2x8GB so I would think I'd be getting 32GB from these two, but I don't. That's never been a problem for about 5 years. I did a mem test from the boot screen and the 2x4GB test ok. The 2x16GB hangs the system. So I thought that was it. But after I removed those sticks the crashing is still happening. It must be a hardware issue of some sort because the exact same code compiles and runs fine in Win10 and on a Raspberry Pi. What should I look for? Everything else in Ubuntu runs just fine. I run a very old clone of an XP laptop in a VMWare VM, share a directory and mount that from Ubuntu. That's where all the code is. I can mount it from the pi or the Win10 laptop. All that works fine.

The code can be linked to either SDL 1.2 or SDL2 and also uses some boost stuff. Both the SDL and the SDL2 builds crash in the same way.

General public release (full version)


New development version (just the source code, requires the installation folder from above)


Thanks.

---

### Post by wildmanne39 on 2021-05-02
Hello, I removed the zip files, the links were not loading for me, if you just want our volunteers to look at your code you can post it here between code tags. We discourage posting files of this type because we have no way of knowing what is in it without opening it and that is a risk we do not want our members to take.

---

### Post by James_Lehman on 2021-05-02
Well, ok. I guess if anyone wants to look at them I can let them know where to look.

The new development version of the code is almost 94 thousand lines of active code, not counting comments or other fluff.

LaserBoy has been FOSS for 13 years and there is even an older version of it available via apt.

It's pretty well vetted.

If you go to
[https://laserboy.org/](https://laserboy.org/)
you can read some really old information about it and see some pictures of a laser projector controlled by LaserBoy.

There is also a forum and a code directory with every public release ever put out there (in .../code/).

---

### Post by TheFu on 2021-05-02
valgrind should find bad pointers.  [https://valgrind.org/docs/manual/mc-manual.html](https://valgrind.org/docs/manual/mc-manual.html) Back when I was coding, we used Purify - a commercial tool.  We also had strict coding standards around memory management which prevented stuff like this.  

It isn't hard. Just a few rules.
[LIST]
[*]Always set unused pointers to NULL. Don't trust the implementation in a compiler to do this magically. Different compilers have different memory cleaning. Perhaps the code assumes memory is zero'd automatically and it isn't?
[*]Always check that memory allocation actually worked.
[*]When freeing memory, set the pointer back to NULL too.   Much better to get a null pointer exception than have a wild pointer accessing storage that may or may not be untainted/modified.
[/LIST]

If using C++, there are "smartptr" classes which can make implementation easier. I was never a fan. I don't like magic.

---

### Post by James_Lehman on 2021-05-02
I appreciate the insight, but I can assure you I am well versed in the use of pointers. I've been programming in C/C++ for over 25 years both professionally and recreationally, almost exclusively with GCC and mingw. I have already demonstrated that the problem is not in my code. The problem is that pointers into the heap are getting corrupted somehow just on my Ubuntu machine. I'm willing to guess that it would be fine on any other Ubuntu system known to be working properly. I'm just wondering what to look for. I have used valgrind and it changes the behavior of the executable quite a bit. It slows it down considerably and when I run it this way, I can't seem to make it crash.

---

### Post by James_Lehman on 2021-05-03
My current theory is that something has changed about the way structure member packing is working. I don't use any pragma commands to alter the default behavior, but there are indications that somehow it is different. It only seems to effect the application that I am compiling and running. Were there any recent updates that may have effected this?

---

