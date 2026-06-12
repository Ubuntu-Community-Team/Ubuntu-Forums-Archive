---
title: "Samba Usbdisk Ubuntu Server???"
date: 2008-04-14
forum: Server Platforms
---

### Post by rado3105 on 2008-04-14
HI i am trying to get sharing my usb disk connected to usb port on ubuntu server. The format is vfat. I have problem to see if that usb disk is mounted and i have problem to find out mount point of that disk to set it in smb.conf
Can you help how to find out if that disk is recognised and conected and how to set path to that disk in samba.?

---

### Post by cdenley on 2008-04-14
Is your usb drive always going to be connected at boot? You should create a static mount point in /etc/fstab, or else your usb drive might be mounted somewhere else another time.

To see what drives are connected
```

sudo fdisk -l

```

To see what filesystems are mounted
```

cat /etc/mtab

```

To find the uuid of your usb drive's partition so your system won't mount another drive instead
```

ls -l /dev/disk/by-uuid

```

---

