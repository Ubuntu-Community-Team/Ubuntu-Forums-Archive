---
title: "Crashfest in fresh XP, normal in ubuntu, any ideas?"
date: 2008-03-05
forum: Windows
---

### Post by oedipuss on 2008-03-05
Ok, I've just reinstalled winXP, in a small partition. 
All was normal, drivers, etc, but after a very short while, it started raining blue screens with page_faults.
This is not a winxp sucks thread, crashes are much more frequent than a normal XP installation could account for. 
So, I'm worried that a piece of hardware has gone bad (my pc is quite old), but everything works in Ubuntu, without the slightest indication that something's wrong..

Is there any test suite application I can use to check disks, gpu, ram and other components, preferably from ubuntu ?

---

### Post by rickyjones on 2008-03-05
> **oedipuss said:**
> Ok, I've just reinstalled winXP, in a small partition. 
All was normal, drivers, etc, but after a very short while, it started raining blue screens with page_faults.
This is not a winxp sucks thread, crashes are much more frequent than a normal XP installation could account for. 
So, I'm worried that a piece of hardware has gone bad (my pc is quite old), but everything works in Ubuntu, without the slightest indication that something's wrong..

Is there any test suite application I can use to check disks, gpu, ram and other components, preferably from ubuntu ?

Start with a simple memory test. One thing I love about Ubuntu is that it has memtest86 already setup and ready to go from the live CD. If all your memory passes successfully then you might be looking at a hard drive issue. The easiest way to rule this out is to find a known good hard drive and swap them temporarily. If the errors go away then you know what the issue is.

I hope this points you in the right direction!

-Richard

---

