---
title: "How Do I Disable Apache2 from Running on Startup?"
date: 2007-09-13
forum: Server Platforms
---

### Post by Cris987 on 2007-09-13
I'm running feisty kubuntu, if that makes a difference.

---

### Post by Matt Yun on 2007-09-13
In a terminal console, do the following commands:

To stop apache2 for this session only:
**sudo /etc/init.d/apache2 stop**

To remove apache2 permanently from startup scripts:
**sudo update-rc.d apache2 remove**

To reinstate apache2 in the startup scripts:
**sudo update-rc.d apache2 defaults**

---

### Post by TheReaper on 2007-09-14
Edit /etc/default/apache2 as root and set NO_BOOT to 1.

greets

---

