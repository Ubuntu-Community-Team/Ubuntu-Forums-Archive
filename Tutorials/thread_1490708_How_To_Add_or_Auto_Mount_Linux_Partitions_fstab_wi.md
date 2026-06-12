---
title: "How To Add or Auto Mount Linux Partitions fstab with ownership change"
date: 2010-05-22
forum: Tutorials
---

### Post by meka4996 on 2010-05-22
How To Add/Auto Mount Linux Partitions fstab with ownership change

Basic How To Add or Automatically Mount Linux Partitions fstab ext3 ext4 ntfs fat32 with ownership & permission change

Check what partitions are in the computer:
```
$ sudo fdisk -l
```
showing sizes/blocks in Bytes, format id 7= NTFS, b= FAT32, 83= ext3 or ext4 [see $ blkid]

Check all partition uuids and formats by...
```
$ blkid
``` 

Mount partitions temporarily to see if it works...
Make a new directory for the mount point of the partition XYZ or sda1 or hdb1... "dataXYZ" means it's a data partition of /dev/XYZ or /dev/sda1 or /dev/hdb1
```
$ sudo mkdir /mnt/temp
```

```
$ sudo mount /dev/XYZ /mnt/temp
```
If you have an old distro, then add "-t ext4","-t ext3", or "-t ntfs":
```
$ sudo mount -t ext4 /dev/XYZ /mnt/temp
```
```
$ sudo mount -t ext3 /dev/XYZ /mnt/temp
```
```
$ sudo mount -t ntfs /dev/XYZ /mnt/temp
```


To check if it's mounted, $ df -hT for sizes and format:
```
$ df -hT
```

Then check what is inside it, and make sure this is the partition you want:
```
$ ls /mnt/temp
``` 

Now let's un-mount all partitions except the root partition of this running linux distro by ...
```
$ sudo umount -a
``` 

Then check if it is indeed not mounted
```
$ df -hT
```  

If you want to wipe it clean, backup your data and format the partitions.
```
$ sudo mkfs.ext3 /dev/dataXYZ
```  
```
$ sudo mkfs.ext4 /dev/dataXYZ
```  

Check if you can mount it...
```
$ sudo mount /dev/XYZ /mnt/temp
```
```
$ sudo mount /dev/XYZ /mnt/temp
```

Check if it's mounted
```
$ df -hT
```

Then check what is inside it, and make sure this is the partition you want:
```
$ ls /mnt/temp
``` 

If all is well and you decide to make it automatically mounted at booting up, then continue on the following...

1) Un-mount all devices
```
$ sudo umount -a  
```
... check it by "df -hT", seeing it is indeed un-mounted

2) Make a folder in /media or /mnt, NOT under /home!!
under /mnt (no icon on your desktop, hiding partitions for guest users) or under /media (showing icon on your desktop). 
```
$ sudo mkdir /mnt/datasdb7 
```

3) Get the partition uuid. It is better to use uuid to specify the partitions you want. Otherwise if you change the partition table later on like moving partitions, merging partitions, resizing partitions, the uuid will change then you need to update your fstab with the new uuid.
```
$ sudo blkid  
```

4) Back up the fstab file.
```
$ sudo cp /etc/fstab /etc/fstab.ubuntu904_may2010 
```

Check if the new file fstab.ubuntu904_may2010 is actually there
```
$ ls 
```

5) Open the fstab file 
```
$ sudo gedit /etc/fstab 
```

