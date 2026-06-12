---
title: "raid trouble?"
date: 2016-08-22
forum: Server Platforms
---

### Post by maclenin on 2016-08-22
Just a "quick" couple of questions about a raid1 setup on a clean desktop install of xubuntu 16.04. 

A. Background

Disks /dev/sdb and /dev/sdc were part of a RAID + LVM configuration in the immediately previous (12.04) install.

The current raid1 array is being used for data only.

The current system resides on a separate disk /dev/sda and is not part of this raid configuration.

I created the raid array and added the ext4 file system to /dev/md0:
```
sudo mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdb /dev/sdc
sudo mkfs.ext4 /dev/md0

```

I created a mount point and added an entry to fstab:
```
# /dev/md0
UUID=x-x-x-x-x /home/server/shared ext4 defaults 0 0
```

I scanned array details into the mdadm.conf file:
```
sudo mdadm --detail --scan /dev/md0 >> /etc/mdadm/mdadm.conf 
```

A mdadm --detail /dev/md0 shows:
```
/dev/md0:
        Version : 1.2
  Creation Time : Sun Aug 21 17:50:26 2016
     Raid Level : raid1
     Array Size : 976631488 (931.39 GiB 1000.07 GB)
  Used Dev Size : 976631488 (931.39 GiB 1000.07 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

  Intent Bitmap : Internal

    Update Time : Mon Aug 22 09:38:30 2016
          State : clean 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           Name : server:0  (local to host server)
           UUID : a:a:a:a
         Events : 2576

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       32        1      active sync   /dev/sdc

```

A mdadm --examine of /dev/sdb shows:
```
/dev/sdb:
          Magic : same as sdc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : a:a:a:a
           Name : server:0  (local to host server)
  Creation Time : Sun Aug 21 17:50:26 2016
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 1953263024 (931.39 GiB 1000.07 GB)
     Array Size : 976631488 (931.39 GiB 1000.07 GB)
  Used Dev Size : 1953262976 (931.39 GiB 1000.07 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=48 sectors
          State : clean
    Device UUID : b:b:b:b

Internal Bitmap : 8 sectors from superblock
    Update Time : Mon Aug 22 09:38:30 2016
  **Bad Block Log : 512 entries available at offset 72 sectors**
       Checksum : b - correct
         Events : 2576


   Device Role : Active device 0
   Array State : AA ('A' == active, '.' == missing, 'R' == replacing)
```

A mdadm --examine /dev/sdc shows:
```
/dev/sdc:
          Magic : same as sdb
        Version : 1.2
    Feature Map : 0x1
     Array UUID : a:a:a:a
           Name : server:0  (local to host server)
  Creation Time : Sun Aug 21 17:50:26 2016
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 1953263024 (931.39 GiB 1000.07 GB)
     Array Size : 976631488 (931.39 GiB 1000.07 GB)
  Used Dev Size : 1953262976 (931.39 GiB 1000.07 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=48 sectors
          State : clean
    Device UUID : c:c:c:c

Internal Bitmap : 8 sectors from superblock
    Update Time : Mon Aug 22 09:38:30 2016
  **Bad Block Log : 512 entries available at offset 72 sectors**
       Checksum : c - correct
         Events : 2576


   Device Role : Active device 1
   Array State : AA ('A' == active, '.' == missing, 'R' == replacing)
```

B. Questions

1. In performing fsck.ext4 on devices /dev/sdb and /dev/sdc, I receive the following identical output, for both (sd**b** is shown). A "bad block" reference appears, again (as it did in --examine). Are these bad signs? Should this be reparable?
```
e2fsck 1.42.13 (17-May-2015)
ext2fs_open2: Bad magic number in super-block
fsck.ext4: Superblock invalid, trying backup blocks...
fsck.ext4: Bad magic number in super-block while trying to open /dev/sd**b**

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>
```

2. A "mounted" icon representing the raid array (dev/md0) appears on my desktop. The array is also mounted at the fstab-described mount point. When I click on the desktop icon, it seems to open to the raid array. When I umount /dev/md0 - BOTH the desktop icon and fstab-reference to the raid array are unmounted. Can I remove the desktop icon? Does the raid array's presence on the Desktop as well at its fstab mount point represent a problem?

Thanks for any guidance!

---

### Post by maclenin on 2016-08-23
An update with regard to question 1.

SMART self-tests of both drives... 

sudo smartctl -t short /dev/sd*
sudo smartctl -t long /dev/sd*

..."Completed without error".

Question 2. re: Desktop mounted "raid icon" still perplexes....

Thanks, again, for any guidance!

---

### Post by steeldriver on 2016-08-23
I'm not surprise that fsck gets confused when you point it to /dev/sd[ab] - remember the filesytem is on the *array*, not on the underlying disk members

