---
title: "Glamor"
date: 2014-04-13
forum: Ubuntu Development Version
---

### Post by mayagrafix on 2014-04-13
Does it work with 14.04? I get an error message (Package dependencies cannot be resolved) when I try to install with ubuntu software center.
> **Package dependencies cannot be resolved**
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.
The following packages have unmet dependencies:
xserver-xorg-glamoregl-lts-saucy:i386: 
xserver-xorg-video-glamoregl:i386: Depends: libglamor0 (= 0.6.0-0ubuntu4) but 0.6.0-0ubuntu4 is to be installed
                                   Depends: libc6 (>= 2.3.6-6~) but 2.19-0ubuntu6 is to be installed
                                   Depends: libegl1-x11 but it is a virtual package
                                   Depends: libgbm1 (>= 8.1~0) but 10.1.0-4ubuntu4 is to be installed
                                   Depends: xorg-video-abi-15 but it is a virtual package
                                   Depends: xserver-xorg-core (>= 2:1.14.99.902) but 2:1.15.0-1ubuntu7 is to be installed

---

### Post by Gavin77 on 2014-04-14
> **mayagrafix said:**
> Does it work with 14.04? I get an error message (Package dependencies cannot be resolved) when I try to install with ubuntu software center.
> 
**xserver-xorg-glamoregl-lts-saucy**

The file you should be installing is **xserver-xorg-video-glamoregl**.  On my system, it was already installed.

---

### Post by frank18 on 2014-04-14
> **mayagrafix said:**
> Does it work with 14.04? I get an error message (Package dependencies cannot be resolved) when I try to install with ubuntu software center.

Today i did a fresh install of Ubuntu 14.04 with an iso image that i had made a month ago and also had all kinds of problems to install software,did not have flash player working right,couldn't install ubuntu restricted extras and so on.  i struggled for some time,i even made a couple installs, till i decided to do sudo apt-get upgrade instead of update and all the latest software was installed,i don't know why ! normally when one does a fresh install and then install updates it installs all new software,but this time it was not the case,never happened to me.

---

### Post by grahammechanical on 2014-04-14
On my trusty and in it software centre I see two glamor packages already installed and two not installed.

Installed

xserver-xorg-video-glamoregl
libglamor0

Not Installed

libglamor-dev
xserver-xorg-glamor-lts-saucy

That last one is used for upgrading from Precise to Trusty. Why do you need to install it?

Regards.

---

