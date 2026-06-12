---
title: "Cannot get Flash installed"
date: 2016-01-14
forum: Ubuntu/Debian BASED
---

### Post by Brian_Childs on 2016-01-14
I have the latest Debian installed from the NOOBS 1.5.0 and I want to install Flash to work with Web 3.8.2

I get the following error message when I try:

----------------------------
sudo apt-get install flashplugin-nonfree
Reading package lists...
Building dependency tree...
Reading state information...
Package flashplugin-nonfree is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'flashplugin-nonfree' has no installation candidate
----------------------------
This is what my /etc/apt/sources.list contains:
------------------
deb [http://mirrordirector.raspbian.org/raspbian/](http://mirrordirector.raspbian.org/raspbian/) jessie main contrib non-free rpi
# Uncomment line below then 'apt-get update' to enable 'apt-get source'
#deb-src [http://archive.raspbian.org/raspbian/](http://archive.raspbian.org/raspbian/) jessie main contrib non-free rpi

----------------------

Help please

---

### Post by howefield on 2016-01-14
Thread moved to the "*Ubuntu/Debian BASED*" forum

---

