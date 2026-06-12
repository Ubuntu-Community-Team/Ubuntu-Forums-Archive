---
title: "assemble failed out-of-date raid5?"
date: 2015-05-11
forum: Server Platforms
---

### Post by OrcLex on 2015-05-11
I need help with my raid5 after it crashed because of bad sectors.
Previously I could re-assemble it with
```

    # mdadm --assemble --force -v /dev/md0 /dev/sde1 /dev/sdf1 /dev/sdg1 /dev/sdh1 /dev/sdi1
```

but while doing a backup it crashed again and now I'm not able to re-assemble it anymore because two disks are out-of-date:

```
    # mdadm --assemble --force -v /dev/md0 /dev/sde1 /dev/sdf1 /dev/sdg1 /dev/sdh1 /dev/sdi1
    mdadm: looking for devices for /dev/md0
    mdadm: /dev/sde1 is identified as a member of /dev/md0, slot -1.
    mdadm: /dev/sdf1 is identified as a member of /dev/md0, slot 0.
    mdadm: /dev/sdg1 is identified as a member of /dev/md0, slot 1.
    mdadm: /dev/sdh1 is identified as a member of /dev/md0, slot 2.
    mdadm: /dev/sdi1 is identified as a member of /dev/md0, slot 3.
    mdadm: added /dev/sdg1 to /dev/md0 as 1
    mdadm: added /dev/sdh1 to /dev/md0 as 2 (possibly out of date)
    mdadm: added /dev/sdi1 to /dev/md0 as 3 (possibly out of date)
    mdadm: failed to add /dev/sde1 to /dev/md0: Device or resource busy
    mdadm: added /dev/sdf1 to /dev/md0 as 0
    mdadm: /dev/md0 assembled from 2 drives - not enough to start the array.
```

As you can see here only two devices **sdf1** and **sdg1** have set the latest update time (+ spare, but it has not finished rebuilding).

```
     mdadm --examine /dev/sd[efghi]1 | egrep 'dev|Update|Role|State|Chunk Size'
    /dev/sde1:
              State : clean
        Update Time : Sun May 10 04:15:59 2015
         Chunk Size : 512K
       Device Role : spare
       Array State : AA.. ('A' == active, '.' == missing, 'R' == replacing)

    /dev/sdf1:
              State : clean
        Update Time : Sun May 10 04:15:59 2015
         Chunk Size : 512K
       Device Role : Active device 0
       Array State : AA.. ('A' == active, '.' == missing, 'R' == replacing)

    /dev/sdg1:
              State : clean
        Update Time : Sun May 10 04:15:59 2015
         Chunk Size : 512K
       Device Role : Active device 1
       Array State : AA.. ('A' == active, '.' == missing, 'R' == replacing)

    /dev/sdh1:
              State : clean
        Update Time : Sat May  9 23:10:06 2015
         Chunk Size : 512K
       Device Role : Active device 2
       Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)

    /dev/sdi1:
              State : active
        Update Time : Sat Dec  7 12:43:00 2013
         Chunk Size : 512K
       Device Role : Active device 3
       Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
```

I did not change any data on the raid since the update time from the other two devices **sdh1** and **sdi1**. I don't need to resync all data, I just need to backup the last files, so I just need to mount it a last time read-only.

Is there any way to do this? :confused: Maybe I can force it to ignore the out-of-date? I'm wondering why *--force* doesn't work anymore...


Hm, for the next try, the devices are busy but *lsof /dev/sd[efghi]1* gives me no output.


