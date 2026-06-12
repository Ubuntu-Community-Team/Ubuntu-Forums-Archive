---
title: "Software RAID Failure Ubuntu server 12.04"
date: 2013-08-14
forum: Server Platforms
---

### Post by soapdude on 2013-08-14
Hello, I am a user of many flavors of Ubuntu, but this is my first Ubuntu server. I am running two 2TB HDDs in a RAID 1 setup. The server has always run great with little maintenance from me until last night. I rebooted the server after installing lamp, and it wouldn't boot back up. I entered recovery mode, and was given the error that RAID had failed. I was able to boot normally through the recovery console. I then removed the HDDs and tried to boot them as single items one at a time. Both of them boot fine. I browsed the forums here a bit, and decided I needed this information for you:

```
cat /proc/mdstatPersonalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid1 sda2[1]
      1949965120 blocks super 1.2 [2/1] [_U]
      
md0 : active raid1 sda1[1]
      3414976 blocks super 1.2 [2/1] [_U]
      
unused devices: <none>



```

And this:

```
sudo mdadm --examine /dev/sda1/dev/sda1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID :5603467b:9c5dcb9d:e3ae857c:beff72f6
           Name : server:0  (local tohost server)
  Creation Time : Mon Nov  5 13:58:102012
     Raid Level : raid1
   Raid Devices : 2
 Avail Dev Size : 6830080 (3.26 GiB3.50 GB)
     Array Size : 3414976 (3.26 GiB3.50 GB)
  Used Dev Size : 6829952 (3.26 GiB3.50 GB)
    Data Offset : 4096 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID :4b36d6a3:82546dba:1a1abcc8:63bf9134
    Update Time : Wed Aug 14 12:22:452013
       Checksum : 3c1dde8a - correct
         Events : 783


   Device Role : Active device 1
Array State : .A ('A' == active, '.' == missing) 
```

and finally this:

```
sudo mdadm --examine /dev/sdb1/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID :5603467b:9c5dcb9d:e3ae857c:beff72f6
           Name : server:0  (local tohost server)
  Creation Time : Mon Nov  5 13:58:102012
     Raid Level : raid1
   Raid Devices : 2
 Avail Dev Size : 6830080 (3.26 GiB3.50 GB)
     Array Size : 3414976 (3.26 GiB3.50 GB)
  Used Dev Size : 6829952 (3.26 GiB3.50 GB)
    Data Offset : 4096 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID :dbcadac4:6c4d78a4:51395cd5:8fd4d6d7
    Update Time : Mon Aug 12 21:42:412013
       Checksum : f70f7dc3 - correct
         Events : 46
   Device Role : Active device 0
   Array State : AA ('A' == active, '.' == missing)
cat /proc/mdstat 
```

This may be helpful as well:

```
sudo fdisk -l
Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00052ab0


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     6836223     3417088   fd  Linux raid autodetect
/dev/sda2   *     6836224  3907028991  1950096384   fd  Linux raid autodetect


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00099087


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048     6836223     3417088   fd  Linux raid autodetect
/dev/sdb2   *     6836224  3907028991  1950096384   fd  Linux raid autodetect


Disk /dev/md0: 3496 MB, 3496935424 bytes
2 heads, 4 sectors/track, 853744 cylinders, total 6829952 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


Disk /dev/md0 doesn't contain a valid partition table


Disk /dev/md1: 1996.8 GB, 1996764282880 bytes
2 heads, 4 sectors/track, 487491280 cylinders, total 3899930240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000


Disk /dev/md1 doesn't contain a valid partition table



```

I'm sorry, but I really don't know where to begin to fix this. I am comfortable using the command line for day to day things, and setting up/installing, configuring software, etc.. The server is currently running just fine, but I'm assuming RAID isn't working? Thank you very much in advance for your help!

---

### Post by DuckHook on 2013-08-14
I'm completely out of my depth on RAID so cannot help you directly. My only observation is that you are posting on the "Absolute Beginners" forum which is mismatched to the depth of knowledge you require. You would be better served asking a forum moderator to move your thread to "General Help" or "Server Platforms". I'm sure the gurus there would be much better equipped to help you.

