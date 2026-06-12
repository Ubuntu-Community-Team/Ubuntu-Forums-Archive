---
title: "(Leightweight) Linux questions..."
date: 2009-10-19
forum: The Cafe
---

### Post by Dullstar on 2009-10-19
So, some friends of mine and I would like to make our own Linux distribution, but I must ask - what distributions are lightweight (for the lightweight version)?  I must ask what would make a good base here.

There's no guarantee that we'll finish this project, but, you know?  It just sounds like something that would be fun to do.

---

### Post by the fix it man on 2009-10-19
Probably depends on what type of functionality and/or usability you want.

I always like XfcE.

---

### Post by Skripka on 2009-10-19
> **the fix it man said:**
> Probably depends on what type of functionality and/or usability you want.

I always like XfcE.

That is the crux of the matter, so to speak (sometimes I kill myself).  Have no Xorg/GUI at all-and you can have a really fast system...

---

### Post by Dullstar on 2009-10-19
XFCE has been decided, but we're talking base distribution. :)

---

### Post by coldReactive on 2009-10-19
> **Dullstar said:**
> XFCE has been decided, but we're talking base distribution. :)

Ubuntu minimal?

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

then **sudo apt-get install xfce4**

that will install the base xfce 4.6 desktop into your ubuntu-based base.

---

### Post by dominiquec on 2009-10-19
For base distribution you might want to try D*mn Small Linux or Tinycore Linux / Microcore Linux.

I'm fiddling with Microcore Linux these days: very small, just under 6MB for the basic distro.

---

### Post by earthpigg on 2009-10-19
how lightweight do you want to go?

Ubuntu's base (Ubuntu before 100 daemons and services are loaded) is light enough for anything with around 128 mb of ram and perhaps less.

if you stick to anything debian-based, the process will be ridiculously easy:

[http://en.wikipedia.org/wiki/Remastersys](http://en.wikipedia.org/wiki/Remastersys)

---

### Post by Pogeymanz on 2009-10-19
You might want a more advanced distro like Crux, Gentoo, Slackware or Arch.

---

### Post by CharmyBee on 2009-10-19
I've had good luck with Puppy Linux. DSL, not so much, feels a bit antiquated.

---

### Post by Skripka on 2009-10-19
> **CharmyBee said:**
> I've had good luck with Puppy Linux. DSL, not so much, feels a bit antiquated.

That is because DSL has, unfortunately, been put out to pasture.

---

### Post by Dullstar on 2009-10-19
So Puppy is lightweight?  That one has been inserted into my notebook of plans, and I told my friends I'd check on whether it was actually lightweight.

---

### Post by CharmyBee on 2009-10-19
> **Dullstar said:**
> So Puppy is lightweight?  That one has been inserted into my notebook of plans, and I told my friends I'd check on whether it was actually lightweight.

I've ran it on a Pentium laptop strapped to a tiny dual-booting Windows hard drive, so if it's not lightweight running on this thing then it doesn't exist.
The only slow event in my Puppy adventure was the layering of the file system in its pup save file on its second boot-up. It took 8 minutes for that to go, but that's only the first time.

---

### Post by Dullstar on 2009-10-19
Thanks, guys!

---

### Post by Pogeymanz on 2009-10-19
Yes, but Puppy doesn't feel like a "real" distro to me. The whole logging in as Root, plus the lack of a good package manager, etc. It's not really supposed to be more than a LiveCD/USB, I think.

---

### Post by -grubby on 2009-10-20
> **Dullstar said:**
> So, some friends of mine and I would like to make our own Linux distribution, but I must ask - what distributions are lightweight

You want to make Yet Another Distro and yet you don't have a good working knowledge on the current ones? tsk, tsk

---

### Post by earthpigg on 2009-10-20
> **-grubby said:**
> You want to make Yet Another Distro and yet you don't have a good working knowledge on the current ones? tsk, tsk

***worst*** case scenario, assuming they are down with the [Four Fundamental Software Freedoms]("http://en.wikipedia.org/wiki/The_Free_Software_Definition#The_definition") and GPL: they will learn some stuff.

when that is the absolute worst that can happen, my vote is to applaud the project.

---

### Post by TheNosh on 2009-10-20
> **Pogeymanz said:**
> Yes, but Puppy doesn't feel like a "real" distro to me. The whole logging in as Root, plus the lack of a good package manager, etc. It's not really supposed to be more than a LiveCD/USB, I think.

puppy was my primary system for about a year. it's not exactly the best in terms of ease of use, larger repos would be nice, but it's certainly workable and it's definitely a "real" distro. it ran really well with Xfce.

---