```
# mdadm --assemble --force --verbose /dev/md0 /dev/sde1 /dev/sdf1 /dev/sdg1 /dev/sdh1 /dev/sdi1
mdadm: looking for devices for /dev/md0
mdadm: /dev/sde1 is busy - skipping
mdadm: /dev/sdg1 is busy - skipping
mdadm: /dev/sdh1 is busy - skipping
mdadm: /dev/sdi1 is busy - skipping
mdadm: Merging with already-assembled /dev/md/m08002-lin:data2gb
mdadm: /dev/sdi1 is identified as a member of /dev/md/m08002-lin:data2gb, slot 0.
mdadm: /dev/sdh1 is identified as a member of /dev/md/m08002-lin:data2gb, slot 2.
mdadm: /dev/sdg1 is identified as a member of /dev/md/m08002-lin:data2gb, slot 1.
mdadm: /dev/sde1 is identified as a member of /dev/md/m08002-lin:data2gb, slot -1.
mdadm: /dev/sdf1 is identified as a member of /dev/md/m08002-lin:data2gb, slot 3.
mdadm: /dev/sdg1 is already in /dev/md/m08002-lin:data2gb as 1
mdadm: /dev/sdh1 is already in /dev/md/m08002-lin:data2gb as 2
mdadm: failed to add /dev/sdf1 to /dev/md/m08002-lin:data2gb: Device or resource busy
mdadm: /dev/sde1 is already in /dev/md/m08002-lin:data2gb as -1
mdadm: /dev/sdi1 is already in /dev/md/m08002-lin:data2gb as 0
mdadm: /dev/md/m08002-lin:data2gb assembled from 1 drive and 1 spare - not enough to start the array.


# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md127 : inactive sdi1[0](S) sdh1[3](S) sdg1[1](S) sde1[4](S)
      7813529600 blocks super 1.2
       
unused devices: <none>                                                                                                                                                                                         

```


Devices are busy. So I tried to stop and re-assemble it:

```

# mdadm --stop /dev/md127                                                                                                                                                                        
mdadm: stopped /dev/md127                                                                                                                                                                                      


# mdadm --assemble --force --verbose /dev/md0 /dev/sde1 /dev/sdf1 /dev/sdg1 /dev/sdh1 /dev/sdi1                                                                                           
mdadm: looking for devices for /dev/md0                                                                                                                                                                        
mdadm: /dev/sde1 is identified as a member of /dev/md0, slot -1.                                                                                                                                               
mdadm: /dev/sdf1 is identified as a member of /dev/md0, slot 3.                                                                                                                                                
mdadm: /dev/sdg1 is identified as a member of /dev/md0, slot 1.                                                                                                                                                
mdadm: /dev/sdh1 is identified as a member of /dev/md0, slot 2.                                                                                                                                                
mdadm: /dev/sdi1 is identified as a member of /dev/md0, slot 0.                                                                                                                                                
mdadm: added /dev/sdg1 to /dev/md0 as 1                                                                                                                                                                        
mdadm: added /dev/sdh1 to /dev/md0 as 2 (possibly out of date)                                                                                                                                                 
mdadm: added /dev/sdf1 to /dev/md0 as 3 (possibly out of date)                                                                                                                                                 
mdadm: failed to add /dev/sde1 to /dev/md0: Device or resource busy                                                                                                                                            
mdadm: added /dev/sdi1 to /dev/md0 as 0                                                                                                                                                                        
mdadm: /dev/md0 assembled from 2 drives - not enough to start the array.                                                                                                                                       


# mdadm --run /dev/md0                                                                                                                                                                           
mdadm: error opening /dev/md0: No such file or directory           

```

Why is here no device **md0**??? :confused:                                                                                                                                        
/dev/md0 was assembled from 2 drives?!...


```

# cat /proc/mdstat                                                                                                                                                                               
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]                                                                                                                          
unused devices: <none>                                                                                                                                                                                         

```

So trying again to assemble **md127**:

```

# mdadm --assemble --force --verbose /dev/md127 /dev/sde1 /dev/sdf1 /dev/sdg1 /dev/sdh1 /dev/sdi1                                                                                                
mdadm: looking for devices for /dev/md127                                                                                                                                                                      
mdadm: /dev/sde1 is identified as a member of /dev/md127, slot -1.                                                                                                                                             
mdadm: /dev/sdf1 is identified as a member of /dev/md127, slot 3.                                                                                                                                              
mdadm: /dev/sdg1 is identified as a member of /dev/md127, slot 1.                                                                                                                                              
mdadm: /dev/sdh1 is identified as a member of /dev/md127, slot 2.
mdadm: /dev/sdi1 is identified as a member of /dev/md127, slot 0.
mdadm: added /dev/sdg1 to /dev/md127 as 1
mdadm: added /dev/sdh1 to /dev/md127 as 2 (possibly out of date)
mdadm: added /dev/sdf1 to /dev/md127 as 3 (possibly out of date)
mdadm: failed to add /dev/sde1 to /dev/md127: Device or resource busy
mdadm: added /dev/sdi1 to /dev/md127 as 0
mdadm: /dev/md127 assembled from 2 drives - not enough to start the array.


# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
unused devices: <none>


# mdadm --run /dev/md0
mdadm: error opening /dev/md0: No such file or directory


# mdadm --run /dev/md127
mdadm: error opening /dev/md127: No such file or directory

```

