---
title: "Make bootable windows usb"
date: 2016-10-26
forum: Windows
---

### Post by freeworld4 on 2016-10-26
How do I do this? I tried various guides online and none worked so far. Tried unetbootin and dd. No luck thus far.

---

### Post by sudodus on 2016-10-27
You can try ***mkusb-nox*** from the unstable PPA (it is a new feature, so it is not tested enough to go into the stable PPA).

I assume that you run standard Ubuntu or a flavour of Ubuntu: Kubuntu, Lubuntu ... Xubuntu). ***mkusb-nox*** works in some (but not all) other linux distros.

See these links,

[How to install mkusb-nox from the unstable PPA](https://help.ubuntu.com/community/mkusb/gui#from_the_unstable_PPA)

```
sudo add-apt-repository universe  # this line only for standard Ubuntu

sudo add-apt-repository ppa:mkusb/unstable
sudo apt-get update

sudo apt-get install mkusb-nox

# or if you want all three packages
sudo apt-get install mkusb mkusb-nox usb-pack-efi
```

[Making a USB drive to install Windows](https://help.ubuntu.com/community/mkusb/v7#Making_a_USB_drive_to_install_Windows)

[mkUSB-quick-start-manual-nox.pdf](http://phillw.net/isos/linux-tools/mkusb/mkUSB-quick-start-manual-nox.pdf)

-o-

*Edit:* Notice that you can only boot the Windows ***installer*** from USB, not an installed Windows system. Windows must be installed into an internal drive.

---

### Post by yancek on 2016-10-27
I've never used dd myself but from what I have read, it should work.  If you read the unetbootin home page, it states specifically that it is designed for Linux and will not work with windows so give that up. 

Here's another option at the link below.

[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html)

---

### Post by C.S.Cameron on 2016-10-27
[ATTACH=CONFIG]271809[/ATTACH]> **sudodus said:**
> 

*Edit:* Notice that you can only boot the Windows ***installer*** from USB, not an installed Windows system. Windows must be installed into an internal drive.

We have had good luck booting Windows from VBox installed in Ubuntu on a USB3 flash drive.

Mkusb is the best tool for making such a flash drive.

Screen shot attached

---

### Post by sudodus on 2016-10-27
*@freeworld4*

What do you want, a USB drive to install Windows or an installed Windows system in a USB drive?

---

### Post by freeworld4 on 2016-10-28
I want to use hiren's boot cd burned to usb. I need it to fix my drive all software tools I used in ubuntu to fix the ntfs recommends using chkdsk instead when they fail. I would also like to eventually install windows and also mac os x to usb maybe. I'll try mkusb thanks.

---

### Post by freeworld4 on 2016-10-28
[COLOR=#000000]I want to use hiren's boot cd burned to usb. I need it to fix my drive all software tools I used in ubuntu to fix the ntfs recommends using chkdsk instead when they fail. I would also like to eventually install windows and also mac os x to usb maybe. I'll try mkusb thanks.[/COLOR]

---

### Post by sudodus on 2016-10-29
I used Hiren's boot CD long ago, before I learned how to boot from USB. I don't know if the iso file of "Hiren's boot CD" can be used to create a working boot USB drive. If it is a 'linux hybrid iso file' (for example booting with grub or syslinux/isolinux), mkusb can do it. Otherwise you must search for instructions via the internet.

The Windows ***installer*** can be installed to a USB boot drive, but not Windows itself, but there is a work-around: put a virtual machine into a linux system in a USB drive and install Windows into the virtual machine. This is legal, if you have a valid license for Windows. I have no experience of MacOS, but I think it is illegal to install it into anything but Mac computers.

Let us know how it works, and ask if you need help with some details. Good luck :-)

---

### Post by C.S.Cameron on 2016-10-29
Info on running HBCD from USB:
[http://www.hiren.info/pages/bootcd-on-usb-disk](http://www.hiren.info/pages/bootcd-on-usb-disk)
In the past Ubuntu Forums has banned any discussion of the methods that allow installation of MacOS in VBox or USB drive, although there is lots of info elsewhere.
Windows XP can be run directly from flash drive using the Ngine method, very slowly on USB2, have not tried USB3.
Windows 10 on VBox on Ubuntu on USB3 is usable if you have over 4GB RAM on Host, 32GB is better.

---

