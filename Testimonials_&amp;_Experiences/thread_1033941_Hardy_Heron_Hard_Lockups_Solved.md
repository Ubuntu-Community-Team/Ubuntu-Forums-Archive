---
title: "Hardy Heron Hard Lockups Solved"
date: 2009-01-07
forum: Testimonials &amp; Experiences
---

### Post by zero244 on 2009-01-07
Ok it took three clean installs to get this right.
I run a nvidia 7600 GS card, which is a good speedy card but a little twitchy with Ubuntu.

First install I used the latest drivers from Nvidia and installed them manually.
Machine ran smooth and fast at some point It started locking up.
Hard reset to reboot.
These are all random lockups it might happen at 10 minutes or 2 hours. 
Though I couldn't run over six hours without a lockup.

Second install I used the envyng method. Again everything ran smooth.
Same hard lockups.

Third install I selected the drivers from the Ubuntu repos. The ones that Ubuntu installs when you enable compiz.
I thought that fixed the problem.
It did seem to lengthen the time between lockups, but it eventually locked up too.

Then I ran into this link:

[https://lists.ubuntu.com/archives/ubuntu-users/2008-December/169368.html](https://lists.ubuntu.com/archives/ubuntu-users/2008-December/169368.html)

I applied the changes to send audio requests around Pulseaudio. In essence taking Pulseaudio out of the process.
By the way Im using a SB FX2 card which seems to be very compatible with Ubuntu.

Bottom line after doing these changes I have not had a single lockup since.

I like Hardy Heron it feels like a good solid release. I am not impressed with Pulseaudio. Ubuntu's audio format in the past has worked fine.

Knowing what I know now I could install Hardy without problems in less than an hour.
Unfortunately it took me 3 days to run this problem down.

From past experience with Ubuntu, I have found hard lockups doing everyday tasks usually end up being Video or Audio related.

Other than these two issues to resolve I haven't found anything else that is quirky.
So I will be staying with Hardy for some time.

Good luck!

---

### Post by wolfen69 on 2009-01-07
glad you got things sorted. hardy is turning out to be a great OS.

---

### Post by solwic on 2009-01-07
> **zero244 said:**
> 
I applied the changes to send audio requests around Pulseaudio. In essence taking Pulseaudio out of the process.
By the way Im using a SB FX2 card which seems to be very compatible with Ubuntu.


It's not your sound card, it's Pulseaudio.  It's junk.  Broken, useless, worthless, hindering junk.  

:P

---

### Post by jrusso2 on 2009-01-07
Yes I agree, this computer runs that Video card and Hardy and I have not had a single lockup but I run a Turtle Beach PCI soundcard.

---

### Post by zero244 on 2009-02-14
FINAL UPDATE PROBLEM SOLVED:

My random lockups, meaning my mouse and keyboard would lock up hard.
Turned out to be my USB wireless keyboard and mouse.
I plugged my USB reciever into the PS\2 connections using adapters to adapt USB to PS\2.
I have not had another lockup or freeze since.
Ubuntu Hardy is running great.
Hardy is really a sophisticated advanced OS. I really like it.

---

