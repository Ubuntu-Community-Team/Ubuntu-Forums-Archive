---
title: "usb virtualbox"
date: 2009-03-29
forum: Virtualisation
---

### Post by emtjr928 on 2009-03-29
I am using virtualbox from sun latest version not ose. My usb mouse and keyboard work fine but can't get win 2000 in vb to let me connect to my harmony remote. I have myself set up as user of vbox. Usb controller etc are enabled in setup of vb.I am attaching the following fyi. What am I missing?

```
emtjr928@emtjr928-desktop:~$ mount | grep usb
procbususb on /proc/bus/usb type usbfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
emtjr928@emtjr928-desktop:~$ cat /etc/group | grep vboxusers
vboxusers:x:125:emtjr928
emtjr928@emtjr928-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=72d940d7-4904-45c3-a9d1-e3d722d3181d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=e6240924-5c2b-4f3d-acda-13e53451f085 /home           ext3    relatime        0       2
# /dev/sda1
UUID=1e624d5a-4e3b-48b1-af28-3a5f154550aa /media/storage  ext3    relatime        0       2
# /dev/sda6
UUID=adee6531-7a89-48b2-bb45-484c73827704 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
#/dev/sdb1        
UUID=6e3c7645-56b5-45be-96f4-27d5560f836e /media/backup   ext3
defaults     0        2
usbfs /proc/bus/usb usbfs auto 0 0
# For USB access with Virtualbox
none	/proc/bus/usb	usbfs	devgid=125,devmode=664	0	0
emtjr928@emtjr928-desktop:~$ 


```

---

### Post by emtjr928 on 2009-03-30
Solved _reinstalled_ guest additions and everything is fine.

---

