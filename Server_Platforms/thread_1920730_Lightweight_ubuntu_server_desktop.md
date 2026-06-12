---
title: "Lightweight ubuntu server desktop"
date: 2012-02-05
forum: Server Platforms
---

### Post by createdcreature on 2012-02-05
I was wondering how I would create a normal GNOME, KDE, XFCE, Blackbox or Fluxbox desktop with nothing on it (software to be of my choice, not the ubuntu team's) with a standard installation of Ubuntu server, e.g. have an empty install of gnome, and fine-tune every bit of software in the system.

---

### Post by ajgreeny on 2012-02-05
> **Robert Moyse said:**
> I was wondering how I would create a normal GNOME, KDE, XFCE, Blackbox or Fluxbox desktop with nothing on it (software to be of my choice, not the ubuntu team's) with a standard installation of Ubuntu server, e.g. have an empty install of gnome, and fine-tune every bit of software in the system.
Don't go for the server system but preferably the Minimal Install CD [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD).  You can then choose what you want on the system.

---

### Post by josephmills on 2012-02-05
there is also "core"
```
sudo apt-get install lxde-core
```
is one there are also Other light-weight ones out there that are old but work great. like fvm IceWm ect. Hope that this helps

---

### Post by arrrghhh on 2012-02-06
> **josephmills said:**
> there is also "core"
```
sudo apt-get install lxde-core
```
is one there are also Other light-weight ones out there that are old but work great. like fvm IceWm ect. Hope that this helps

This ^^.

Also, most that run servers do so GUI-less, because it's much easier to maintain package-management-wise.  Plus, it's much leaner.  If you truly want lightweight, run without a DE.

If you find yourself *needing* a DE, go for the minimal install and add whatever DE you want.  Do **not** go for the server install tho.  Fitting a square peg into a round hole if you put a DE on top of the server edition ;).

---

### Post by collisionystm on 2012-02-06
If you want really light, just install Ubuntu Server and use Byobu

---