What's happening here??? :confused:
Can someone help me please?


Complete information to the raid5 devices:

```
    # mdadm --examine /dev/sd[efghi]1
    /dev/sde1:
              Magic : a92b4efc
            Version : 1.2
        Feature Map : 0x0
         Array UUID : a87dfb70:2ecd03f9:ee62b434:fc637218
               Name : m08002-lin:data2gb
      Creation Time : Mon Sep  2 12:48:02 2013
         Raid Level : raid5
       Raid Devices : 4
    
     Avail Dev Size : 3906764800 (1862.89 GiB 2000.26 GB)
         Array Size : 5860145664 (5588.67 GiB 6000.79 GB)
      Used Dev Size : 3906763776 (1862.89 GiB 2000.26 GB)
        Data Offset : 262144 sectors
       Super Offset : 8 sectors
       Unused Space : before=262064 sectors, after=1024 sectors
              State : clean
        Device UUID : 624d3873:7970ba27:da0f511a:45367bdd
    
        Update Time : Sun May 10 04:15:59 2015
           Checksum : 599a5235 - correct
             Events : 108804
    
             Layout : left-symmetric
         Chunk Size : 512K
    
       Device Role : spare
       Array State : AA.. ('A' == active, '.' == missing, 'R' == replacing)
    /dev/sdf1:
              Magic : a92b4efc
            Version : 1.2
        Feature Map : 0x0
         Array UUID : a87dfb70:2ecd03f9:ee62b434:fc637218
               Name : m08002-lin:data2gb
      Creation Time : Mon Sep  2 12:48:02 2013
         Raid Level : raid5
       Raid Devices : 4
    
     Avail Dev Size : 3906764800 (1862.89 GiB 2000.26 GB)
         Array Size : 5860145664 (5588.67 GiB 6000.79 GB)
      Used Dev Size : 3906763776 (1862.89 GiB 2000.26 GB)
        Data Offset : 262144 sectors
       Super Offset : 8 sectors
       Unused Space : before=262064 sectors, after=1024 sectors
              State : clean
        Device UUID : 4827a499:12980366:0de13b87:541a9b5e
    
        Update Time : Sun May 10 04:15:59 2015
           Checksum : ac5a08f2 - correct
             Events : 108804
    
             Layout : left-symmetric
         Chunk Size : 512K
    
       Device Role : Active device 0
       Array State : AA.. ('A' == active, '.' == missing, 'R' == replacing)
    /dev/sdg1:
              Magic : a92b4efc
            Version : 1.2
        Feature Map : 0x0
         Array UUID : a87dfb70:2ecd03f9:ee62b434:fc637218
               Name : m08002-lin:data2gb
      Creation Time : Mon Sep  2 12:48:02 2013
         Raid Level : raid5
       Raid Devices : 4
    
     Avail Dev Size : 3906764800 (1862.89 GiB 2000.26 GB)
         Array Size : 5860145664 (5588.67 GiB 6000.79 GB)
      Used Dev Size : 3906763776 (1862.89 GiB 2000.26 GB)
        Data Offset : 262144 sectors
       Super Offset : 8 sectors
       Unused Space : before=262064 sectors, after=1024 sectors
              State : clean
        Device UUID : 8c959d62:3b9c1eac:6f8d7d92:13454ab4
    
        Update Time : Sun May 10 04:15:59 2015
           Checksum : 1c5f5282 - correct
             Events : 108804
    
             Layout : left-symmetric
         Chunk Size : 512K
    
       Device Role : Active device 1
       Array State : AA.. ('A' == active, '.' == missing, 'R' == replacing)
    /dev/sdh1:
              Magic : a92b4efc
            Version : 1.2
        Feature Map : 0x0
         Array UUID : a87dfb70:2ecd03f9:ee62b434:fc637218
               Name : m08002-lin:data2gb
      Creation Time : Mon Sep  2 12:48:02 2013
         Raid Level : raid5
       Raid Devices : 4
    
     Avail Dev Size : 3906764800 (1862.89 GiB 2000.26 GB)
         Array Size : 5860145664 (5588.67 GiB 6000.79 GB)
      Used Dev Size : 3906763776 (1862.89 GiB 2000.26 GB)
        Data Offset : 262144 sectors
       Super Offset : 8 sectors
       Unused Space : before=262064 sectors, after=1024 sectors
              State : clean
        Device UUID : df6b9eab:ea3c6e3a:47858e6d:1eb0783d
    
        Update Time : Sat May  9 23:10:06 2015
           Checksum : 57f1e4b2 - correct
             Events : 108796
    
             Layout : left-symmetric
         Chunk Size : 512K
    
       Device Role : Active device 2
       Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
    /dev/sdi1:
              Magic : a92b4efc
            Version : 1.2
        Feature Map : 0x0
         Array UUID : a87dfb70:2ecd03f9:ee62b434:fc637218
               Name : m08002-lin:data2gb
      Creation Time : Mon Sep  2 12:48:02 2013
         Raid Level : raid5
       Raid Devices : 4
    
     Avail Dev Size : 3906764800 (1862.89 GiB 2000.26 GB)
         Array Size : 5860145664 (5588.67 GiB 6000.79 GB)
      Used Dev Size : 3906763776 (1862.89 GiB 2000.26 GB)
        Data Offset : 262144 sectors
       Super Offset : 8 sectors
       Unused Space : before=262064 sectors, after=1024 sectors
              State : active
        Device UUID : fbc64ec7:a97a36c1:69cc3812:37878af1
    
        Update Time : Sat Dec  7 12:43:00 2013
           Checksum : 507acca4 - correct
             Events : 83904
    
             Layout : left-symmetric
         Chunk Size : 512K
    
       Device Role : Active device 3
       Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)



```

