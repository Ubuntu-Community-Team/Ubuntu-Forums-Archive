---
title: "Run Virtual Box In Ubuntu 18.04 LTS"
date: 2018-05-04
forum: Virtualisation
---

### Post by nandarusfikri on 2018-05-04
hello guys .. im want to install Virtual box to 

when you want to insta

Hello guys .. i want install virtual box in Ubuntu 18.04... but the moment running vbox ... I have one Problem ...
you can see below this message 

Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

[COLOR=#0000ff]'/sbin/vboxconfig'[/COLOR]

as root.

where: suplibOsInit what: 3 VERR_VM_DRIVER_NOT_INSTALLED (-1908) - The support driver is not installed. On linux, open returned ENOENT.

---

### Post by kerry_s on 2018-05-04
how did you install?

---

### Post by SeijiSensei on 2018-05-04
Use the method described at the VirtualBox site: [https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLlinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLlinuxdistributions)

You'll never have problems with compiling kernel drivers or using the Extension Pack if you take this approach.

---

