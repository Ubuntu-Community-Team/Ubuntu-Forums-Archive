---
title: "Problem with DKMS in Ubuntu 11.04"
date: 2011-08-18
forum: Virtualisation
---

### Post by SLA_leandrin on 2011-08-18
Hi all,

I am having a serious issue with my VirtualBox system since the last kernel upgrade in Ubuntu 11.04
The problem is that dkms cannot start the vboxdrv. Apparently installation have gone well but modprobe vboxdrv just doesn't works and I cannot run any of my images. I have tried downgrading VirtualBox to 3.x versions and 4.x versions but it did not work.

My system specifications are:

- Ubuntu 11.04 
- Kernel 2.6.38-10-generic
- VirtualBox 4.2.1

Everytime I try to run vbox I get this message:

```
sudo /etc/init.d/vboxdrv setup
```

And when I run that command:

```
* Stopping VirtualBox kernel modules                                    [ OK ] 
* Uninstalling old VirtualBox DKMS kernel modules                       [ OK ] 
* Trying to register the VirtualBox kernel modules using DKMS           [ OK ] 
* Starting VirtualBox kernel modules                                           
* modprobe vboxdrv failed. Please use 'dmesg' to find out why
```


Nothing to see in dmesg command relative to vboxdrv.
The file /var/log/vbox-install.log says:

```
Uninstalling modules from DKMS
  removing old DKMS module vboxhost version  4.1.2

-------- Uninstall Beginning --------
Module:  vboxhost
Version: 4.1.2
Kernel:  2.6.38-10-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
- Uninstallation
   - Deleting from: /lib/modules/2.6.38-10-generic/updates/dkms/
- Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetflt.ko:
- Uninstallation
   - Deleting from: /lib/modules/2.6.38-10-generic/updates/dkms/
- Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetadp.ko:
- Uninstallation
   - Deleting from: /lib/modules/2.6.38-10-generic/updates/dkms/
- Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxpci.ko:
- Uninstallation
   - Deleting from: /lib/modules/2.6.38-10-generic/updates/dkms/
- Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....(bad exit status: 139)

DKMS: uninstall Completed.

------------------------------
Deleting module version: 4.1.2
completely from the DKMS tree.
------------------------------
Done.
Attempting to install using DKMS

Creating symlink /var/lib/dkms/vboxhost/4.1.2/source ->
                 /usr/src/vboxhost-4.1.2

DKMS: add Completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=2.6.38-10-generic -C /lib/modules/2.6.38-10-generic/build M=/var/lib/dkms/vboxhost/4.1.2/build.................
cleaning build area....

DKMS: build Completed.

vboxdrv.ko:
Running module version sanity check.
- Original module
   - No original module exists within this kernel
- Installation
   - Installing to /lib/modules/2.6.38-10-generic/updates/dkms/

vboxnetflt.ko:
Running module version sanity check.
- Original module
   - No original module exists within this kernel
- Installation
   - Installing to /lib/modules/2.6.38-10-generic/updates/dkms/

vboxnetadp.ko:
Running module version sanity check.
- Original module
   - No original module exists within this kernel
- Installation
   - Installing to /lib/modules/2.6.38-10-generic/updates/dkms/

vboxpci.ko:
Running module version sanity check.
- Original module
   - No original module exists within this kernel
- Installation
   - Installing to /lib/modules/2.6.38-10-generic/updates/dkms/

depmod....(bad exit status: 139)
```

DKMS: install Completed.


I really don't know what to do, any help will be appreciated.

Regards.
LS

---

### Post by dino99 on 2011-08-21
from synaptic:

remove/purge dkms & virtualbox then reinstall them
(nothing destroyed ;))

---

### Post by SLA_leandrin on 2011-08-21
Did that already!!
Didn't worked...

So far the only "solution" - more like a walkaround was starting with the previous kernel installed, 2.6.38-8-generic

---

### Post by '76 on 2011-08-21
maybe try build-dep?

---

