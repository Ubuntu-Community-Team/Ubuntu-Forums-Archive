---
title: "VirtualBox will not run after latest update"
date: 2019-08-14
forum: Virtualisation
---

### Post by cscj01 on 2019-08-14
I am running Ubuntu 18.04.03 x64 Gnome-flashback, kernel 5.0.0-25-generic, and VirtualBox 6.0.10 r132072 (Qt5.9.5).  After the latest software upgrade, I cannot launch any of my VM's.  I get the following messgae:```
RTRinitEX failed with rc=-1912 (rc=-1912)
The VirtualBox kernel modules do not match this version of VirtualBox. The installation of VirtualBox was apparently not successful. Executing

'/sbin/vboxconfig'

may correct this. Make sure that you are not mixing builds of VirtualBox from different sources.

where: supR3HardenedMainInitRuntime what: 4 VERR_VM_DRIVER_VERSION_MISMATCH (-1912) - The installed support driver doesn't match the version of the user. 
```I ran the following with the results shown:```
sudo /sbin/vboxconfig
[sudo] password for butch: 
vboxdrv.sh: Stopping VirtualBox services.
vboxdrv.sh: Starting VirtualBox services.
```What do I need to do to fix this?

---

### Post by lammert-nijhof on 2019-08-18
I'm running the same versions of the kernel and Virtualbox without any problems, but I do run Ubuntu 19.04.. Did you update your Virtualbox extension pack, when you updated to 6.0.10? To be sure re-install it or re-install Virtualbox completely.

---

