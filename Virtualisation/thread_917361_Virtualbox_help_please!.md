---
title: "Virtualbox help please!"
date: 2008-09-11
forum: Virtualisation
---

### Post by Ikith on 2008-09-11
VirtualBox will not start until this problem is fixed. Please consult /var/log/vbox-install.log to find out why the kernel module does not compile. Most probably the kernel sources were not found. Install them and execute

/etc/init.d/vboxdrv setup

as root.

Install.log:
Makefile:127: *** Error: unable to find the sources of your current Linux kernel. Specify KERN_DIR=<directory> and run Make again. Stop.

I have:
linux-headers-2.6.24-19-generic
module-assistant
build-essential

I used this guide to fix my wireless drivers (its probably relevant):
[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)

Please help me out.

EDIT: FIXED THE PROBLEM! I FEEL STUPID! The kernel module installed was proposed therefore having proposed unchecked when requesting the kernel headers lead to me installing earlier headers than the kernel I have. Rechecked proposed did requested the modules and boom it worked.

---

### Post by Thelasko on 2008-09-12
Please go to thread tools and select "mark thread solved."

---

