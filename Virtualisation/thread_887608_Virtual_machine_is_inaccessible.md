---
title: "Virtual machine is inaccessible"
date: 2008-08-12
forum: Virtualisation
---

### Post by lmtraub on 2008-08-12
I installed the new version of Vitualbox (1.6) on Ubuntu 8.04. Everything was working until I needed to reboot back to Windoze to backup my hard drive with Mozy as they don't have a Linux version yet. 

Now my virtual machine shows to be Inaccessible with a shared folder host path '/media/New Volume/downloads' to be non-accessible. Is there an easy way to fix this short of deleting and recreating the vm?

Also, what is the easiest way to get USB support in the vm? I've already edited the /etc/init.d/mountdevsubfs.sh and /etc/fstab files. I've added the correct groups and added my user id but the vm still doesn't see my external USB drive or my USB flash drive.

Any help is greatly appreciated.

Thanks.

---

### Post by solitaire on 2008-08-12
you Using VMware?

This might be an issue:
There is a HUGE bug in VMWare associated with Today's date!

[http://it.slashdot.org/article.pl?sid=08/08/12/1120235](http://it.slashdot.org/article.pl?sid=08/08/12/1120235)
[http://www.deploylinux.net/matt/2008/08/all-your-vms-belong-to-us.html](http://www.deploylinux.net/matt/2008/08/all-your-vms-belong-to-us.html)

---

### Post by lmtraub on 2008-08-12
Actually like my post says I'm using Virtualbox 1.6.

Thanks anyway.

---

### Post by solitaire on 2008-08-12
Drat! should read this stuff before i hit "Post Quick Reply" :D:D

---

