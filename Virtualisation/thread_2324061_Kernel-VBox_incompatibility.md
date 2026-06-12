---
title: "Kernel-VBox incompatibility"
date: 2016-05-10
forum: Virtualisation
---

### Post by JKyleOKC on 2016-05-10
After updating my kernel via Software Updater today, to 3.0.13-86, the system failed upon restarting, complaining about VirtualBox 5.0.20. A restart, selecting the 3.0.13-85 kernel, removed the problem, but the system now insists it needs to restart to complete an update. Upon restarting, the insistence is still there!

Apparently kernel -86 and VBox 5.0.20 are incompatible. Anyone able to determine which needs fixing?

---

### Post by QDR06VV9 on 2016-05-10
Hi JKyleOKC
Sometimes, it's easier to just have apt-get fix the problem that have been created, which installs missing dependencies 

```
 sudo apt-get -f install
```
and also
```
 dpkg -r virtualbox*.deb
 dpkg -i virtualbox*.deb

```
 And just a guess here but have you installed
```
 sudo apt-get install dkms linux-header-generic ...

```
But i always use a PPA for VB...If you are interested
```
sudo sh -c 'echo "deb http://download.virtualbox.org/virtualbox/debian $(lsb_release -cs) contrib" >> /etc/apt/sources.list.d/virtualbox.list' 

```
```
sudo apt-get update
sudo apt-get install VirtualBox-5
```
Hope this is usefull

---

### Post by JKyleOKC on 2016-05-10
I've been using the PPA for a couple of years now, at least, and VBox works just fine with the -85 kernel. However over on the VBox forums there's another compatibility-problem report. However that one involves Ubuntu 16.04 and I'm still on Xubuntu 14.04.4, and also that problem seems to involve a name-change of vboxdrv to rcvboxdrv, which **might** be part or possibly all of the problem I'm having.

Since my problem occurs only when I run the -86 kernel, I suspect that it's due to some change there. VBox itself hasn't been changed since Software Updater last modified it through the PPA.

Thanks for the quick response! Perhaps a kernel guru will come across this thread and have a few ideas.

---

### Post by QDR06VV9 on 2016-05-10
Well sorry to hear that.
I am running
> VirtualBox Graphical User Interface Version 5.0.20_OSE r106931
© 2004-2016 Oracle Corporation
Copyright © 2016 Oracle Corporation and/or its affiliates. All rights reserved

With Kernel: 4.5.3-1 with no problems
And according to them a fix was issued: [https://gcc.gnu.org/bugzilla/show_bug.cgi?id=55940](https://gcc.gnu.org/bugzilla/show_bug.cgi?id=55940)
Referred by [https://www.virtualbox.org/ticket/11035](https://www.virtualbox.org/ticket/11035)

---

