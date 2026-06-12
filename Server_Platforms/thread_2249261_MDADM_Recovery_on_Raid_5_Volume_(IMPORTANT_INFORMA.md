---
title: "MDADM Recovery on Raid 5 Volume (IMPORTANT INFORMATION at STAKE)"
date: 2014-10-20
forum: Server Platforms
---

### Post by BigNotch44 on 2014-10-20
Okay, so I've exhausted the threads to try and recover my array here and am at a point where I believe I may have lost some VERY important information.  So, I'd like you guys/gals to look at it one last time for me before I declare it a loss.

I have 4 drives setup as an R5 volume which at the time was running degraded.  I had my replacement drive on order and low-and-behold my array goes offline with another failure.  After rebooting the system, the remaining three drives came back online (sdb1, sdd1, and sde1) and the failed drive (sdf1) remained offline.  While re-assembling the array I received the following:

```
root@ServerNotch:~# mdadm --assemble /dev/md4 /dev/sdb1 /dev/sdd1 /dev/sde1 
mdadm: /dev/md4 assembled from 2 drives - not enough to start the array.

```

Okay, so VERY bad that now my array is flagged as 2 failed drives.  When running an fdisk -l, all looks fine with the arrays and all showing "Linux-Raid-AutoDetect".  Figuring that no real hardware failures occurred, I ran the assemble command with a --force to clear the failed flag.  Here's what I got:

```
root@ServerNotch:~# mdadm --assemble /dev/md4 /dev/sdb1 /dev/sdd1 /dev/sde1 
mdadm: /dev/md4 assembled from 2 drives - not enough to start the array.
root@ServerNotch:~# mdadm --assemble --force /dev/md4 /dev/sdb1 /dev/sdd1 /dev/sde1 
mdadm: forcing event count in /dev/sde1(2) from 787025 upto 787034
mdadm: clearing FAULTY flag for device 2 in /dev/md4 for /dev/sde1
mdadm: failed to add /dev/sdb1 to /dev/md4: Device or resource busy
mdadm: /dev/md4 assembled from 2 drives - not enough to start the array.

```

When I ran a cat on /proc/mdstat, I got the following:

```
root@ServerNotch:~# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md4 : active raid5 sdb1[0] sde1[4](F) sdd1[1]
      4395407616 blocks level 5, 256k chunk, algorithm 2 [4/2] [UU__]
      
md3 : active raid1 sdc4[1] sda4[0]
      8000256 blocks [2/2] [UU]
      
md2 : active raid1 sdc3[1] sda3[0]
      818511680 blocks [2/2] [UU]
      
md1 : active raid1 sdc2[1] sda2[0]
      149998784 blocks [2/2] [UU]
      
md0 : active raid1 sdc1[1] sda1[0]
      248896 blocks [2/2] [UU]

```

What's interesting is that mdadm found sdb1 as busy but is flagging sde1 as the failed drive.  So when I ran an --Examine on sde1, I got no superblock:

```
root@ServerNotch:~# mdadm --examine /dev/sde1 
mdadm: No md superblock detected on /dev/sde1.

```

When I run an --Examine on sdb1 I get the following:
```
root@ServerNotch:~# mdadm --examine /dev/sdb1 
/dev/sdb1:
          Magic : a92b4efc
        Version : 00.90.00
           UUID : 814d9c27:f04a9e2d:097c049d:1ea44462 (local to host ServerNotch)
  Creation Time : Fri Jul 24 22:56:46 2009
     Raid Level : raid5
  Used Dev Size : 1465135872 (1397.26 GiB 1500.30 GB)
     Array Size : 4395407616 (4191.79 GiB 4500.90 GB)
   Raid Devices : 4
  Total Devices : 3
Preferred Minor : 4

    Update Time : Mon Oct 20 17:02:08 2014
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 2
  Spare Devices : 0
       Checksum : 3904145c - correct
         Events : 787046

         Layout : left-symmetric
     Chunk Size : 256K

      Number   Major   Minor   RaidDevice State
this     0       8       17        0      active sync   /dev/sdb1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       49        1      active sync   /dev/sdd1
   2     2       0        0        2      faulty removed
   3     3       0        0        3      faulty removed

```

Again, looks like my array is showing the 2 failures of death.  I'm not sure if there is anything else that can be done to save my data (which only a portion of was backed up offsite), but maybe there are some dying last moment commands I could try to put this array back together.  What I believe I do have going for me is that it isn't a 2 physical drive failure, but the corrupt superblock may be enough to knock me out here...

Thanks for your help in advance!

---

### Post by tgalati4 on 2014-10-21
That is a problem with RAID5.  Your Use Case demonstrates why RAID6 (and above) was developed.  Running RAID5 in degraded mode is risky--when you lose the 2nd disk, you loose all of your data.  Which is why the mantra:  *RAID is not a backup strategy.*

I would pull out your drives and work with each one, one at a time.  It's possible that your PSU is failing to supply current to all of your spinners.  That would be an easy fix.  Check the SMART parameters of each disk individually.  If they all pass, then there is some hope.  If you get some nasty, hardware errors on 2 of them, then simple mdadm one-liners will not put Humpty Dumpty and all of his bits back together again.

```
sudo smartctl -a /dev/sdb
```

---

### Post by BigNotch44 on 2014-10-25
Here's what I got on /dev/sdb1

```

ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   117   099   006    Pre-fail  Always       -       155810576
  3 Spin_Up_Time            0x0003   100   099   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   100   100   020    Old_age   Always       -       170
  5 Reallocated_Sector_Ct   0x0033   001   001   036    Pre-fail  Always   FAILING_NOW 4094
  7 Seek_Error_Rate         0x000f   081   060   030    Pre-fail  Always       -       160414157
  9 Power_On_Hours          0x0032   048   048   000    Old_age   Always       -       45970
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   100   100   020    Old_age   Always       -       169
184 Unknown_Attribute       0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Unknown_Attribute       0x0032   100   100   000    Old_age   Always       -       1
189 High_Fly_Writes         0x003a   089   089   000    Old_age   Always       -       11
190 Airflow_Temperature_Cel 0x0022   070   037   045    Old_age   Always   In_the_past 30 (255 255 30 28)
194 Temperature_Celsius     0x0022   030   063   000    Old_age   Always       -       30 (0 21 0 0)
195 Hardware_ECC_Recovered  0x001a   045   023   000    Old_age   Always       -       155810576
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       25735444083600
241 Unknown_Attribute       0x0000   100   253   000    Old_age   Offline      -       2164664820
242 Unknown_Attribute       0x0000   100   253   000    Old_age   Offline      -       2165252182


```

Reallocated_Sector_Ct is failing... What does this mean? Recoverable?

---

### Post by nerdtron on 2014-10-26
We had raid5 before, 2 drives failed with important data, man professional recovery is too darn expensive! But we were all able to recover data.

---

### Post by BigNotch44 on 2014-10-27
Hmmm... who do you recommend for professional recovery?

---

### Post by nerdtron on 2014-10-27
You can call the supplier of the server and you can tell that the you need to recover data. They can either offer you recovery services or recommend another company.

---

### Post by tgalati4 on 2014-10-27
Failing reallocateable sectors could indicate that the hard drive has run out of places to store bad-sector data.  This is bad, and not fixable.  Each drive has a certain number of sectors reserved to hold data when a bad sector is found.  The command *badblocks* will print out those sectors.  If you have too many bad sectors, and the drive runs out of reallocation space, then those sectors have been lost forever.  The rest of the data should be recoverable, but those lost sectors could be in a critical location--like describing the RAID layout for the drive.

You said that 2 drives failed.  What was the SMART status of the second drive that failed?

A professional recovery service may be able to save the data in this situation.  Rebuilding RAID pools manually is not trivial.  I would expect a lot of manhours to perform this.

---

### Post by TheFu on 2014-10-27
> **nerdtron said:**
> You can call the supplier of the server and you can tell that the you need to recover data. They can either offer you recovery services or recommend another company.

The guys at myharddrivedied.com are excellent. Scott Moulton teaches (literally) the class on data recovery.
You can find his videos and presentation on youtube, but without the specialized equipment and experience it is impossible to reproduce his results for us.

Just so it is clear - backups - event 5x backups are cheaper than data recovery services.

---

