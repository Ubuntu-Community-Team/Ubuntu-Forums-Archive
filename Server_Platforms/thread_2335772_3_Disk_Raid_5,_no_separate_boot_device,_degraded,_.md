---
title: "3 Disk Raid 5, no separate boot device, degraded, advice on getting it back up"
date: 2016-09-01
forum: Server Platforms
---

### Post by jim.hitch on 2016-09-01
Hi

Very amateur linux / server person here. My server has done me proud for the last 5 or 6 years, but have recently lost one disk. I wasn't aware until after the event of the default setting BOOT_DEGRADED=false, so now device boots into initramfs. Looking through the forums I get the impression that as there is no separate boot device I will find it very difficult, if not impossible to boot in a degraded state. 

My other option, therefore is to remove the failed disk (sdc) and add a new one. However, though the array responds to mdadm commands when it comes to examining the ok disks (sda & sdb), it  is failing to add a new disk (sdd) as it can't find any array information (due to the loss of sdc?). Equally, I seem unable to label sdc as failed before removal as mdadm can't see sdc.

Thinking through the options, the only solution I have to this is to turn off the machine, open the case and physically swap the present sdc disk for a new one in the same place. Will this work?

btw, I do have it all backed up (around 750 gb), but it's online, so would take a while to restore!

Would really appreciate some help on this.

---

### Post by darkod on 2016-09-01
I'm confused. You mention sdd but without taking the machine offline? Did you already add a new disk (physically) or not?

If you did, it should be fairly easy to add it to the array. But first reply to this question and we'll take it from there.

And whatever you do, don't panic and be careful. There a re plenty of cases where the situation went from good to much worse because of running a wrong mdadm command. :)

---

### Post by jim.hitch on 2016-09-01
Darko

Sorry, I've not been clear. I'm not totally au fait with RAID, sometime ago (a year or two?), I added another disk which was to be used as a spare. I can't for the life of me remember if I ever added it as a spare. So yes, that's sdd, and it's connected, But (and I'm at work now, so not at the machine) it's not showing in mdadm examine (or whatever the command is to display the /dev/md0 details), so either it's not added, never was, or has also failed.

> And whatever you do, don't panic and be careful. There a re plenty of cases where the situation went from good to much worse because of running a wrong mdadm command. 

Yes! I've been a linux user for around a decade, and have learnt that they hard way!

Jim

---

### Post by darkod on 2016-09-01
OK. To view the array details (this should show any spares), and assuming the array is /dev/md0:
```
sudo mdadm -D /dev/md0
```

The --examine is used on members (partitions), not on whole arrays. That gives you details about each partition, like:
```
sudo mdadm --examine /dev/sda1
sudo mdadm --examine /dev/sdb1
etc
```

If the machine is not booting degraded, do you have it booted now? I understand yes... Otherwise you will either need to try and boot it once by adding manual option in grub line, or get a ubuntu desktop live cd/usb and work from live mode. You can use live mode to look into the machine too.

If you have it booted now, when you get home post the output of:
```
cat /proc/mdstat
sudo mdadm -D /dev/md0
sudo parted -l (that's small L)
```

That should be enough to start.

---

### Post by jim.hitch on 2016-09-02
OK, here we go:

```
root@sysresccd /root % cat /proc/mdstat  
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sda1[0](S) sdb1[1](S)
      1953519616 blocks super 1.2

```

Below it says **raid0**, is that just because it's only seeing two disks? If I run ```
mdadm --examine /dev/sda1
``` for either sda1 or sdb1 I get info which gives correct info of **raid5**.

```
root@sysresccd /root % mdadm -D /dev/md0
/dev/md0:
        Version : 1.2
     Raid Level : raid0
  Total Devices : 2
    Persistence : Superblock is persistent

          State : inactive

           Name : sysresccd:0  (local to host sysresccd)
           UUID : 23a2926c:a5af0f28:c5ef95a8:f07a1a3d
         Events : 2414

    Number   Major   Minor   RaidDevice

       -       8        1        -        /dev/sda1
       -       8       17        -        /dev/sdb1

