---
title: "Vlc titlebar flicker/bleedthrough in full screen mode."
date: 2014-01-17
forum: Ubuntu Development Version
---

### Post by nuttzo31 on 2014-01-17
Using an up to date trusty 64bit i find that there is an occasional flicker or bleedthrough of the titlebar when vlc is fullscreen. It happens usually when the control box appears and disappears when mousing. It only flickers briefly but it is annoying, has anyone else experienced this?

---

### Post by mc4man on 2014-01-17
Sure - easily reproducible.  (fullscreen vlc, expose controls
Probably a bug, likely related to compiz ( have you tested in a non compiz session?

---

### Post by mc4man on 2014-01-17
What you can test - 
open ccsm
In Composite plugin > Unredirect Match remove vlc, ie.  & !(class=Vlc)
See if it works any better
 
Not excluding vlc from 'unredirect fullscreen windows' may cause other issues, doesn't cause tearing here put could show something 'off' at very top of screen in some vids

---

### Post by nuttzo31 on 2014-01-18
I can't seem to reproduce it anymore after  i did a fresh reinstall from the latest daily build. Only thing i changed was to remove the acpi_os=linux from the grub default line and added the intel.conf file to use the intel backlight.

---

### Post by nuttzo31 on 2014-01-18
Ok it's come back, it seems it only does it when i am watching a 4:3 movie and when the mouse is on the crop bars. If the mouse is on the movie it doesn't do it, maybe there is a bug report somewhere about it.

edit 
 now its doing it all the time, will have to keep investigating.

---

### Post by nuttzo31 on 2014-01-18
Seems it's a long standing issue with vlc and unity, removing the  !(class=vlc) from ccsm causes long freezes and lockups when switching bettween vlc and another app, will just have to put up with it i suppose or maybe try mate desktop instead.

---

### Post by nuttzo31 on 2014-01-19
Have reinstalled ubuntu 12.04.4 daily 64 bit and there is no problem with vlc there. There must be some sort of regression between ubuntu 12.04 and 14.04

---

### Post by rocky-oceans on 2014-01-20
Did you test with the same VLC version?

---

### Post by nuttzo31 on 2014-01-20
No I might have to manually compile the version used in trusty for precise.

---

