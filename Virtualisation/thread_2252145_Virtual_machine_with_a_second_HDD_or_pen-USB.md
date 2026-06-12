---
title: "Virtual machine with a second HDD or pen-USB"
date: 2014-11-09
forum: Virtualisation
---

### Post by markodd on 2014-11-09
Hey there,

I'm running ubuntu 14.04 on an SSD and I've an HDD that currently has windows 7 installed on it.. I was wondering if it's possible to install a VM in the HDD, as to not waste space on the SSD? If this is possible, could it also be done using a Pen-usb instead of the HDD?

How would I go about doing that, using VirtualBox?

---

### Post by sudodus on 2014-11-10
It is possible to install a VM in any drive (read-write mass storage device). Just configure where to store the virtual machine and the virtual drive. But be aware that the USB 2 connection is much slower than that of an internal drive, or USB 3 or eSATA.

See this link and links from it concerning the speed of USB [pen]drives

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

---

### Post by QIII on 2014-11-10
I always put the virtual disk on a different physical drive anyway to avoid read/write conflicts with the host.

---

### Post by markodd on 2014-11-10
Is putthing the virtual disk on a different physical drive easily done using VirtualBox? I was playing with the settings and didn't come across anything that would let me choose a drive..

---

### Post by sudodus on 2014-11-11
1. Either put ***the whole virtualbox directory*** in the external drive:

- move .VirtualBox to the external drive
- create a symbolic link with the same name in the home directory and point to the moved directory


2. or create ***virtual machine files and virtual drive files*** in the external drive:

Example: Select where to create a virtual drive [I][B]for a powered off machine
[/B][/I]
Storage -- SATA controller -- [COLOR=#006400]**+**[/COLOR] add hard disk -- create new disk -- ... -- Location -- click on the folder symbol and select where to create it.

---

