---
title: "Compiz -- CPU Intensive"
date: 2012-09-09
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by makitso on 2012-09-09
I am running the latest 12.10 in Virtualbox.  I noticed that Compiz is running at it is really eating cpu.  Changed to 4 cpu's and its better now.

So, is Compiz an indicator that I am running in degraded mode e.g. fallback?  System Settings/Details notes driver unknown, experience standard.

---

### Post by dino99 on 2012-09-09
compiz is not bug free yet :( and with virtualbox thats full adventure :P

better to install gnome-classic (without effects) aka gnome-session-fallback

---

### Post by jbicha on 2012-09-09
I think broken 3D in VirtualBox is [bug 1039157]("http://pad.lv/1039157"); fortunately that patch is small so that will hopefully get fixed soon. After that's fixed, [bug 1030891]("http://pad.lv/1030891") might cause you problems with Unity or GNOME Classic with effects.

---

