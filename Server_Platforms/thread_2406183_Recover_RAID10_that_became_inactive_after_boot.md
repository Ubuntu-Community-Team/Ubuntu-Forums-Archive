---
title: "Recover RAID10 that became inactive after boot"
date: 2018-11-17
forum: Server Platforms
---

### Post by sifounakis on 2018-11-17
I recently created a Raid10 with four 3TB drives, got everything working, copied all my files over, and the raid became inaccessible after a reboot.


I've been doing a bunch of searching on this and I'm not sure how to proceed.




_**Background:**_
I had a working RAIDZ with three 3TB drives and decided to switch to a RAID10 with four 3TB drives (I bought one more).


I copied all the files over to a spare drive, disbanded the RAIDZ, assembled the RAID10, copied my files back, and everything seemed to work.


I thought I had rebooted and checked that everything still worked, but once I rebooted, the RAID10 became inactive and I can't seem to make it active again.




_**Mistakes I think I made:**_
1. Not exhaustively testing everything while I still had the backups. (Definitely.)
2. I used the raw 4th drive and forgot to repartition the 3 existing drives before creating the RAID10.
3. I created the RAID10 following a guide that pointed at the raw drives [sdb, sdc, sdd, sdf] instead of at partitions [sdb1, sdc1, sdd1, sdf1] (NOTE: The backup USB hard drive was sde, but after rebooting, the drives are listed sdb-sde).




_**Diagnostics:**_
This is scary because it only sees one of the 4 drives:


```
cat /proc/mdstat
    Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
    md0 : inactive sdd[3](S)
          2930134488 blocks super 1.2
    
    unused devices: <none>
```




This is scary because it lists the drives as a zfs_member:


```
lsblk -o NAME,SIZE,FSTYPE,TYPE,MOUNTPOINT
    NAME     SIZE FSTYPE            TYPE MOUNTPOINT
    loop0    2.3M squashfs          loop /snap/gnome-calculator/238
    loop1   34.6M squashfs          loop /snap/gtk-common-themes/818
    loop2    2.3M squashfs          loop /snap/gnome-calculator/260
    loop3  140.9M squashfs          loop /snap/gnome-3-26-1604/70
    loop4   42.1M squashfs          loop /snap/gtk-common-themes/701
    loop5    2.2M squashfs          loop /snap/gnome-calculator/222
    loop6    3.7M squashfs          loop /snap/gnome-system-monitor/57
    loop7   14.5M squashfs          loop /snap/gnome-logs/45
    loop8   87.9M squashfs          loop /snap/core/5662
    loop9     13M squashfs          loop /snap/gnome-characters/124
    loop10  87.9M squashfs          loop /snap/core/5548
    loop11    13M squashfs          loop /snap/gnome-characters/139
    loop12  14.5M squashfs          loop /snap/gnome-logs/43
    loop13    13M squashfs          loop /snap/gnome-characters/117
    loop14  34.2M squashfs          loop /snap/gtk-common-themes/808
    loop15 140.7M squashfs          loop /snap/gnome-3-26-1604/74
    loop16   3.7M squashfs          loop /snap/gnome-system-monitor/54
    loop17  87.9M squashfs          loop /snap/core/5742
    loop18   3.7M squashfs          loop /snap/gnome-system-monitor/51
    loop19  14.5M squashfs          loop /snap/gnome-logs/40
    sda    111.8G                   disk
    &#9500;&#9472;sda1 103.8G ext4              part /
    &#9500;&#9472;sda2     1K                   part
    &#9492;&#9472;sda5     8G swap              part [SWAP]
    sdb      2.7T                   disk
    &#9500;&#9472;sdb1   2.7T zfs_member        part
    &#9492;&#9472;sdb9     8M                   part
    sdc      2.7T                   disk
    &#9500;&#9472;sdc1   2.7T zfs_member        part
    &#9492;&#9472;sdc9     8M                   part
    sdd      2.7T linux_raid_member disk
    sde      2.7T                   disk
    &#9500;&#9472;sde1   2.7T zfs_member        part
    &#9492;&#9472;sde9     8M                   part
```




Is there hope that if I can get them considered to be part of a linux_raid_member that I can get things working?


Or is the reality that the system thought it was still ZFS and zapped the superblocks?




Examine shows:


```
mdadm --examine /dev/sd[bcdefghijklmn]
    /dev/sdb:
       MBR Magic : aa55
    Partition[0] :   4294967295 sectors at            1 (type ee)
    /dev/sdc:
       MBR Magic : aa55
    Partition[0] :   4294967295 sectors at            1 (type ee)
    /dev/sdd:
              Magic : a92b4efc
            Version : 1.2
        Feature Map : 0x1
         Array UUID : 96442f9a:57385f26:b9e90509:0e527d07
               Name : sifounakis.com:0  (local to host sifounakis.com)
      Creation Time : Wed Nov 14 23:12:52 2018
         Raid Level : raid10
       Raid Devices : 4
    
     Avail Dev Size : 5860268976 (2794.39 GiB 3000.46 GB)
         Array Size : 5860268032 (5588.79 GiB 6000.91 GB)
      Used Dev Size : 5860268032 (2794.39 GiB 3000.46 GB)
        Data Offset : 264192 sectors
       Super Offset : 8 sectors
       Unused Space : before=264112 sectors, after=944 sectors
              State : clean
        Device UUID : 250241b1:d1832e3c:ed412124:954a20f2
    
    Internal Bitmap : 8 sectors from superblock
        Update Time : Fri Nov 16 20:14:28 2018
      Bad Block Log : 512 entries available at offset 32 sectors
           Checksum : 5ea53bb5 - correct
             Events : 30006
    
             Layout : near=2
         Chunk Size : 512K
    
       Device Role : Active device 3
       Array State : AAAA ('A' == active, '.' == missing, 'R' == replacing)
    /dev/sde:
       MBR Magic : aa55
    Partition[0] :   4294967295 sectors at            1 (type ee)
```




