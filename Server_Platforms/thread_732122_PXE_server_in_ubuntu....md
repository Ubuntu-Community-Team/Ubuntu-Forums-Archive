---
title: "PXE server in ubuntu..."
date: 2008-03-22
forum: Server Platforms
---

### Post by Mia_tech on 2008-03-22
is it possible to install a PXE server in ubuntu where I can push an computer image to several pc?

thanks

---

### Post by ubernoob on 2008-03-22
yes. Try to google it. There are several good howto's, so i can't bother to write another one here.

---

### Post by faulkes on 2008-03-22
> **Mia_tech said:**
> is it possible to install a PXE server in ubuntu where I can push an computer image to several pc?

thanks

[https://help.ubuntu.com/community/PXEInstallServer](https://help.ubuntu.com/community/PXEInstallServer)

Thanks,

Faulkes

---

### Post by Mia_tech on 2008-03-23
> **faulkes said:**
> [https://help.ubuntu.com/community/PXEInstallServer](https://help.ubuntu.com/community/PXEInstallServer)

Thanks,

Faulkes

thanks for the link, very helpful, but I have a few questions, would this be an automated install, or would it need user interaction?.. also what is netkit-inetd? and what the pxelinux.0 entry in the dhcp server file means?

thanks

---

### Post by faulkes on 2008-03-23
> **Mia_tech said:**
> thanks for the link, very helpful, but I have a few questions, would this be an automated install, or would it need user interaction?.. also what is netkit-inetd? and what the pxelinux.0 entry in the dhcp server file means?

thanks

netkit-inetd is a virtual package for inetutils-inetd:

```

aptitude show inetutils-inetd

Description: Internet super server
Inetd is the daemon that listens on various TCP and UDP ports and 
spawns programs that can't or won't do it for themselves.

```

pxelinux.0 file is generally a text file containing information which
tells the booting host what it needs to do.  Typically this file is
created from the syslinux package (although it can be hand
crafted as well.)

```

aptitude show syslinux

Description: Bootloader for Linux/i386 using MS-DOS floppies
SYSLINUX is a boot loader for the Linux/i386 operating system 
which operates off an MS-DOS/Windows FAT filesystem. It is 
intended to simplify first-time installation of Linux, and for 
creation of rescue and other special-purpose boot disks. 
 
It can also be used as a PXE bootloader during network boots. 

```

A good walk-through is available at both the syslinux mainpage:

[http://syslinux.zytor.com/pxe.php](http://syslinux.zytor.com/pxe.php)

and 

[http://wiki.antlinux.com/pmwiki.php?n=HowTos.SetupPxeBoot](http://wiki.antlinux.com/pmwiki.php?n=HowTos.SetupPxeBoot)

Thanks,

Faulkes

---

### Post by Mia_tech on 2008-03-23
is it possible to use the same method to multicast a windows image to several machines using ubuntu as the multicast server?

thanks

---

