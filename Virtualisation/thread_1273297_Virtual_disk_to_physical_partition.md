---
title: "Virtual disk to physical partition?"
date: 2009-09-23
forum: Virtualisation
---

### Post by DariusS on 2009-09-23
(I posted this question earlier in the general help section, ignorant to the existence of this board. My apologies, and if you feel the need to delete one or both, my feelings will not be hurt.)

:confused::confused::confused:

For lack of finding any info on this, I figured I'd ask those who would know best.
What I'm trying to accomplish is moving my virtual disk (WinXP Pro) to a physical partition and make it bootable.
You may be wondering at the purpose for this, as I am an avid Linux user. I do however need windows for college, as many of my classes require proprietary office software and others that just wont run in wine. This has worked fine in the past with a virtual machine, but the hassle and load on my machine has convinced me that I'd rather have a full-fledged install rather than patching devices and such through Linux.
I'm considering doing a fresh install, but I've been using the virtual install for so long it'd take way too long to get everything re-installed and configured, besides all the issues with licenses, etc.

So, if anyone knows of the possibility or steps necessary to pull off such a feat, I would be greatly appreciative.

P.S. I did do a forum search prior to posting to no avail, but if I've missed something I apologize.

Thanks again.

---

### Post by SecretCode on 2009-09-24
You could try making an image of the XP virtual installation using clonezilla or similar, and then restoring it to a physical partition.

Note however that you will probably have to reactivate your copy of XP; you will need to install it to a primary partition (I think); you should definitely back up your Linux partition too!

---

