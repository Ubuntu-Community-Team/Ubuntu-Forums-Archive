---
title: "RAID1 fsck error at boot"
date: 2009-08-28
forum: Server Platforms
---

### Post by R.Bucky on 2009-08-28
I just reinstalled my RAID1 (had to reorganize disks). I created md0 (/boot), md1 (swap), and md2 (/). On boot, I receive an fsck error as noted in the screen shot attached. However, my /proc/mdstat appears fine as does mdadm --detail /dev/md0 and so on. Any takers on why I receive this nasty boot error as seen on the screenshot?

```
md2 : active raid1 sdb3[0] sdc3[1]
      242236032 blocks [2/2] [UU]
      
md1 : active raid1 sdb2[0] sdc2[1]
      979840 blocks [2/2] [UU]
      
md0 : active raid1 sdb1[0] sdc1[1]
      1951744 blocks [2/2] [UU]

```

and

```
 sudo mdadm --detail /dev/md2
/dev/md2:
        Version : 00.90.03
  Creation Time : Thu Aug 27 16:12:16 2009
     Raid Level : raid1
     Array Size : 242236032 (231.01 GiB 248.05 GB)
  Used Dev Size : 242236032 (231.01 GiB 248.05 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 2
    Persistence : Superblock is persistent

    Update Time : Fri Aug 28 05:03:05 2009
          State : active
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 20bb810a:53c5f6cc:ac961fba:4f1545a7
         Events : 0.11

    Number   Major   Minor   RaidDevice State
       0       8       19        0      active sync   /dev/sdb3
       1       8       35        1      active sync   /dev/sdc3


```

---

### Post by bhepdogg on 2009-09-30
I'm having a similar problem with my raid1 array that I have recently setup.  I don't get the exact same error as you do, but you can see the details on my post over at linuxquestions.org:
[http://www.linuxquestions.org/questions/ubuntu-63/raid1-array-says-devmd0-does-not-have-a-valid-partition-table-wont-auto-mount-757872/#post3701417](http://www.linuxquestions.org/questions/ubuntu-63/raid1-array-says-devmd0-does-not-have-a-valid-partition-table-wont-auto-mount-757872/#post3701417)

It looks like yours is giving an error regarding a bad UUID.  The UUID that I put in /etc/fstab is not the UUID that I got from running the mdadm --detail on the device.  I was having problems mounting my raid array until I used the UUID from the blkid command.  What is the UUID for /dev/md2 when you run the command blkid?

---

### Post by R.Bucky on 2009-09-30
My UUID would differ from yours and everyone else. The UUID is a unique, 128-bit identifier. If we had the same numbers I might be kind of creeped out. In the end, I simply reinstalled my RAID1 array. It was far less time consuming and proved to be the safe option.
[http://buckycomputing.net/blog/raid1-installation-p2/](http://buckycomputing.net/blog/raid1-installation-p2/)

---

### Post by fjgaude on 2009-10-03
It should be clear that the UUID you get from **mdadm.conf** file is not the UUID you mount the array with. The **blkid** is that one. I've never used other than the array name to mount because there can be no mixing up the name.

---

### Post by rolnik on 2009-10-03
I'm seeing a similar fsck error on reboot as R.Bucky shows in his .jpg, except that I've narrowed the problem (impacting /dev/md2) to be my reliance (in some mdadm.conf file settings) on an external bitmap.  In other words, I drop down into the same 'error 8' provoked administrative console (with some mdadm.conf settings).  I can boot (w/o the 'error 8' but still have other issues) when I simply remove the bitmap reference from mdadm.conf.  So right now, I'm bitmap-free in my mdadm.conf.

See my three flavors of mdadm.conf at:
[http://ubuntuforums.org/showthread.php?p=8046072#post8046072](http://ubuntuforums.org/showthread.php?p=8046072#post8046072)  

If anybody know how to tell Ubuntu to _quit_ assembling a RAID array, that would be a great help, since the benefits of an external bitmap outway the small penalty I have in manually addembling/mounting /dev/md2 (and restarting a few processes).

---

### Post by fjgaude on 2009-10-03
Anything wrong with putting a line in your fstab file to auto mount the array at boot time?

---

