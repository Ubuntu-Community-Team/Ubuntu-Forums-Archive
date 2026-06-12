---
title: "RAID - spurious 'device' appears spontaneously"
date: 2009-05-17
forum: Server Platforms
---

### Post by qajaq on 2009-05-17
I'm trying to set up a simple, 2-device, RAID-1 array to be used as the basis of a Kubuntu 9.04 file server, but I cannot get the RAID to remain intact.

I'm using two identically-sized (264 GB) partitions, sda7 and sdb3, on two identical SATA HDDs, both formatted to ext3 and flagged as RAID devices with gParted.

I can initially create, activate, and mount the RAID as follows.

```
mdadm -Cv /dev/md0 -l1 -n2 /dev/sda7 /dev/sdb3
mdadm -As /dev/md0
mount /dev/md0 /datalib
```

I do have a /etc/mdadm/mdadm.conf file that includes

```
DEVICE     /dev/sda7 /dev/sdb3

ARRAY      /dev/md0 devices=/dev/sda7,/dev/sdb3 level=1 auto=md num-devices=2
```

Up to this point, everything appears to be working. But once I stop the RAID (either with mdadm -S /dev/md0, or by rebooting), a spurious device md_d0 shows up in the /dev directory listing, along with a /dev/md subdirectory and four links in the /dev directory that point to md_d0p* devices in the ./md subdirectory.

This spurious md_d0 device claims sdb3:

```
# cat /proc/mdstat
md_d0 : inactive sdb3[1](S)
        276920320 blocks

md0 : inactive sda1[0](S)
      276920320 blocks

unused devices: <none>
```

At this point, sdb3 cannot be made a part of my real md0 until I issue the command to stop the bogus device with mdadm -S md_d0.

Also at this point,  neither the native parted program on my Kubuntu installation nor the gParted live-CD recognize the filetype for sdb3, but fdisk reports it as still being an ext3-formatted partition.

I have never explicitly created md_d0, nor have I ever tried to partition md0. This behavior recurs even after I've removed and reformatted both the sda7 and sdb3 partitions, whether with or without the RAID flag set.

---

### Post by fjgaude on 2009-05-19
Well, from my experience, I don't know how you got that **mdadm.conf** file... I don't think it was created by **mdadm**, eh?

An array is normally assembled by the common UUID created by mdadm when the array was first created. It's in the drives' superblocks.

If you can show results of this command we might be able to recommend what to do next:

```
sudo mdadm --detail /dev/md0
```

Let us know what happens, please.

---

### Post by qajaq on 2009-05-19
The mdadm.conf came from me. I wrote it based on recommendations in the mdadm.conf man pages and elsewhere.

Running mdadm --detail /dev/md0 from boot-up returned the following:
```
mdadm: md device /dev/md0 does not appear to be active.
```

After running mdadm -As /dev/md0, the mdadm --detail /dev/md0 command returns:
```
/dev/md0:
        Version: 00.90
  Creation Time: Sun May 17 21:15:07 2009
     Raid Level: raid1
     Array Size: 276920320 (264.09 GiB 283.57 GB)
  Used Dev Size: 276920320 (264.09 GiB 283.57 GB)
   Raid Devices: 2
  Total Devices: 1
Preferred Minor: 0
    Persistence: Superblock is persistent

    Update Time: Sun May 17 21:18:24 2009
          State: clean, degraded
 Active Devices: 1
Working Devices: 1
 Failed Devices: 0
  Spare Devices: 0

           UUID: b3e5a7f8:0a458f24:0b3923ae:1f8d05e4 (local to host Kodiak)
         Events: 0.5

    Number   Major   Minor   RaidDevice State
       0       0        7        0      active sync  /dev/sda7
       1       0        0        1      removed
```

The result is the same (except for the Update Time) if I stop both md0 and md_d0, then re-start md0.

---

### Post by fjgaude on 2009-05-20
Okay, now run the -E command on each of the partitions of the array, like so:

```
sudo mdadm -E /dev/sdb3
sudo mdadm -E /dev/sda7
```

See if the UUID is the same for each? They should be but likely are not.

And the UUID you saw in the -D command, b3e5a7f8:0a458f24:0b3923ae:1f8d05e4, is what goes into the **mdadm.conf** file, and not the drive names.

I would suggest that your either rename the mdadm.conf file or delete it and then remove **mdadm** from your system. Reboot, then re-install mdamd and then run this command:

```
sudo mdadm --assemble --scan
```

Just like that, in the order suggested. From doing this a new mdadm.conf file will be auto created by mdadm. You might look at it and see the changes.

---

