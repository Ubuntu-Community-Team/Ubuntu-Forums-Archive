---
title: "Bug with MESA + rbdoom3-BFG on AMD Mobility 5870M"
date: 2018-04-23
forum: Ubuntu Development Version
---

### Post by sonsofblades on 2018-04-23
Tried running rbdoom3-BFG installed from universe repos last night on most current patched Ubuntu 18.04 beta, and the game launched, but the exact symptoms shown in this thread over on GIT.
Example output of window, not sitting at my affected computer at the moment.: 
[IMG]https://user-images.githubusercontent.com/310927/29747228-69b035f4-8ac0-11e7-8df8-867c3cb49b91.jpg[/IMG]

[https://github.com/RobertBeckebans/RBDOOM-3-BFG/issues/386](https://github.com/RobertBeckebans/RBDOOM-3-BFG/issues/386)

Just wanting to make the Devs aware that this was happening. 

If needed, I will get output from 

Hardware this was tested on: 
Asus G73JH, Intel I7-740QM, AMD Mobility 5870M with 1GB GDDR5 vram, 12 GB DDR3, 1x240GB ssd, 1x128GB SSD. Drives are managed by BTRFS in spanned pool with balanced metadata

---

### Post by QIII on 2018-04-23
Hello!

The Ubuntu Forums are a user community volunteer help forum.  Developers rarely stumble in here except by pure accident.  This is not a bug reporting venue.

If the issue is with tge application itself, then anything in the Universe repo will have to be addressed with the MOTU that packages it or the game developers.

If it's the AMD driver or MESA, we can't fix it, but might offer suggestions.  Bugs woukd have to be reported elsewhere.

Which driver do you have installed.

---

### Post by sonsofblades on 2018-04-23
For the record, I have been running Linux for a while at this point, but I finally have decided to make my mark on the Ubuntu forums.

> **QIII said:**
> Hello!

The Ubuntu Forums are a user community volunteer help forum.  Developers rarely stumble in here except by pure accident.  This is not a bug reporting venue.

If the issue is with tge application itself, then anything in the Universe repo will have to be addressed with the MOTU that packages it or the game developers.

If it's the AMD driver or MESA, we can't fix it, but might offer suggestions.  Bugs woukd have to be reported elsewhere.

Which driver do you have installed.

Fresh install with no tweaks, so I would imagine radeonsi/radeon, as that's the newest one for Juniper (baked into the kernel, AMD PRO doesn't support it), though I don't have the machine in front of me at the moment to grep it. Once I get home I'll check.

[https://github.com/RobertBeckebans/RBDOOM-3-BFG/issues/137](https://github.com/RobertBeckebans/RBDOOM-3-BFG/issues/137)

Seems to point to the variant of Mesa misreporting the variant of GLSL or OpenGL that the hardware actually supports.

I will of course report this via Launchpad to the devs, but to have some others validate that this is a problem would be helpful, of course.

---

