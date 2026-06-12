---
title: "the kernel is the operating system????"
date: 2008-05-04
forum: The Cafe
---

### Post by nite owl on 2008-05-04
Hi I am currently completing my degree in Computer Science and one of the books assigned for one of my units in systems programming quite clearly stated that in unix the operating system is called the kernel??

I have always believed that the operating system is built on top of the unix kernel, and that flat out statement of 'the operating system is called the kernel' isn't entirely accurate??

---

### Post by Delever on 2008-05-04
It comes down to how they define what operating system is.

---

### Post by Joeb454 on 2008-05-04
> **Delever said:**
> It comes down to how they define what operating system is.

This is very true, as without a kernel what would you have?

---

### Post by Bigtime_Scrub on 2008-05-04
> **nite owl said:**
> Hi I am currently completing my degree in Computer Science and one of the books assigned for one of my units in systems programming quite clearly stated that in unix the operating system is called the kernel??

I have always believed that the operating system is built on top of the unix kernel, and that flat out statement of 'the operating system is called the kernel' isn't entirely accurate??

In computer science, the kernel is the central component of most computer operating systems (OS). Its responsibilities include managing the system's resources (the communication between hardware and software components). As a basic component of an operating system, a kernel provides the lowest-level abstraction layer for the resources (especially memory, processors and I/O devices) that application software must control to perform its function. It typically makes these facilities available to application processes through inter-process communication mechanisms and system calls.

These tasks are done differently by different kernels, depending on their design and implementation. While monolithic kernels will try to achieve these goals by executing all the code in the same address space to increase the performance of the system, microkernels run most of their services in user space, aiming to improve maintainability and modularity of the codebase. A range of possibilities exists between these two extremes.







From what I understand from reading this, the Kernal is a part of the O.S. but is not it itself. It's just a piece of the whole.

---

### Post by nite owl on 2008-05-04
> **Delever said:**
> It comes down to how they define what operating system is.

True but I feel they have mashed the two together, The operating system is built on top of the kernel and utilizes its services.

Just like all the different flavors of ubuntu are built on top of the same kernel but with different Operating systems??

As said above...

From what I understand from reading this, the Kernal is a part of the O.S. but is not it itself. It's just a piece of the whole.

.... Thankyou for that statement

---

### Post by Joeb454 on 2008-05-04
Personally I define the operating system as a piece of software allowing interaction between the Human user & the computer hardware.

That's just my opinion however :)

---

### Post by Delever on 2008-05-04
Yes, I agree, but as in every branch of science there is world of definitions, so you have somewhat adapt to them. However I think in this case that statement is wrong.

---

### Post by nite owl on 2008-05-04
In fact I think that the sentence should be, 'The operating system is called the operating system' lol

---

### Post by bodhi.zazen on 2008-05-04
And the controversy rages on ...

[http://en.wikipedia.org/wiki/GNU/Linux_naming_controversy](http://en.wikipedia.org/wiki/GNU/Linux_naming_controversy)

---

### Post by SunnyRabbiera on 2008-05-04
well in terms of linux yes linux is the kernel and what is built around it and into it is the operating system.
Linux is a unique case, the kernel itself can be considered a OS on its own as the barebones linux has a lot of features that a simple kernel doesnt have...
In windows terms the kernel is not the operating system however everything is tied to the kernel thus why there are so many issues in it, microsofts idea is to combine both the core of the Operating system and the kernel into one.
This is both very brilliant and stupid at the same time, on one side there is no extra need to compile a GUI as its included with the core, but on the other side if something happens to penetrate the GUI it can have devastating effects on the kernel...
Look at Microsoft internet explorer to see what I mean here, IE in windows XP and Vists is tied DIRECTLY to the core and the core is tied DIRECTLY to the kernel, so heaven forbid anything happen to IE.
Trust me I have seen first hand of how far a piece of malware can enter into the system thanks it IE's vulnerabilities.

---

### Post by nite owl on 2008-05-04
> **bodhi.zazen said:**
> And the controversy rages on ...

[http://en.wikipedia.org/wiki/GNU/Linux_naming_controversy](http://en.wikipedia.org/wiki/GNU/Linux_naming_controversy)


The use of the word "Linux" to refer to the kernel, the operating system, and entire distributions, often leads to confusion about the distinctions among the three. Many GNU packages are a key part of almost every Linux distribution. 

Media sources frequently make erroneous statements such as claiming that the entire Linux operating system (rather than simply the kernel) was written from scratch by Torvalds in 1991.

....
Because of this confusion, legal threats and public relations campaigns apparently directed against the kernel, such as those launched by the SCO Group or the Alexis de Tocqueville Institution (AdTI), have been misinterpreted by many commentators who assume that the whole operating system is being targeted. These organisations have even been accused of deliberately exploiting this confusion


...Exactly, As said above the kernel is just apart of the whole operating system, you cant just call the entire operating system 'the kernel'.

---

### Post by kshtjsnghl on 2008-05-04
As fas as i understood the concept, an operating system consists of the kernel( which takes care of memory management, processs cheduler,etc. ) and many applications which run on the kernel for the comfort of the user...

So same opinion, i think the kernel is the part of the operating system but actually you can even have the kernel only as constituting the operating system..9without the applications provided)

---

### Post by swoll1980 on 2008-05-04
you don't even need a kernel. Technically speaking you could write software that directly interacted with the hardware (bypassing a kernel) though it would only work on the hardware it was programed to work on. Possible, but not practical

---

### Post by Locke_99GS on 2008-05-04
Let's define;

operate: to cause systems or equipment to function.
system: a group of independent but interrelated elements comprising a unified whole.



There's your answer.

---

### Post by Sinkingships7 on 2008-05-04
To me:

The kernel is the core of the system, written to work very closely with the hardware. The kernel contains all of the code for I/O, memory management, etc.

The operating system is the layer written to use the kernel. This includes the filesystem, software, and the code that was written to determine how the code of the kernel should be used.

Kernel code can be used in many different ways, depending on what the operating system code demands from it. The operating system calls code from the kernel to determine how to use the hardware.
In other words, the kernel itself does not directly use the hardware, but rather serves as an instruction set, "displaying" a list of "options" for the operating system to choose from.



That's how I view it, and me and a buddy are attempting to write a kernel ourselves, just for the learning experience.

---

### Post by Joeb454 on 2008-05-04
> **Sinkingships7 said:**
> me and a buddy are attempting to write a kernel ourselves, just for the learning experience.

I hope you know some seriously low level language (i.e. assembly). A little C might help too...

---

### Post by Sinkingships7 on 2008-05-04
> **Joeb454 said:**
> I hope you know some seriously low level language (i.e. assembly). A little C might help too...

C.

It's not a serious project. Just for fun. Kinda just to see what we can do, if anything :lolflag:

---

