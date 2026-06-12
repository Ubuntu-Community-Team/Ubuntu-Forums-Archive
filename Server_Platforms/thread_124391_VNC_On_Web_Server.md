---
title: "VNC On Web Server"
date: 2006-02-01
forum: Server Platforms
---

### Post by intellidenuser on 2006-02-01
Hey,

I have a web server running in a public location. I need to be able to lock the screen/log out (so ppl dont mess with it). At the same time, I need remote access to the box. 

Everytime I log out of the box, VNC server quits working (a known issue). The same occurs when I lock the screen. Does anyone know a fix/workaround for this?

---

### Post by superm1 on 2006-02-01
You can try using a different VNC server, perhaps that runs on the X server instead of a per user basis.  I'm not sure how to go about it in ubuntu, but in gentoo I'm able to install RealVNC, and build a module for xorg that gets loaded as soon as gdm starts for me.

---

### Post by intellidenuser on 2006-02-07
Ok, I ran a apt get to install the latest version of vnc server hoping it would help but to no avail. Is there a VNC log file I can edit to change this or do I need to modify Ubuntu somewhere?   :-k

---

### Post by intellidenuser on 2006-02-08
Anyone?

---

### Post by intellidenuser on 2006-02-10
Ok, found the fix. Have to use XDMCP over VNC:

[http://www.ubuntuforums.org/showthread.php?t=42941](http://www.ubuntuforums.org/showthread.php?t=42941)

U rock intangible!

---

### Post by tonkatruck on 2006-02-18
ssh ...

---

