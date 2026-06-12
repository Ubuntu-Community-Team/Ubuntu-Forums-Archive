---
title: "Problems installing latest VirtualBox."
date: 2012-06-12
forum: Virtualisation
---

### Post by MrT76 on 2012-06-12
I'm having problems installing latest VirtualBox.

 It all started when I had problems expanding hard drive space, so I was told that it would be easier in the latest VirtualBox.
 I had VirtualBox OSE version 3.1.6
 Now, I have tried uninstalling that VirtualBox version and tried to install version 4.1.16

 But I can not find any icon to start VirtualBox
 I typed in a terminal

 dpkg-L virtualbox

 Got the answer

 thobbe @ Torbjorn-desktop: ~ $ dpkg-L virtualbox
 Package "virtualbox" is not installed.
 Use dpkg - info (= dpkg-deb - info) to examine archive files,
 and dpkg - contents (= dpkg-deb - contents) to list the contents.
 thobbe @ Torbjorn-desktop: ~ $

I have Ubuntu 10.04
 My English is not the best, but I hope you understand and can help me anyway.

---

### Post by wilee-nilee on 2012-06-12
You are or have installed from here correct? The lucid version.
[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

Right click the desktop then launcher name it and use this as the command, and it should launch.
```
/usr/bin/virtualbox
```
Command runs in the terminal as well.

---