---

### Post by darkod on 2015-05-11
Hold on. How many members did you have in the array, 4 or 5? Because you keep mentioning 5 devices and trying to assemble it with 5 devices but your last examine results say Raid Devices 4.

---

### Post by tgalati4 on 2015-05-11
It's possible that *mdadm* would not update the out-of-date devices until the spare was rewritten.  Since this pool is relatively small (2 TB of data, 2 TB free), I would wait longer for the spare to finish then try the force assemble.  

What are the SMART parameters of the drives that are out-of-date?  Perhaps they are having physical problems which would make assembly non-trivial.

---

### Post by darkod on 2015-05-11
Maybe I am misunderstanding the situation but in the first post I don't see a spare mentioned anywhere. If a spare existed from the start (if the array layout was 4+1), it should have activated immediately when the first disk failed. If a spare was added after the first failed disk, I don't see that mentioned directly. Nor the commands.
If a spare was added after the second failed disk, that is not the right way to go. You can't even add a spare when the array is already failed (not degraded, failed).

So lets wait for the OP to explain instead of making assumptions. That's why I don't want to suggest commands to run until he gives more info about the array layout. Because the --examine results say 4 devices, not 5.

---

### Post by OrcLex on 2015-05-12
Previously the raid consited of 4 devices and then I added a 5th spare device. This is when the raid crashed the first time. I think it has not finished syncing to 5 drives. I could re-assemble the raid and backup data after trying to give *mdadm* all 5 devices that should be used for the raid. I could access the raid, resyncing started again and I was doing backups until the next crash happend when reading bad blocks on one physical drive.

> **tgalati4 said:**
> It's possible that *mdadm* would not update the out-of-date devices until the spare was rewritten.  Since this pool is relatively small (2 TB of data, 2 TB free), I would wait longer for the spare to finish then try the force assemble.

Hm, then I should see rebuilding in */proc/mdstat*, shouldn't I? But there is nothing...

