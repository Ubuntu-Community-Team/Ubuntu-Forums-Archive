---
title: "[SOLVED] Diable Server Screensaver?"
date: 2008-08-11
forum: Server Platforms
---

### Post by DjangosClouds on 2008-08-11
Hi,
   I'm running Ubuntu Server 7.04 (Feisty Fawn), problem is that after a few minutes of inactivity the screen goes blank and we don't want it to (we have status info on the screen).
   I have tried altering /etc/console-tools/config so that:
BLANK_TIME=0
POWERDOWN_TIME=0
But it doesn't solve the problem.

Anyone got any other ideas?

Cheers,
   Al

---

### Post by dca on 2008-08-11
See if using 'setterm' with options works...
 
[http://linuxreviews.org/quicktips/screenblanking/](http://linuxreviews.org/quicktips/screenblanking/)

---

### Post by DjangosClouds on 2008-08-12
It works! Thank you.
I've added:
setterm -blank 0
to /etc/bash.bashrc
and now it works just fine.
Cheers,
   Al

---