What is the output of 

```

sudo blkid -c /dev/null

```

---

### Post by darkod on 2016-08-24
The desktop icon seems to be kind of a shortcut, so having it together with the fstab mount should not be a problem. Like you said, when you unmount the icon is also gone.

But it is strange for a shortcut to appear on its own. You didn't mention you created it. It might be a result mounting in /home. Usually the best place to mount is a completely new folder inside root or a subfolder inside /mnt. You should avoid mounting in /media or /home. But it will work.

And another thing, you used the full disks (/dev/sdb and /dev/sdc) instead of using partitions. With mdadm SW raid, it's best to create partitions on the disks (one or more depending how many arrays you want) and use them to create the arrays (/dev/sdb1 and /dev/sdc1). Not the disks directly. But it will work this way too... Only in the future if a disk fails and you want to replace it with a new one, if the new is only few MiB smaller than the current ones, it will not be accepted. You can't add a smaller disk/partition into existing raid array. And HDDs of "same size" are not IDENTICALLY same...

---

### Post by maclenin on 2016-08-24
Thanks, folks!

A. **steeldriver!**

Here's the requested output of sudo blkid -c /dev/null
```
/dev/sda1: UUID="a1-a1-a1-a1" TYPE="ext2" PARTUUID="sameas5-01"
/dev/sda5: UUID="a5-a5-a5-a5-a5-a5-a5" TYPE="LVM2_member" PARTUUID="sameas1-05"
/dev/sdc: UUID="same-uuid-as-sd-[bc]" UUID_SUB="unique-id-to-sd-c" LABEL="server:0" TYPE="linux_raid_member"
/dev/sdb: UUID="same-uuid-as-sd-[bc]" UUID_SUB="unique-id-to-sd-b" LABEL="server:0" TYPE="linux_raid_member"
/dev/mapper/xubuntu--vg-root: UUID="unique-id-to-vg-root" TYPE="ext4"
/dev/mapper/xubuntu--vg-swap_1: UUID="unique-id-to-vg-swap" TYPE="swap"
```

Notes:
1. Before posting my OP, I ran sudo mdadm --stop and --remove on /dev/md0 to - in my mind - remove the raid array overhead and more "cleanly" run fsck and smartctl on /dev/sd[bc] - though I see TYPE= "linux_raid_member" in the [bc] blkid output....
2. Does /dev/sd[bc] being a "linux_raid_member"  explain (away) the **Bad Block Log : 512 entries available at offset 72 sectors** output from sudo mdadm --examine /dev/sd[bc]?
3. Does it make sense for me to sanitise my UUIDs, when posting them here?

B. **darkod!**

Correct, I did NOT create the Desktop shortcut. Perhaps, the raid array from the previous install (12.04) was recognised in the new install (16.04) - before I reformatted it - and mounted, by default, in /media - as the mount point created previously had been removed via the new install (16.04)? Then when I created the new mount point within /home - I didn't notice a change - as the array remained visible on the Desktop - mounted via /home now, instead of via /media? 

