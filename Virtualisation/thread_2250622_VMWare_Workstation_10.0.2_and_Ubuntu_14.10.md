---
title: "VMWare Workstation 10.0.2 and Ubuntu 14.10"
date: 2014-10-29
forum: Virtualisation
---

### Post by ToraxOutlaw on 2014-10-29
I can't seem to find an answer for this anywhere on the internet. I'm having issues trying to get VMWare Workstation 10.02 to install on Ubuntu 14.10, it keeps coming up with an error when trying to install the modules. I have the error log here, if anyone can shed any light on this that will be fantastic. Here is a copy of the error log.

[ATTACH]257595[/ATTACH]

---

### Post by ToraxOutlaw on 2014-10-29
Ok so I uninstalled it, wipe my harddrive and started again with a fresh install on Ubuntu 14.10 on my Acer C720 Chromebook, now I'm getting a different error log. I would like to get this installed please so if anyone know how, help a fellow Ubuntu user out.

[ATTACH]257596[/ATTACH]

---

### Post by tripp98 on 2014-11-02
Here is a link to the install procedure for 13.10

[http://itsfoss.com/install-vmware-player-ubuntu-1310/](http://itsfoss.com/install-vmware-player-ubuntu-1310/)



It sounds like you are missing step one.  having the build essentials and headers installed prior to installing vmware.

---

### Post by ToraxOutlaw on 2014-11-03
I already have the latest version. This is the readout from my terminal:

deadpool@chrubuntu:~$ sudo apt-get install build-essential linux-headers-$(uname -r)
[sudo] password for deadpool: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-3.17.0-031700rc1-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
deadpool@chrubuntu:~$

---

### Post by ToraxOutlaw on 2014-11-07
So any suggestions on how to fix this and get it to install?

---

### Post by apple6 on 2014-11-07
Apparently most people on here use VirtualBox - that's what I was told earlier so I've been using that instead. 

I've also been told not to have more that one VM on a system... So I deleted VMWare

---

### Post by QIII on 2014-11-07
I can't look at your text file as I am on my cell phone, but I will make an observation that is not likely far from the mark.

If you are using Chrubuntu, which is a kludge, it might be difficult to determine if there is something about that which is causing problems.  This may include kernel, header or build-essential differences.

It might possibly be that VT-x is not turned on in your BIOS -- which you may want to check.

---

### Post by houstonbofh on 2014-11-09
It can be done on 14.04 and without build essential as I did it.  Not sure what your error is, but it is possible on 14.04...

---

### Post by sammiev on 2014-11-09
> **houstonbofh said:**
> It can be done on 14.04 and without build essential as I did it.  Not sure what your error is, but it is possible on 14.04...

I'm using 14.10 and have VMware installed and I'm not sure why your getting any errors. It was a very easy ride to install any software into VMware.

It seems it's looking for a directory that is not there. It maybe a installation error.

---

### Post by chick2 on 2014-11-10
I'm using VMWare 10.0.4 and Ubuntu 14.10, also had no installation issues.  Same with VMWare 10.0.3, and with Ubuntu 14.04

---

