---
title: "Virtualbox Error, i can't run VM"
date: 2017-10-04
forum: Virtualisation
---

### Post by nalazzabi on 2017-10-04
When i Click on Start to run a VM , i get this error:
RTR3InitEx failed with rc=-1912 (rc=-1912)

The VirtualBox kernel modules do not match this version of VirtualBox. The installation of VirtualBox was apparently not successful. Executing

[COLOR=#0000ff]'modprobe vboxdrv'[/COLOR]

may correct this. Make sure that you do not mix the OSE version and the PUEL version of VirtualBox.

where: supR3HardenedMainInitRuntime what: 4 VERR_VM_DRIVER_VERSION_MISMATCH (-1912) - The installed support driver doesn't match the version of the user.
====
i have tried purge and remove everything and reinstall again but it doesn't work.
the result of dpkg -l virtualbox* | grep ^i , is:

ii  virtualbox                     5.1.28-dfsg-1 amd64        x86 virtualization solution - base binaries
ii  virtualbox-dkms                5.1.28-dfsg-1 all          x86 virtualization solution - kernel module sources for dkms
ii  virtualbox-qt                  5.1.28-dfsg-1 amd64        x86 virtualization solution - Qt based user interface
i can't find the issue , it seems like everything is good , by the way am using Linux backbox 4.10.0-35-generic ...

---

### Post by wildmanne39 on 2017-10-04
Did you do:
```
sudo modprobe vboxdrv
```
Moved to virtualisation.

---

### Post by Bucky Ball on 2017-10-05
Did you install Virtualbox directly from the official Ubuntu repositories (using 'Software' or another package manager or a terminal) or manually from a third-party (a website or somewhere else)? Installing Virtualbox from the official repositories is the best way to get the correct Virtualbox for your release/kernel. 

If you have installed manually from a third-party you will run into more problems down the track as you will also want 'Guest Additions' and probably 'Virtualbox extensions', both of which need to match the kernel/Virtualbox version you are using. This might get messy as you need to make sure you are going for the right packages. 

May not be your issue, but just thinking 'out loud' and hope it helps somehow. Good luck.

---

### Post by SeijiSensei on 2017-10-05
Actually if you install [from the Oracle repositories]("https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions"), it uses dkim to compile a module that matches the current kernel whenever it updates.  I've never had a kernel incompatibility using this method.  

After a VB update, you are prompted to download and install the matching extensions.

---

### Post by Bucky Ball on 2017-10-05
> **SeijiSensei said:**
> Actually if you install [from the Oracle repositories]("https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions"), it uses dkim to compile a module that matches the current kernel whenever it updates.  I've never had a kernel incompatibility using this method.  

After a VB update, you are prompted to download and install the matching extensions.

Thanks. Learn something everyday. I'll try this next time. :)

---

