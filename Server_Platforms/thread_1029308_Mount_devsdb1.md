---
title: "Mount /dev/sdb1"
date: 2009-01-03
forum: Server Platforms
---

### Post by masque7 on 2009-01-03
Hi guys, running a headless server, and using PuTTy on my windows box to SSH into it (like being able to access my files anywhere with WinSCP.)

Just installed a storage drive and used Webmin to format it as NTFS (which seems to have worked). How do I mount the partition and set it up for Samba sharing so I can read/write?

The device shows as /sdb1/

I tried to understand something over [here](http://www3.wiredgorilla.com/content/blogcategory/53/62/), but couldn't take it all in. Any ideas? Just trying to mount a drive here so I can access it on my Windows box. Samba's already set up for the master hdd. If it's easier, I could partition it as FAT32 instead.

---

### Post by masque7 on 2009-01-05
```
sudo fdisk -l

Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x18351834

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4905    39399381   83  Linux
/dev/sda2            4906        4998      747022+   5  Extended
/dev/sda5            4906        4998      746991   82  Linux swap / Solaris

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xaaaaaaaa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2434    19551073+   7  HPFS/NTFS
```
I can get into the drive, just can't write changes to it. How do I give myself access? :/

---

### Post by cariboo on 2009-01-06
Create a mount directory anywhere you want,   I would suggest in /media, then make sure you have ntfs-3g installed, then mount the drive using the following command:

```
sudo mount /dev/sdb1 /media/<directory>
```

Then edit /etc/samba/smb.conf to add the disk as a share. To automount the drive on boot add it to /etc/fstab eg:

```
/dev/sdb1   /media/<directory>    ntfs-3g    defaults    0 0
```

Jim

---

### Post by masque7 on 2009-01-06
update: reformatted the drive as ext3 (was nothing on the drive)

did a 
```
sudo mkdir /media/disk
```then mounted it with ```
sudo mount /dev/sdb1 /media/disk
```did a ```
sudo nano /etc/samba/smb.conf
``````
[disk]
        comment = second hdd
        writeable = yes
        path = /media/disk/
        write list = masque7
```i basically copied that from the shares that were already set up there, just replacing the path to /media/disk/ instead of say /home/masque7/

if i go to \\192.168.1.130\disk on my windows box it takes me into the directory, and shows the "lost+found" folder. I can't write anything onto it at all. ideally i'd like to be able to use sFTP so i can remotely manage my shareslike i do with my /home/* directories 

```
sudo nano /etc/fstab
``````
/dev/sdb1  /media/disk  ext3  suid,dev,exec  0  0
```no idea if that's set up right. guess i've made progress because I can actually see /media/disk/, i just don't seem to have the right permissions to write to it

---

### Post by Iowan on 2009-01-06
Does your Windows box know how to handle an ext3-formatted share?

---

### Post by masque7 on 2009-01-25
> **Iowan said:**
> Does your Windows box know how to handle an ext3-formatted share?
Yeah, since this is a second share I'm adding here. Ideally I would like to be able to use the second hdd as well with torrentflux.

---

