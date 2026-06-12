---
title: "VirtualBox"
date: 2008-07-31
forum: Virtualisation
---

### Post by noodle sorcerer on 2008-07-31
I've been trying to get virtualbox to run anything at all for about a week now. Ive looked online and can't find any help. Whenever i try setting up a new OS (from an .iso) and get it all set up etc,etc.. and I always get this same error:
  
```

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}


```

..and I don't know what to do...

---

### Post by jonian_g on 2008-07-31
Open a terminal and type:

```
sudo apt-get install virtualbox-ose-modules-generic
```

---

### Post by overdrank on 2008-07-31
Moved :)
Hi and I believe the the error message explains it. 
```
VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
```

---

### Post by noodle sorcerer on 2008-07-31
> **jonian_g said:**
> Open a terminal and type:

```
sudo apt-get install virtualbox-ose-modules-generic
```

i've done that and they've been installed


so what is that thing theyre talking about wasn't created?

---

### Post by jonian_g on 2008-07-31
Maybe there's been an error. Reinstalling will fix it.

To get a newer version of virtualbox go here:

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

---

### Post by detrate on 2008-07-31
Are you sure you're getting the same Error?  After I installed vbox, I had to add myself to the user group to use it.

---

