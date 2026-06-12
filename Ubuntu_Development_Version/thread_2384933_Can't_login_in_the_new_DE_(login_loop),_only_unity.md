---
title: "Can't login in the new DE (login loop), only unity can login"
date: 2018-02-14
forum: Ubuntu Development Version
---

### Post by miguelpires on 2018-02-14
Hi,
I update from 16.04 directly to 18.04, and now I've this problem.
I can't login in the new DE (gnome session) but only can login to unity.
I've a Ndvia and only the 340 driver works correctly.
Can someone help me out to correct the problem
Regards
Miguel

---

### Post by dino99 on 2018-02-14
First be sure to use genuine versions (no ppa ones), downgrade in case. Then clean the system with gtkorphan (purge the packages found), and bleachbit as root but carefully select the options (no app opened). Logout/in again. If you still have a login loop, then switch to 'nouveau' and remember that wayland session is not recommended, but xorg one. Note you are supposed to login with gdm3, nothing else.

---

### Post by miguelpires on 2018-02-16
Hi,
I've done that, and I continue to have the login loop. If I use noveau the boot don't go to the GIU, and it stops. 
I edit the #/etc/gdm3/custom.conf" to WaylandEnable=false and still no login, only unity works. Any ideas?
Regards
Miguel

---

