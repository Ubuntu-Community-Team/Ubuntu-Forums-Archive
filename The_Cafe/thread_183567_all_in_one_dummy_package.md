---
title: "all in one dummy package?"
date: 2006-05-28
forum: The Cafe
---

### Post by NESFreak on 2006-05-28
after installing ubuntu you have a base install, now i was wondering is there a sort of dummy package that i can select that installs everysting including the nvidia drivers and restrected codecs. (not like automatix but a package that automaticaly depends on the latest codecs and whenever someting new comes out it will install it (just like the base install dummy, but for a more desktop multimedia home use)

is there a reposity that contains some sort of package like this? cause it would, i gues, make everithing even simpeler than playing a mediafiel in a fresh windows install.

NESFreak

---

### Post by tkjacobsen on 2006-05-28
i thing the seveas repository have some kind of multimedia-codec-dummy-package:
[https://wiki.ubuntu.com/SeveasPackages](https://wiki.ubuntu.com/SeveasPackages)


This is a description from a multimedia dummy:
ubuntu-multimedia-gnome 
Description: Ubuntu multimedia packages - GNOME version More... 

This package will install a complete multimedia system for the GNOME desktop,
including codecs, players and catalog programs


It is safe to remove this package again after installed, the services themself
will not be removed with it
 
Package: ubuntu-multimedia-gnome_0.0.4_i386.deb

---

