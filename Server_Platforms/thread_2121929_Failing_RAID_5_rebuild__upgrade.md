---
title: "Failing RAID 5 rebuild / upgrade"
date: 2013-03-03
forum: Server Platforms
---

### Post by tealio on 2013-03-03
I've been attempting to upgrade / rebuild a RAID 5 array since Wendnesday.  For those reading later on, it's Sunday now.

I'm trying to migrate my data from a 3x1TB to a 3x2TB.  I don't have enough SATA ports to have both arrays up, even if they're both running degraded with 2 drives each.

It has nearly rebuilt acouple of times, but it keeps failing near the end (around 99%).

I was able to catch the error message with dmesg | tail

```
[24817.339543] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[24817.344244] ata4.00: irq_stat 0x40000001
[24817.348939] ata4.00: failed command: READ DMA EXT
[24817.353637] ata4.00: cmd 25/00:00:f0:0b:d5/00:04:6c:00:00/e0 tag 0 dma 524288 in
[24817.353638]          res 51/40:2f:b1:0f:d5/00:00:6c:00:00/e0 Emask 0x9 (media error)
[24817.372326] ata4.00: status: { DRDY ERR }
[24817.377020] ata4.00: error: { UNC }
[24817.389240] ata4.00: configured for UDMA/133
[24817.393942] ata4: EH complete

```

If it fails again this time (I'm at 95.5%) I'm going to try to run the array degraded and copy over the data to a new 2TB RAID1 1x2TB.

If that works i'll then add another drive to the RAID1.  

I've read that converting a 2-disk RAID1 to a 3-disk RAID5 is possible.  When i get to that point i'll need some guidance.

Until then, any translation of the error messages would be appreciated.

---

### Post by darkod on 2013-03-03
Hold on. What is it that you are trying to do exactly? Move from 3x1TB to 3x2TB array?

If that is the case and your 3x1TB array is working fine at the moment, you don't need both arrays up at the same time in parallel. Use this article by the forum member rubylaser to replace all disks with bigger ones, one by one. This is VERY IMPORTANT, you replace them one by one and LET THE ARRAY SYNC before replacing the next disk. Do not just do it one after the other, It needs to fully sync before replacing the next disk.
[http://zackreed.me/articles/69-mdadm-replace-smaller-disks-with-larger-ones](http://zackreed.me/articles/69-mdadm-replace-smaller-disks-with-larger-ones)

---

### Post by tealio on 2013-03-03
That's what i started out trying... one of the disks is giving me read errors, and I'm not sure which one... it just finished the rebuild of the original array, so im back to square one, but... i think there's enough of a problem with one of these disks that i can't use it to rebuild onto a new disk.  I've tried twice, i think i removed different disks, but each time the rebuild failed with one new disk and 2 originals.  That's why i'm thinking about pulling a disk, and instead of rebuilding the array with a new larger disk, i can copy the data from the old disks to a new 1 disk RAID 1.  also, (i think) this leaves me able to just pop in those 3 original disks and they should all resync with data intact.  Not so sure they'll be left in a recoverable state if i replace one at a time... 

my resyncs on the old array with a new disk are taking about 8 hours.  so far i've waited thru this twice with a last second failure.  Then i had to rebuild the original disks, and that failed once too... so... my thinking at this point is to get all the data onto a new disk and then turn that into a new RAID5... That would at least take the failing disk out of the equation.

Is what i'm proposing just a bad idea?  Is there any way to tell which disk is giving read errors? I REALLY don't want to wait this out again just to have another failure...

---

### Post by darkod on 2013-03-03
If you suspect HW failure, try reading the SMART data using smartmontools. But I don't know all the options to use and to understand their results, you will have to google about using smartmontools. But it should be faster and most importantly safer than failing disks and see if the array gets rebuild.

After the smart results, and depending what they say, you might consider having two degraded raid5 arrays instead of thinking about raid1 for the new disks and then reshaping them to raid5. But you will need at least 4 sata ports for two degraded raid5 arrays (old array with two disks working, the new array created with two disks and missing member).

---

### Post by tealio on 2013-03-03
i thought about that too (the 2 degraded RAID5s)... I only have 4 SATA ports, and my OS is on one... so I'd have to do the copy in a live environment...

it actually seems like my best option as far as time goes... is there any reason to NOT do this in a live environment?

---

### Post by darkod on 2013-03-03
None that I can think of, except that it might last for hours to copy the data so the live session will have to be booted for hours and hopefully doesn't reboot.

---

### Post by tealio on 2013-03-03
just mounted the RAID and it said there were filesystem errors.  running fsck fixed the errors, but dmesg also contained errors like posted above.  does ata4 (as in the error) correlate to SATA port 4?  because if it does, i can make sure to remove that disk when i do the copy... or... i could risk it and try a one-at-a-time replacement again... thoughts?

---

### Post by tealio on 2013-03-03
ok... ran the SMART self-test and /dev/sdb failed with a read error ... so how do i identify which physical drive is /dev/sdb ?

*** EDIT *** 
nm... found my own answer: 

hdparm -i /dev/sdb will give me the serial number... compare to drive label

---

### Post by tealio on 2013-03-03
so I've identified the bad drive... should i do the one-drive-at-a-time starting by pulling /dev/sdb out first? or the live CD method with 2 degraded arrays?

---

### Post by darkod on 2013-03-03
I would do the one replacement at a time starting with sdb.

If you already used some of the new disks in mdadm don't forget to zero the superblock first before trying to add them to md0 so that the existing superblock info doesn't clash. The disk should be considered as "brand new" without any superblock on it.

---

### Post by tealio on 2013-03-03
OK... it's syncing in the new drive now at around 100000K/s.  i'll know something in a few hours... 

assuming it all goes well, once i've got all the 2tb drives in it'll still be a 2TB array.  just ```
mdadm /dev/md0 --grow --size=max
``` to increase the size of the array, then ```
resize2fs /dev/md0
``` to expand the filesystem. I'm not using partitions, so that should be all i have to do right?

---

### Post by darkod on 2013-03-03
Sounds right.

---

