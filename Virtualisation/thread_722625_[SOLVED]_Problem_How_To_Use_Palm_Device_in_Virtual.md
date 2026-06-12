---
title: "[SOLVED] Problem: How To Use Palm Device in VirtualBox"
date: 2008-03-12
forum: Virtualisation
---

### Post by ByteDoc on 2008-03-12
I have found enough hints in this forum to get regular USB devices into my VirtualBox Windows XP (Flash Drive), but I still lack one thing:

Problem: Making a Palm device show up in VirtualBox, so the virtual Windows XP can use it (Palm Desktop).

I may have missed some helpful threads, if so, please apologize - but be so kind as to post me the links nonetheless ;)

Hope to get some help,
Thx
ByteDoc

---

### Post by ByteDoc on 2008-03-18
After numerous tries, reading a lot more, playing around a bit, I found that the solution was quite simple in the end:

The Palm device only shows up in VirtualBox when a HotSync is running/has been initiated. So all I had to do was to press HotSync on the device, then after a second it would show up in the status bar at the bottom of the VirtualBox window in the USB submenu.
=> Voila, Palm goes VirtualBox

I think it took me so long because I never tried to HotSync while I still had gPilot/jPilot configured, because I didn't want to sync with them when trying to make it work in VirtualBox. gPilot/jPilot deactivated, and there you go.

---

### Post by Doby on 2009-03-04
I am running 8.10 and virtualbox 2.1 guest xp.  xp sees my centro but when I run hotsync it connects only with jpilot, and when jpilot is not running it times out.

---

### Post by garitd on 2009-04-29
yeah im on 9.04 and i am having the exact same problem =(

---