Good luck!

---

### Post by soapdude on 2013-08-14
Thank you DuckHook.. I feel like an absolute beginner here, but I guess you're right!

---

### Post by SaturnusDJ on 2013-08-14
Your examines are messed up. Can you do them again for every array member?
```

mdadm --examine /dev/sda1
mdadm --examine /dev/sdb1
mdadm --examine /dev/sda2
mdadm --examine /dev/sdb2

```

---

### Post by soapdude on 2013-08-15
Thanks for the reply. Here they are!

```
sudo mdadm --examine /dev/sda1[sudo] password for howard: 
/dev/sda1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 5603467b:9c5dcb9d:e3ae857c:beff72f6
           Name : server:0  (local to host server)
  Creation Time : Mon Nov  5 13:58:10 2012
     Raid Level : raid1
   Raid Devices : 2


 Avail Dev Size : 6830080 (3.26 GiB 3.50 GB)
     Array Size : 3414976 (3.26 GiB 3.50 GB)
  Used Dev Size : 6829952 (3.26 GiB 3.50 GB)
    Data Offset : 4096 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 4b36d6a3:82546dba:1a1abcc8:63bf9134


    Update Time : Thu Aug 15 15:14:18 2013
       Checksum : 3c1f5905 - correct
         Events : 981




   Device Role : Active device 1
   Array State : .A ('A' == active, '.' == missing)



```

```
sudo mdadm --examine /dev/sda2/dev/sda2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : b7194b1f:398f8f86:c7bf4b30:88fcf85f
           Name : server:1  (local to host server)
  Creation Time : Mon Nov  5 13:58:28 2012
     Raid Level : raid1
   Raid Devices : 2


 Avail Dev Size : 3899930624 (1859.63 GiB 1996.76 GB)
     Array Size : 1949965120 (1859.63 GiB 1996.76 GB)
  Used Dev Size : 3899930240 (1859.63 GiB 1996.76 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 25751207:3134b635:d41c0cff:a9a8a152


    Update Time : Thu Aug 15 15:17:18 2013
       Checksum : ea369053 - correct
         Events : 60201




   Device Role : Active device 1
   Array State : .A ('A' == active, '.' == missing)



```

```
sudo mdadm --examine /dev/sdb1/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 5603467b:9c5dcb9d:e3ae857c:beff72f6
           Name : server:0  (local to host server)
  Creation Time : Mon Nov  5 13:58:10 2012
     Raid Level : raid1
   Raid Devices : 2


 Avail Dev Size : 6830080 (3.26 GiB 3.50 GB)
     Array Size : 3414976 (3.26 GiB 3.50 GB)
  Used Dev Size : 6829952 (3.26 GiB 3.50 GB)
    Data Offset : 4096 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : dbcadac4:6c4d78a4:51395cd5:8fd4d6d7


    Update Time : Mon Aug 12 21:42:41 2013
       Checksum : f70f7dc3 - correct
         Events : 46




   Device Role : Active device 0
   Array State : AA ('A' == active, '.' == missing)



```

```
sudo mdadm --examine /dev/sdb2/dev/sdb2:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : b7194b1f:398f8f86:c7bf4b30:88fcf85f
           Name : server:1  (local to host server)
  Creation Time : Mon Nov  5 13:58:28 2012
     Raid Level : raid1
   Raid Devices : 2


 Avail Dev Size : 3899930624 (1859.63 GiB 1996.76 GB)
     Array Size : 1949965120 (1859.63 GiB 1996.76 GB)
  Used Dev Size : 3899930240 (1859.63 GiB 1996.76 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 00a738b5:1e96535f:e9105531:f6910d33


    Update Time : Wed Aug 14 12:19:36 2013
       Checksum : d4a89c3d - correct
         Events : 269




   Device Role : Active device 0
   Array State : A. ('A' == active, '.' == missing)



```

---

