---
title: "Done It Finally"
date: 2013-07-14
forum: Virtualisation
---

### Post by jaysonn on 2013-07-14
Well all i've done it, i've finally switched to linux, switched off windows as my main source....
But I would like to run a win OS as a VM, not as a dual boot.....

Therefore, could anyone reccomend which is the most reliable, simple to use VM for ubuntu v12.10 please?
& if you could point me too a download site this would aslo be appreciated!!!

Thanks team (in advance)

---

### Post by The Spectre on 2013-07-14
VirtualBox works great...

[https://www.virtualbox.org/](https://www.virtualbox.org/)

---

### Post by 2Stoned on 2013-07-14
> **The Spectre said:**
> VirtualBox works great...

[https://www.virtualbox.org/](https://www.virtualbox.org/)


The best VM for Linux imo.

---

### Post by JKyleOKC on 2013-07-14
+10

I have almost a dozen vbox VMs on this machine, although I never run more than two of them at a time and try to avoid even that many since I have only 3 GB of RAM available and don't want to force swap file usage. I started with VMWare Server 2.0 (no longer available) but found vbox to be much more user-friendly. When you download from the Oracle site linked above, be sure to get the extension pack in addition to the main file -- it's required if you want to use USB devices in the VMs, and the docs are not extremely clear about this.

---

### Post by ibjsb4 on 2013-07-14
Virtualbox here too and [downloading from the site]("https://www.virtualbox.org/wiki/Linux_Downloads") seems to work better.

---

### Post by supershin on 2013-07-16
> Note: Ubuntu/Debian users might want to install the dkms package to ensure that the VirtualBox host kernel modules (vboxdrv, vboxnetflt and vboxnetadp) are properly updated if the linux kernel version changes during the next apt-get upgrade. For Debian it is available in Lenny backports and in the normal repository for Squeeze and later. The dkms package can be installed through the Synaptic Package manager or through the following command:

sudo apt-get install dkms

If you want the latest install and don't mind manually updating it, install from the site otherwise you can install from the ubuntu repo.

---

### Post by jaysonn on 2013-07-17
Thank you All for your support VirtualBox it is then as the 1st off....:)

---

