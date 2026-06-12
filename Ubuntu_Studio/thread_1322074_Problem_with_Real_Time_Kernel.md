---
title: "Problem with Real Time Kernel"
date: 2009-11-10
forum: Ubuntu Studio
---

### Post by fabiotheimpaler on 2009-11-10
Hey, I have a slight problem.  Whenever I try to boot from the Rt kernel in GRUB, I get this message: 
[INDENT]udevadm trigger is not permitted while udev is unconfigured.3
udevadm settle is not permitted while udev is unconfigured.
svgalib: cannot open /dev/mem[/INDENT]

What does this all mean?  What is udev, and how do I configure it?  I'm running Ub. Karmic.

Any suggestions?

---

### Post by Stochastic on 2009-11-11
Please file a bug against the RT kernel in launchpad.net as this looks like a very serious issue that should not occur.

[https://bugs.launchpad.net/ubuntu/+source/linux-rt/+filebug](https://bugs.launchpad.net/ubuntu/+source/linux-rt/+filebug)

---

### Post by goldenshale on 2009-11-30
I get the same error, so the RT kernel is completely not usable right now.  Anyone have thoughts on how to go about debugging this?  I upgraded from a Jaunty install, so my guess is that this was a problem with an incomplete or incorrect upgrade...

---