At least one drive has bad blocks, physically bad sectors. When I'm home again I can get SMART output. But that's not the problem - I can live with some non-readable files as long as I know which files are broken and I can backup the other files. I just need to reassemble the raid a last time - readonly is sufficient...


As you can find above after assembling [*mdadm --assemble --force --verbose /dev/md127 /dev/sde1 /dev/sdf1 /dev/sdg1 /dev/sdh1 /dev/sdi1*]
- that looks good for me to re-assemble the raid md127 (4 devices and 1 spare):

```
mdadm: /dev/sde1 is identified as a member of /dev/md127, slot -1.
mdadm: /dev/sdf1 is identified as a member of /dev/md127, slot 3.
mdadm: /dev/sdg1 is identified as a member of /dev/md127, slot 1.
mdadm: /dev/sdh1 is identified as a member of /dev/md127, slot 2.
mdadm: /dev/sdi1 is identified as a member of /dev/md127, slot 0.
```  

but 

```
mdadm: added /dev/sdg1 to /dev/md127 as 1
mdadm: added /dev/sdh1 to /dev/md127 as 2 (possibly out of date)
mdadm: added /dev/sdf1 to /dev/md127 as 3 (possibly out of date)
mdadm: failed to add /dev/sde1 to /dev/md127: Device or resource busy
mdadm: added /dev/sdi1 to /dev/md127 as 0
mdadm: /dev/md127 assembled from 2 drives - not enough to start the array
```

**sde1** is spare, as you can see in the last output *mdadm --examine /dev/sd[efghi]1* from my first thread.
/dev/md127 is assembled from 2 drives but not using the out-of-date drives. Shouldn't force the parameter *--force* mdadm to use out-of-date drives?
So how can I assemble them now or how can I clear the out-of-date status?

---

### Post by darkod on 2015-05-12
Before trying to force anything, there is something I don't like. If you compare the second CODE section from your first post and your last post, the raid members position is reported differently. Why and how would it change it? Running a wrong assemble command?
In your first post the order is f-g-h-i and in the last post it's i-g-h-f. Were you swapping hdd cables maybe? So the disks changed letters?

I wouldn't bother adding the spare to assemble right now. Until you bring the array up it is worthless anyway. I would stick with --assemble with only the 4 disks and make sure you use the correct order when putting them into the command (although I think mdadm can figure that out). If you wanna try, try adding --force --run to --assemble. That would be the next step if it doesn't start with only --force.

---

### Post by tgalati4 on 2015-05-12
Your situation illustrates one of the problems with RAID5, failure of 2 physical drives during a syncing operation which causes the entire pool to fail.  It's possible that /proc/mdstat was not updated because *mdadm* was performing an internal consistency check and never got to update the status.

What was the reason for adding the spare disk drive?  Had the RAID5 pool failed previously?  The fact that the RAID5 started to resync after reassembling seems consistent with an intermittent disk failure (perhaps heat or power supply problem).  Adding the 5th disk could have pushed the power supply over the limit.

Another thing to consider, if one disk has bad blocks, that disk's controller will attempt to move those sectors to reserve sectors and that could mess up the timing of the RAID5 striping.  This could cause some operations to take a really long time and result in further corruption of the RAID by forced rebooting.

---

### Post by darkod on 2015-05-12
There is something wrong with the superblocks on the devices. If you look at the examine results, sdf1 and sdg1 for Array State say AA.. (two active devices, two missing), while sdh1 and sdi1 say AAAA (like all devices are good). Even though they say they are part of the same array, the four partitions have different info for Array State. It should be the same...

It seems that somehow at one point 2 devices started acting diffrently from the other 2 and the superblock is out of sync now. I believe all forms of --assemble try to assemble using the superblock values, I am not sure you can activate the array at this point using only assemble. Not if I am right and the superblock difference is actually stopping it to assemble and activate.

What you could try, and is little risky, is to zero the superblocks on all four partitions and use --create with --assume-clean (DO NOT use it without this option). Just --create is used to create new blank array, which starts immediate initial sync. When you add --assume-clean you tell the command not to do the initial sync which keeps the data currently on the partitions. mdadm should be smart enough to use this data.

