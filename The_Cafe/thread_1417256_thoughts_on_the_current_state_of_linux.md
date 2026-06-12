---
title: "thoughts on the current state of linux"
date: 2010-02-27
forum: The Cafe
---

### Post by SIGTERMer on 2010-02-27
I'm not trying to start anything here, but linux is getting larger with every repo commit. and things don't seem to be slowing sown ether. As much appreciation I have for this amazing work of art, I'm starting to get concerned about where this is heading and I'm sure I'm not alone.

Despite the many features a monolithic kernel introduces, it doesn't fare as well in the accessibility and maintainability areas.

How possible is it for linux to be converted into a microkernel (leaving aside all political influences)? by this I mean stripping down all but the core and turning everything else to user space processes while maintaining compatibility with current systems (in other words, a drop in replacement).

---

### Post by aviedw on 2010-02-27
Im not sure if i fully understand you. They seem to constantly update the kernel. I dont always agree with installing that new kernel right away because it always resets my xserver and i have to manually install my Nvidia drivers again. Its not that big of a deal but it just gets annoying. 

Now what im not sure about is when you say Linux are you talking about all of the distros out there or are you just talking about Ubuntu

There are many Distro's out there that come pretty bare bone shall i say. Slack or Arch to some. 

I think what your suggesting is the major difference between BSD and Linux, i think BSD is closer to what your talking about. 

Are you familiar with BSD?

---

### Post by prodigy_ on 2010-02-27
You only need a true microkernel OS for mission critical environments where you're willing to sacrifice performance and simplicity to achieve absolutely maximum stability.

Early versions of NT used microkernel. Since v4.0 it's on hybrid kernel.

I don't think that Linux will go away from monolithic kernel anytime soon. The benefits are unclear (Linux is quite stable as it is now) and most users wouldn't like the implied drop in performance.

> **aviedw said:**
> I think what your suggesting is the major difference between BSD and Linux, i think BSD is closer to what your talking about.
Sorry, but that's wrong. Most BSD flavors use monolithic kernels (with the exception of DragonFly BSD):
[http://en.wikipedia.org/wiki/Comparison_of_BSD_operating_systems](http://en.wikipedia.org/wiki/Comparison_of_BSD_operating_systems)

---

### Post by 3rdalbum on 2010-02-27
"Linux is getting larger and larger" and "We need everything to be in userspace" are not necessarily related.

The Linux microkernel system would take up more lines of code than the monolithic kernel, or at best the same. If different things are in different processes, there would most probably be less code reuse. Plus you need to add the interprocess-communication, and the kernel devs would need to support the old monolithic kernel for a while too (or develop a compatibility layer).

You'd end off with the same number of developers working with the same amount of code, only some of it would be running slower because it's in userspace.

You can actually make Linux smaller by compiling a lot of it as modules, or even not compiling them in at all.

I personally am against microkernels. Mac OS X has a "hybrid" kernel; and if you boot it up in recovery mode to reset a password or something you have to start up twenty different services by hand before you can actually get anything done.

---

### Post by SIGTERMer on 2010-02-27
> **aviedw said:**
> Im not sure if i fully understand you. They seem to constantly update the kernel. I dont always agree with installing that new kernel right away because it always resets my xserver and i have to manually install my Nvidia drivers again. Its not that big of a deal but it just gets annoying. 


you too :)


As you mentioned, there are many light distros out there, but I'm talking about the linux kernel itself from a technical point of view.
From a programmers prospective, The kernel in its current state means that less people are able to make changes easily or add new code. with a microkernel structure, the kernel will be far more accessible and easer to understand (and debug).

As for BSD, I thought it also had a monolithic kernel. please correct me if I'm wrong.

---

### Post by SIGTERMer on 2010-02-27
> **3rdalbum said:**
> 
The Linux microkernel system would take up more lines of code than the monolithic kernel, or at best the same. If different things are in different processes, there would most probably be less code reuse. Plus you need to add the interprocess-communication, and the kernel devs would need to support the old monolithic kernel for a while too (or develop a compatibility layer).

You'd end off with the same number of developers working with the same amount of code, only some of it would be running slower because it's in userspace.


It's true that a microkernel would take up more lines of code, but the kernel itself would be clearly defined. it would more easy to deal with, and modifying main parts of it would be far less cumbersome.
less code reuse shouldn't be a problem if everything is defined clearly. 

slowness a major issue with microkernels, but I think its worth the simplicity we get in return. and if things are carefully implemented, the resulting system might not be that much slower then the current one.

---

### Post by V for Vincent on 2010-02-27
The thing is, we probably can't afford the performance loss that comes with a microkernel. If Linux was a lot slower than windows or OSX, that'd cost us a lot of users. Obviously, kernel bugs aren't something we should tolerate, either, but those aren't intrinsic to the kernel design. I've read that solaris has a very interesting type of kernel that's kind of module-based without the performance hit.

---

### Post by aviedw on 2010-02-27
> **SIGTERMer said:**
> you too :)


As you mentioned, there are many light distros out there, but I'm talking about the linux kernel itself from a technical point of view.
From a programmers prospective, The kernel in its current state means that less people are able to make changes easily or add new code. with a microkernel structure, the kernel will be far more accessible and easer to understand (and debug).

As for BSD, I thought it also had a monolithic kernel. please correct me if I'm wrong.

Thanks for clearing that up for me. When it comes to dealing with the kernel it scares me the way the windows registry use to scare me LOL. I need to read up on it more.

---

### Post by steveneddy on 2010-02-27
I would think that if you wanted a faster kernel to deal with on your machine that you would compile your own. this was you will have a kernel that is meant for your machine and none of the extras.

I think there is an application that allows you to get and compile your own kernel called [kernel check]("http://kcheck.sourceforge.net/").

this app will help you DL and compile the latest kernel sources for your machine.

---

### Post by aviedw on 2010-02-27
I wonder if there are any down sides to compiling your kernel? 

My system is running so smooth but there just so much to learn that i always end up doing something crazy to my system and then i spend hours trying to figure out what i did wrong. 

I think this kernel thing might be my next Everest :D

---

### Post by SIGTERMer on 2010-02-28
> **steveneddy said:**
> I would think that if you wanted a faster kernel to deal with on your machine that you would compile your own. this was you will have a kernel that is meant for your machine and none of the extras.

I think there is an application that allows you to get and compile your own kernel called [kernel check]("http://kcheck.sourceforge.net/").

this app will help you DL and compile the latest kernel sources for your machine.

Thanks steveneddy, but I'm not looking for speed here. I merely want the kernel to be more `hackable'. the source code for a microkernel would contain far less code then a monolithic one. and would be much easier to understand thoroughly.

but it seems that the extra overhead introduced by such a kernel is simply too much. so I doubt I'll be seeing a linux microkernel anytime soon. sigh...

---

