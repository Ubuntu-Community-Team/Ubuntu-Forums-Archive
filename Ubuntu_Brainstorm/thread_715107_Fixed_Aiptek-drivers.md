---
title: "Fixed Aiptek-drivers"
date: 2008-03-04
forum: Ubuntu Brainstorm
---

### Post by Steveway on 2008-03-04
Since the Aiptek-driver has finally been fixed and a new owner arrived, Hardy needs to ship the fixed version to be truely "Hardy".
The new Owner's name is, René van Paassen and he seemed to have fixed the driver, finally.
The version has been bumped to 1.1.1 and it should have fixed most bugs.
Tarballs are still only avaiable for the old broken version that still comes with Ubuntu (that version is from 2006!).
Hopefully the Ubuntu-devs make a new .deb soon and maybe they could add a script that checks lsusb for something like this:
```
Bus 001 Device 002: ID 08ca:0021 Aiptek International, Inc. APT-2 Tablet
```
(That's from my tablet.) 
And then add the appropiate lines to the xorg.conf like in this how-to: [http://ubuntuforums.org/showthread.php?t=122735&highlight=aiptek](http://ubuntuforums.org/showthread.php?t=122735&highlight=aiptek)
I hope to see updates comming through soon.

(Link to the gitweb: [http://gitweb.freedesktop.org/?p=xorg/driver/xf86-input-aiptek.git;a=summary](http://gitweb.freedesktop.org/?p=xorg/driver/xf86-input-aiptek.git;a=summary) )

Bug Reported: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-aiptek/+bug/198599](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-aiptek/+bug/198599)

---

### Post by 23meg on 2008-03-04
Please file a bug report. You'll also need a feature freeze exception.

[https://wiki.ubuntu.com/FreezeExceptionProcess](https://wiki.ubuntu.com/FreezeExceptionProcess)

---

