---
title: "Is there a vanilla Gnome metapackage?"
date: 2017-08-01
forum: Ubuntu Development Version
---

### Post by spupazza on 2017-08-01
Is there a Gnome vanilla meta-package I could use to install Gnome desktop environment starting from a Ubuntu Server installation in Artful?

---

### Post by slickymaster on 2017-08-01
[https://packages.ubuntu.com/search?keywords=gnome-desktop-environment&searchon=names](https://packages.ubuntu.com/search?keywords=gnome-desktop-environment&searchon=names)

---

### Post by spupazza on 2017-08-01
> **slickymaster said:**
> [https://packages.ubuntu.com/search?keywords=gnome-desktop-environment&searchon=names](https://packages.ubuntu.com/search?keywords=gnome-desktop-environment&searchon=names)

that metapackage is not present in Artful as far as I can see.
There's a meta simply called gnome, but version is 3.22+1ubuntu2. I'm just not sure if it will work correctly seeing the 3.22 and not 3.24 nomenclature.

---

### Post by #&amp;thj^% on 2017-08-01
[https://launchpad.net/ubuntu/artful/+source/ubuntu-gnome-meta](https://launchpad.net/ubuntu/artful/+source/ubuntu-gnome-meta)

---

### Post by BenginM on 2017-08-01
for the Gnome desktop , you need to install the package [ubuntu-gnome-desktop]("https://packages.ubuntu.com/search?suite=artful&keywords=ubuntu-gnome-desktop")

---

### Post by thierrybo on 2017-09-09
Don't use the ubuntu-gnome-desktop package in artful. Canonical did not yet removed it in current beta but this package was only useful before 17.10/ artful. Now you just have to install "gnome-session" and choose "GNOME" instead of Ubuntu on the login screen.

---

