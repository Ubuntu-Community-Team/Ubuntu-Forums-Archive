---
title: "Where do I found an PXE diskless boot image for server"
date: 2014-09-22
forum: Server Platforms
---

### Post by RL600 on 2014-09-22
Hello all,

I am setting up an diskless boot option inside of my network. 

I have an Cisco router with an DHCP server. 
Within the DHCP config I set the TFTP server to an vmware vsphere server. 
On the server (on an Ubuntu virtual machine) inside the map where my TFTP server is pointing to I put the file from here [http://cdimage.ubuntu.com/netboot/](http://cdimage.ubuntu.com/netboot/) (14.04 ["netboot.tar.gz"]("http://archive.ubuntu.com/ubuntu/dists/trusty-updates/main/installer-amd64/current/images/netboot/netboot.tar.gz")). 
This works perfectly!! I booted on an different PC and it works.

But this option gives me an install prompt on startup. 
What I want (if possible) is an diskless boot option. 
So when I start up on an different PC it picks up the PXE image.
Then the pc usages the server as storage an uses its own hardware recourses. 
So I need the user to usage the local hardware recourses and not something like LTSP.

**Where do I found an diskless  boot image which I can put inside of my TFTP folder?**

Thanks in advanced,

RL600

P.S. Thanks for moving

---

### Post by cariboo on 2014-09-22
Moved to Server Platforms.

---

