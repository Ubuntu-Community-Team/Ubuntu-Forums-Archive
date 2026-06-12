---
title: "Ubuntu Server install does not recognise SD card (Desktop install does)"
date: 2014-07-27
forum: Server Platforms
---

### Post by joelittlejohn on 2014-07-27
Hi

I'm trying to install Ubuntu Server 14.04 Server on my Zotac ZBOX. I need to install Ubuntu to the SD card, so I do this by inserting the SD card and using a bootable USB stick as the installation media. When I use the Desktop version of Ubuntu, the installer recognises the 16Gb SD Card as the installation target. When I use the Server version of Ubuntu, the installer doesn't show the SD card as a target, it only shows the USB stick (which obviously, is not where I want to install the OS). I've tried exiting the Server installer and dropping to the root shell but [FONT=courier new]fdisk -l[/FONT] also doesn't show the SD card.

Does anyone know why the Ubuntu Desktop installer would see the SD card but the Ubunter Server installer does not? Could it be something to do with the different kernel modules that are loaded?

My reason for needing the Server install is that I need a very 'barebone' installation on which to run XBMC.

---

### Post by gordintoronto on 2014-07-27
How about: sudo fdisk -l
or: sudo blkid

Is the SD card formatted as ext4? Have you confirmed that the computer will actually boot from an SD card?

Is there some reason you can't devote a couple of GB of the hard drive to the OS?

---

### Post by joelittlejohn on 2014-07-28
Hi

> **gordintoronto said:**
> How about: sudo fdisk -l

No need to sudo, I'm dropped into a root shell by the installer. [FONT=courier new]fdisk -l[/FONT] lists the USB stick but that's the only device.

> **gordintoronto said:**
> Is the SD card formatted as ext4?

Yes. However I don't think the problem is related to mounting (or anything related to the partitions). The device doesn't seem to be present. The only values in [FONT=courier new]/dev[/FONT] are [FONT=courier new]/dev/sda[/FONT] and [FONT=courier new]/dev/sda1[/FONT], and these refer to the USB stick.

> **gordintoronto said:**
> Have you confirmed that the computer will actually boot from an SD card?

Yes, if I use the Desktop installer I can install to the SD card and then boot from it. It all works correctly, it's just the Server installer that doesn't seem to find the SD Card as a target device.

> **gordintoronto said:**
> Is there some reason you can't devote a couple of GB of the hard drive to the OS?

This machine needs to run permanently from an SD card. It won't have an HDD for most of the time, and if it does, it will only be temporary.

Some more info: I've noticed that when I leave the Ubuntu Server installer and enter the root shell, I can run [FONT=courier new]udevadm monitor[/FONT] and watch the SD card reader events. When I remove and reinsert the card I see the 'add' and 'remove' events. So the hardware is obviously recognised and being monitored in some way, it just doesn't seem to be available as a storage device.

---

