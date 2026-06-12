---
title: "Ubuntu 14 LTS via USB Install Issue Mounting"
date: 2016-09-02
forum: Server Platforms
---

### Post by Bashed on 2016-09-02
Always worked before, burned Ubuntu 14 LTS ISO via Rufus to an 8GB USB Key to install on a Dell PE R610 Server. 

It boots into the installation just fine, but for some reason I get this error.

[IMG]http://i.imgur.com/tR9frlU.jpg[/IMG]

---

### Post by cariboo on 2016-09-02
Open System Settings->Software & Updates and make sure the CD-ROM is not enabled, see screenshot:

[[img]https://s12.postimg.org/hlh7llwy1/Screenshot_from_2016_09_02_15_48_15.png[/img]](https://postimg.org/image/hlh7llwy1/)

---

### Post by sudodus on 2016-09-03
Maybe your iso file was not downloaded correctly, or you used a bad version.

- Did you check the iso file and at boot 'check the disk' alias check that all program packages are good?
- Ubuntu Server 14.04.1 LTS works for me, the first point release with the Trusty kernel.

It works for me to install a basic system (I selected no particular server package) like this:

1. Get **ubuntu-14.04.1-server-amd64.iso** via torrent
2. Install it with [mkusb-nox (text interface) or mkusb (GUI)](https://help.ubuntu.com/community/mkusb) into a USB pendrive
3. Boot and run the installer of Ubuntu Server

***Edit:*** If you must install from Windows, please try a *cloning* tool, for example [Win32 Disk Imager](https://wiki.ubuntu.com/Win32DiskImager/iso2usb).

---

