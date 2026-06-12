---
title: "[SOLVED] Virtual Box - wont run?"
date: 2008-07-13
forum: Virtualisation
---

### Post by stevebakerj on 2008-07-13
Installed VirtualBox 1.6.2 on 8.04.1 KDE4.1 Beta box, all went well

```
xxxxxxx@kde4-desktop:~$ sudo sh /home/xxxxxx/downloads/VirtualBox-1.6.2-Linux_x86.run
[sudo] password for xxxxxxx:
Verifying archive integrity... All good.
Uncompressing VirtualBox for Linux installation........
VirtualBox Version 1.6.2 (Sat May 31 04:03:49 CEST 2008) installation
Removing previous installation of VirtualBox 1.6.2 from /opt/VirtualBox-1.6.2
Installing VirtualBox to /opt/VirtualBox-1.6.2
Building the VirtualBox kernel module

VirtualBox has been installed successfully.

You will find useful information about using VirtualBox in the user manual
  /opt/VirtualBox-1.6.2/UserManual.pdf
and in the user FAQ
  http://www.virtualbox.org/wiki/User_FAQ

We hope that you enjoy using VirtualBox.
```

but when I try to run VirtualBox I get this

```
xxxxxxx@kde4-desktop:/opt/VirtualBox-1.6.2$ virtualbox
The program 'virtualbox' is currently not installed.  You can install it by typing:
sudo apt-get install virtualbox-ose
bash: virtualbox: command not found
xxxxxxx@kde4-desktop:/opt/VirtualBox-1.6.2$
```

What am I missing?

---

### Post by cherva on 2008-07-13
The command is ```
VirtualBox
``` (capital V and B). Don't you have it somewhere in the menus ? In GNOME VirutalBox is under System tools...

---

### Post by stevebakerj on 2008-07-13
> **cherva said:**
> The command is ```
VirtualBox
``` (capital V and B). Don't you have it somewhere in the menus ? In GNOME VirutalBox is under System tools...

Thanks, but with capitals I get the following error:

```
xxxxxxx@kde4-desktop:~$ VirtualBox
/opt/VirtualBox-1.6.2/VirtualBox: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
```

and I cannot find libstdc++.so.5 in the repos

Yes I have the shortcut in my menus but all I get if I click is a bouncing VB icon then nothing...

---

### Post by tuxneo on 2008-07-13
I think you can try to install virtual box with the ubuntu package ([http://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/VerifyItem-Start/virtualbox_1.6.2-31466_Ubuntu_hardy_i386.deb?BundledLineItemUUID=RYtIBe.m70IAAAEbrWVJihwj&OrderID=.GZIBe.mvMEAAAEboWVJihwj&ProductID=lo5IBe.oSVAAAAEZ7akZKqcY&FileName=/virtualbox_1.6.2-31466_Ubuntu_hardy_i386.deb]("http://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/VerifyItem-Start/virtualbox_1.6.2-31466_Ubuntu_hardy_i386.deb?BundledLineItemUUID=RYtIBe.m70IAAAEbrWVJihwj&OrderID=.GZIBe.mvMEAAAEboWVJihwj&ProductID=lo5IBe.oSVAAAAEZ7akZKqcY&FileName=/virtualbox_1.6.2-31466_Ubuntu_hardy_i386.deb"))
It's the best and simplest way ;)

---

### Post by stevebakerj on 2008-07-13
> **tuxneo said:**
> I think you can try to install virtual box with the ubuntu package ([http://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/VerifyItem-Start/virtualbox_1.6.2-31466_Ubuntu_hardy_i386.deb?BundledLineItemUUID=RYtIBe.m70IAAAEbrWVJihwj&OrderID=.GZIBe.mvMEAAAEboWVJihwj&ProductID=lo5IBe.oSVAAAAEZ7akZKqcY&FileName=/virtualbox_1.6.2-31466_Ubuntu_hardy_i386.deb]("http://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/VerifyItem-Start/virtualbox_1.6.2-31466_Ubuntu_hardy_i386.deb?BundledLineItemUUID=RYtIBe.m70IAAAEbrWVJihwj&OrderID=.GZIBe.mvMEAAAEboWVJihwj&ProductID=lo5IBe.oSVAAAAEZ7akZKqcY&FileName=/virtualbox_1.6.2-31466_Ubuntu_hardy_i386.deb"))
It's the best and simplest way ;)

Thanks now sorted :)

---

### Post by tuxneo on 2008-07-13
Perfect ;)

---

