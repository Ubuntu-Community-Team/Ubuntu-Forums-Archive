---
title: "Install Ubuntu over the Internet"
date: 2007-11-02
forum: The Cafe
---

### Post by Black Mage on 2007-11-02
Is there a way I can install Ubuntu over the internet? Like, I know the ip address, which is external and behind a firewire, and I want to install Ubuntu from server over the internet to another computer without me being there, but the computer being on. Is this possible?

---

### Post by seshomaru samma on 2007-11-03
I googled "Ubuntu network install" and came up with
[this]("http://wiki.koeln.ccc.de/index.php/Ubuntu_PXE_Install")

---

### Post by etorvinen on 2009-05-30
download and install the "minimal ISO" from the ubuntu site.

since i have a dell my installation frezes during the installation. the minimal ISO uses the internet to download all the files.

found my info here: 
[http://ubuntuforums.org/showthread.php?t=625852](http://ubuntuforums.org/showthread.php?t=625852)


the ISOs can be found here: 
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

hope it helps

---

### Post by ssam on 2009-05-30
sounds like you want to do a **remote install**. I think it is possible, but you may need to have linux already installed on the machine, have ssh access to it, have partitions already existing (i think its possible to unmount swap and install onto that if thats all you have).

you will probably need to use debootstrap, and to have a good knowledge or partitioning, packages, repositories, bootlaoders and the command line.

---

### Post by kevin11951 on 2009-05-30
would KVM-Over-IP work?  ive never used em, but they appear to be what you are looking for.  [http://en.wikipedia.org/wiki/KVM_switch#KVM_over_IP](http://en.wikipedia.org/wiki/KVM_switch#KVM_over_IP)

---

### Post by don_quixote on 2009-05-30
I remember doing this with Debian in 1999 or so, and I remember it being exceedingly simple.  Would like to know if Ubuntu has something like that.

---

### Post by Dreamglider on 2009-11-11
> **don_quixote said:**
> I remember doing this with Debian in 1999 or so, and I remember it being exceedingly simple.  Would like to know if Ubuntu has something like that.

Same here i installed Ubuntu of the internet. i booted from floppie disk(Two disks of memory serves me right) and the rest was as a standard CD isntall.
I Just cant find the url to the howto again sorry :/

---

