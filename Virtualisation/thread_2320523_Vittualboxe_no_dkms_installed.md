---
title: "Vittualboxe no dkms installed"
date: 2016-04-14
forum: Virtualisation
---

### Post by valereguerin on 2016-04-14
Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please install virtualbox-dkms package and load the kernel module by executing

[COLOR=#0000ff]'modprobe vboxdrv'[/COLOR]

as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

where: suplibOsInit what: 3 VERR_VM_DRIVER_NOT_INSTALLED (-1908) - The support driver is not installed. On linux, open returned ENOENT. 

```
freeman@Sniper-one:~$ inxi -b
System:    Host: Sniper-one Kernel: 4.5.0-040500rc7-generic x86_64 (64 bit)
           Desktop: Gnome 3.18.4 Distro: Ubuntu 16.04 xenial
Machine:   Mobo: Gigabyte model: G1.Sniper Bios: Award v: F1 date: 01/17/2011
CPU:       Quad core Intel Core i7 930 (-HT-MCP-) speed: 2794 MHz (max)
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Tahiti PRO [Radeon HD 7950/8950 OEM / R9 280]
           Display Server: X.Org 1.18.3 drivers: ati,vesa (unloaded: fbdev,radeon)
           Resolution: 1920x1080@60.00hz
           GLX Renderer: Gallium 0.4 on AMD TAHITI (DRM 2.43.0, LLVM 3.8.0)
           GLX Version: 3.0 Mesa 11.2.0
Network:   Card: D-Link System DGE-528T Gigabit Ethernet Adapter
           driver: r8169
Drives:    HDD Total Size: 1499.6GB (26.5% used)
Info:      Processes: 365 Uptime: 1 day Memory: 2652.4/7852.8MB
           Client: Shell (bash) inxi: 2.2.35 

```

sudo apt-get install --reinstall dkms

always the same message

sudo modprob vboxprv

the same...  
where: suplibOsInit what: 3 VERR_VM_DRIVER_NOT_INSTALLED (-1908) - The support driver is not installed. On linux, open returned ENOENT.

---

### Post by ajgreeny on 2016-04-15
Although you are using the development version 16.04 this query is more related to virtualisation so I have moved the thread to the Virtualisation forum.

Has there been a recent kernel upgrade for 16.04; I have it as a VBox guest and can not remember when last a kernel appeared in the updates?  That often throws the error you are seeing, though it is usually easily overcome.

What version of VBox are you using, and which version of the guest-additions do you have , if any?

---

### Post by valereguerin on 2016-04-15
5.0.16  guest addition not installed yet because i can't run OS


 Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please install virtualbox-dkms package and load the kernel module by executing

[COLOR=#0000ff]'modprobe vboxdrv'[/COLOR]

as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

where: suplibOsInit what: 3 VERR_VM_DRIVER_NOT_INSTALLED (-1908) - The support driver is not installed. On linux, open returned ENOENT.

---

### Post by MAFoElffen on 2016-04-15
The version of dkms is is asking about, is not the full dmks package, but is rather the package "virtualbox-dkms", which is the Linux kernel module for VirtualBox (I think, off the top of my head, that it is vboxdrv.so). You would reinstall it via:
```

sudo apt-get install --reinstall virtualbox-dkms

```
That would fix that error ... But you getting this error prompts me to ask questions on how you arrived at that error:

Did you have VirtualBox Installed previously (was working) and it arrived at this error after an update or upgrade? Or was this error on a new installation of VirtualBox?

If it was "fresh," and if it was from the beta2 repo, please report that as a bug in Launchpad, so that they can get that corrected in time for the release this month.

---

### Post by valereguerin on 2016-04-16
```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade 
```

today solve the problem ! it's ready now !

---

