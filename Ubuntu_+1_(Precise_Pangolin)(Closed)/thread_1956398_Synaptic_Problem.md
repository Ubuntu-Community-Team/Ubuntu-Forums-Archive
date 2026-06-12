---
title: "Synaptic Problem"
date: 2012-04-10
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by cates044 on 2012-04-10
I'm trying to get synaptic package manager installed but the problem is that I have no internet as the ethernet port does not work and to get wifi drivers fixed I need synaptic to uninstall the current drivers.

I have tried to manually install synaptic's deb but I get this:
```
Selecting previously unselected package synaptic.
(Reading database ... 127288 files and directories currently installed.)
Unpacking synaptic (from .../synaptic_0.75.7_i386.deb) ...
dpkg: dependency problems prevent configuration of synaptic:
 synaptic depends on libept1.4.12; however:
  Package libept1.4.12 is not installed.
 synaptic depends on libvte9 (>= 1:0.24.0); however:
  Package libvte9 is not installed.
dpkg: error processing synaptic (--install):
 dependency problems - leaving unconfigured
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Errors were encountered while processing:
 synaptic

```

When I try to launch synaptic nothing happens, then Software Center tells me that I need to "repair catalog".

Any clue on how I can fix this?

Thanks

Dell Inspiron 1501
Ubuntu 12.04 b2

---

### Post by firo2011 on 2012-04-10
" sudo apt-get install -f "        should work bro (without quotes though)

---

### Post by cates044 on 2012-04-10
> **firo2011 said:**
> sudo apt-get install -f        should work bro
The problem is that I have no internet connection though.

---

### Post by firo2011 on 2012-04-10
Download those two packages from packages.ubuntu.com on the computer your writing this on. 
libept1.4.12 && libvte9

---

### Post by firo2011 on 2012-04-10
Or if you know the names of what you need to remove just do it manually with the apt-get remove command

---

### Post by mc4man on 2012-04-10
you need to also acquire the current precise versions of 
libept1.4.12
libvte9 
Place them & the synaptic package in an empty folder, cd to that folder in a terminal & run
```
sudo dpkg -i *.deb
```

---

### Post by cates044 on 2012-04-10
Thank you both very much I synaptic is up and running now.

---

