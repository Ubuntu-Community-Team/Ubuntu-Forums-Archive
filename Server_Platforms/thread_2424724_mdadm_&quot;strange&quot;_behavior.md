---
title: "mdadm &quot;strange&quot; behavior"
date: 2019-08-13
forum: Server Platforms
---

### Post by giovanesaggio on 2019-08-13
Hi guys,

I've just moved my home server from Windows 2016 to Ubuntu Server 18.04 and I configured my disks (3x2TB) in a (software) raid5 array using mdadm.
After the configuration all works well, I can see and mount my md device so everything's good.

Now, _just for my curiosity_, I tried to shut down the machine and unplug one of the disks, expecting to have a degradated (but accessible) raid at the next reboot. But this is not the case, the array of the 2 disks is marked as "inactive" and I can not figure out why. Is there anything "strange" or am I missing anything?
When I plug-in back the third disk everything re-start working as expcted, the raid is marked as "active" and can be mounted as expected.

Thanks in advance

---

### Post by LHammonds on 2019-08-13
Are 3 disks all you have in the system?  Where does /boot reside?  I would think you have 2 small drives in RAID 1 (mirroring) with /boot on it.

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

---

### Post by giovanesaggio on 2019-08-14
Sorry, I forgot to specify: the 3 disks are data disk, the system is installed on a separate 120gb ssd (no raid, no mdadm).

---

### Post by SeijiSensei on 2019-08-14
What do you get when you run

```
sudo mdadm --detail /dev/md*
```

---

### Post by giovanesaggio on 2019-08-14
> **SeijiSensei said:**
> What do you get when you run

```
sudo mdadm --detail /dev/md*
```

This is what I get with one of the disks disconnected:

```
mdadm: Unknown keyword/dev/md0:
           Version : 1.2
        Raid Level : raid0
     Total Devices : 2
       Persistence : Superblock is persistent


             State : inactive
   Working Devices : 2


              Name : server:0  (local to host server)
              UUID : 1bb40417:aa865066:7fd51115:fa7851f5
            Events : 12837


    Number   Major   Minor   RaidDevice


       -       8       33        -        /dev/sdc1
       -       8       17        -        /dev/sdb1
```


While this is the result with all the 3 disks connected.

```
mdadm: Unknown keyword/dev/md0:
           Version : 1.2
     Creation Time : Mon Aug 12 11:22:07 2019
        Raid Level : raid5
        Array Size : 3906762752 (3725.78 GiB 4000.53 GB)
     Used Dev Size : 1953381376 (1862.89 GiB 2000.26 GB)
      Raid Devices : 3
     Total Devices : 3
       Persistence : Superblock is persistent


     Intent Bitmap : Internal


       Update Time : Wed Aug 14 13:48:52 2019
             State : clean
    Active Devices : 3
   Working Devices : 3
    Failed Devices : 0
     Spare Devices : 0


            Layout : left-symmetric
        Chunk Size : 512K


Consistency Policy : bitmap


              Name : server:0  (local to host server)
              UUID : 1bb40417:aa865066:7fd51115:fa7851f5
            Events : 12837


    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       8       33        1      active sync   /dev/sdc1
       3       8       49        2      active sync   /dev/sdd1
```

Essentially a working "active" RAID5 becomes an "inactive" RAID0 and not a "degradated" RAID5. I can not figure out why.

---

### Post by SeijiSensei on 2019-08-14
That is strange.  Did you disconnect the power cable or the SATA cable?  Does it matter?

---

### Post by giovanesaggio on 2019-08-14
> **SeijiSensei said:**
> That is strange.  Did you disconnect the power cable or the SATA cable?  Does it matter?

Only the sata cable, but I just tried removing the power cable and the result is the same.

My concern is that an actual disk failure would make all my data inaccessible :confused: maybe the result with a failed but connected disk is different but... How can I know? And a disk may break and be not readable at all, as if it would be disconnected so... This RAID seems to be not realiable at all.

EDIT: I've found [this]("http://fibrevillage.com/storage/676-how-to-fix-linux-mdadm-inactive-array"), that seems to be similar to my issue. However, this does not explain why the array is marked as invalid with a wrong raid level :confused:

---

### Post by SeijiSensei on 2019-08-14
> My concern is that an actual disk failure would make all my data inaccessible 

Routine backups are your friend.

I've never been a fan of RAID5 myself.  My most serious data loss came when I had a RAID5 with one dead disk.  Before I could replace it, another one failed, and all my data was gone. Nowadays I stick to RAID1 with daily backups.

---

### Post by giovanesaggio on 2019-08-14
> **SeijiSensei said:**
> Routine backups are your friend.

I've never been a fan of RAID5 myself.  My most serious data loss came when I had a RAID5 with one dead disk.  Before I could replace it, another one failed, and all my data was gone. Nowadays I stick to RAID1 with daily backups.

Yeah, that's for sure ;) In fact i bought a 4TB external drive to backup all the content of the RAID.
I've chosen RAID5 instead of RAID1/10 because I only have 3 disks, so I would have had a stand-alone disk. The behavior anyway seems to be the same with RAID1 (and RAID6) arrays: when a disk is removed the array is marked as "inactive" and the level moved to RAID0. Theorically the procedure in the link I've posted should solve the issue but it is not what I would have instinctively done in case of failure.

Off-topic: rsync is ok for data backup?

---

### Post by SeijiSensei on 2019-08-15
> **giovanesaggio said:**
> Off-topic: rsync is ok for data backup?

I use rsync every night to back up three cloud servers and my local server.  Like you, I have a 4 TB outboard drive to which I write everything. It's big enough to store five days worth of backups, plus one from each of the past seven months. I wrote a bash script to do all this.  

Using the --files-from and --exclude-from switches to rsync lets you define the directories you want to back up and those you want to exclude in simple text files.

---

### Post by giovanesaggio on 2019-08-19
> **SeijiSensei said:**
> I use rsync every night to back up three cloud servers and my local server.  Like you, I have a 4 TB outboard drive to which I write everything. It's big enough to store five days worth of backups, plus one from each of the past seven months. I wrote a bash script to do all this.  

Using the --files-from and --exclude-from switches to rsync lets you define the directories you want to back up and those you want to exclude in simple text files.

Sorry for the late response, thank you! :)

Just to close the discussion, in case someone encounter the same issue, I tried to unplug a disk while the system was running: in this case the array was correctly moved to "degradated" state but it was still accessibile (even after a reboot). In the very end, I think the "problem" is the fact that mdadm needs to "record" the changes in the array and can not automagically detect what happened when the system was powered off (such as an unplugged disk).

---

