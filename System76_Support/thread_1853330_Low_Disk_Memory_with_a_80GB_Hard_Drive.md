---
title: "Low Disk Memory with a 80GB Hard Drive"
date: 2011-10-02
forum: System76 Support
---

### Post by JVV on 2011-10-02
Hello, 

I installed Ubuntu 10.04 LTS - the Lucid Lynx in October 2010 after my Microsoft XP system crashed due to a virus. I have a 80GB hard drive split into a 37GB hard drive and second hard drive of 43GB. 
I keep getting messages saying my memory is low and after reading other threads I typed df -h into the terminal to get:

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             6.9G  6.2G  374M  95% /
none                  494M  296K  493M   1% /dev
none                  498M  460K  497M   1% /dev/shm
none                  498M  192K  497M   1% /var/run
none                  498M     0  498M   0% /var/lock
none                  498M     0  498M   0% /lib/init/rw

How can I easily expand this 6.9G to 12GB?

Thank you

---

### Post by 3Miro on 2011-10-02
You can use an Ubuntu liveCD to resize the partitions on your hard drive. Boot from the liveCD and start Gparted.

However, MAKE SURE TO BACKUP EVERYTHING IMPORTANT!!!! If the resize messes up, you may lose all data on your hard drive.

---

### Post by drewbenn on 2011-10-02
Can you go into terminal and issue the command: ```
sudo fdisk -l
```  and post its output?  That will display the partition table for your hard drive, so we can see where the missing space has gone (since you are apparently using an ~7GB partition but you don't think you have it partitioned that way).

---

### Post by JVV on 2011-10-02
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4463    35849016    7  HPFS/NTFS
/dev/sda2            4464        9730    42301578    f  W95 Ext'd (LBA)
/dev/sda5            4464        8778    34660164+   7  HPFS/NTFS
/dev/sda6            8779        9682     7260160   83  Linux
/dev/sda7            9683        9730      379904   82  Linux swap / Solaris

---

### Post by drewbenn on 2011-10-02
So, what that shows is two main partitions: a 34GB "HPFS/NTFS" partition (your Windows partition) and then a "W95 Ext'd (LBA)" partition.  That second partition holds 3 partitions itself, another "HPFS/NTFS" (33GB, readable by Windows) partition, a 6.9GB Linux partition and a .36GB Linux swap partition.

Are you using that 33GB /dev/sda5 partition for anything?  If not, I *assume* that is where you will want to look to for extra space.

If you don't want to repartition (and you'll have to get help from someone other than me if you are going to repartition), you could try just mounting that partition and using it for storage, with a command like:

```
mkdir ~/Desktop/sda5_mount
sudo mount /dev/sda5 ~/Desktop/sda5_mount
```

(the 'mount' command might give you an error if it doesn't automatically pick the partition type; hopefully it will give you some useful errors if that's the case.)

---

