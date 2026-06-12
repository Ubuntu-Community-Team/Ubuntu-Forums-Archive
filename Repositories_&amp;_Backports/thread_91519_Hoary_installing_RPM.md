---
title: "Hoary installing RPM?"
date: 2005-11-17
forum: Repositories &amp; Backports
---

### Post by poptones on 2005-11-17
Why am I getting an updater alert to install librpm and rpm?

---

### Post by cstudent on 2005-11-17
Have you used alien to convert a rpm file to a deb?

Bill

---

### Post by poptones on 2005-11-17
No, I've never used alien. Never used RPM. I can't even find it in the log. Is librpm and rpm installed by default?

---

### Post by codejunkie on 2005-11-17
[quote=poptones]No, I've never used alien. Never used RPM. I can't even find it in the log. Is librpm and rpm installed by default?[/quote] i think alien is installed by default in hoary if your using breezy you have to install it with ```
sudo apt-get install alien
``` then you can convert the .rpm to .deb with ```
sudo alien -d nameofpackage.rpm
``` and then install the .deb package it made with ```
sudo dpkg -i nameofpackage.deb
``` just a warning though converting rpm's is a hit or miss thing it might work with some things but your better off just sticking with .deb packages because it can cause some major breakage.
edit: sorry i read the post wrong, it's just a security update to those packages because alien is installed by default in hoary.

---

### Post by aysiu on 2005-11-17
What do the Synaptic descriptions of rpm and librpm say?

---

### Post by bored2k on 2005-11-17
**rpm** is installed by default in Ubuntu. It's used in conjunction with **alien** to convert rpm packages to deb.

[QUOTE=The RPM package]Description: Red Hat package manager
 If you want to install Red Hat Packages then please use the alien
 package. Using rpm directly will bypass the Debian packaging system!
[/QUOTE]
>  Alien allows you to convert LSB, Red Hat, Stampede and Slackware Packages
 into Debian packages, which can be installed with dpkg.
 .
 It can also generate packages of any of the other formats.
 .
 This is a tool only suitable for binary packages.


---

