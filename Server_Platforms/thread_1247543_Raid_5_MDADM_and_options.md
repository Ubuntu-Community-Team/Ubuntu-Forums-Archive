---
title: "Raid 5 MDADM and options"
date: 2009-08-23
forum: Server Platforms
---

### Post by nownto on 2009-08-23
I have a box that has built on raid 5, but I believe it is fakeRaid so therefor I must use software raid, this is where the problems start. I tried to setup MDADM, everything went good, but when i reboot I always loose one of the drives and it refuses to mount. I just got these drives out of a Win 7 raid 5 configuration so I know there good, but can't seem to get them going strong in Ubuntu. So my question is, is there a guide or something that will show me step by step on how to set it up? I've done multiple setup on multiple guides but all end the same way. Also is there an alternative to MDADM that works the same? Really looking for something to work so I don't have to go to Windows Home Server. Thanks for any input.


p.s. the raid 5 is the main thing but I also want to run ssh, ftp, http, etc ... so thats why I'm not going with freeNAS or something of that sort.

---

### Post by fjgaude on 2009-08-23
Your array has how many drives?

What does this show:

```
sudo mdadm -E /dev/md0
```

assuming the array name is /dev/md0

Have you created a mountpoint?

What does the /etc/mdadm/mdadm.conf file contain?

---

### Post by JonLy on 2009-08-24
I'm also having the same issue, i know that i need to add something to some config files but not sure what:
 
sudo mdadm -E /dev/md0
mdadm: No md superblock detected on /dev/md0.
 
and there are no files in /etc/mdadm/
 
Please help :P
 
the raid is started (manually) and i can write to it, i used the following commands to start it:
 
mdadm --assemble /dev/md0 /dev/sda /dev/sdb /dev/sdc
sudo mount -o rw /dev/md0 /media/file_store/
 
and i am the owner of /media/file_store.
 
Cheers
Jon
 
