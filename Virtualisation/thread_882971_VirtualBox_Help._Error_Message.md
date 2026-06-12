---
title: "VirtualBox Help. Error Message?"
date: 2008-08-07
forum: Virtualisation
---

### Post by Landscapeman on 2008-08-07
I keep getting this message any ideas?

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {d5a1cbda-f5d7-4824-9afe-d640c94c7dcf}

Along with that I have received this message in terminal:
No suitable module for running kernel found

---

### Post by Perpetual on 2008-08-07
> **Landscapeman said:**
> I keep getting this message any ideas?

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {d5a1cbda-f5d7-4824-9afe-d640c94c7dcf}

Along with that I have received this message in terminal:
No suitable module for running kernel found

[Ubuntugeek]("http://www.ubuntugeek.com/howto-install-virtualbox-16-in-ubuntu-804hardy-heron-including-usb-support.html") has a good How To.  Also, I have had problems with the VBox in the Ubuntu repositories and better luck when downloading it from the VBox [site]("http://www.virtualbox.org/wiki/Downloads").

---

### Post by .nedberg on 2008-08-07
The error message tells you what to do. In a terminal type:
```
sudo /etc/init.d/vboxdrv setup
```

You probably updated your kernel

---

### Post by Perpetual on 2008-08-07
> **.nedberg said:**
> The error message tells you what to do. In a terminal type:
```
sudo /etc/init.d/vboxdrv setup
```

You probably updated your kernel

Whoops, I thought it was a new install of VBox.

---

