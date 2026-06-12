---
title: "How to mount USB devices on Ubuntu Servers?"
date: 2005-11-17
forum: Server Platforms
---

### Post by ff2k on 2005-11-17
Hello,

I'm trying to mount a USB HDD Enclosure. I'm checked the /var/log/messages and it seems USB devices aren't automatically recognized. Maybe because hotplug isn't installed by default? The script, /etc/init.d/hotplug isn't there. :confused: 

My setup:

Ubuntu 5.10 Server
Matrix USB HDD Enclosure USB2.0
  w/ Maxtor 80GB inside

---

### Post by petterah on 2005-11-20
Hi, i guess there are no hotplug, hal or anything on the ubuntu server profile... you could mount the usb disk manually, by checking the dmesg og /var/log/messages for device, like sda1 or something, if you don't get anything, try loading the usb-storage driver or scsi system, i don't remember these module names, but google will hjelp you. modprobe takes care of the module loading for each module. When these modules are loaded, the device will show up in /var/log/messages, and then the mount is simple:

mount -t vfat /dev/sda1 /mnt/usbdisk

Make sure the filesystem is fat32, or replace with correct filesystem, and make sure the disk is recognized as sda1 and the directory /mnt/usbdisk exists. :)

---

### Post by darkfame on 2005-11-20
The module needed to mount usb drives is usb-storage.
Type sudo modprobe usb-storage to load it.

---

### Post by ff2k on 2005-11-21
Hi guys,

Thanks for your help. None work though. I tried installing hal, autofs & pmount but whenever I plug in a usb device, it doesn't show in the logs so doing an fdisk -l /dev/scsidevice doesn't work.

:confused:

---

