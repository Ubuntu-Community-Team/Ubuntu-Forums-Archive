---
title: "Xfce desktop environment question"
date: 2022-09-19
forum: Ubuntu/Debian BASED
---

### Post by f23948 on 2022-09-19
Any Linux distro came with Xfce desktop environment is for 15 years old computer or older, is that correct?

---

### Post by Dennis N on 2022-09-19
Maybe. You have to try it and see. Many people have old laptops that still work with current releases. I have Xubuntu 20.04 installed on a 2007 Dell, for example.

---

### Post by guiverc on 2022-09-19
I'm using a 2009 dell desktop (optiplex 960 with c2q-q9400 cpu) currently and have Xubuntu/Xfce installed on this box (my install contains multiple DEs installed; I'm using Lubuntu/LXQt currently as I am most of the time. This box is the *development* release meaning *kinetic* currently; ie. what will be released as 22.10.

My current 2009 dell is also dual boot; my other OS is Ubuntu 20.04 LTS which includes the same GNOME (Ubuntu Desktop), XFCE (Xubuntu), LXQt (Lubuntu) and even MATE (Ubuntu-MATE) on the same install (*ie. I like multiple DEs installed; I worry about RAM usage far more than the disk used by multiple desktops installed; ie. what apps co-exist in RAM at the same time not caring much about what's also on my disk*).

I'm not sure what you're asking, but I use in QA the following boxes (all being core2 era)

- hp dc7700 (c2d-e6320, 5gb, nvidia quadro nvs 290)
- hp dc7900 (c2d-e8400, 4gb, intel 4 series integrated i915)
- dell [optiplex] 745 (c2d-6600, 6gb, amd/ati radeon rv516/x1300/x1550)
- dell [optiplex] 755 (c2d-e6850, 5gb, amd/ati radeon rv516/x1300/x1550)
- dell [optiplex] 755 (c2d-e8300, 8gb, amd/ati radeon rv610/radeon hd2400 pro/xt)
- dell [optiplex] 780 (c2q-q9400, 8gb, amd/ati cedar radeon hd 5000/6000/7350/8350)
- dell [optiplex] 960 (c2q-q9400, 8gb, amd/ati cedar radeon hd 5000/6000/7350/8350)

- lenovo thinkpad sl510 (c2d-t6570, 2gb ram, i915)
- motion computing j3400 (c2d-u9400, 4gb, intel mobile 4 series)

the oldest of which is the 2005 HP DC7700  (*though CPU was upgraded, with  RAM hanged many times*), and Xubuntu is a system I test frequently on all those (*and more*).

In fact the dc7700 & its unusual video card actually performs best on recent releases when used with Xubuntu/XFCE (*the issue relates to kernel module related; but seems to misbehave mostly in GNOME or KDE*)

I don't know what you're asking though. I do use old hardware to QA (*Quality Assurance*) test Xfce or Xubuntu using the aforementioned hardware (*on older releases I used other 745 & 755 boxes too*).   I also do testing for Debian too, using the same hardware.

For older releases (eg. *i386, my last i386 only box was manufactured in 2007*) I used older hardware that I didn't list, which included pentium 4, pentium M, and pentium D processors. On these older CPUs, there was a different with release. eg. MATE ported from GTK2 to GTK3 by 16.04 which made the MATE slow down rather significantly on old-slow CPUs; the porting of Xfce from GTK2 to GTK3 occurred much later, and again with me noticing the slowdown during QA/testing..  LXDE which was GTK2 had it's GTK3 port abandoned & a developer blog about how much *heavier *GTK3 was, which led to the switch to the LXQt desktop as a replacement instead. Lubuntu using LXQt was faster (18.10, 19.04) than Xfce for those releases using pentium 4/M/D *i386 *processors, but the difference was not really detectable on any c2d or better processor in my opinion... thus release can matter.  What matters more though in my view is how you use it; matching desktop & apps so they share resources as much as possible (ie. using *lighter* LXQt with GTK3 apps makes no sense; XFCE maybe heavier than LXQt but when used with GTK3 apps Xfce is more RAM efficient thus the result is lighter; but likewise Xfce a mistake if using Qt5 apps)

Some distributions take care of resources better than others... Some take care to match desktop & apps they install, which result in an resource *efficient* install; others go purely for visual features for the creator whom is usually on a reasonably modern machine.  I'd suggest not making assumptions, and look at what you're after.

Xubuntu & Debian tend to make reasonable & efficient assumptions *in my view*. They (Debian vs. Ubuntu) are created with different mindsets though (*even if some people are common in the teams*) thus their assumptions may not match your end-usage.. I'd always test & confirm yourself, or look up details using [https://packages.ubuntu.com/](https://packages.ubuntu.com/) or [https://www.debian.org/distrib/packages](https://www.debian.org/distrib/packages) for a *mental* feel of how they'll exist in your machine when run...

---

### Post by f23948 on 2022-09-20
thank you guys. Solved.

---

