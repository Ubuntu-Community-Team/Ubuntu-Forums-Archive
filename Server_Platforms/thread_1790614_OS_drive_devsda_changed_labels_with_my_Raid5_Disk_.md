---
title: "OS drive /dev/sda changed labels with my Raid5 Disk /dev/sdc"
date: 2011-06-25
forum: Server Platforms
---

### Post by newbuntu007 on 2011-06-25
My original config:

****Partition/Drive info****

/dev/sda Boot---------->  298.09 GB Hitachi HDT72503   
20GB /
16GB /swap
50GB /var
20GB /tmp
20GB /home
4GB  /usr

/dev/sdb Raid Array 1  1.82 TB SAMSUNG HD204UI   
/dev/sdc Raid Array 2 1.82 TB SAMSUNG HD204UI   
/dev/sdd Raid Array 3 1.82 TB SAMSUNG HD204UI   
/dev/sde Raid Array 4 1.82 TB SAMSUNG HD204UI   
/dev/sdf  Raid Array  5 1.82 TB SAMSUNG HD204UI



1. For some odd reason I tried connecting to a samba share as I had it setup and I could not.  

2. Looked at webmin and it said my whole /dev/md0 RAID5 was being used..about 7.8TBs.

decided to check my RAID5 setup and drives and noticed 

****NEW Partition/Drive info****
 
 
 /dev/sda Raid Array 1  1.82 TB SAMSUNG HD204UI   
 /dev/sdb Raid Array 1  1.82 TB SAMSUNG HD204UI   

  /dev/sdc1 /
  /dev/sdc2 /swap
  /dev/sdc5 /var
  /dev/sdc6 /tmp
/dev/sdc7 /home
/dev/sdc8 /usr
 
/dev/sdd Raid Array 2 1.82 TB SAMSUNG HD204UI   
 /dev/sde Raid Array 3 1.82 TB SAMSUNG HD204UI   
 

What could of happened?  I didn't connect any new drives or anything.  I had checked my "mdadm.conf" and "fstab" and everything looked the same?

Is there a fix or so I have to start all over?

---

### Post by TechSupportx86 on 2011-06-25
[http://ubuntuforums.org/showthread.php?t=1707996](http://ubuntuforums.org/showthread.php?t=1707996)

Try this. i had the same problem not long ago and this fixed it. You are probably using the logical name like i was. Open up fstab and use the UUID to mount the device to a directory. Here is what mine looks like for reference:


```
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
#
#===========================================================================================#
proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=5c002a94-6ae3-4357-bf2c-090217ef13de /               ext4    errors=remount-ro 0       1
UUID=5a2d87be-a882-4a22-9ca4-43ffe61f8d0e none            swap    sw              0       0
#
#
# OPSYS DRIVES ABOVE LINE
#============================
# SAMBA DRIVES BELOW LINE
#
#
UUID=ce835409-e66b-4192-9ad4-1366dd7cee3a /media/kari   ext3    defaults        0       2
UUID=b89ca9c2-3af3-4ef2-b3e9-cf70963e547f /media/cate   ext3    defaults        0       2
UUID=50c68d71-9118-4dae-b0af-af8b29d20ef1 /media/dani   ext3    defaults        0       2
#UUID=3bf06e96-65c6-46e5-93fd-018611adc4bd /media/down  ext3    defaults        0       2
#/dev/sdd1      /media/500      auto    defaults,umask=000      0       2
```

---

### Post by newbuntu007 on 2011-06-26
Hey thanks for the help, that is neat and organized.  Now I'm running a RIAD5 with this system and the only drive that did appear was my /dev/md0 drive that is related to my Samba drives but its a whole raid drive, not individual samba drives.

I noticed you have individual SAMBA drives with Ids but my drives were in a RAID5 config= /dev/md0 in Fstab.

Two of my RAID5 drives moved 1 level up from /sdb & /sdc to /sda and sdb.

Do I still put all 5 drives with their UUID's then create my RAID 5 /dev/md0?

---

### Post by arrrghhh on 2011-06-27
> **newbuntu007 said:**
> Hey thanks for the help, that is neat and organized.  Now I'm running a RIAD5 with this system and the only drive that did appear was my /dev/md0 drive that is related to my Samba drives but its a whole raid drive, not individual samba drives.

I noticed you have individual SAMBA drives with Ids but my drives were in a RAID5 config= /dev/md0 in Fstab.

Two of my RAID5 drives moved 1 level up from /sdb & /sdc to /sda and sdb.

Do I still put all 5 drives with their UUID's then create my RAID 5 /dev/md0?

You should **always** reference the disk using UUID.  The /dev locations can (and will) change, UUID's will never change.

---

