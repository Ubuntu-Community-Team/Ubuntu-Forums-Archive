---
title: "Cannot edit correct xorg.conf"
date: 2008-05-04
forum: Virtualisation
---

### Post by GenPirate on 2008-05-04
In terminal I type sudo gedit etc/X11/xorg.conf and it opens a non existing xorg.conf in home/jay/etc/x11 why won't it point to the correct file?

---

### Post by GenPirate on 2008-05-04
I was able to do it by:

Alt+F2
Type in -> gksu gedit /etc/X11/xorg.conf
Press OK or hit Enter

---

### Post by seamuso on 2008-05-04
> **GenPirate said:**
> In terminal I type sudo gedit etc/X11/xorg.conf and it opens a non existing xorg.conf in home/jay/etc/x11 why won't it point to the correct file?

because of the path ..

you used .. 

etc/X11/xorg.conf

it should be 
/etc/X11/xorg.conf

the leading / makes a huge difference for where the location is.

---

