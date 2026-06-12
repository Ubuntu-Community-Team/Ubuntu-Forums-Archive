---
title: "Ubuntu Server: Finding USB Hard drive"
date: 2009-02-20
forum: Server Platforms
---

### Post by wstout on 2009-02-20
I am trying to mount a USB hard drive. I am a little green on the server side of things but I have had no luck finding the drive to be able to mount it. It is formatted NTFS, I am wondering if that could be some of my problems. I am running server 8.04.ubun

---

### Post by tubezninja on 2009-02-22
The server edtion of ubuntu doesn't have an auto mount feature, so you'll have to tell it to mount the drive from the command line.

First, you'll need to find out what device assignment it was given:

```
sudo fdisk -lu
```

This will list all of the drives attached to the server. Output should be something like:

```
Disk /dev/sda: 73.4 GB, 73406611456 bytes
254 heads, 63 sectors/track, 8959 cylinders, total 143372288 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000c39a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   137441177    68720557+  83  Linux
/dev/sda2       137441178   143361917     2960370    5  Extended
/dev/sda5       137441241   143361917     2960338+  82  Linux swap / Solaris

Disk /dev/sdb: 73.4 GB, 73406611456 bytes
255 heads, 63 sectors/track, 8924 cylinders, total 143372288 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000c7721

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   143364059    71681998+  83  Linux

Disk /dev/sdc: 73.4 GB, 73406611456 bytes
255 heads, 63 sectors/track, 8924 cylinders, total 143372288 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000c98d1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   143364059    71681998+  83  Linux

```

Your output will of course be different, showing drive sizes according to whatever you have installed.  If the USB drive was the last device hooked up, then it will probably be the last one on the list (in my case, the last one is /dev/sdc1).

Once you know the device name, you're going to need to make an empty directory somewhere that will be the mount point for this drive. Once you've done that, you can mount the drive:

```
sudo mount -t ntfs-3g /dev/sdc1 /your/mountpoint
```

Of course, replace "/dev/sdc1" with the appropriate device name and "/your/mountpoint" with the path to the empty directory you created.

If at any point you need to disconnect the drive, you should unmount it first:

```
sudo umount /your/mountpoint
```

Make sure no users are accessing or writing to the drive, or even sitting with an idle shell prompt on a directory in that drive, or the drive will not unmount.

---

### Post by wstout on 2009-02-22
scaredpoet: thanks for all the info. I have dug a little deeper and I believe I have problems with my actual USB card. This is on an old Compaq Proliant 1600 server. It doesn't have normal bios, or at least normal by today's standards. It has some stuff that has to be written to the hard drive, but make long story short it wasn't letting the PCI USB card be detected.... I think

---

### Post by wstout on 2009-02-22
I got this to running. My first problem was the PCI card and my server weren't getting along, that's not an Ubuntu problem at all. Second thing was that NTFS was being a pain so I backed up and formatted to ext3 and it was plug 'n play. Since the whole point was to be extra storage ext3 made the most sense by a long shot anyway.

---

### Post by tubezninja on 2009-02-22
Glad to hear you got it sorted out!

---

### Post by wstout on 2009-02-22
Sacredpoet, thanks for the help!

---

