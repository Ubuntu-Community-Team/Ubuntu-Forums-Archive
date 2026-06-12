---
title: "XenServer 5.6 &amp; Ubuntu 10.04 guest: Installation of grub-pc failed"
date: 2010-06-24
forum: Virtualisation
---

### Post by jan.jonas on 2010-06-24
I'm running XenServer 5.6 and I have a Ubuntu 10.04 guest system.

I followed the instructions from here to set up the Ubuntu 10.04 guest system: [http://www.jansipke.nl/installing-xenserver-tools-on-ubuntu-10-04](http://www.jansipke.nl/installing-xenserver-tools-on-ubuntu-10-04)

After installing the apache2 web server the system requires the package "grub-pc", but unfortunately the installation failed:

Setting up grub-pc (1.98-1ubuntu6) ...
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)

How could I get more information/logs about the problem that causes the installation of grub-pc to fail?

---

### Post by jan.jonas on 2010-06-25
I think I found the reason for the problem: The grub2 installation does not support virtual hard disks like /dev/xvdX. 
The path from here [https://bugs.launchpad.net/ubuntu/+bug/524434](https://bugs.launchpad.net/ubuntu/+bug/524434) fixed the problem.

---

