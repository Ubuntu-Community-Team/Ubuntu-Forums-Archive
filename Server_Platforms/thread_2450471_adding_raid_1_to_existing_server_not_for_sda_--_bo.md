---
title: "adding raid 1 to existing server not for sda -- boot  but to  sdb (adding  sdc)"
date: 2020-09-14
forum: Server Platforms
---

### Post by tross9 on 2020-09-14
I want to setup raid 1 for my existing sdb drive, ( my main data storage)  
  system info --- this is a home server and a comppany production server ( mainly used to my storage and website )
    sda boot drive
    sdb data storage ( database and client backup )  



I found several posting on adding raid 1 to sda and they refer to commands that will allow the dive to be part of the boot up, I assume that is if the drive is the boot drive.
   do i need to do these commands like

--make sure that the array is reassembled automatically at boot, we will have to adjust the /etc/mdadm/mdadm.conf file. We can automatically scan the active array and append the file by typing:


$sudo mdadm --detail --scan | sudo tee -a /etc/mdadm/mdadm.conf




--Afterwards, you can update the initramfs, or initial RAM file system, so that the array will be available during the early boot process:


$sudo update-initramfs -u




--Add the new filesystem mount options to the /etc/fstab file for automatic mounting at boot:


$echo '/dev/md0 /mnt/md0 ext4 defaults,nofail,discard 0 0' | sudo tee -a /etc/fstab

---

### Post by SeijiSensei on 2020-09-14
I've built machines where /boot is an ordinary partition, but the remaining partition is used in a RAID 1 with a second drive. Most times, though, I set up a separate RAID 1 with two additional drives. 

Here's an example of the first setup:
```

# mdadm --detail /dev/md0
/dev/md0:
        Version : 1.1
  Creation Time : Wed Jan 24 17:31:42 2018
     Raid Level : raid1
     Array Size : 924393472 (881.57 GiB 946.58 GB)
  Used Dev Size : 924393472 (881.57 GiB 946.58 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

  Intent Bitmap : Internal

    Update Time : Mon Sep 14 11:12:41 2020
          State : clean 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           Name : myserver:0
           UUID : 75c8705b:ffad312e:c38afe3a:646c71af
         Events : 29301

    Number   Major   Minor   RaidDevice State
       0       8        4        0      active sync   /dev/sda4
       1       8       49        1      active sync   /dev/sdd1

```
This device uses a large partition on the boot drive, /dev/sda, and an identically-sized partition on a second drive /dev/sdd. I mount this as /home. /dev/sda1 is /boot, /dev/sda3 is the root of the Linux filesystem.

Here's an example of the second arrangement:
```

        Version : 1.2
  Creation Time : Sat Jun  4 16:00:51 2016
     Raid Level : raid1
     Array Size : 2930133824 (2794.39 GiB 3000.46 GB)
  Used Dev Size : 2930133824 (2794.39 GiB 3000.46 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Mon Sep 14 10:46:27 2020
          State : clean 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           Name : bigraid:0
           UUID : 7d5eb78b:9387031d:01c42ba3:dd74ca7e
         Events : 1101

    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       1       8       17        1      active sync   /dev/sdb1

```
This device uses all the space on two, 2 TB, drives, /dev/sdb and /dev/sdc.

---

### Post by tross9 on 2020-09-14
Thanks for replying,

I may have confused my question,

   the post/example i've seen refer to creating a raid 1 on the existing SDA drive,
 
 ( currently have to physical HDs in the system , adding a third )  
  i'll not be touching my SDA but adding a third hard drive( SDC ) to mirror my existing SDB drive.  
 
 so do I ignore the command like
[COLOR=#000000] -- make sure that the array is reassembled automatically at boot

 seeing that these two drives are not part of the main boot up process. ( they do need to be mounted, as part of the boot up ,of course)

 [/COLOR]

---

### Post by slickymaster on 2020-09-14
Thread moved to **Server Platforms** for a better fit

---

### Post by darkod on 2020-09-14
No, the part to have the array reassembled at boot is for all arrays. Otherwise it won't assemble it on each reboot. So you have to do that part too.

Basically what you need to do is:
1. Create one big partition on sdc, that will be sdc1 (if you want one big array with the whole disk space)
2. Create one new array using sdc1 and one missing member (for example array name md0)
3. Move your data from sdb to the array md0
4. Create new blank partition table on sdb (erase the whole disk), then create identical size partition sdb1 (as the one sdc1)
5. Add the sdb1 as member to md0

That is on high level. If you get stuck on specific commands, ask.

---

### Post by rsteinmetz70112 on 2020-09-14
Don't forget to add the array to fstab. Use UUID because drive letter may change especially if you add USB drives.

---

### Post by tross9 on 2020-09-15
Thanks, all of these post will help.

  i'll update the status of this post when I finish the install.  ( it take me a few days to get time to work on that server)

---

