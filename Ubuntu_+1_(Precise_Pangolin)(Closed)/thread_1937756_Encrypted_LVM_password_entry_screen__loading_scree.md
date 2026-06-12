---
title: "Encrypted LVM password entry screen / loading screen &quot;invisible&quot;"
date: 2012-03-08
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by daltonlaffs on 2012-03-08
I made a previous topic about this, but it was also about several other issues that turned out to be unrelated, so here.

I installed 12.04 beta 1 64-bit from the Alternate disc, and set up an encrypted LVM. However, on first boot (and every boot since), the password entry screen has been "invisible" -- the monitor is either black, purple (the GRUB loader's color?), or has a flashing terminal cursor but nothing written.

I can still type the password and it will still eventually get to LightDM and the graphics will come back. However, I would certainly like to be able to see what I'm doing.

Anyone have any idea what to do here? Could it have something to do with the fact that I have an Nvidia 450 GTS *and* an i5 2500k with integrated Intel graphics?

---

### Post by ti1ion on 2012-03-11
Several threads on this, but unfortunately no solutions.  I have the same problem with a Dell 6420 laptop with NVIDIA graphics.

---

### Post by ti1ion on 2012-03-30
See this thread: [http://ubuntuforums.org/showthread.php?p=11803186](http://ubuntuforums.org/showthread.php?p=11803186)

I installed the proprietary driver for my Nvidia card to resolve the problem.

Sorry for double posting.  Just did not want to leave this hanging.

---

