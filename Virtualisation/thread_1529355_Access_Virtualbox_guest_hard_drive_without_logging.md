---
title: "Access Virtualbox guest hard drive without logging in/using Virtualbox?"
date: 2010-07-12
forum: Virtualisation
---

### Post by EarthMind on 2010-07-12
Is it possible for me to access my Ubuntu server Guest hard drive contents without logging into the OS (which doesn't work) or by using third-party software?

---

### Post by EarthMind on 2010-07-12
I managed to do it by running a liveCD in Virtualbox.

---

### Post by TheFu on 2010-07-12
It will depend on your host OS and the disk format of the client .VDI file.  I've seen $40 mount-anything programs for MS-Windows, so if your host is MS-Windows, you could be in luck.  I routinely mount VM .img files on my Xen host for rdiff-backup needs, but I'm very careful that the client (DomU) is not running at the time.

It seems the vbox forums have discussed this too.
[http://forums.virtualbox.org/viewtopic.php?t=4748](http://forums.virtualbox.org/viewtopic.php?t=4748)

---

