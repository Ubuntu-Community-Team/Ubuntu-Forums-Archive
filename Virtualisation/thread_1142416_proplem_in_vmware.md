---
title: "proplem in vmware"
date: 2009-04-29
forum: Virtualisation
---

### Post by mesh0 on 2009-04-29
hi i have problem in vmware i downloaded it .tar.gz

and when ask me [B]In which directory do you want to keep your virtual machine files?

[/B]i answer of this  /media/disk/h/Programs/Programs 2/hesham2

because i don't have free space in default  


[php]mesho@mint:~/vmware-server-distrib$ sudo ./vmware-install.pl
A previous installation of VMware Server has been detected.

The previous installation was made by the tar installer (version 4).

Keeping the tar4 installer database format.

You have a product that conflicts with VMware Server installed.  Continuing 
this install will first uninstall this product.  Do you wish to continue? 
(yes/no) [yes] y

Error: Unable to execute "/media/disk/h/Programs/Programs 2/Hesham2/vmware-uninstall.pl.

Uninstall failed.  Please correct the failure and re run the install.

Execution aborted.
[/php]

I Have Ubuntu 9.04 Filnal

---

### Post by veloce on 2009-04-29
Try uninstalling the old version that's in the default location first:

/usr/bin/vmware-uninstall.pl

If the uninstallation doesn't correct it, search the forums for uninstalling vmware - it sometimes leaves traces around the system that confuse the installer.  These need to be deleted manually.

---

