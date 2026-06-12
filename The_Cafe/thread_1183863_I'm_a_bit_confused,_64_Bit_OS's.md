---
title: "I'm a bit confused, 64 Bit OS's"
date: 2009-06-10
forum: The Cafe
---

### Post by -gabe-noob- on 2009-06-10
What is the difference between 64 Bit OS's and the normal OS's? (I'm assuming they're called 32 bit, maybe its x86? No idea.) 

I think the 64 bits can harness all the ram on your computer and the others can only use like 3.25 Gigs, is that true?


If somthing says the 64 Bit processors are supported (and its a normal version) does it mean that it can harness all the ram?


I just don't understand, so an explanation, or link to some place I could read would be appreciated.

---

### Post by EndPerform on 2009-06-10
Most 32bit operating systems (referred to as x86) can only address up to 3.5GB of RAM.  Additionally, 64bit also performs a bit better at computational things.

64bit processors are backwards compatible with 32bit operating systems.  So you can use Ubuntu x86 on an Intel Core 2 chip without issue.  If the machine has 4GB of RAM, it won't address all of it without running the server kernel, though.

---

### Post by Therion on 2009-06-10
More than you want to know regarding 32 bit vs. 64 bit computing.  

Protip:  Skip about half-way down the page to the **Pros and Cons** section for the executive summary.

[http://en.wikipedia.org/wiki/64-bit](http://en.wikipedia.org/wiki/64-bit)

---

### Post by mdmarmer on 2009-06-10
You can try both, dual boot -- you can share a home partition if you want.  That's what I've usually done.  If you decide which you like better, you can pick one.

Mike

[http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/69585-should-you-choose-32-bit-64-bit-linux.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/69585-should-you-choose-32-bit-64-bit-linux.html)

---

### Post by Dougie187 on 2009-06-10
Also, just so you know. x86 is simply the instruction set that the processor uses. Both 32bit and 64bit use x86 instruction sets, so both are technically x86 processors. However, 32bit is typically referred to as x86, and 64bit is typically referred to as x86_64.

---

### Post by SunnyRabbiera on 2009-06-10
But honestly there is little difference between the 64bit kernel and the 32bit kernel, it all goes down to optimization.
The only things 64bit lacks right now is the right amount of compatibility with certain kinds of hardware and software.
But that gap is bound to close once more OS use 64bit, especially windows.

---

### Post by cariboo on 2009-06-10
Actually x86 is just short hand for 386,486,586,686 etc.

---

### Post by t0p on 2009-06-10
64 bit OSes are optimized for 64 bit processors. 32 bit OSes are optimized for 32 bit processors.

Oh, and you do not pluralize by apostrophizing.

---

### Post by -gabe-noob- on 2009-06-10
Thanks for the help all!

---

### Post by lisati on 2009-06-10
You might want to compare the difference between 32-bit and 64-bit with the difference between a highway with 32 lanes and one with 64 lanes: one highway has a larger capacity for traffic than the other. (If anyone wants to continue with this analogy, that's fine with me)

> **cariboo907 said:**
> Actually x86 is just short hand for 386,486,586,686 etc.
You might even include, depending on circumstances, 8086/8088, 80186 and 80286, but these ones I've just mentioned don't run 32-bit software. If you tried, the results would be what some textbooks call "undefined" (in other words, it could result in anything from a program dying gracefully to a spectacular crash)
> **t0p said:**
> Oh, and you do not pluralize by apostrophizing.
I wish to suggest "OSes" as an alternative to OS's

---

