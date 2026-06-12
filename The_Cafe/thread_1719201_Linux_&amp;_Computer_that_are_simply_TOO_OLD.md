---
title: "Linux &amp; Computer that are simply TOO OLD"
date: 2011-04-01
forum: The Cafe
---

### Post by StephanG on 2011-04-01
I've been thinking about this for a while:

As computers are becoming faster and faster, are the oldest computers that are still operational are also slowly becoming faster.  I mean, a PC can only run for a limited period of time before something breaks that can't be replaced anymore.

One of Linux's many advantages, is that can still run well on reasonably old hardware, with many distro's designed for that specific purpose.  But where do we draw the line?

My father said that his first computer didn't have a hard drive at all.  And then later he got one with a grand AWESOME 20MB!!!  Now obviously, if we want Linux to run on computers that old, we start hurting our own community, because the kernel needs to be kept incredibly small, support for USB, CDROM, etc. is a waste of space in a PC that predates such devices by eons.

Even the lighweight desktops like XFCE, LXDE, etc. will quickly become irrelevant if they sacrifice features that users want, just so that it can run on hardware that doesn't exist anymore.

So, my question is a bit philosophical:  **How do we, as a community decide what is too old?**

I'm interested to hear what you think.

---

### Post by 3Miro on 2011-04-01
In short: "We" don't ever make such a decision.

Whenever a significant number of people are interested in running Linux on a set of old computers (say hardware that was popular in 2000), then they make their own distribution. When those people upgrade to a newer system, they may lose interest in the old distribution and it will probably die out. Over time, the effort to keep the old hardware alive overwhelms the people willing to keep it alive; this is a "natural" process. There should never be anything made or decided by the community that will specifically prevent people from running Linux on old computers.

Desktop environments are rarely designed for low end machines. XFCE is suitable for old machines, but it is not designed for old machines. I use XFCE on 6 core, 8GB RAM, Nvidia GTX260, 1.5GB total HDD space. I do that not because I cannot run Gnome or KDE, I use XFCE because it is faster. XFCE and LXDE are desined to be light and fast so that the rest of the system resources can be spend on other tasks.

A DE or WM can be designed specifically for old computers, but then we are back in the same situation as special Linux distributions.

---

### Post by cafejunkie on 2011-04-01
I have an old Dell Inspiron 4000 from 2002. It is a PIII 1Ghz, with 384MB of RAM. I run Arch Linux with a (very nice) openbox set up and it flies.
Like said above, there will always be specific distros for people who want to run on low end (sometimes ancient) hardware. Specifically, the distros like Arch and especially Gentoo where you can just build up your own system. 
As far as where to draw the line goes, user-friendly distros like Ubuntu should focus on the future rather than backwards compatibility. I attempted to run maverick on that PIII once and it was brutally slow, even with LXDE! (I blame the bloat :P).
The kernel will happily run on anything and you can always compile your own custom kernel. I say hardware older than 5 years doesn't need to be supported directly by the distro maintainers. If your hardware is that old and you want to "revive it" there are plenty of options but distro maintainers shouldn't incorporate those options at the expense of innovation and new features. In short, backwards compatibility is evil :P

---

### Post by wojox on 2011-04-01
It's just evolution that decides. If it didn't I'd have a pet dinosaur.

---

### Post by Hur Dur on 2011-04-01
I'd say anything that is less than 15 years old would be usable with the latest Linux kernel, and a lightweight window manager. Of course, this is implying that you don't plan on running Ubuntu, SUSE, Fedora, or any other big name distros. However, Arch, Debian and Slackware would run relatively quick on a machine with at least 64mb RAM. These are the distros that do not drop support for older hardware, although, I believe that it would be beneficial for Ubuntu's developers to drop support on older machines, which it seems that they already have done.

---

### Post by mmix on 2011-04-01
most computers are turing-based. yes, it is old.

---

