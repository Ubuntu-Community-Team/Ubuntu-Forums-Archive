---
title: "Touchpad breaks when typing / using function keys"
date: 2012-03-13
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by rrohde on 2012-03-13
Just curious of anybody else came across this: 

I am on a MacBook Pro (5,2) and after logging in, my touchpad usually works just fine. However, as soon as I start to use the keyboard by either typing inside the Unity Dash or pressing a function key (e.g. adjusting the keyboard backlight), the touchpad stops working completely until I log out and back in again. On the other hand, my external USB mouse keeps working perfectly. 

I assume this is a xserver-xorg-input-synaptics issue, but I might be wrong. My current version is: 

xserver-xorg-input-synaptics:
  Installed: 1.5.99~git20120223-0ubuntu2
  Candidate: 1.5.99~git20120223-0ubuntu2
  Version table:
 *** 1.5.99~git20120223-0ubuntu2 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/main amd64 Packages
        100 /var/lib/dpkg/status


I posted this bug on Launchpad already ([https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/938039](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/938039)), but so far no fix (and sadly, no communication with any developer). This is a regression as my touchpad worked perfectly until a few weeks ago. 

Any hints, tips or ideas? 

This is a very frustrating bug and very counter productive at work.

---

### Post by mc4man on 2012-03-13
touchpads are taken some hits during PP dev, your issue is obviously hardware specfic
Whether it is the xserver-xorg-input-synaptics  package in whole, part, or not all wouldn't know, you could try reverting it to some of the previous & see if any change
(touchpads have also been affected by other packages like the gtk+3 ones

Any of the **1.5 **packages here can be downgraded to without trouble, if no change try another one or upgrade back to current

[https://launchpad.net/ubuntu/precise/+source/xserver-xorg-input-synaptics](https://launchpad.net/ubuntu/precise/+source/xserver-xorg-input-synaptics)

---

### Post by rrohde on 2012-03-13
Thank you for your reply! I will try and downgrade that package and see if it changes the behavior.

---

