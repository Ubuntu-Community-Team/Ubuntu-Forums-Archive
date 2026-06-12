---
title: "Software RAID (mdadm) problems after updates"
date: 2008-07-19
forum: Server Platforms
---

### Post by CooLGeeK on 2008-07-19
I just wanted to share my experience in case somebody encounters the same problems I had to face.

I created a RAID 5 array with 3 devices.
(/dev/md0 is composed of /dev/sdb1 /dev/sdc1 and /dev/sdd1)
One of the devices eventually failed and was automatically removed from the array.
Since 2 of 3 raid devices are present the raid array is still working and ok.
However, suddenly one of the 2 remaining raid device failed/disconnected.

PROBLEM 1:
After such incident, mdadm refuses to start my raid array /dev/md0.

SOLUTION 1:
Since I am confident that there is nothing wrong with the 2 remaining raid devices, I went on to assemble the raid array.
```
sudo mdadm --assemble /dev/md1 -f /dev/sdb1 /dev/sdc1
```

After that the raid array is up and running again but with only 2 of 3 devices working for RAID 5 array.

I checked the array by:
```
sudo mdadm --detail /dev/md1
```

It says that the raid array is clean but degraded. It's degraded because the RAID 5 array is missing 1 device component.

I went to check the file system of the RAID array:
> sudo fsck /dev/md0

I added another disk and created a Linux Raid partition on it with identical sizes as the other raid devices using the "fdisk" command.
I used the blocks/cylinders NOT the mega/gigabytes to set the size of the new partition (/dev/sdd1).

To add the newly created partition, I did:
> sudo mdadm --manage /dev/md1 --add /dev/sdd1

After which I added the output of:
> sudo mdadm --detail --scan
to the file /etc/mdadm/mdadm.conf. I removed all the old RAID array definitions in the file.


PROBLEM 2:
After updating my system (Ubuntu 8.04.1), my RAID array won't start.
When I tried manually assembling the RAID array, mdadm says that the raid devices does not exist.
I checked the /dev/disk/by-id directory and INDEED! the device file pertaining to the disks EXIST! but the device files pertaining to the Linux RAID partitions DO NOT EXIST!.

SOLUTION 2:
Since the problem is missing device files (like /dev/sdd1), I recreated the device files by opening each disk with the fdisk command:
> sudo fdisk /dev/sdd
and I just press the **P** key to list the partitions.
when I see that there is indeed a Linux RAID partition I press the **W** key.

After doing this for all the disks with missing device files for Linux RAID partitions, I go on to re-assemble the RAID array:
> sudo mdadm --assemble /dev/md1 /dev/sdb1 /dev/sdc1 /dev/sde1

Hope this helps! :)

---

### Post by CooLGeeK on 2008-07-21
Ok guys, I figured out why there are missing device nodes OR device file (i.e. no /dev/sdb1 even if /dev/sdb exists and there is a partition inside it) pertaining to my Linux raid partitions...

When I started making a raid array I used RAID 5 to include /dev/sdb1, /dev/sdc1 and /dev/sdd1 which are Linux raid partitions occupying the entire disks /dev/sdb, /dev/sdc and /dev/sdd, respectively.

But then, ONE of the disks failed physically. This is still fine because I'm using RAID (the purpose of it is to preserve data despite disk failures).

Unfortunately for me another disk failed NOT because of disk failure but because of loose cable connection.
After that, the raid array would not reconstruct anymore.
I secured the cable connections and added a brand new disk.

This is where I made an unfortunate error. I re-assembled the raid array using the disks (/dev/sdb and /dev/sdc) instead of the raid partitions (/dev/sdb1 and /dev/sdc1).

After realizing my mistake, I then correctly re-assembled the raid array using the raid partitions (/dev/sdb1 and /dev/sdc1) but I have to use --force option.
Yes, I can re-assemble the raid array using only two (2) of the three (3) drives because I was using RAID 5.

After that I keep having two (2) md device (/dev/md0 and /dev/md1).

I FOUND OUT: 
There is a conflict between the two (2) md devices because there is a raid superblock both on the raid partitions and disk containing the raid partition.
mdadm automatically creates md devices or raid array by scanning the disk partitions in the system for raid superblocks (because this is the setting in /etc/mdadm/mdadm.conf).
Because of this conflict, the device nodes for my raid partitions do not exist, hence, the error:

Looking at ...
```
ls -l /dev/sd*
```
There is really NO DEVICE NODES for my raid partitions! Hence, the raid array cannot be automatically assembled.

After successfully extracting my data from the raid (for safety), I used the --zero-superblock option on the disks containing the raid partitions...
```
sudo mdadm --zero-superblock /dev/sdb
sudo mdadm --zero-superblock /dev/sdc
```
The first time I ran the above commands there were no output.
When I try to run them again, the following appears:
> mdadm: Unrecognised md component device - /dev/sde

This only means that there is no more md or raid superblock on the disk itself but only on the partitions.

After that, the device nodes for my raid partitions now appears and the md device which should not appear does not appear anymore.


I will continue experimenting and I will keep you updated...
That's all for now.

---

### Post by fjgaude on 2008-07-21
Yep, one little mistake can lead us to learning what we don't know.

One way, I think, to clear everything on a drive is:

```
sudo dd if=/dev/urandom of=/dev/sd[n]
```

Such may take some time but if the zero-superblock doesn't work this will.

Please do keep us informed as to how you are doing.

---