_**I tried assembling with no luck:**_


```
mdadm --assemble /dev/md0 /dev/sd[bcde]
    mdadm: Cannot assemble mbr metadata on /dev/sdb
    mdadm: /dev/sdb has no superblock - assembly aborted
```




Same result with the --force option.




_**I have not tried recreating the RAID10:**_

I have not tried recreating the RAID10 for fear of making irrecoverable changes (if it's not already), but this page seems to make it seem like it might be a possibility:
[https://ubuntuforums.org/showthread.php?t=1972690](https://ubuntuforums.org/showthread.php?t=1972690)




_**What can I do?**_
Does anyone have any suggestions for things I should try or options I should consider?


Thank you so much for taking the time to look this over and help.

---

### Post by darkod on 2018-11-17
One question (although it's too late to undo it now).
Did you create new blank partition tables on the disks or you simply used them to create mdadm array? I am just wondering how come that ZFS metadata is still there...

In this situation you don't seem to have much options. I would search online if there is a procedure to remove ZFS metadata without deleting all data on the disk. If you could achieve that, then recreating the mdadm array with --assume-clean option will keep all data intact. And it should not revert to zfs after a reboot (because you cleaned up the metadata).

When recreating the array you need to use the same disk order as the first time, but I assume you know it. And the --assume-clean will tell mdadm not to delete data already on the disks.

So you main problems seems to be getting rid of zfs metadata actually. And hoping that the reboot didn't reassemble the "old zfs array" in any way, deleting your data in the process.

---

### Post by sifounakis on 2018-11-17
Thanks for the quick response darkod. Your response made me feel a lot more confident in my assessment of the situation and to proceed.

The --assume-clean option worked and I'm in the process of copying all the data off of the drives (that'll take about 20 hours).


_**Additional information for others stumbling on this:**_

_RAIDZ Metadata:_
I had originally made sure to delete the RAIDZ pool before creating the RAID 10 since I was afraid it would come back and do nasty things if ZFS got access to the disks first. When I couldn't access the RAID 10, I checked "zpool status" and it said there were no available pools, so I was hopeful that ZFS hadn't touched the drives. When I saw the zfs_member label, I figured that metadata might have been causing Linux to interpret the drives differently and look for the superblocks in the wrong place, but I was afraid to jump to the --clean-option and cause any (more?) permanent damage.

Even with the partition tables and metadata a mess the way it was, I believe the RAID ignores all that and just looks at the drive itself as a block of memory, which is why the --clean-option works. The steps to create the RAID 10 also clarify that the partition tables will be meaningless once you create the RAID, which I think is why I thought everything would be ok the first time around. I forgot to take into account that the operating system would need to understand the metadata before it hands the disks to the RAID and that would be where things would break during boot.


_Drive order:_
As darkod mentioned, you definitely need to know the order of the drives for this to work, otherwise the raid would think the wrong data was striped or different data was a mirror.

Luckily, I knew the order of the drives (even though they got moved around because the USB hard drive was removed) based on the metadata and physical layout of the motherboard connections

```
Original   -->   New
===============
/dev/sdb (3TB,ZFS)  -->  /dev/sdb
/dev/sdc (3TB,ZFS)  -->  /dev/sdc
/dev/sdd (3TB,ZFS)  -->  **/dev/sde**
/dev/sde (2TB,USB)  --> removed
/dev/sdf  (3TB,NEW)  --> **/dev/sdd**
```

I had originally used the following command to create the RAID 10:
```
sudo mdadm --create --verbose /dev/md0 --level=10 --raid-devices=4 /dev/sdb /dev/sdc /dev/sdd /dev/sdf
```

But I needed to use the following code to recreate the RAID 10:
```
sudo mdadm --create --verbose --assume-clean /dev/md0 --level=10 --raid-devices=4 /dev/sdb /dev/sdc /dev/sde /dev/sdd
```

Once the RAID was created, I mounted the drive as read-only (not that it would have mattered much if the data was actually gone, but it was just a piece of mind thing) and found the data in tact.

After that, it was just a matter of keeping calm, setting up the next steps, and waiting for the data to copy.


_Next steps:_

[LIST=1]
[*]Copy the data off the drives (about 20 hours)
[*]Verify copied data
[*]Destroy the RAID 10
[*]Create new blank partition tables on the disks
[*]Recreate and sync the RAID 10
[*]Set the RAID 10 to be reassembled at boot
[*]Create a test file on the RAID 10
[*]Reboot the machine
[*]Verify everything works as expected
[*]Copy all files back to the RAID 10
[*]Finally stop worrying
[/LIST]


Thanks again, darkod!

Wish I could buy you a beer!

---

### Post by darkod on 2018-11-17
Cool, great that you could recreate it to copy the data.

When creating the new gpt partition tables (it has to be gpt because you want big 3TB partition on the disks) don't forget to create the 3TB partitions this time. And use that to create the new array.

Cheers.

---

### Post by sifounakis on 2018-11-17
> [COLOR=#000000]When creating the new gpt partition tables (it has to be gpt because you want big 3TB partition on the disks) don't forget to create the 3TB partitions this time. And use that to create the new array.[/COLOR]

Thanks for this follow-up! I'll make sure to do just that.

I think we can mark this thread as [SOLVED].

---

### Post by darkod on 2018-11-17
You can mark it as solved in Thread Tools above the first post.

---

### Post by sifounakis on 2018-11-17
Done. Thanks again!

---

