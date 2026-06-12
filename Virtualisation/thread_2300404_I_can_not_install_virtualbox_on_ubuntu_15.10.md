---
title: "I can not install virtualbox on ubuntu 15.10"
date: 2015-10-25
forum: Virtualisation
---

### Post by pavelexpertov on 2015-10-25
Hi, I have installed ubuntu 15.10 to replace linux mint, but the virtualbox can't be installed on it due to dependency issue of libvpx1 dependency. I got libvpx2 installed but can't find libvpx1 on synaptic. Is there a way to install it? Thanks

---

### Post by afz12 on 2015-10-25
Hi pavelexpertovv

I notice the same issue with Ubuntu 15.10 for all versions of Virtualbox using the gdebi installer. It worked OK in mint (possibly based on U14.04?) However it does install OK using the software centre.

---

### Post by Skaperen on 2015-10-26
[more to read on this issue with links for libvpx1 .deb files]("http://www.linuxandubuntu.com/home/solved-virtualbox-is-not-installing-in-ubuntu-1510-due-to-missing-dependency-libvpx1")

---

### Post by howefield on 2015-10-26
> **pavelexpertov said:**
> Hi, I have installed ubuntu 15.10 to replace linux mint, but the virtualbox can't be installed on it due to dependency issue of libvpx1 dependency. I got libvpx2 installed but can't find libvpx1 on synaptic. Is there a way to install it? Thanks

Taking the libvpx1 package from the Vivid repository and installing it before the installing the Virtualbox package worked for me.

[http://packages.ubuntu.com/vivid/libvpx1](http://packages.ubuntu.com/vivid/libvpx1)

---

### Post by saurav_kumar2 on 2015-10-26
There is a bug with Oracle virtualbox.
Can you please check if the hardware virtualisation is enabled from your BIOS?

---

### Post by pavelexpertov on 2015-11-20
Apologies for lateness, anyways, I have managed to install virtualbox via a package. How weird that I can't use the latest virtualbox for fixed bugs. Ohh well...

---

