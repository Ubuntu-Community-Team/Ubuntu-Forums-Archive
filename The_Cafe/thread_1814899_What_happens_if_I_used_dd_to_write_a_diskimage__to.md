---
title: "What happens if I used dd to write a diskimage  to a partition of my HD?"
date: 2011-07-30
forum: The Cafe
---

### Post by ninjaaron on 2011-07-30
I realise this is nearly a tech-support question, but It's about Chromium OS, and it's a very hacky, unofficial sort of thing.  I want to try and install it on my machine.  The weird thing about it is that when I installed the image on my USB, it created like 13 tiny partitions and two main ones (those are the only two that mount).  I tried copying those two partitions to partitions on my harddrive as per some instructions I found on the web, and grub recognized one of them, but refused to load it.

I was thinking about installing chromium to my computer to see what kind of performance I can get that way, but I don't know what all those weird tiny partitions will do to my computer.

And dd is scary.  I feel like I'm gonna **** myself every time I use it.

---

### Post by mips on 2011-07-30
> **ninjaaron said:**
> 
And dd is scary.

Amen!

I always double/triple check my syntax when using dd.

I once did a fdisk -l to identify a drive many moons ago and then rebooted for a reason I cannot remember and continued using dd unkown to me that the device allocation had changed after the boot so I obviously wrote to the wrong drive, I nearly cried :D

---