:edit, thought this might be useful too:
sudo mdadm --query --detail /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Sat Aug 22 22:26:28 2009
     Raid Level : raid5
     Array Size : 2930276864 (2794.53 GiB 3000.60 GB)
  Used Dev Size : 1465138432 (1397.26 GiB 1500.30 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent
    Update Time : Mon Aug 24 22:14:09 2009
          State : clean
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0
         Layout : left-symmetric
     Chunk Size : 256K
           UUID : 568a9357:1a53daf0:d0dc6795:fb84cf6c
         Events : 0.4
    Number   Major   Minor   RaidDevice State
       0       8        0        0      active sync   /dev/sda
       1       8       16        1      active sync   /dev/sdb
       2       8       32        2      active sync   /dev/sdc

---

### Post by fjgaude on 2009-08-27
The --detail output looks correct... all is okay. I don't believe you should use the -E command on an array, just on a drive in the array.

Anyway, you are good to go.

---

### Post by superfly85 on 2009-09-07
Try adding something like this to fstab:

/dev/md0 /mnt/md0 ext4 defaults 1 2

And.... This for the mdadm config:

mdadm --detail --scan > /etc/mdadm/mdadm.conf

---

### Post by tgrimley on 2009-09-08
> **fjgaude said:**
> The --detail output looks correct... all is okay. I don't believe you should use the -E command on an array, just on a drive in the array.

Anyway, you are good to go.

> **fjgaude said:**
> Your array has how many drives?

What does this show:

```
sudo mdadm -E /dev/md0
```


This made me giggle..

---

### Post by NullHead on 2009-09-08
> **nownto said:**
> I have a box that has built on raid 5, but I believe it is fakeRaid so therefor I must use software raid, this is where the problems start. I tried to setup MDADM, everything went good, but when i reboot I always loose one of the drives and it refuses to mount. I just got these drives out of a Win 7 raid 5 configuration so I know there good, but can't seem to get them going strong in Ubuntu. So my question is, is there a guide or something that will show me step by step on how to set it up? I've done multiple setup on multiple guides but all end the same way. Also is there an alternative to MDADM that works the same? Really looking for something to work so I don't have to go to Windows Home Server. Thanks for any input.


p.s. the raid 5 is the main thing but I also want to run ssh, ftp, http, etc ... so thats why I'm not going with freeNAS or something of that sort.

This may not be what you're looking for, but sometimes I get a harddrive that, for some unknown reason, isn't in my array. 

```
sudo mdadm /dev/md0 -a /dev/(missing hdd)
```
Then check /etc/mdstat to see if your device is there; probably rebuilding. ```
cat /proc/mdstat
```

---

### Post by superfly85 on 2009-09-08
Gparted does not recognize my RAID 5 but I can write to the folder where the drive is mounted (/dev/md0  --> /mnt/md0 ), am I doing something wrong ?

sudo fdisk -l

Disk /dev/md0: 2000.4 GB, 2000409591808 bytes
255 heads, 63 sectors/track, 243202 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

    Device Boot      Start         End      Blocks   Id  System
/dev/md0p1               1      121602   976762583+  8e  Linux LVM


what is md0p1?

---

### Post by tgrimley on 2009-09-08
At some point (not sure when, as I run 8.04 on my server, and I noticed it in my 9.10 VM) mdadm started adding a partition bit to the path.

so md0p1 is your first partition on your md0 raid device.  try mounting it the same.  You're able to write to /mnt/md0 because it's probably located on your / mount point before you properly mount hte raid volume

---

### Post by superfly85 on 2009-09-09
can't find /dev/md0p1 in /etc/fstab or /etc/mtab

---

### Post by superfly85 on 2009-09-09
does it matter that I copied all my data to the mount point for /dev/md0 which is /mnt/md0?  how wrong is this?

---

### Post by tgrimley on 2009-09-09
> **superfly85 said:**
> can't find /dev/md0p1 in /etc/fstab or /etc/mtab

What does ```
cat  /proc/mdstat
```say?

> **superfly85 said:**
> does it matter that I copied all my data to the mount point for /dev/md0 which is /mnt/md0?  how wrong is this?

Well, depending on how big your root partition is, it could be very wrong.  But if your array isn't mounted then copying there is totally wrong.  Be careful with your data.. For instance if I copied to my /data mount point with /dev/md0 not mounted I'd be in trouble:
```

tgrimley@gutsy:~$ df /dev/md0 / -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/md0              3.7T  2.0T  1.7T  55% /data
/dev/hda1              29G   14G   14G  51% /

```

---

### Post by fishy6969 on 2009-09-09
I've had problems with mdadm raid not starting which seems to be caused by grub messing up the disk namings eg sdb on reboot moving to sdj or whatever. This thread finally gave me the solution -

[http://ubuntuforums.org/showthread.php?t=410136](http://ubuntuforums.org/showthread.php?t=410136)

---

### Post by fjgaude on 2009-09-09
Hey, md doesn't use the drive names to assemble the array, but uses the special UUID created when the array was first created. It's the one in the /etc/mdadm/mdadm.conf file. It is not used to mount the array. So drive order makes no difference.

---

### Post by fishy6969 on 2009-09-09
Agreed, but using UUID as default I think was only introduced as the default option fairly recently in mdadm. I'm probably wrong though....

---

### Post by joeinbend on 2009-09-09
as far as I know, assembling your RAID based on UUID has always been the preferred method, for the reasons mentioned before, that the drive designations can change depending on how the disks are initialized on startup. using the UUID and telling it to look for /dev/sd* is the way to go.

---

### Post by fishy6969 on 2009-09-09
I agree entirely. I've started using UUID extensively in UDEV rules etc.

---

### Post by fjgaude on 2009-09-09
> **fishy6969 said:**
> Agreed, but using UUID as default I think was only introduced as the default option fairly recently in mdadm. I'm probably wrong though....

It's been that way for as long as I can remember, at least two years.

When array is first created the UUID of the array is put in the superblock of each drive, and from then on out an assemble using the single UUID... has nothig to do with the drives' names.

---