```

You'll notice below that sdd has a gpt partition table, that's because I did that since this all happened, before I wised up and posted here! sdd has never been actively used for data.

```
root@sysresccd /root % parted -l  
Model: ATA WDC WD10EARS-00Y (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary               boot, raid


Model: ATA WDC WD10EZRX-00L (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary               raid


Model: ATA WDC WD10EARS-00Y (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary               raid


Model: ATA WDC WD10EADS-00M (scsi)
Disk /dev/sdd: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name     Flags
 1      1049kB  1000GB  1000GB               primary  raid


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label
Model: ATAPI iHAS124 B (scsi)                                             
Disk /dev/sr0: 482MB
Sector size (logical/physical): 2048B/2048B
Partition Table: unknown
Disk Flags: 

```

Thanks again for your help on this.

---

### Post by darkod on 2016-09-02
Can you please post the --examine for all, sda1, sdb1 and sdc1. I need to see something there...

It is not a problem that sdd has gpt table, with only difference that you would not be able to install grub on its MBR. So you have a choice to delete the gpt table and put msdos table, or keep it as it is. You said there is no data on it, so redoing the table doesn't change anything. And it will make the disk equal as the other raid members.

---

### Post by jim.hitch on 2016-09-03
> It is not a problem that sdd has gpt table, with only difference that you would not be able to install grub on its MBR. So you have a choice to delete the gpt table and put msdos table, or keep it as it is. You said there is no data on it, so redoing the table doesn't change anything. And it will make the disk equal as the other raid members.

Yes, that would be my preference too. I know I'm being lazy, but could you give me the command for that? (3 kids under 7 all missing their movies and tv shows here!)

> **darkod said:**
> Can you please post the --examine for all, sda1, sdb1 and sdc1. I need to see something there...

```
mdadm --examine /dev/sda1
/dev/sda1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 23a2926c:a5af0f28:c5ef95a8:f07a1a3d
           Name : sysresccd:0  (local to host sysresccd)
  Creation Time : Tue Feb 25 21:22:04 2014
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 1953519616 (931.51 GiB 1000.20 GB)
     Array Size : 1953518592 (1863.02 GiB 2000.40 GB)
  Used Dev Size : 1953518592 (931.51 GiB 1000.20 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
   Unused Space : before=1968 sectors, after=1024 sectors
          State : active
    Device UUID : 5819fbdb:f8d256fa:9a5c42d5:15c28d2e

    Update Time : Thu Jul 28 11:41:12 2016
       Checksum : 6674f8d0 - correct
         Events : 2414

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : AAA ('A' == active, '.' == missing, 'R' == replacing)
```

```
root@sysresccd /root % mdadm --examine /dev/sdb1       
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 23a2926c:a5af0f28:c5ef95a8:f07a1a3d
           Name : sysresccd:0  (local to host sysresccd)
  Creation Time : Tue Feb 25 21:22:04 2014
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 1953519616 (931.51 GiB 1000.20 GB)
     Array Size : 1953518592 (1863.02 GiB 2000.40 GB)
  Used Dev Size : 1953518592 (931.51 GiB 1000.20 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
   Unused Space : before=1968 sectors, after=1024 sectors
          State : active
    Device UUID : 1edf8330:1fd4314b:c2de68c4:a3015af8

    Update Time : Thu Jul 28 11:41:12 2016
       Checksum : c4cb8173 - correct
         Events : 2414

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 1
   Array State : AAA ('A' == active, '.' == missing, 'R' == replacing)
```

```
root@sysresccd /root % mdadm --examine /dev/sdc1
mdadm: No md superblock detected on /dev/sdc1.
```

```
root@sysresccd /root % mdadm --examine /dev/sdd1
mdadm: No md superblock detected on /dev/sdd1.
```

---

### Post by darkod on 2016-09-03
Weird, it looks like sdc1 has no superblock. Either completely failed or somehow lost. However the disk seems to be read correctly by both parted and --examine.

First the easy thing. The partitioning. To list the partitions on sda in MiB (I prefer working in units MiB) you can use:
```
sudo parted /dev/sda unit MiB print
```

Note down the partition #1 start and end MiB. Then on sdd:
```
sudo parted /dev/sdd
unit MiB   (set units to work with)
print   (make sure you are working on sdd before deleting the table!!!)
mklabel msdos   (creates new msdos table)
mkpart primary <start> <end>   (create partition from start to end in MiB, identical as on sda)
set 1 raid on   (set raid flag on)
quit   (quit parted prompt)
```

That's it, after you should have sdd1 identical as on sda1/sdb1/sdc1.

Now for the raid... As you see in the --examine both sda1 and sdb1 have same Events counter (2414) which is very optimistic about assembling the array. Let see:
```
sudo mdadm --stop /dev/md0   (stop current not working array)
sudo mdadm --assemble --verbose /dev/md0 /dev/sda1 /dev/sdb1
```

That will try assembling it with only sda1 and sdb1 and it should work because two members are enough for raid5. Try that first and let me know how it goes, there are other things to try if it fails.

---

### Post by jim.hitch on 2016-09-03
OK, that's done, this is what I got on the final command:

```
root@sysresccd /root % mdadm --assemble --verbose /dev/md0 /dev/sda1 /dev/sdb1
mdadm: looking for devices for /dev/md0
mdadm: /dev/sda1 is identified as a member of /dev/md0, slot 0.
mdadm: /dev/sdb1 is identified as a member of /dev/md0, slot 1.
mdadm: added /dev/sdb1 to /dev/md0 as 1
mdadm: no uptodate device for slot 4 of /dev/md0
mdadm: added /dev/sda1 to /dev/md0 as 0
mdadm: /dev/md0 assembled from 2 drives - not enough to start the array while not clean - consider --force.
```

I'm writing from the sysresccd environment in the machine itself, so I'll post this and then try and reboot.

---

### Post by jim.hitch on 2016-09-04
Nope, that didn't work. I'll post the output of some of the commands you suggested above and see what, if anything, has changed.

First, though, some extra info from the boot sequence which I haven't mentioned before.

First up, on boot I get this:

```
Error: failure reading sector 0x808 from 'hd1'.
```

Second, here is a picture of the end of the failed boot sequence:

[IMG]https://s4.postimg.org/k9vv1nl7h/IMG_20160904_044744175.jpg[/IMG]

Any use?

---

### Post by jim.hitch on 2016-09-04
Has anything changed:

```
root@sysresccd /root % mdadm -D /dev/md0
/dev/md0:
        Version : 1.2
     Raid Level : raid0
  Total Devices : 2
    Persistence : Superblock is persistent

          State : inactive

           Name : sysresccd:0  (local to host sysresccd)
           UUID : 23a2926c:a5af0f28:c5ef95a8:f07a1a3d
         Events : 2414

    Number   Major   Minor   RaidDevice

       -       8        1        -        /dev/sda1
       -       8       17        -        /dev/sdb1
```

```
root@sysresccd /root % cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sda1[0](S) sdb1[1](S)
      1953519616 blocks super 1.2
```

```
root@sysresccd /root % parted -l
Model: ATA WDC WD10EARS-00Y (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary               boot, raid


Model: ATA WDC WD10EZRX-00L (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary               raid


Model: ATA WDC WD10EARS-00Y (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary               raid


Model: ATA WDC WD10EADS-00M (scsi)
Disk /dev/sdd: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  1000GB  1000GB  primary               raid


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label
Model: ATAPI iHAS124 B (scsi)                                             
Disk /dev/sr0: 482MB
Sector size (logical/physical): 2048B/2048B
Partition Table: unknown
Disk Flags: 
```

```
root@sysresccd /root % mdadm --examine /dev/sda1
/dev/sda1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 23a2926c:a5af0f28:c5ef95a8:f07a1a3d
           Name : sysresccd:0  (local to host sysresccd)
  Creation Time : Tue Feb 25 21:22:04 2014
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 1953519616 (931.51 GiB 1000.20 GB)
     Array Size : 1953518592 (1863.02 GiB 2000.40 GB)
  Used Dev Size : 1953518592 (931.51 GiB 1000.20 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
   Unused Space : before=1968 sectors, after=1024 sectors
          State : active
    Device UUID : 5819fbdb:f8d256fa:9a5c42d5:15c28d2e

    Update Time : Thu Jul 28 11:41:12 2016
       Checksum : 6674f8d0 - correct
         Events : 2414

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 0
   Array State : AAA ('A' == active, '.' == missing, 'R' == replacing)
```

```
root@sysresccd /root % mdadm --examine /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 23a2926c:a5af0f28:c5ef95a8:f07a1a3d
           Name : sysresccd:0  (local to host sysresccd)
  Creation Time : Tue Feb 25 21:22:04 2014
     Raid Level : raid5
   Raid Devices : 3

 Avail Dev Size : 1953519616 (931.51 GiB 1000.20 GB)
     Array Size : 1953518592 (1863.02 GiB 2000.40 GB)
  Used Dev Size : 1953518592 (931.51 GiB 1000.20 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
   Unused Space : before=1968 sectors, after=1024 sectors
          State : active
    Device UUID : 1edf8330:1fd4314b:c2de68c4:a3015af8

    Update Time : Thu Jul 28 11:41:12 2016
       Checksum : c4cb8173 - correct
         Events : 2414

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 1
   Array State : AAA ('A' == active, '.' == missing, 'R' == replacing)
```

Should I try the --force command as suggested? If so, can you give me the command just to make sure I don't get it wrong?

Many thanks again for your time on this.

---

### Post by darkod on 2016-09-04
Hmmm... Yes, the --force was the next thing to try. Just add it to the previous one, so the command would be:
```
sudo mdadm --stop /dev/md0   (in case it's running)
sudo mdadm --assemble --force --verbose /dev/md0 /dev/sda1 /dev/sdb1
```

Also, few things to note from the screenshot you posted.

One, you seem to be having LVM on top of the raid too. I didn't know that but it shouldn't be a problem, we need to get the array up first anyway. Is that correct, you have LVM on top of md0?

In the boot sequence it complains of sdc, so if you manage to assemble the array with the above, better to first try adding sdd1 to it, instead of sdc1. Do you agree? In such case, and assuming the above assembles md0, it would simply be:
```
sudo mdadm /dev/md0 --add /dev/sdd1
cat /proc/mdstat
```

The second command is to check the status of the array from time to time and see if it finished the rebuild after adding sdd1. Do not reboot until the rebuild is finished, I think it will not load the OS until it has all three members.

Another thing is getting me worried, the message that it has some read errors on hd1 too. If I remember correctly, the HDDs start counting from hd0 so hd1 would be sdb. Now, you already have issues reported with sdc but if also sdb is failing on you, it might be problematic to even finish the rebuild after adding sdd1. If sdb1 fails, you are stuck again with one half-rebuilt member (sdd1) and one failed one (sdb1). So a raid5 array will fail when two members are missing.

But right now I don't see another option except the above, to try the assemble with force and add sdd1 as third member. And hope for the best...

On a side note, this setup is strange to me, did it work like this from first installation? I was under the impression you can't have the boot files on raid5, and that you need at least raid1 device for /boot if not the whole /. Maybe it works, I have simply never tried to have root on raid5.

---

### Post by jim.hitch on 2016-09-04
Ok, now I'm getting a little excited...

> The second command is to check the status of the array from time to time and see if it finished the rebuild after adding sdd1. Do not reboot until the rebuild is finished, I think it will not load the OS until it has all three members.

The --force and --add command appear to have worked, the array is rebuilding now.

> Another thing is getting me worried, the message that it has some read errors on hd1 too. If I remember correctly, the HDDs start counting from hd0 so hd1 would be sdb. Now, you already have issues reported with sdc but if also sdb is failing on you, it might be problematic to even finish the rebuild after adding sdd1. If sdb1 fails, you are stuck again with one half-rebuilt member (sdd1) and one failed one (sdb1). So a raid5 array will fail when two members are missing.

Eek, let's hope that it works. However, as I said above, this is all backed up.

> But right now I don't see another option except the above, to try the assemble with force and add sdd1 as third member. And hope for the best...

... my fingers are crossed.

> On a side note, this setup is strange to me, did it work like this from first installation? I was under the impression you can't have the boot files on raid5, and that you need at least raid1 device for /boot if not the whole /. Maybe it works, I have simply never tried to have root on raid5.

I first built this same set up about 5 years ago, and it looks like the rebuild dates from 2014. As I'm not an computer guy in my day job, I tend to have bursts of activity building something like this and then forget most of what I've learnt subsequently. So, I would have built it the way that I 'thought' was best according to what I found online. I vaguely remember the idea of a separate /boot device, but it doesn't look as if I went with it. So yes, it does seem to work! 

I've been meaning to update the build for some time, if I get this recovery sorted, I can then move on to that, these days a separate SDD for the OS looks like the option.

I'll post the results of the rebuild when I have them. And what to do about sdc?

---

### Post by darkod on 2016-09-04
Once you have the OS back up, I would run a smart test on sdc to confirm it is good/bad. We'll find some tutorial for that, there are plenty. The package I think is smartmontools which installs tools to use the HDD SMART data and let you know if a disk is good or bad.

If it turns out to be good you can add it to md0 to be as spare, if you want.
If sdc is bad, you can consider whether you want to buy a new one and add it as spare, or just remove sdc and leave the system as it is.

---

### Post by jim.hitch on 2016-09-04
It booted into the OS, and appears to be working now, though it kicked out the same errors on boot with hd1 and then sdc1. I've run short SMART tests, which is a great tool, but now will look at next steps. 

btw, there IS a root partition, it is in the LVM, not sure where I got that idea from.

I'll mark this as solved now.  Many many thanks for your time and patience.

---

### Post by darkod on 2016-09-04
Of course there is a root partition, linux can't function without one. :) There are various setups possible, but one thing is sure: there has to be root partition.

Glad you got it sorted out. Good job.
 
If you are in a position to do so, I would do a full backup on external hdd or something, just in case until you are sure the disks/array is all good.

---

