---
title: "Is there a Linux as small as DSL but as easy to install as Ubuntu and uses GRUB?"
date: 2009-03-25
forum: The Cafe
---

### Post by Newuser1111 on 2009-03-25
Is there a Linux as small as DamnSmallLinux but as easy to install as Ubuntu and uses GRUB?

---

### Post by lisati on 2009-03-25
There's [Deli Linux]("http://www.delilinux.de/") which I briefly had installed on an old machine recently, but I think it uses LILO instead of GRUB.

---

### Post by Newuser1111 on 2009-03-25
But I just need to install to get GRUB so I can install Ubuntu from a flashdrive. Would LILO also work for that?


The computer isn't very old(Acer Aspire 3003LCi) but it's DVD drive has some problems.

---

### Post by cheapie on 2009-03-25
I think you could (somehow) use LILO as an option in the GRUB menu.

---

### Post by Newuser1111 on 2009-03-25
> **cheapie said:**
> I think you could (somehow) use LILO as an option in the GRUB menu.What?

---

### Post by MaxIBoy on 2009-03-25
Google "chainloading lilo from grub." You'll find tutorials.

---

### Post by DeadSuperHero on 2009-03-25
I don't know how easy-to-use SLiTAZ is, but I know it's really lightweight!

You could also try Puppy Linux or build a system from scratch on top of Debian-minimal.

EDIT: Try [WattOS]("http://maketecheasier.com/wattos-a-lightweight-ubuntu-for-your-old-computer/2008/07/15"), it's a slimmed-down Ubuntu with a functional GNOME desktop.

---

### Post by kk0sse54 on 2009-03-25
> **Newuser1111 said:**
> But I just need to install to get GRUB so I can install Ubuntu from a flashdrive. Would LILO also work for that?


The computer isn't very old(Acer Aspire 3003LCi) but it's DVD drive has some problems.

Lilo is just another boot loader like grub that would work just fine with Ubuntu, otherwise check out

tinycore
austrumi
slitaz, just to name a few

---

### Post by Twitch6000 on 2009-03-25
crunchbang is a nice slimmed down version of ubuntu.

There is also tiny core linux,but installing it is somewhat tricky.

---

### Post by Newuser1111 on 2009-03-25
The OS just has to be small on a CD so the install would have no or less errors.

I want it to be easy to install so I don't install onto the wrong partition by mistake.

I want it to have GRUB because that is what I know how to use to get my Acer laptop to boot USB drives.

EDIT:
Used Puppy Linux.

---

### Post by init1 on 2009-03-25
> **Newuser1111 said:**
> But I just need to install to get GRUB so I can install Ubuntu from a flashdrive. Would LILO also work for that?


The computer isn't very old(Acer Aspire 3003LCi) but it's DVD drive has some problems.
I know Slax used to use LILO to boot USB drives. Syslinux is a lot easier to use though, so I would recommend that.

---

### Post by cardinals_fan on 2009-03-25
SliTaz is your best bet for a lightweight, powerful, and useful microdistro.  However, if all you need is a GRUB installer, you could try [Super Grub Disk]("http://www.supergrubdisk.org/") or [SystemRescueCd]("http://www.sysresccd.org/Main_Page").

---

### Post by mkvnmtr on 2009-03-25
There is a Ubuntu minimal install disk you can download. It has grub, the kernel and some command line utilities. I think it is about 11Mb total. Then from the command line you install just what you want. It might be the quickest way to get grub.

---

### Post by Newuser1111 on 2009-03-25
This thread has already been solved on first page.
But I can't change the thread title.

---

### Post by MaxIBoy on 2009-03-25
Yeah, the [solved] feature, along with the "thanks" feature, has been disabled due to excessive strain on the forum's server (that's right, it's all on a single box.)

---

### Post by Chemical Imbalance on 2009-03-25
> **MaxIBoy said:**
> Yeah, the [solved] feature, along with the "thanks" feature, has been disabled due to excessive strain on the forum's server (that's right, it's all on a single box.)

Really?  One server?!?! :shock:

wow.

---

### Post by K.Mandla on 2009-03-25
May I be so bold ...

[http://kmandla.wordpress.com/ubuntu-gtk12-remix/](http://kmandla.wordpress.com/ubuntu-gtk12-remix/)

---

### Post by amitabhishek on 2009-03-26
> **Mr. Psychopath said:**
> ... or build a system from scratch on top of Debian-minimal.

Hmmm...sounds interesting...You have some resource on that? Do mean something like *debootstrap*?

---

### Post by MaxIBoy on 2009-03-26
> **Chemical Imbalance said:**
> Really?  One server?!?! :shock:

wow.I think so. I know that, at some point, everything got moved to a Xeon box on semi-permanent loan from Canonical. I don't know if they've added more hardware since then, but since those things are expensive, I doubt they could.

---