and edit it according to following examples..
see reference [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

# For ext3 and ext4 partitions
# /dev/sdb7, data partition sdb7
UUID=5da3c09a-8984-4d27-88b6-55d322203e08 /mnt/datasdb7         ext3    relatime,errors=remount-ro  0   2

The "0" after "ro" is <dump>, which enables or disables backing up of the device/partition (the command dump). This field is usually set to 0, which disables it.

The "2" at the end is <pass num>, which controls the order in which fsck checks the device/partition for errors at boot time. The root device should be 1. Other partitions should be 2, or 0 to disable checking. 

[http://blogs.koolwal.net/2009/01/30/installing-linux-on-usb-part-4-noatime-and-relatime-mount-options/](http://blogs.koolwal.net/2009/01/30/installing-linux-on-usb-part-4-noatime-and-relatime-mount-options/)
3. relatime – A filesystem mount with this option causes the access time to be updated if they are (before the update has occurred) earlier than the modification time. This significantly cuts down the writes caused by atime updates. However not many people use this option because they are simply not aware of it.

To summarize, relatime is a good compromise between  atime (most expensive) and noatime (least expensive).

[http://ubuntuforums.org/showthread.php?t=199587](http://ubuntuforums.org/showthread.php?t=199587)
errors=remount-ro will mount the filesystem in read-only mode in case there are any problems with it. This prevents you from potentially losing data using a bad filesystem.

If this happened to one of your partitions, you should probably boot from a livecd or floppy (if it's not on your root partition, you can boot on recovery mode) and then run fsck on the affected disk.



6) For NTFS, FAT32, or FAT16 partitions, use dmask=027,fmask=137. 
If using dmask=000,fmask=111, all your files will be executable. 

# NTFS partitions 
# /dev/XYZ
UUID=12102C02102CEB81  /mnt/dataXYZ  ntfs-3g  auto,users,uid=1000,gid=100,dmask=027,fmask=137,utf8  0  0

# NTFS partitions for various locales, use $ locale -a 
UUID=12102C02102CEB82  /mnt/dataXYZ  ntfs-3g defaults,locale=en_US.utf8 0 0

# FAT32 and FAT32 partitions
# /dev/XYZ
UUID=12102C02102CEB83 /mnt/dataXYZ vfat defaults,user,exec,uid=1000,gid=100,umask=000 0 0

# /dev/XYZ
UUID=12102C02102CEB84 /mnt/dataXYZ vfat defaults,user,dmask=027,fmask=137 0 0

# HFS+ in Mac OS X
# /dev/XYZ
UUID=12102C02102CEB85 /mnt/dataXYZ rw,exec,auto,users 0 0


7) re-login/reboot ubuntu

8_1) check where the partition mount point is: 
```
$ df -hT 
```
   check the partition ownership: ```
$ ls -l /mnt 
```

8_2) change the owner of the folder using chown. 
```
$ sudo chown your_username:your_username /mnt/dataXYZ 
```
```
$ sudo chown JohnK:JohnK /mnt/dataXYZ 
```
```
$ sudo chown -R JohnK:JohnK /mnt/dataXYZ 
```
-R is to change the permission on all files that are in the subdirectories.[Recurrsive function]
```
$ sudo chown JohnK:JohnK myfile 
```

##Note: Fat32 partitions do not support permissions on files

8_3) copy a file[with size of a few MB] into it, then check if the disk space of that partition decreases: 
```
$ df -hT 
```

9) Then create a symbolic link [they only appear to be folders inside a partition...]
right click on the folder-> make link-> cut and paste links to your home directory


10) Boot up each linux os for testing.

References:
Ext4 Howto
[https://ext4.wiki.kernel.org/index.php/Ext4_Howto](https://ext4.wiki.kernel.org/index.php/Ext4_Howto)

Introduction to fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

How to edit and understand /etc/fstab - 1.1
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

GUI Fstab Editing with PySDM
[http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

Can access mounted data partition only as root
[http://ubuntuforums.org/archive/index.php/t-996665.html](http://ubuntuforums.org/archive/index.php/t-996665.html)

To revoke partition authorization:
System-> Administration-> Authorizations-> Storage: Mount File Systems From Internal Drives-> Revoke

---

### Post by sprop on 2012-04-30
Or using a GUI: Storage Device Manager. Easy and effective. Thanks Pablito.

[http://usemoslinux.blogspot.com/2011/11/como-auto-montar-particiones-al-inicio.html](http://usemoslinux.blogspot.com/2011/11/como-auto-montar-particiones-al-inicio.html)

---