I hear you - and will follow your suggestion with regard to mounting in / or /mnt - though I was never aware of the "auto-mount-icon-on-the-Desktop" feature when creating a mount point in /home (probably because this is the first time I've created a mount point in /home) - though I (think I) understand the logic re: /media.

If I were to remove the two disks [bc] from the raid array and reformat them as separate disks - would they appear as 2 separate drives / icons on the Desktop - auto-mounted in /media (by label / UUID)?

I also hear you re: creating at least 1 partition on the raid disks. I have generally accepted the defaults when creating partitions, however, you seem to be indicating that I should confirm (via fdisk, for example) that the size of the single "1" partition, even on two "same-sized" disks is identical - before creating (rebuilding) the array? What if the replacement disk / partition (sdf1, for example, in a raid 1 array originally comprised of sdd1 and sde1) is LARGER than the failed (sde1) disk? Is the replacement logic, to map sdd1 (active) onto / into sdf1 (replacement)? Therefore, since sdf1 is LARGER than sdd1, sdd1 will still map / fit / sync "into" the LARGER sdf1?

Thanks, again!

---

### Post by maclenin on 2016-08-24
So - trial by combat....

1. First, and with hearty thanks due to [**rubylaser**]("https://ubuntuforums.org/showthread.php?t=1646982&p=10247465#post10247465")...

```
sudo umount /dev/md0
sudo mdadm --stop /dev/md0
sudo mdadm --zero-superblock /dev/sdb1
sudo mdadm --zero-superblock /dev/sdc1
sudo rm mdadm.conf
```

...I was able to recover from a raid-induced warm welcome to emergency mode - in the wake of disruptive reformat testing (and system restart) before **completely removing any trace of the raid array**....

In addition to the fundamentals provided by rubylaser, I also commented out reference to the raid device in fstab (after a fortuitous journey down journalctl -xb way)....

1.a. The disruptive format testing - I did reformat sd[bc] - using fdisk - adding a partition (1) and the ext4 file system (using mkfs.ext4) to both disks. Both disks now appear as separate 1TB icons on my desktop - and can both be mounted via /media (and differentiated by UUID)....

2. My speculation is that the issues I am reporting are format/raid management-related (i.e. human error) and not hardware issues....

Thanks for any additional comments!

---

### Post by darkod on 2016-08-25
Now you lost me completely... I thought you had important data on the raid and it's being used, and you just destroyed it. :)

Do you actually have a problem or you are just playing around?

Concerning the desktop shortcuts, you are also posting in the wrong subsection for that because the ubuntu server version by default has no GUI (hence no desktop) and as far as I know it does not automatically mount any new disks, USB or SATA.

The ubuntu desktop on the other hand, is designed to be more "user friendly" and mounts USB sticks and disks in /media as soon as you plug them in. And I think it does create desktop shortcut. But I've seen that for USB, not for SATA. On mu PC I have ubuntu desktop 14.04 and 3 HDDs. The 2 HDDs that do not contain the OS are not automounted until you click on them in the File Explorer (Nautilus). And no desktop shortcut is created... So, I don't know what's happening with your machine and if this is important for you at all.

For the raid clean up, yes, it is always recommended to zero the superblock on any partition/device that has been used in mdadm raid and is removed from it. Especially if you want to use it for new mdadm array.

And the disk size I was mentioning... If you use the whole disk like /dev/sdb and later want to replace it with /dev/sdc which turns out to be few MBs smaller, mdadm will not allow you because it can't introduce a smaller member in the array. On the other hand if you create a partition sdb1 leaving the last 15-20MBs unused (unpartitioned) and sdc is little smaller, that still allows you to create sdc1 with same size as sdb1 and mdadm to accept it. That's why on raid disks I always leave the last 15-20MBs unpartitioned.

If the new disk is bigger, no problem. But if it's smaller, then you have a problem when using whole disks in mdadm.

If you compare disks size in MBs of different manufacturers/models you will see that they are not identical in MBs size.

---

### Post by maclenin on 2016-08-25
**darkod!**

I HAD important data on the raid array - which I moved to a backup drive - offline - before commencing the clean install of xubuntu 16.04 on a box containing drives sda, sdb, sdc....

I have now installed xubuntu 16.04 OS on sda, separately and distinctly from the data-only raid array (comprised of sd[bc]). 

As I began to reformat and reconstitute the "clean" raid array - on the clean install of xubuntu 16.04 - I ran into the issues I described in my OP:

1. Bad block errors

2. Icon on the Desktop

I posted my thread here (Server Platforms) because I wanted to understand the possible implications of these (potentially raid-related) issues - and test them and resolve them - before deploying the newly-constituted raid array.

I think I now understand BOTH issues as, perhaps, being related to human error / gaps in my understanding.

The Bad block errors (as far as fsck is concerned) have been resolved by a complete and thorough "zeroing" of the previous raid array (/dev/md0 consisting of /dev/sdb1 and /dev/sdc1).
```
sudo umount /dev/md0
sudo mdadm --stop /dev/md0
sudo mdadm --zero-superblock /dev/sdb1
sudo mdadm --zero-superblock /dev/sdc1
sudo rm mdadm.conf
```
If the previous array has an entry in fstab, that entry must be removed or commented out (#) and then revised after creating a new array (or prepare for a welcome to emergency mode on restart).

The Icon on the Desktop is almost certainly related to what you describe regarding the auto-mounting tendencies of (xubuntu) desktop vs. (xubutnu) server - as well as my own (flawed) /home directory mounting strategy.

I will also take care when formatting disks for use as raid devices - to make certain they are partitioned - at least once - and sized in the manner you describe (i.e. like for like)!

Gracias!

---

### Post by darkod on 2016-08-25
Yes, as explained above, the fsck was complaining because you were running it against the disks and they did not have the filesystem. In mdadm raid the md device has the filesystem. That part is clear.

As for the icons, do you mean an actual desktop icon, or an icon in the Unity bar (the left side bar introduced in ubuntu in 12.04 I think)? It is normal to have the icon in the Unity bar, but the partition is not mounted at that moment. If you open Nautilus you will see that you can't use it under /media. But if you click on the partition (either in Unity or Nautilus), it mounts it at that moment.

Anyway if you plan to use the disks permanently, mount them under /mnt or similar and see how that reacts in the Unity bar.

If you have resolved your queries don't forget to mark the thread as Solved. You can do that in Thread Tools above the first post.

---

### Post by maclenin on 2016-08-25
Agreed - all clear re: fsck - and partitioning, formatting, creating and disassembling raid1 arrays....

As for the icons - I am using **[COLOR="#6699FF"]X[/COLOR]**ubuntu - so NO Unity (for me) - a simply "standard" desktop environment - the icons (mounted and unmounted) are appearing on the Desktop workspace itself (not in a sidebar or panel)....

If I plug in an external USB device - a Desktop icon appears - it mounts automatically - in /media/home_directory_name/USB_label - and is also accessible via its "mounted" icon on the Desktop, which shows the path /media/home_directory_name/USB_label.

If I format an internal SATA hard drive - a Desktop icon appears - it does NOT mount automatically - though, if manually mounted, it appears in /media/home_directory_name/SATA_UUID - and is also accessible via its "mounted" icon on the Desktop, which shows the path /media/home_directory_name/SATA_UUID.

If I create a folder - say ~/xyz - within ~/ - the folder ~/xyz will be accessible only via the ~/ directory.

If I create a mount point - say ~/shared - within ~/ - the device mounted at ~/shared will be accessible via the ~/shared directory as well as via its "mounted" icon on the Desktop, which shows the path ~/shared.

Yes - I will mount my raid array either in /mnt or some other / location - per your guidance (and create a Desktop shortcut, if required)!

Do you have any other "NB"?

Again, gracias!

---

### Post by darkod on 2016-08-25
Ah, yes, you mentioned xubuntu but I wasn't sure if it carries Unity or not.

In such case it seems like a feature of xubuntu to show the mounted HDDs on the Desktop. :)

I think you have it all covered now, I can't think of anything else to add...

---

### Post by maclenin on 2016-08-25
That's a wrap, then!

Thanks for the patient guidance!

Will mark as [SOLVED]!

Notes, to follow - as relevant.

Cheers!

---

### Post by maclenin on 2016-08-26
Not quite out of the woods as I reconstruct my raid array, it seems (re: bad blocks)?

A mdadm --examine of /dev/sdb1 shows:
```
/dev/sdb1:
          Magic : same as sdc1
        Version : 1.2
    Feature Map : 0x1
     Array UUID : a:a:a:a
           Name : server:0  (local to host server)
  Creation Time : Fri Aug 26 23:04:18 2016
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 1953263024 (931.39 GiB 1000.07 GB)
     Array Size : 976631488 (931.39 GiB 1000.07 GB)
  Used Dev Size : 1953262976 (931.39 GiB 1000.07 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=48 sectors
          State : active
    Device UUID : b:b:b:b

Internal Bitmap : 8 sectors from superblock
    Update Time : Fri Aug 26 23:21:58 2016
  **Bad Block Log : 512 entries available at offset 72 sectors**
       Checksum : b - correct
         Events : 215

   Device Role : Active device 0
   Array State : AA ('A' == active, '.' == missing, 'R' == replacing)
```

A mdadm --examine /dev/sdc1 shows:
```
/dev/sdc1:
          Magic : same as sdb1
        Version : 1.2
    Feature Map : 0x1
     Array UUID : a:a:a:a
           Name : server:0  (local to host server)
  Creation Time : Fri Aug 26 23:04:18 2016
     Raid Level : raid1
   Raid Devices : 2

 Avail Dev Size : 1953263024 (931.39 GiB 1000.07 GB)
     Array Size : 976631488 (931.39 GiB 1000.07 GB)
  Used Dev Size : 1953262976 (931.39 GiB 1000.07 GB)
    Data Offset : 262144 sectors
   Super Offset : 8 sectors
   Unused Space : before=262056 sectors, after=48 sectors
          State : active
    Device UUID : c:c:c:c

Internal Bitmap : 8 sectors from superblock
    Update Time : Fri Aug 26 23:25:29 2016
  **Bad Block Log : 512 entries available at offset 72 sectors**
       Checksum : c - correct
         Events : 258

   Device Role : Active device 1
   Array State : AA ('A' == active, '.' == missing, 'R' == replacing)
```

Thanks, again, for any guidance!

---

### Post by maclenin on 2016-08-28
Perhaps, **Bad Block Log** is merely notice of its preparedness to record any...bad blocks...should need be....

sudo mdadm --examine-badblocks /dev/sdb1 shows:
```
Bad-blocks list is empty in /dev/sdb1
```

sudo mdadm --examine-badblocks /dev/sdc1 shows:
```
Bad-blocks list is empty in /dev/sdc1
```

Which strike me all as good signs?

---

