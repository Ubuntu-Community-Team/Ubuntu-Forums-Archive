---
title: "Lubuntu 16.04 - Google Earth"
date: 2015-12-25
forum: Ubuntu Development Version
---

### Post by WillEllen on 2015-12-25
I'm trying to install Google Earth (32-bit) in Lubuntu 16.04 but Synaptic Package Manager requires lsb-core to be installed.  When I try to install that, this is what I get:

$ sudo apt-get install lsb-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package lsb-core is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'lsb-core' has no installation candidate

I found a file   'lsb-core_3.2-14ubuntu2_i386.deb'   but that requires other dependencies and will not install.
lsb-base is installed.

Any suggestions beside using Lubuntu 15.10? 

BillEllen

---

### Post by QDR06VV9 on 2015-12-25
This has been talked about here [http://ubuntuforums.org/showthread.php?t=2306007&p=13405154](http://ubuntuforums.org/showthread.php?t=2306007&p=13405154) (Post #5)
Regards

---

### Post by WillEllen on 2015-12-25
I installed the following in order listed without any problem:

1.  lsb-security_4.1+Debian13+nmu1_i386.deb
2.  lsb-invalid-mta_4.1+Debian13+nmu1_all.deb
3.  lsb-core_4.1+Debian13+nmu1_i386.deb
4.  google-earth-stable_current_i386.deb

All is well, thank you

---

