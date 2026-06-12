---
title: "xorg constantly crashing"
date: 2013-04-08
forum: Ubuntu Development Version
---

### Post by jinjorge on 2013-04-08
running gnome version of Raring and this morning after running apt-get update/dist-upgrade xorg is constantly crashing.

opened the following bug [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1166295](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/1166295)

anyone else seeing something similar? The computer is unusable as I never know when it's going to crash.

J

---

### Post by dino99 on 2013-04-08
as you early get a compiz issue (missing plugin), you might run ccsm (compizsettingmanager) and set the allowed plugin(s), then run:

compiz --replace ccp &
setsid unity

---

