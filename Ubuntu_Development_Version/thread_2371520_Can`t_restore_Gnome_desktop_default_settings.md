---
title: "Can`t restore Gnome desktop default settings"
date: 2017-09-15
forum: Ubuntu Development Version
---

### Post by sebastian1978 on 2017-09-15
After update from 17.04 to 17.10 my Gnome desktop is a mess. I tryed Gnome Tweaks, rm -rf .gnome .gnome2 .gconf .gconfd .metacity .cache .dbus .dmrc .mission-control .thumbnails ~/.config/dconf/user ~.compiz*
Still have bottom panel, ugly colors and unreadable fonts in notification area. Please help

---

### Post by dino99 on 2017-09-15
Start gtkorphan & bleachbit (as root, but select carefully the options) to clean the system, and then reboot

---

