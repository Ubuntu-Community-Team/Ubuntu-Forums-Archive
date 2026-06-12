---
title: "Uh-Oh, There is an usr dir in /usr"
date: 2009-12-19
forum: Security
---

### Post by MechaMechanism on 2009-12-19
So wandering around I see an usr dir in /usr.  So now it goes like this...
"/usr/usr/share/applications"

The only third party applications I have installed are GoogleEarth and Picasa which are no longer installed and they came from medibuntu.  Is there a way to find out how these dir got created.  Right now they are empty, just dir only.  I checked with Nautilus hidden files turned on and with ls -a.  Any other tricks I can use.  This bothers me enough that if I can't find the answer I might just reinstall.  Any help would be appreciated.

---

### Post by diesch on 2009-12-19
```
dpkg -S /usr/usr
``` tells you if it belongs to any package. If not just remove it.

---

### Post by MechaMechanism on 2009-12-19
> **diesch said:**
> ```
dpkg -S /usr/usr
``` tells you if it belongs to any package. If not just remove it.
Awesome reply.  That worked.  I'm trying out a new software called Shotwell and sure enough it belongs to Shotwell.  I installed it from an Ubuntu PPA.  I will contact them and let them know about this.  Thanks again.

---

