---
title: "Automount /dev/sda1 ext3 at boot"
date: 2008-04-14
forum: Server Platforms
---

### Post by phillips321 on 2008-04-14
Hi guys,

Plenty of threads on automounting ntfs and fat32 etc.. but how do i automount my usb ext3 hard drive at boot?

I would like it to be mounted to /media/data with rw access for all users

fstab currently looks like this

```
phillips321@LinuxHTTP:~$ cat /etc/fstab 
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1     /media/data      ext3     defaults,errors=remount-ro 0     0
phillips321@LinuxHTTP:~$ 
```

Any ideas on how to do this?

Cheers

---

### Post by sisco311 on 2008-04-14
[FONT=monospace][about file permissions, owners and groups]("https://help.ubuntu.com/community/FilePermissions")

create a new group:
```
sudo addgroup my_goup
```change the owner of the partition to root:my_group,set the permissions and add the users to the group my_grop
```
sudo chown -R root:my_group /media/data
``````
sudo chmod -R 775 /media/data
``````
sudo usermod -a -G my_group **username**
```[/FONT]

---

### Post by phillips321 on 2008-04-14
umm that doesn't help :(, i need to actually be able to mount the disk before i can edit the permission.

/dev/sda1 is not mounted correctly,

mount command doesn't show it mounted

i can manually mount it and everything is fine i just need it mounted after boot automatically

any thing i can post the output of to help you guys help me?

Cheers again :)

---

### Post by sisco311 on 2008-04-14
pleas post the output of:
```
sudo fdisk -l
```

---

### Post by phillips321 on 2008-04-14
this is the output (via ssh) after manually mounting the disk.

```
phillips321@LinuxHTTP:~$ sudo fdisk -l

Disk /dev/hda: 20.0 GB, 20000268288 bytes
255 heads, 63 sectors/track, 2431 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         122      979933+  82  Linux swap / Solaris
/dev/hda2   *         123        2431    18547042+  83  Linux

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   83  Linux
phillips321@LinuxHTTP:~$ 

```

i've noticed that for some reason if i boot with the disk plugged in i cant manually mount it, i have to unplug/replug it and then mount it from /dev/sdb1

---

