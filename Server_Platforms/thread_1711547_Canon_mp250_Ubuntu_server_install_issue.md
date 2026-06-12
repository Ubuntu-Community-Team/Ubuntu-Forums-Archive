---
title: "Canon mp250 Ubuntu server install issue"
date: 2011-03-21
forum: Server Platforms
---

### Post by eminrg on 2011-03-21
hello 

my system runs on ubuntu server 10.10 64bit 

when i try to install a canon mp250 printer and give ./install.sh command i get this result :

eminrg@Server:/usr/share/cnijfilter-mp250series-3.40-1-deb$ sudo ./install.sh
==================================================

Canon Inkjet Printer Driver Ver.3.40-1 for Linux
Copyright CANON INC. 2001-2010
All Rights Reserved.

==================================================
An error occurred. The package management system cannot be identified.
eminrg@Server:/usr/share/cnijfilter-mp250series-3.40-1-deb$

what could be the problem ?

---

### Post by thomasw_lrd on 2011-03-21
> **spyderpride said:**
> I think I figured it out...

First, and not sure if this is entirely relevant or not, unplug printer  from the USB port and delete the improperly configured printer from  System--Administration--Printing.  Just right click on it and delete it.

Install ia32-libs. Note that you need to have the box checked for the canonical partner repository in Software Sources.

```
sudo apt-get install ia32-libs
```Install the i386 debs as such:
```

sudo dpkg --force-architecture -i cnijfilter-common_3.20-1_i386.deb
sudo dpkg --force-architecture -i cnijfilter-mp250series_3.20-1_i386.deb

```I did this and it worked.  I hate to say this, but if it would have been a snake it would have bit us in the face.  

This gets the printing working, scanning will take more work (compiling from latest sane-backends source). [http://ubuntuforums.org/showthread.php?t=1314209&page=2](http://ubuntuforums.org/showthread.php?t=1314209&page=2)

This will work.

---

