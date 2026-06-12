---
title: "Can't install any update after error installing snapd"
date: 2018-06-13
forum: Ubuntu Development Version
---

### Post by corradoventu on 2018-06-13
running sudo apt upgrade many updates are correclty done but 
Setting up snapd (2.33+18.10ubuntu3) ... the installation stops and no other updates can be done 

snapd (2.33+18.10ubuntu3) cosmic never finishes installing. Can't install any other updates. 
[https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1776622](https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1776622)

---

### Post by dino99 on 2018-06-13
I did not got that problem; do you have recently cleaned your install (via gtkorphan/bleachbit) or use some ppa(s) that could possibly introduce conflicts ?

---

### Post by corradoventu on 2018-06-17
Problem happens with Cosmic installed from ISO Ubuntu 18.10 "Cosmic Cuttlefish" - Alpha amd64 (20180527) but not from Ubuntu 18.10 "Cosmic Cuttlefish" - Alpha amd64 (20180509) same PC different partition. I'm not using any PPA.
[https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1776622](https://bugs.launchpad.net/ubuntu/+source/snapd/+bug/1776622)
same problem also on a different hardware installed from Ubuntu 18.10 "Cosmic Cuttlefish" - Alpha amd64 (20180611)

---

### Post by corradoventu on 2018-06-28
Solved following suggestions in [https://ubuntuforums.org/showthread.php?t=2393347&page=3](https://ubuntuforums.org/showthread.php?t=2393347&page=3)

---

