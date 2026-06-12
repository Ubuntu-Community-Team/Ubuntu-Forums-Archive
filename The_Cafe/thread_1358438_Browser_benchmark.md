---
title: "Browser benchmark"
date: 2009-12-18
forum: The Cafe
---

### Post by Pasdar on 2009-12-18
I benchmarked some browsers (used peacekeeper). My systems specs:
Kubuntu 64Bit, fresh install, only restricted extras installed, ATI 4570 (using the open-source drivers that get installed automatically)
T4 class Intel cpu.

Linux 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:02:15 UTC 2009 x86_64 GNU/Linux

glxgears show
1754 frames in 5.0 seconds, I have ten fold this when ATI proprietary is installed. Just so you know it could affect the results once I install them.

server glx version string: 1.2
client glx version string: 1.4
GLX version: 1.2
OpenGL vendor string: Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string: 2.1 Mesa 7.6
OpenGL shading language version string: 1.20

**Results:**

Chrome 4.0.249.43: **3104**  (This is actually considerably higher than what I get on windows with everything installed for best performance)

SRWare Iron 4.0.227.0: **2903** (Even Iron performs better than my chrome on windows)

Firefox 3.5.6: **1402** (Performs worse than its windows version by 200+ points)

Opera 10.10: **1359** (Performs worse than its windows version by 200+ points)

Konqueror 4.3: **1236** (At least it performs twice better than internet explorer 8 on windows 7)

The difference between Chrome at the top (which is the beta version from their google site) and the Iron could be because for Chrome Beta I have the 64bit version installed, and for Iron... they only have a 32bit version.

The Chromium daily build got stuck (twice I tried) halfway through, so no results for that. I'd like to try Safari with wine, since safari on windows scores nearly identical to chrome.

---

### Post by Skripka on 2009-12-18
Huh.  Given my hardware (see sig):

Rekonq (QtWebkit): 2745
Opera 10.20: 1762

---

### Post by Xbehave on 2009-12-18
Try it with DRI (DRI2 needs a new kernel but just DRI can be got from xorg crack pushers) or with flgrx to see how much of a performance difference the graphics card makes (i doubt it's much)


The reason Linux versions of Firefox get lower scores is because they are not Optimized by PGO (try using swiftweasel), I would guess it's the same for Opera but don't know anything about their build system?

---

### Post by lovinglinux on 2009-12-18
> **Xbehave said:**
> The reason Linux versions of Firefox get lower scores is because they are not Optimized by PGO (try using swiftweasel), I would guess it's the same for Opera but don't know anything about their build system?

Swiftweasel is not only optimized with PGO, but also with processor specific flags, which makes a lot of difference.

Performance of Firefox also depends on other factors, like the state of databases, the type and number of installed extensions. See [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567) for tips on how to improve it's performance (see my benchmarks there).

---

