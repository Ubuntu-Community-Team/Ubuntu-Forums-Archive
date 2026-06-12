---
title: "Preventing the X Server to load at startup in Ubuntu Server 12.04"
date: 2012-05-12
forum: Server Platforms
---

### Post by hipertrofia on 2012-05-12
Hi, I just recently installed Ubuntu Server 12.04. Because I want to be able to use the GUI in some particular occasions I also installed the package ubuntu-desktop. However, the main use for my server is SSH and web, so I would like to disable the default loading of the Gnome desktop every time the system boots. Instead, I want to be able to use startx from the command line to start the GUI whenever I want. Does anybody know how to do this?

---

### Post by sandyd on 2012-05-13
> **hipertrofia said:**
> Hi, I just recently installed Ubuntu Server 12.04. Because I want to be able to use the GUI in some particular occasions I also installed the package ubuntu-desktop. However, the main use for my server is SSH and web, so I would like to disable the default loading of the Gnome desktop every time the system boots. Instead, I want to be able to use startx from the command line to start the GUI whenever I want. Does anybody know how to do this?

Rename /etc/init/gdm.conf to /etc/init/gdm.conf.off to disable GDM autostarting.

You are going to have to edit your ~/.initrc to start gnome/openbox/whatever

---

