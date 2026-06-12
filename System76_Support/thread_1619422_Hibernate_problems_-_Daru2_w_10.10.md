---
title: "Hibernate problems - Daru2 w/ 10.10"
date: 2010-11-11
forum: System76 Support
---

### Post by werewolves on 2010-11-11
Since upgrading to 10.10 (32 bit) yesterday on my Daru2, I have been having hibernate issues.  The hibernate is very unreliable.  Sometimes it works, and sometimes it doesn't.

Any advice?

---

### Post by werewolves on 2010-11-11
PS: I also tried Uswsusp, no dice.

---

### Post by isantop on 2010-11-12
I think this is due to a bug in the Ubuntu installer which causes your swap partition to be too small. Does the computer suspend fine? If so, that's probably it.

To get it fixed, you can either reinstall Ubuntu and manually partition to have a swap that is at least as big as your RAM, or you can use a LiveCD to shrink your root partition, then expand your home partition.

---

### Post by werewolves on 2010-11-12
I just checked Disk Utility, and my swap is 2GB which is the same size as my RAM.

Suspend has never worked on the Daru2.

---

### Post by werewolves on 2010-11-13
OK, this is weird.  I did a fresh install, but am still having the same problem.

However, what I have discovered through trial and error is that I only have a consistent problem hibernating when I have Chrome running!!

Any ideas about that?

---

### Post by isantop on 2010-11-15
It may be the Chrome, or some child process of it, is eating lots of RAM, which is overflowing to swap, meaning there is not enough space available to suspend in. You might try resizing the partitions so that the sawp is something like twice the RAM size and see if that helps.

---

### Post by brydonhunter on 2010-11-15
I have the same issue with hibernation. When I use a lot of Flash in Chrome, it seems to stick during the hibernation process. I was figuring it had to do with Chrome's video acceleration, the open source ATI drivers, something in 10.10 X-server.

Any other ideas?

[EDIT] I have an 8 G swap for 4 G of RAM, don't think I'm overloading the swap file[/EDIT]

---

### Post by werewolves on 2010-11-18
Still having occasional failures hibernating, even when I'm not running Chrome.  Frustrating...

---

### Post by isantop on 2010-11-19
Did you check your swap partition? Also, which graphics drivers are you using?

---

### Post by werewolves on 2010-11-20
Yeah, like I said above, my swap partition is 2GB.  The same as my memory.

Whatever the default for: "Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)" is.

Not sure what the command to determine the video driver version is.

---

### Post by isantop on 2010-11-22
Does it work consistently better when you don't have a big load on the system, or does it seem load independent. If it happens under high load, then it's probably similar to my Chrome issue above.

---

### Post by werewolves on 2010-11-22
If I'm not running Chrome, it only happens occasionally.  But with Chrome shut down, there is almost no load.

---

