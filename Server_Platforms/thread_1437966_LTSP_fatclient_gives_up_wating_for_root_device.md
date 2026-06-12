---
title: "LTSP fatclient gives up wating for root device"
date: 2010-03-24
forum: Server Platforms
---

### Post by pjssilva on 2010-03-24
Hello,

I tried to follow the instructions in 

[https://help.ubuntu.com/community/UbuntuLTSP/FatClients](https://help.ubuntu.com/community/UbuntuLTSP/FatClients)

to set up a fat client. Everything was going smooth, the installation of the chroot went well, the client started to boot (and even showed the boot logo) and then... I get the following messages:

----------

Gave up waiting for root device Common problems:

- Boot args (cat /proc/cmdline)
 - Check rootdelay= (did the system wait long enough?)
 - Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /opt/ltsp/amd64 does not exist. Dropping to a shell!

-----------

Then the system drops into a busybox shell. I don't know what is going wrong. My
/proc/cmdline is:

ro initrd=initrd.img quiet splash nbdport=2000 BOOT_IMAGE=vmlinuz 

Any hints of what must be going on? One weird thing I noticed is that the file 

/usr/sbin/nbdrootd /opt/ltsp/images/amd64.img

was not created by ltsp-build-client. I tried to manually run ltsp-update-image but it didn't help.

---

