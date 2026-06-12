---
title: "Need help wine can't find cdrom"
date: 2010-05-25
forum: Wine
---

### Post by ronnielsen1 on 2010-05-25
Ok, I'm trying to get reader rabbit working in wine (and with the exception of graphics, it works great) but when it installs it sets up the menu with 

> env WINEPREFIX="/home/ron/.wine" wine start /Unix /home/ron/.wine/dosdevices/c:/windows/profiles/ron/Start\ Menu/Programs/The\ Learning\ Company/Reader\ Rabbit\'s\ Kindergarten.lnk

It starts and complains that it can't find cdrom and quits. If I browse directly through nautilus and go to 

> /media/cdrom0/AUTORUN/AUTORUN.EXE


It works great. If I enter into a terminal and enter wine /media/cdrom0/AUTORUN/AUTORUN.EXE
it also works. If I edit the menus and edit the command to reflect wine /media/cdrom0/AUTORUN/AUTORUN.EXE
it can't find cdrom

---

### Post by ronnielsen1 on 2010-05-25
I've been experimenting with wine lately. When I first tried it years ago it didn't seem to work for anything. It actually appears pretty good now. I've learned more about wine in the last couple of days (dll overrides, etc) and it's starting to interest me.
Plus the fact, I've recently added a gig of memory and my computer is lightning fast now (even with xp running in virtualbox and full compiz)

---

### Post by cogadh on 2010-05-25
How do you have the CD-ROM drive configured in the "Drives" tab of winecfg?

---

### Post by ronnielsen1 on 2010-05-25
D: /media/cdrom0

---

### Post by ronnielsen1 on 2010-05-27
Still haven't figured it out. I know there's a workaround that works but it bugs me it won't work when I edit the menu. It doesn't make sense

---

