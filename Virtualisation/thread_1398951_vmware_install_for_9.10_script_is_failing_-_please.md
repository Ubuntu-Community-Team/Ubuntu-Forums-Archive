---
title: "vmware install for 9.10 script is failing - please help"
date: 2010-02-05
forum: Virtualisation
---

### Post by phil_elvey on 2010-02-05
Hi,

I am attempting to install vmware server 2.0.2 on ubuntu 9.10 using this simple guide:

[http://radu.cotescu.com/2009/10/30/how-to-install-vmware-server-2-0-x-on-ubuntu-9-10-karmic-koala/](http://radu.cotescu.com/2009/10/30/how-to-install-vmware-server-2-0-x-on-ubuntu-9-10-karmic-koala/)

however the script won't execute and I can't figure out why.  Does anyone figure out why?

Below is a copy of my terminal, showing the the folder the archive is in is just a directory off / and 2 attempts at executing the script, one pointing just at the folder (containing the archive) and one pointing to the archive itself.

```
phil@phil-myth:/$ cd vmware
phil@phil-myth:/vmware$ ls
VMware-server.2.0.2-203138.i386.tar.gz           vmware-server-distrib
vmware-server-2.0.x-kernel-2.6.31-14-install.sh
phil@phil-myth:/vmware$ sudo ./vmware-server-2.0.x-kernel-2.6.31-14-install.sh /vmware
There is no archive containing VMware Server in the path you indicated!

phil@phil-myth:/vmware$ sudo ./vmware-server-2.0.x-kernel-2.6.31-14-install.sh /vmware/VMware-server.2.0.2-203138.i386.tar.gz
There is no archive containing VMware Server in the path you indicated!

phil@phil-myth:/vmware$
```Your help is appreciated

---

### Post by phil_elvey on 2010-02-07
Fixed.

Problem was when moving the VMware archive file from one directory to another with "mv" I accidently replaced a - with a . causing the script not to recognise the file - doh!!!

---

### Post by felixvah on 2010-05-03
> **phil_elvey said:**
> Fixed.

Problem was when moving the VMware archive file from one directory to another with "mv" I accidently replaced a - with a . causing the script not to recognise the file - doh!!!

Can you explain in more detail.  I got the same issue but not able to fix the path.  Please paste in an example here if possible.  thank you

---