### Post by SaturnusDJ on 2013-08-15
It looks like the array somehow broke, and the members that are hosted by /dev/sdb started a life of their own.

From your information I understand data is intact on both drives.
The quickest way to fix this is to zero the superblocks on /dev/sdb[1,2] and add them back to /dev/md[0,1].
The problem with this is that you most likely will only have one copy of your data during the sync. Chances are if this one drive(/dev/sda) fails while the sync is in progress, all data might be lost.

A more safe solution is to take a new disk and add that as member together with /dev/sda. Then you'll always have your data at /dev/sdb.

It's not that the quick solution is totally dangerous, but you won't be the first guy losing data because drive failure in the syncing process. If you go with the quick solution be sure to double check the S.M.A.R.T. data first. It's by the way always a good idea to keep an eye on the S.M.A.R.T. data, maybe this whole problem originates from there. You can use the smartmontools program for this.

---

### Post by soapdude on 2013-08-15
Thank you very much for the response here. I think I will go with the safe method, but just out of curiosity, how would I go about zeroing the superblock and adding them back? The RAID setup was done with the initial install and mostly handled by Ubuntu. Also, if I purchase a third disk, how will I go about adding it as a member? Thank you!

---

### Post by SaturnusDJ on 2013-08-15
You would do this for the quick way:
```

mdadm --zero-superblock /dev/sdb1
mdadm --zero-superblock /dev/sdb2

mdadm --manage /dev/md0 --add /dev/sdb1
mdadm --manage /dev/md1 --add /dev/sdb2

```
After a normal fail you would first remove the disks, but it appears they already aren't listed in the array anymore.


When you got a third disk, you need to copy the partition layout to match /dev/sda. Earlier ```
sfdisk -d /dev/sda | sfdisk /dev/sdc
``` worked. Your fdisk doesn't complain about a GPT table layout, so I assume it still works. Otherwise use Parted. After this, you will add the new members to the arrays with the commands as above:
```

mdadm --manage /dev/md0 --add /dev/sdb1
mdadm --manage /dev/md1 --add /dev/sdb2

```
A resync should start.

If you have backups, you may go with the quick way.
If you don't have backups I strongly advise to start making them from now. Some years ago I managed to destroy a RAID1 array. A good learning moment. ;)
And again, take a look at the S.M.A.R.T. values to make sure this problem didn't start because of a drive failure.
```

smartctl -a /dev/sda
smartctl -a /dev/sdb

```

Check S.M.A.R.T. for the new disk also just to make sure it actually is a new, healthy disk.
If you want to go insanely safe you should test the new drive before putting it to use (just saying): [http://ubuntuforums.org/showthread.php?t=2121244](http://ubuntuforums.org/showthread.php?t=2121244)

---

### Post by tgalati4 on 2013-08-15
I'm going to guess that after the LAMP installation, that you rebooted right away.  RAID1 (especially software RAID) needs some time to sync properly.  It's possible that the shutdown interrupted the sync process (because LAMP is a large data stack) and it might take a few minutes to get a proper mirror on the second drive.  When you rebooted, mdadm correctly detected this lack of sync and you were able to boot from each because LAMP is not required for boot up.

Had you tested your LAMP function on each drive, I would guess that it would work on one drive and not work on the second drive, until the sync was completed.

How long did you wait after the LAMP installation before rebooting?

---

### Post by soapdude on 2013-08-20
Thank you SaturnusDJ for a thorough answer. You've been a huge help. I am planning on purchasing two new drives to first perform the safe rebuild of the RAID1 and then to create a second one for additional storage. This server is used mostly as a backup drive for our office computers (and as a shared HDD for passing files through the network). The LAMP server is being installed to host a MYSQL database. The databases directory is backed up to a cloud server. 

tgalati4 I think you may be correct about this... I'm not sure how long I waited, but it definitely wasn't long. How long does the sync take? I wasn't aware of this! Thank you!

---

### Post by soapdude on 2013-08-30
Thanks for this! I successfully rebuild my RAID array today :)

---

