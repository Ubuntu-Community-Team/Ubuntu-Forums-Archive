---
title: "Seamonkey 2.31 does not show HTML5 video and Flash video/audio (2.30 does)"
date: 2014-12-19
forum: Ubuntuzilla
---

### Post by Wladimir Mutel on 2014-12-19
On 2 my systems, after upgrade of Seamonkey-mozilla-build from 2.30 to 2.31, the browser stopped playing HTML5 video (black window, only audio is heard), as well as it stopped running Flash plugins (no audio/video at all)
Reverting Seamonkey to 2.30 helps. 
One system is running 64-bit Kubuntu 14.04 with latest LTS updates, xserver-xorg-core 2:1.15.1-0ubuntu2.5 and xserver-xorg-video-intel 2:2.99.910-0ubuntu1.3. CPU is Core i3 4130T with integrated graphics. Display is 1920x1200 DVI (LG W2600HP)
Another system uses 64-bit Kubuntu Vivid, xserver-xorg-core 2:1.16.2.901-1ubuntu3 and xserver-xorg-video-intel 2:2.99.916+git20141119-1~exp1ubuntu1. CPU is Core i3 U380 (380UM) with integrated graphics, display is 1366x768 (Acer 1830T laptop). 
On both systems, desktop composition is enabled. Flash plugin is 11.2.202.425 everywhere.

Can you please give me some directions on where to look next to investigate this problem ?

---

### Post by nanotube on 2014-12-20
Hi Wladimir,

I just tested here on my 64bit xubuntu and the latest seamonkey. both html5 and flash videos (i checked on random youtube videos) worked fine.

Can you try testing with a fresh profile with no addons, themes, or other modifications, to see if the problem persists?

If not, then you get to try figuring out which addon causes the problem. if problem persists with fresh profile, then I would suggest contacting the seamonkey team directly. here's a link:
[http://www.seamonkey-project.org/community#bugreport](http://www.seamonkey-project.org/community#bugreport)

Since ubuntuzilla only packages unmodified seamonkey releases, the upstream project is your best bet for getting help.

Cheers,
nanotube

---

### Post by Wladimir Mutel on 2014-12-23
ok, I needed to disable FlashBlock 1.3.19 to get everything back right.
FlashBlock upgrade to v.1.3.20 did not help, 1.5.17 also was not installable.
Probably will have to go without FlashBlock for a while.

---

### Post by nanotube on 2014-12-23
Aha I see. I guess you can contact the flashblock extension authors if you want them to fix it for seamonkey 2.31.
Alternatively, just go into addons manager -> plugins, and set flash plugin to "ask to activate", instead of "always activate". this is essentially equivalent to flashblock.

---