### Post by qajaq on 2009-05-20
I ran the two versions of "mdadm -E /dev/sd..." and got identical UUIDs from the two devices, both of which were the same UUID as I listed above.

Because this is not the only difficulty I've been having with this OS, instead of deleting the mdadm.conf file and un-installing the mdadm application, I completely re-installed Kubuntu 9.04, re-formatting all the partitions. Partitions sda7 and sdb3 were re-formatted as ext3 with the RAID flag set.

After getting the re-installed OS up and running, I re-installed mdadm. The automatically-created mdadm.conf file has no ARRAY defined. When I run "mdadm -E /dev/sda7" I get the message
```
mdadm: No md superblock detected on /dev/sda7
```
Same result with /dev/sdb3. Yet when I run either "parted -l" both of those partitions are listed as "raid"; and when I run "fdisk -l" they're listed as "raid autodetect."

I feel as though I'm going backwards here.

---

### Post by qajaq on 2009-05-21
I manually created the array with

```
mdadm -Cv /dev/md0 -l1 -n2 /dev/sda7 /dev/sdb3
```

and it worked. I checked it with "cat /proc/mdstat" and it showed both devices assembled into the array.

But when I stopped the array

```
mdadm -S /dev/md0
```

...and rebooted the machine, it came up with that spurious md_d0 and all its links into the unwanted subdirectory again.

---

### Post by fjgaude on 2009-05-21
The best I can guess is that the superblocks of the various partitions on the drives are mixed up... other than zeroing them out with **mdadm** I can't think of what to do, starting over with clean partitions on the drives. 

I've never re-created an array without having zeroed the superblocks of the partitions. Once drives are used in an array I always simply assemble them, one way or the other. To get spurious partitions means that some partition has a superblock UUID that mdadm thinks is part of the array.

Good luck!

---

### Post by qajaq on 2009-05-22
Looks like a case of delayed recuperation or spontaneous remission--not sure which.

When I shut down my system last night, I still had the spurious md_d0, etc., showing up in the /dev directory listing, and the /proc/mdstat file still showed only /dev/sda7 available to the array.

This morning, however, when I booted that machine I found both sda7 and sdb3 included in the array and found no spurious md_d0 devices in the /dev listing.

Maybe all it needed after the re-format was a cold re-boot. I don't know. But it's working -- I re-booted four times to make sure it wasn't a one-time fluke.

Thanks for your help, Frank!

---

### Post by fjgaude on 2009-05-22
Great! It's good to get things working correctly, eh?

---

### Post by free beer and brats on 2009-06-16
Hmmm... I'm having this exact same issue with ubuntu 9.04.  I'm attempting to create a raid1 array with 2 1TB drives. It appears that despite mostly similar efforts to the above, my /dev/sdc1 is being held hostage by the unwanted /dev/md_d0 on reboot.  This prevents my wanted /dev/md0 (which assembles and synchs up fine maually), from doing absolutely anything on reboot.

Initially I thought it was mangled superblocks, but these seem to be fine, and identical for each drive of the array (/dev/sdb1==/dev/sdc1).  Any changes I make to /ect/mdadm.conf seem to have no effect.  After boot, if I stop the unwanted /dev/md_d0 array and assemble /dev/md0, everything works just fine.

I would think that /dev/md0 would at least start with a failed drive, since it would only be missing one... but it fails to start at all.  Quite annoying since it mounts as the /home directory.  

I googled around and this does not seem to be an overly common issue, but others seem to be experiencing identical symptoms upon occurrence... Any thoughts on a more systematic cure?  I have not attempted a clean install after the problem appeared, but I'm not really sure how that would help.  

How can I kill this damn /dev/md_d0?? I tried failing /dev/sdc1 and removing it from /dev/md_d0, but mdadm complains that the device does not appear to be active (although I can stop it with --stop).

Frank has always set me strait with all things mdadm so I thought I would ask.

---

### Post by Registered2read on 2009-08-29
Well, I experience the very same thing but with a 4 disks raid10 array. After reboot, only one disk appears as member of /dev/md_d0. The four mdadm -E show that the array is internally consistent.

The box being in a colo 300km away I've removed the array from fstab and I'm looking around for a solution. Reinstalling is not an option any more. I'll try a mdamd.conf with the result of a mdadm --detail --scan

ARRAY /dev/md0 level=raid10 num-devices=4 metadata=01.00 name=store1:0 UUID=47e459d3:b7835518:6870f180:df2968fd

and see what happens the next time I've the occasion to reboot.

(2009-09-16) The box survived the reboot. Explicitly specifying the array did the job.

---

