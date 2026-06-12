---
title: "VirtualBox not working properly"
date: 2008-06-11
forum: Virtualisation
---

### Post by Kymus on 2008-06-11
I'll keep this short and to the point. VirtualBox, when I start a virtual machine, says this:

> 
VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {d5a1cbda-f5d7-4824-9afe-d640c94c7dcf}


How do I "*Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root*"

---

### Post by bollix47 on 2008-06-11
Open a terminal. (Applications > Accessories > Terminal)

Type the following:

```
sudo /etc/init.d/vboxdrv setup
```

Enter your user password when asked.

---

### Post by yman on 2008-06-11
> **Kymus said:**
> I'll keep this short and to the point. VirtualBox, when I start a virtual machine, says this:



How do I "*Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root*"

The current version of the Linux kernel in Hardy is 2.6.24-18. The latest version of the VirtualBox kernel module (or whatever it is) is for the 2.6.24-17 kernel. At least, that's how it is if you are using the virtualbox-ose package from the Hardy repositories. To get the latest working version, without waiting for the update, look for the proprietary edition of VirtualBox at sun.com

---

### Post by simonasambler on 2008-06-11
Download the .deb package right from virtualbox.org a than double click on them to install. It contains also kernel so you dont need to install them additionally. /You have to uninstall first virtual box, cause this is install of whole program not only kernel/

Download link:
[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI")

---

