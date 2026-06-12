---
title: "Is there a size limit on Linux raid autodetect?"
date: 2013-07-17
forum: Server Platforms
---

### Post by 1clue on 2013-07-17
Hi,

Been messing with adding a raid-1 pair to my workstation.  I have it now, but I'm looking at it and it shows half the size I expected.

I have two 3T drives.  I formatted each to be a single partition type 'fd', "Linux raid autodetect".

Now, after I have it set up I get this:
```


$sudo vgs
  VG     #PV #LV #SN Attr   VSize   VFree  
  hddvg1   1   5   0 wz--n- 698.63g 435.15g
  rd1vg1   1   0   0 wz--n- 746.39g 746.39g
  ssdvg1   1   1   0 wz--n- 223.07g 204.44g


$sudo fdisk -l /dev/sdb

Disk /dev/sdb: 3000.6 GB, 3000592982016 bytes
90 heads, 3 sectors/track, 21705678 cylinders, total 5860533168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x345a0cea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               3  1565565871   782782934+  fd  Linux raid autodetect
Partition 1 does not start on physical sector boundary.


```

What's up with that?  Is there some limit on the size of a RAID partition?

I've never used an array with drives this big before, and I don't see anything when I search on limits.

Thanks.

---

### Post by CharlesA on 2013-07-17
What are you using for the RAID? I've always just formatted my RAID partition as ext4, not this "linux raid autodetect" thing.

I have a RAID5 in mdadm and it doesn't exhibit that effect, even though I'm not using LVM.

What does this return?

```
df -h
```

With that being said, I haven't run into any limits.. yet. I'm running a mdadm RAID5 with 3 x 2TB drives and a hardware RAID6 with 5 x 3TB drives, and both show their full capacity.

EDIT: I just checked my LVM and mine looks "OK":

```
root@Thor:~# vgs
  VG   #PV #LV #SN Attr   VSize VFree
  Thor   1   1   0 wz--n- 8.19t    0

```

---

### Post by 1clue on 2013-07-17
I'm just doing what the mdadm instructions say:  In fdisk, give the partition type FD which is linux raid autodetect, instead of 83 for a plain Linux partition or 82 for a swap partition.  There's no ext4 for a partition type AFAICT.

Some of the logical volumes on the RAID array will be ext4, some will probably be xfs, maybe some others.

df -h won't return anything for these yet, there are no volumes on the array; it's just a volume group.

You've checked the size of your volume group, the logical volumes list is 'lvs'

---

### Post by CharlesA on 2013-07-18
> **1clue said:**
> I'm just doing what the mdadm instructions say:  In fdisk, give the partition type FD which is linux raid autodetect, instead of 83 for a plain Linux partition or 82 for a swap partition.  There's no ext4 for a partition type AFAICT.

Some of the logical volumes on the RAID array will be ext4, some will probably be xfs, maybe some others.

df -h won't return anything for these yet, there are no volumes on the array; it's just a volume group.

You've checked the size of your volume group, the logical volumes list is 'lvs'

Huh. I followed this [tutorial]("http://zackreed.me/articles/38-software-raid-5-in-debian-with-mdadm") when I created my mdadm setup, maybe that will help?

Thanks for the command. I'm pretty new to LVM. :p

---

### Post by 1clue on 2013-07-18
Pretty close to what I used, the raid setup is the same.  I'm using raid1 though.  I didn't notice in there where they set partition type, that's kinda necessary if you have boot or root on the raid partition, but I guess I don't in this case so maybe it doesn't matter.

I didn't have my partitions magically resize until I created my array.

LVM is awesome.  Lets you resize "partitions" on the fly (volumes in LVM), create new ones, delete old ones, whatever.  Generally you don't need to reboot for it.  If you intend to use virtualization in any serious sort of way, then it's indispensible IMO.  You can put your guest hard disk in as a host logical volume, which then lets you manage it, grow it, whatever as needed from the host.

Not sure what to do about the raid sizing.  I'll think about it.

---

### Post by steeldriver on 2013-07-18
AFAIK the 'Linux RAID autodetect' is just a flag that says the block device is part of (or is going to be part of) a software RAID array - until you actually create the array fdisk will continue to see only the individual block device(s) and will report their sizes as such

Once you create the array, then *as well as* the 3TB /dev/sdb1, you should see an entry like /dev/md0 which will show the size of the *array *(although fdisk doesn't really handle this stuff well, you would be better using parted)

---

### Post by 1clue on 2013-07-18
Exactly.  The 'linux raid autodetect' is a partition type the same as 'linux' or 'fat32'.  If your boot loader and kernel understand RAID, it also lets your helps your kernel identify partitions which are probably involved in an array, and lets it assemble arrays that way.  Not a problem in my case, I'm booting off an ssd.

Parted wasn't around when I started using Linux.  I haven't gotten around to figuring it out yet.

Creating raid arrays is not my problem, been there and done that often enough that I contemplate not looking at the documentation.  Just never with big drives.  I've only done it with 750g or smaller drives.

I'm positive that before the mdadm --create command I had 3T partitions on /dev/sdb and /dev/sdd.  After the create and the long wait, I discovered that they're much smaller.  I'm trying to figure out why.

---

### Post by steeldriver on 2013-07-18
well I'm not sure exactly what you're asking since your fdisk output doesn't seem to show any RAID, however it looks like sdb was formatted with a MBR partition table (based on the fact that fdisk complains about GPT and tells you to use parted instead) - so that may explain why you're not 'seeing' all of the 3TB?

---

### Post by 1clue on 2013-07-18
Yes it is, I've just reformatted with parted and am rebuilding my RAID.

Thanks.  Thread solved.

---

