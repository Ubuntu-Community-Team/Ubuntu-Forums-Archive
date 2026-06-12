---
title: "microkernels"
date: 2008-12-04
forum: The Cafe
---

### Post by meg23 on 2008-12-04
What do you think about microkernels and minnix. Is a microkernel even practical for an everyday OS?

---

### Post by Npl on 2008-12-04
they are a nice concept, unfortunatly they dont match well with having seperate processpaces - Thats why monolithic kernels are so common nowadays.
A good example for a micro-kernel is the AmigaOS, its was as pure as microkernels could get.

---

### Post by MikeTheC on 2008-12-04
If I'm not mistaken, the kernel in Mac OS X is a micro kernel.

Not being a programmer, I have no personal opinion one way or the other. I know that Linus Torvalds has basically said that micro kernels are interesting and have a certain beauty from an academic study point-of-view, but that they tend to become very complex to work on, and can have the potential to inflict a performance penalty because of all the extra overhead induced by the massive amount of inter-application communication which has to take place between the various different modules.

For what it's worth, Richard Stallman used to be a very serious proponent of micro kernel architecture. Whether he still is or not, I haven't a clue.

My own thinking on the matter is that monolithic kernels are probably better due to the reasons listed above. Anything which prevents needless complexity in a system is almost always a good thing, and anything which prevents needless consumption of overhead is also a good thing.

---

### Post by CholericKoala on 2008-12-04
Mac OSX is not a microkernel.  Their programmers screwed up the first Mach kernel so they had to make a cop-out version, the hybrid kernel which still has all the drivers running inside the kernel.  That's why it still crashses.

Microkernels are far superior to monolithic kernels in every way.  They are equal in speed now that they have been rewritten from scratch.  Nobody will adopt it yet since only hybrid kernels have been popularized.

---

### Post by MikeTheC on 2008-12-04
Bear in mind that asking about monolithic vs microkernel is akin to emacs vs. vi. It's a great way to start a (un)holy war.

And, while we're on the subject of "holy war" material... I don't code, period. It's not my thing in any way. Consequentially, I have no side in kernel discussions, and I have no side in development software. (So, those of you who are on one side or the other of these debates, kindly don't shoot!)

*runs out of thread*

---

### Post by CholericKoala on 2008-12-04
The first gen microkernels sucked due to IPC having too great of an overhead, but this was solved with the second gen L4 microkernel.  At startup, it allocates all memory to one process, only allowing processes to map, demap, and share memory from it.  This means that there is no kernel overhead since nothing needs to go into kernel mode.

---

### Post by Erunno on 2008-12-04
QNX [1] is a poster child of an efficient microkernel which is used in real world applications (mostly embedded devices).

Some elements of microkernels also find there way back into monothilic and mixed kernels now that the processing power of most computers is so vast compared to 20 years ago that the communication overhead is acceptable. For instance, Windows Vista has a framework [2] which allows to write some drivers to run in userspace and which can be loaded/reloaded dynamically.

[1]: [http://www.qnx.com/]("http://www.qnx.com/")
[2]: [http://www.microsoft.com/whdc/driver/wdf/UMDF.mspx]("http://www.microsoft.com/whdc/driver/wdf/UMDF.mspx")

---

### Post by 3rdalbum on 2008-12-04
> **Erunno said:**
> For instance, Windows Vista has a framework [2] which allows to write some drivers to run in userspace and which can be loaded/reloaded dynamically.

This is one of the three reasons why Vista sucks, according to the population - "It's not compatible with my old printer drivers!"

---

### Post by mangar on 2008-12-04
QNX is the poster child of OS engineering in general. 
BeOS was a great hybrid kernel, too bad that's it's dead.
Darwin and NT are Hybrid kernels, with NT moving toward the Microkernel model (MinWin is NOT a microkernel).
Linux is a monolithic kernel with some userspace functionality.

@3rdalbum:
UMDF and KMDF run on top of XP as well - *MDF is an abstraction layer above WDM, that takes care of many of the annoying aspects of windows driver development, such as power management.

WinDbg is a great kernel debugger, verifier.exe and WTM studio are there to make sure you didn't write an overly crashy driver.
Vista does not suck because some obscure manufacturers refuse to spend the time and (quite minimal) effort needed to port the user-mode drivers to Vista). Otherwise, where does it put Ubuntu?

---

