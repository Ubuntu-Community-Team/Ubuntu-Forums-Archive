---
title: "Virtual Box Problem after Updates"
date: 2008-04-13
forum: Virtualisation
---

### Post by hitspace on 2008-04-13
i installed the updates that were needed for ubuntu . halfway through i guess the package manager went and deleted something or changed it. 
what kind of problem am i having i dont understand the output 


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}



i executed  '/etc/init.d/vboxdrv setup' in terminal i got this 


salaam@ubuntu:~$ /etc/init.d/vboxdrv setup
open: Permission denied
 * Stopping VirtualBox kernel module vboxdrv                                    open: Permission denied
                                                                         [ OK ]
open: Permission denied
 * Recompiling VirtualBox kernel module vboxdrv                                 /etc/init.d/vboxdrv: line 155: /var/log/vbox-install.log: Permission denied

open: Permission denied
 * Look at /var/log/vbox-install.log to find out what went wrong
salaam@ubuntu:~$ 

ehh whats wrong here ? 

i really appreciate your help i had some very critical programs in the 
virtual machine

---

