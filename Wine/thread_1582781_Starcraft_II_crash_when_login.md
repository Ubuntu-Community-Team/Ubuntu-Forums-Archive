---
title: "Starcraft II crash when login"
date: 2010-09-27
forum: Wine
---

### Post by techn0scho0lbus on 2010-09-27
Trying to play Starcraft 2.  Can load the game but then it crashes when I input my email and try to log on. 

Please help.

---

### Post by beastrace91 on 2010-09-27
Video card? Driver version? Ubuntu version? Ubuntu bitage? Wine version?

Help us, help you,

~Jeff

---

### Post by techn0scho0lbus on 2010-09-27
> **beastrace91 said:**
> Video card? Driver version? Ubuntu version? Ubuntu bitage? Wine version?

Help us, help you,

~Jeff
Sry, I normally post that.
Gigabyte gtx 450 (1gb) with Nvidia 256.53 drivers.
Ubuntu 10.10
Wine 1.3
Starcraft 1.1
Latest linux kernel

---

### Post by techn0scho0lbus on 2010-09-27
standby, I'm going to get explicit with my kernel version because apparently it can cause errors with starcraft 2

2.6.35-22-generic is what I have.

---

### Post by techn0scho0lbus on 2010-09-27
FIXED!  what a relief

[http://bugs.winehq.org/show_bug.cgi?id=23858](http://bugs.winehq.org/show_bug.cgi?id=23858)
^^ changed the kernel.  I'm still new to linux so i'm not sure if i just upgraded or downgraded the kernel. =p

I used this guide to install SC2: [http://www.thehelper.net/forums/showthread.php?t=147567](http://www.thehelper.net/forums/showthread.php?t=147567)

---

### Post by beastrace91 on 2010-09-27
> **techn0scho0lbus said:**
> FIXED!  what a relief

[http://bugs.winehq.org/show_bug.cgi?id=23858](http://bugs.winehq.org/show_bug.cgi?id=23858)
^^ changed the kernel.  I'm still new to linux so i'm not sure if i just upgraded or downgraded the kernel. =p

I used this guide to install SC2: [http://www.thehelper.net/forums/showthread.php?t=147567](http://www.thehelper.net/forums/showthread.php?t=147567)

Glad to hear it. Don't forget to mark the thread as solved.

~Jeff

---

