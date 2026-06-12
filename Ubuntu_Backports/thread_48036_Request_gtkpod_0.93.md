---
title: "Request: gtkpod 0.93"
date: 2005-07-10
forum: Ubuntu Backports
---

### Post by pulp on 2005-07-10
Hi. It'd be great if the new gtkpod version could be backported. It's already in Breezy.

Thanks so much

---

### Post by Seth on 2005-07-11
[QUOTE=pulp]Hi. It'd be great if the new gtkpod version could be backported. It's already in Breezy.

Thanks so much[/QUOTE]
 Here you are:

[http://sethkinast.com/ubuntu/hoary/backports/gtkpod_0.93.1-1~5.04ubp1_i386.deb](http://sethkinast.com/ubuntu/hoary/backports/gtkpod_0.93.1-1~5.04ubp1_i386.deb)

---

### Post by pulp on 2005-07-12
[QUOTE=Seth]Here you are:

[http://sethkinast.com/ubuntu/hoary/backports/gtkpod_0.93.1-1~5.04ubp1_i386.deb](http://sethkinast.com/ubuntu/hoary/backports/gtkpod_0.93.1-1~5.04ubp1_i386.deb)[/QUOTE]
 I have to thank you. It works perfectly with my ipod-shuffle

---

### Post by timeoff on 2005-07-14
[QUOTE=Seth]Here you are:

[http://sethkinast.com/ubuntu/hoary/backports/gtkpod_0.93.1-1~5.04ubp1_i386.deb](http://sethkinast.com/ubuntu/hoary/backports/gtkpod_0.93.1-1~5.04ubp1_i386.deb)[/QUOTE]


Unfortunately I get the following error........

Selecting previously deselected package gtkpod.
dpkg: regarding gtkpod_0.93.1-1~5.04ubp1_i386.deb containing gtkpod:
 gtkpod-aac conflicts with gtkpod
  gtkpod (version 0.93.1-1~5.04ubp1) is to be installed.
dpkg: error processing gtkpod_0.93.1-1~5.04ubp1_i386.deb (--install):
 conflicting packages - not installing gtkpod
Errors were encountered while processing:
 gtkpod_0.93.1-1~5.04ubp1_i386.deb

presumably I need the version with aac or something? 

T

---

### Post by Seth on 2005-07-14
[QUOTE=timeoff]Unfortunately I get the following error........

Selecting previously deselected package gtkpod.
dpkg: regarding gtkpod_0.93.1-1~5.04ubp1_i386.deb containing gtkpod:
 gtkpod-aac conflicts with gtkpod
  gtkpod (version 0.93.1-1~5.04ubp1) is to be installed.
dpkg: error processing gtkpod_0.93.1-1~5.04ubp1_i386.deb (--install):
 conflicting packages - not installing gtkpod
Errors were encountered while processing:
 gtkpod_0.93.1-1~5.04ubp1_i386.deb

presumably I need the version with aac or something? 

T[/QUOTE]
 I would say uninstall that other one.

---

