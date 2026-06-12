---
title: "Config samba to a second hard drive?"
date: 2010-04-02
forum: Server Platforms
---

### Post by twin-08 on 2010-04-02
Hey guys, I switch to linux 9.10 and I got webmin installed, I was hoping to set up samba so it would share my second hard drive over the network. Is there anyway I could share the second drive?

Here is my fdisk info.

```
Disk /dev/sda: 40.0 GB, 40037760000 bytes
255 heads, 63 sectors/track, 4867 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d8cfa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4836    38845138+  8e  Linux LVM
/dev/sda2            4837        4867      249007+   5  Extended
/dev/sda5            4837        4867      248976   83  Linux

Disk /dev/sdb: 640.1 GB, 640135028736 bytes
16 heads, 63 sectors/track, 1240341 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x79789ada

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               3     1240339   625129472    7  HPFS/NTFS

```

The 640gb hard drive is on a sata raid card, 40gb is an ide drive.

Thanks guys for the help.

Edit, Can you find out the ip of the server via commands not like this ip 192.168.XXX.X

---

### Post by jfmanamtr on 2010-04-02
I am not sure if you can share a drive like you would in Windows. You can however mount that hard drive to a folder under the root filesystem (sudo mount /dev/sdb1 /pathof/folder). Then using samba share that folder to the rest of your network.
 
~John

---

### Post by twin-08 on 2010-04-02
Ye, I need to share the drive, just hope someone helps me.

As I want to use linux on it rather than windows server 08

---

### Post by jfmanamtr on 2010-04-02
You share the drive by mounting it to a folder on the root file system (sudo mount OPTIONS /dev/sdb1 /path/to/share) & then using samba to share that particular folder. By sharing the folder where you mount a drive you are sharing the drive.
 
~John
 
Edit:
 
This [link]("https://help.ubuntu.com/9.10/serverguide/C/samba-fileserver.html") will show you how to share a specific folder. Then all you need to do mount the hard drive to the folder you are sharing & that will give you access to the files accross the network. when you do the mount, you will need to use "-t ntfs" to specify the filesystem. I think you can also mount the drive under Webmin, but I think that any data on it will be whiped when you do that. Hope that helps!
 
~John

---

### Post by twin-08 on 2010-04-02
Got this working all I did was change the path to /media/harddrive name

It worked, w00t.

Thanks all who tried to help.

---

