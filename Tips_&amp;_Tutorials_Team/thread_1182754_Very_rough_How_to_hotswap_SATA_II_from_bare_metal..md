---
title: "Very rough: How to hotswap SATA II from bare metal."
date: 2009-06-09
forum: Tips &amp; Tutorials Team
---

### Post by dmizer on 2009-06-09
Just looking for some input on this and looking for some testers as a few of the spots are a bit vague.

I figured out how to add a new SATA II drive to my server while the server was still running. It took quite a bit of effort and lots of searching to find the answers I needed, so I thought I'd consolidate things.

1) Attach the drive
You'll note that this does nothing other than powers on the drive, your system doesn't know it exists yet.

2) Install scsiadd
I actually used a script called rescan-scsi-bus.sh instead of scsiadd, but I would like to know if scsiadd could be used instead (the script I found doesn't seem to be fully functional, so I'm leery of it).
```
scsiadd -s
```
If scsiadd doesn't work, I'll post the script (or you can google it).

3) Check dmesg
Your drive should now be discovered by the system. You'll see something like this in your dmesg:
```
[80585.974290] sd 8:0:0:0: [sdf] 1953525168 512-byte hardware sectors (1000205 MB)
```
Where "sdf" is the device location (/dev/sdf).

4) Partition the drive with fdisk or gparted

5) Format the drive
```
sudo mkfs.ext3 -b 4096 /dev/sdf1
```

6) Discover the new partition
```
sudo partprobe
```

7) Mount the drive manually or via fstab

7.1) Find the drive's UUID:
```
sudo blkid
```
```
/dev/sdf1: UUID="e90277e9-0659-40b7-bd5f-a5b79ee80947" SEC_TYPE="ext2" TYPE="ext3"
```

7.2) Add the drive to fstab
```
UUID=e90277e9-0659-40b7-bd5f-a5b79ee80947 /media/backup  ext3    relatime,errors=remount-ro 0 1
```

[noparse]8)[/noparse] Change drive ownership (so it's not root)
```
sudo chown -R dmizer:dmizer /dev/sdf1
```

Removing the drive:
Before you remove the drive, you'll need to know the scsi ID of the drive. To do this, you can check dmesg:
```
[ 3486.579096] sd [COLOR="Red"]8:0:0:0:[/COLOR] [sdf] Synchronizing SCSI cache
```

1) Unmount the drive

2) Remove the drive from the scsi table:
```
scsiadd -r [COLOR="Red"]8 0 0 0[/COLOR]
```

You'll hear the drive spin down and click off. Then you can remove it.

Readding the drive:
1) Attach the drive

2) Readd the drive to the scsi table:
```
scsiadd -a 8 0 0 0
```

3) Mount the drive.

---

