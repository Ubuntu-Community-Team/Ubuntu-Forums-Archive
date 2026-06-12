---
title: "unable to use virtualbox"
date: 2016-03-27
forum: Virtualisation
---

### Post by night116 on 2016-03-27
I have been trying to get any virtualbox to work since upgrading to ubuntu 15.10, I have downloaded the latest from from oracle, plus the oneon ubuntu 15.10 software centre, but keep geting the following errors no matter what tip from this forum I use.
Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please install virtualbox-dkms package and load the kernel module by executing

'modprobe vboxdrv'

as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

where: suplibOsInit what: 3 VERR_VM_DRIVER_NOT_INSTALLED (-1908) - The support driver is not installed. On linux, open returned ENOENT. 


failed to open a session for the virtual machine windows7.

---

### Post by night116 on 2016-03-27
I even went back to an older version before v5, but it does the same thing for many many months now.

---

### Post by SeijiSensei on 2016-03-27
If you install from the Oracle repository (see "Debian-based Linux systems" on the Linux download page) it should bring in the required dependencies.  However you can try 
```
sudo apt-get install build-essential dkms
```
and see if that is enough to fix the problem.  It's likely you've never installed the gcc compiler or dkms which manages kernel modules.

---

### Post by MAFoElffen on 2016-03-27
The package to install the vboxdrv dkms kernel module is:
```

sudo apt-get install virtualbox-dkms

```

---

### Post by SeijiSensei on 2016-03-28
> **MAFoElffen said:**
> The package to install the vboxdrv dkms kernel module is:
```

sudo apt-get virtualbox-dkms

```
That's the package from Ubuntu.  Is that true for the version in the Oracle repository as well?  The page on their site only references dkms.  On my system with the [Oracle repositories installed]("https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions") to /etc/apt/sources.list.d/, the main package is called virtualbox-5.0 to distinguish it from the "virtualbox" package from Ubuntu, and I have no virtualbox-dkms.

---

### Post by night116 on 2016-03-29
sudo apt-get install build-essential dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
dkms is already the newest version.
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.

---

### Post by night116 on 2016-03-29
sudo apt-get virtualbox-dkms
E: Invalid operation virtualbox-dkms

---

### Post by night116 on 2016-03-29
nope nothing still works

---

### Post by night116 on 2016-03-29
reinstalled virtualbox 5 form oracle site again installed it as their instructions per page, and still the exact same thing happens.

---

