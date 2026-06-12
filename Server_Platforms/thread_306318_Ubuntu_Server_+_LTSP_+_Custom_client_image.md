---
title: "Ubuntu Server + LTSP + Custom client image"
date: 2006-11-24
forum: Server Platforms
---

### Post by mimiru on 2006-11-24
Hi,

I have installed LTSP with the ltsp-build-client command on an Ubuntu server 6.10 .

My trouble is : How do we add more programs with apt-get ?

If I understood the system use a chrooted system ..... I've tried to do a : chroot /opt/ltsp/i386 apt-get install mytool ......

however it does not appear in the client image (even if I reboot the client)

It appears only if I install it on the root system of my server witch is not quite "clean" ....

I think that I've missed something ...... Someone can help me please ?

Thx

---

### Post by fnjordy on 2006-11-26
Using chroot install the program on the client, but you must remember the entire point of an LTSP system is that the users session runs on the server, so programs need to be installed on the server sans chroot.

---

