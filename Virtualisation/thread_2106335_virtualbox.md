---
title: "virtualbox"
date: 2013-01-18
forum: Virtualisation
---

### Post by MrRandyMarsh on 2013-01-18
hi!
im looking for solution for this:
 
Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

problem, like 5 hours already and cant find any. 

i know this question was ask many times but i realy could not find  solution for me.

---

### Post by MrRandyMarsh on 2013-01-18
realy need help with virtualbox problem
hi!
im looking for solution for this:

"Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary."

problem on my fresh installed ubuntu, like 5 hours already and cant find any. 
p.s
i know this question was ask many times but i realy could not find solution for me.

---

### Post by sdpagent on 2013-01-18
I had the same issue today after updating my ubuntu. What I did to fix it was read the error and do what it said:

execute '/etc/init.d/vboxdrv setup'

[IMG]http://img1.uploadscreenshot.com/images/orig/1/1718384156-orig.png[/IMG]

---

### Post by MrRandyMarsh on 2013-01-18
im getting bash: /etc/init.d/vboxdrv: No such file or directory

, tried to install dkms but it didnt help

---

### Post by lisanels47 on 2013-01-18
Have you done this:

**sudo** /etc/init.d/vboxdrv setup

That fixed the error when we see that.

---

### Post by lisanels47 on 2013-01-18
lisa@lisa-Inspiron-1545:~$ **sudo** /etc/init.d/vboxdrv setup
[sudo] password for lisa: 
 * Stopping VirtualBox kernel modules                                                                                                  [ OK ] 
 * Uninstalling old VirtualBox DKMS kernel modules                                                                                     [ OK ] 
 * Trying to register the VirtualBox kernel modules using DKMS                                                                         [ OK ] 
 * Starting VirtualBox kernel modules                                                                                                  [ OK ] 
lisa@lisa-Inspiron-1545:~$ 


That should fix the issue, if not, re-install virtualbox.

---

### Post by MrRandyMarsh on 2013-01-18
still got same

otto@T100:~$ sudo /etc/init.d/vboxdrv setup
[sudo] password for otto: 
sudo: /etc/init.d/vboxdrv: command not found

---

### Post by CharlesA on 2013-01-18
Threads merged.

How did you install virtualbox?

---

### Post by MrRandyMarsh on 2013-01-19
software center did.

p.s thnx for merging threads

---

### Post by CharlesA on 2013-01-19
OK, so you installed the version from the Ubuntu repos.

Uninstall it and try installing the version found here:
[https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads)

---