This process is a bit risky, probably because it says to zero the superblocks, but is the last option to try when all else fails and you are sure the data on the disks is more or less good (you said you don't mind small corruption). Anyway, you are running out of options...

Very important part of --create is to use the correct device order. When creating new array this doesn't matter but when trying to assemble existing one, it is very important because raid data can be read only when the devices are in the same order as original. I already mentioned that examine outputs seem to show devices "changing order", which might be because of switching sata cables etc... Make sure you know the order of the partitions if you decide to do this. Lets assume the original order was sdf1-sdg1-sdh1-sdi1. Also first make sure you stop any array that might be running after your attempts to assemble it. The procedure would be like:
```
sudo mdadm --stop /dev/md127 (or /dev/md0)
sudo mdadm --zero-superblock /dev/sd[fghi]1
sudo mdadm --create /dev/md0 --level=5 --raid-devices=4 --assume-clean /dev/sdf1 /dev/sdg1 /dev/sdh1 /dev/sdi1
```

Be very careful with the commands, and verify partition names few times before trying this. The order needs to be exactly right, DO NOT forget that. If you are unsure of the original partition order better not to try it.

I hope it can help you. If the array starts wait to see if there is any sync going on, and you can add sde1 right away after any sync finishes. There should not be initial sync but there might be some sync between the disk data I guess. To add sde1 is simple and if any disk is failed sde1 will be used automatically. No need to do anything usually.
```
sudo mdadm /dev/md0 --add /dev/sde1
```

---

### Post by OrcLex on 2015-05-13
I'm not sure if device names have switched. Anyway I figured out the pysical device sde (spare) and removed it. Now the remaining devices are **sde1 sdf1 sdg1** and **sdh1**. So the names have changed again.

After rebooting the raid looks like this (inactive with all 4 devices):

```
# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md127 : inactive sdh1[4](S) sdf1[1](S) sde1[0](S) sdg1[3](S)
      7813529600 blocks super 1.2
       
unused devices: <none>

```

I cannot run the raid:
```
# mdadm --run --verbose /dev/md127 
mdadm: failed to start array /dev/md/m08002-lin:data2gb: Input/output error

```

2 devices are removed:
```
# mdadm --detail --verbose /dev/md127 
/dev/md127:
        Version : 1.2
  Creation Time : Mon Sep  2 12:48:02 2013
     Raid Level : raid5
  Used Dev Size : 1953381888 (1862.89 GiB 2000.26 GB)
   Raid Devices : 4
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Sun May 10 04:15:59 2015
          State : active, FAILED, Not Started 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 512K

           Name : m08002-lin:data2gb
           UUID : a87dfb70:2ecd03f9:ee62b434:fc637218
         Events : 108804

    Number   Major   Minor   RaidDevice State
       0       8       65        0      active sync   /dev/sde1
       1       8       81        1      active sync   /dev/sdf1
       4       0        0        4      removed
       6       0        0        6      removed
```


Now stopping the raid...
```
# mdadm --stop --scan
# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
unused devices: <none>

```

...and re-assembling again in the same device order:
```
# mdadm --assemble --verbose /dev/md127 /dev/sde1 /dev/sdf1 /dev/sdg1 /dev/sdh1
mdadm: looking for devices for /dev/md127
mdadm: /dev/sde1 is identified as a member of /dev/md127, slot 0.
mdadm: /dev/sdf1 is identified as a member of /dev/md127, slot 1.
mdadm: /dev/sdg1 is identified as a member of /dev/md127, slot 2.
mdadm: /dev/sdh1 is identified as a member of /dev/md127, slot 3.
mdadm: added /dev/sdf1 to /dev/md127 as 1
mdadm: added /dev/sdg1 to /dev/md127 as 2 (possibly out of date)
mdadm: added /dev/sdh1 to /dev/md127 as 3 (possibly out of date)
mdadm: added /dev/sde1 to /dev/md127 as 0
mdadm: /dev/md127 assembled from 2 drives - not enough to start the array.

```

It should be the same as above - assembled from 2 devices but there is not /dev/md127:

```
# cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
unused devices: <none>

```

Any ideas, why this is happening? :confused:



So I think I'm running out of options now and maybe I have to try the risky way. Do I have to zero the superblock from all drives? Maybe I can backup the superblocks?
What would *--update=summaries* do? Will it clear the status failed and out-of-date?

I'm not sure about the original order of the devices but isn't the slot number the original ordering number? So the original order here should be **sde sdf sdg sdh**?

```
mdadm: looking for devices for /dev/md127
mdadm: /dev/sde1 is identified as a member of /dev/md127, slot 0.
mdadm: /dev/sdf1 is identified as a member of /dev/md127, slot 1.
mdadm: /dev/sdg1 is identified as a member of /dev/md127, slot 2.
mdadm: /dev/sdh1 is identified as a member of /dev/md127, slot 3.
mdadm: added /dev/sdf1 to /dev/md127 as 1
mdadm: added /dev/sdg1 to /dev/md127 as 2 (possibly out of date)
mdadm: added /dev/sdh1 to /dev/md127 as 3 (possibly out of date)
mdadm: added /dev/sde1 to /dev/md127 as 0

```

If I zero the superblocks and create a new raid using the *assume-clean* parameter, can I mount the filesystem on the raid directly?

---

### Post by darkod on 2015-05-13
Yes, the slot number shows the order. So it should be sde1 sdf1 sdg1 sdh1 in this case.

Another thing crossed my mind. Since you seem sure one of the disks has major bad sectors damage, you can consider assembling/creating the array without this disk, using the 'missing' placeholder instead. A damaged disk is of no much use anyway. Plus that might help minimize problems with corrupted data on that disk due to bad sectors. The downside is that array assembled like that will have a missing member from the start which makes it risky for failure if another disk fails. And you do say a second disk is having some issues too (otherwise the array would have be online and working with a single disk failed).

You said you took the new disk out (formerly sde) but you might consider connecting it again so that you can add it to the array ASAP in case you assemble with the bad disk missing. Also be careful if connecting the new disk again will move the disk labels. Usually BIOS reports the disks in the order of the ports so it's best to populate starting from port 0 (or 1, depending on motherboard labeling). That way the newest disks are "at the end".

Anyway, assuming just the four disks from your post and assuming lets say sdg is the one with many bad sectors, the command to recreate the array would be:
```
sudo mdadm --create /dev/md127 --level=5 --raid-devices=4 --assume-clean /dev/sde1 /dev/sdf1 missing /dev/sdh1
```

That should assemble it.

As for keeping the superblock info before zeroing it, what I found on google with a quick search says something like:
```
sudo mdadm --examine /dev/sd[efgh]1 >> raid.info
```

That should basically save the examine output in the file raid.info in the current folder (if you are running that from your home folder, the file should be there). It's not some great procedure for backup but it will have all the details that examine outputs which is enough to recreate arrays again.

Well, that's about it. Now it's your turn to try this...

For example, read quickly through this thread: [http://ubuntuforums.org/showthread.php?t=2276699](http://ubuntuforums.org/showthread.php?t=2276699). The owner just reported that the --create --assume-clean managed to get his data back. He was not having any luck with --assemble too, like you. He does mention some data was lost/corrupted but I don't think it was a result of the command. He had corruption and loss of the data to start with I think...

---

### Post by OrcLex on 2015-05-15
I could access my raid and backup my files!!

There were two devices with bad sectors and I knew that the raid will crash again while resyncing when it wants to read or write to bad sectors.
So I decided to build up a degraded raid that is not syncing. I cleared all superblocks and created the raid leaving out one damaged device with

```
mdadm --create /dev/md127 --level=5 --raid-devices=4 --assume-clean /dev/sde1 /dev/sdf1 /dev/sdg1 missing
```

I could mount md127 and access all data directly without doing anything else.
Thank you very much for your help!!

---

### Post by darkod on 2015-05-15
Great!!! Now that you have the data backed up on different location, you can think if you want to add a new disk (maybe the one you took out earlier, with zeroed superblock too), and see if maybe it could finish the sync after adding the disk without another disk failing.

If it does fail and brings the raid down, you can do this. Forget about both disks with bad sectors. You have two good disks plus one spare and the data backed up. You can buy another disk and create a new raid5 array, and put the data back. Or something like that...

---

