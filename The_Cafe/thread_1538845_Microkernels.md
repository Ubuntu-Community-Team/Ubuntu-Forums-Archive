---
title: "Microkernels"
date: 2010-07-25
forum: The Cafe
---

### Post by redfox1160 on 2010-07-25
I was reading "Just for Fun" (Linus Torvalds and David Diamond) and saw that Mac OS X was based off of an OS called Mach. In the book, it said that Mach used a microkernel. Does OS X use a microkernel? Do any modern OS's use microkernels, or do they all use monolithic kernels? Thanks.

---

### Post by Starks on 2010-07-25
Windows and Mac are hybrid kernel. Linux is monolithic.

I can't think of any desktop-ready OS that uses a microkernel.

---

### Post by murderslastcrow on 2010-07-25
Menuet OS and other OSes written entirely in assembly code may use Microkernels.

Companies that need an OS for minimal needs like displaying a simple option or touch interface usually take advantage of Linux. Instead of developing their own microkernel, they just strip Linux down to what they need it to be. This is why modularity is awesome, you can throw out what you don't want and keep it to the bare essentials.

---

### Post by redfox1160 on 2010-07-25
> **Starks said:**
> Windows and Mac are hybrid kernel. Linux is monolithic.

I can't think of any desktop-ready OS that uses a microkernel.

What is a hybrid kernel, and are there any advantages/disadvantages to it?

---

