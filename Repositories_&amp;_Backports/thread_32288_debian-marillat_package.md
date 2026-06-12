---
title: "debian-marillat package"
date: 2005-05-06
forum: Repositories &amp; Backports
---

### Post by slava on 2005-05-06
hello 
i am developint a debian-marillat package that will automatically add unofficial debian marillat package repository to sources.list The package works fine but it would be nice if after install it could call apt-get update so that the repository's packages become instantly available. if i try to call apt-get update from postinst script it fails because dpkg is locked by the parent process. thanks for help

---

### Post by poofyhairguy on 2005-05-06
[QUOTE=slava]hello 
i am developint a debian-marillat package that will automatically add unofficial debian marillat package repository to sources.list The package works fine but it would be nice if after install it could call apt-get update so that the repository's packages become instantly available. if i try to call apt-get update from postinst script it fails because dpkg is locked by the parent process. thanks for help[/QUOTE]


Marillat can cause problems. Almost everything in it is in Jdong's repo, made for Ubuntu. Try that instead and see if it works..

---

### Post by slava on 2005-05-07
my problem is not related to which repository is added, but to necessety of updating package list as part of debian-marillat package install. I need to apt-get update as soon as the package installs, so that other packages that depend on it and the repository it makes available can be found

---

### Post by Seth on 2005-05-07
Is it really that complicated for the user to paste in three lines, or use Synaptic and do it by GUI?

Don't waste your time.

---

### Post by slava on 2005-05-07
why don't you please just help me do what i asked...
the package in addition to adding repository registers its gpg keys and it i think it would be very usefull way of automatically adding unofficial packages, so i do not think i am waisting my time

---

### Post by poofyhairguy on 2005-05-07
[http://www.mrbass.org/linux/ubuntu/](http://www.mrbass.org/linux/ubuntu/)

---

