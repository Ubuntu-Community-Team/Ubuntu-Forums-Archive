---
title: "Source code"
date: 2008-12-28
forum: The Cafe
---

### Post by Messyhair42 on 2008-12-28
My interest in computers has always been on the application end of things. but since I've started using ubuntu its grown. when it comes to computers i think of myself as having more of an affinity for hardware (can ya tell i grew up on legos). but if for instance i wanted to make a change to linux what do i have to do to find the source code and edit it?

---

### Post by MaxIBoy on 2008-12-29
A complete Linux distro consists of so much more software than Linux itself. Almost everything can be replaced and swapped out. The two major components shared by every Linux distro are:

The Linux kernel itself ([kernel.org](kernel.org))
The GNU core utilities ([fsf.org](fsf.org),) which are technically optional, but they are pretty much standard.

Both of those links will take you to places where you can get the full source code. Recompiling the Linux kernel is actually pretty common practice, because you can make specific optimizations for your hardware (although, even then, you don't change the actual code.) 


I'd suggest you start out by writing your own software first, as modifying code isn't fun. Also, have in mind exactly what changes you want to make and see if the changes actually need to be done in code (or if there's a replacement piece of software that behaves how you want it to.) Another good thing to do (in terms of gathering general knowledge of how the system ticks) is to break things and then fix them.

---

