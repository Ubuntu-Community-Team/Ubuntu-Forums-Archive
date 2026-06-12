---
title: "Raid5 partition not visible after drive pull"
date: 2010-07-06
forum: Server Platforms
---

### Post by al090187 on 2010-07-06
Hi,

On Friday I accidentally pulled the sata lead from one of the 4 hard drives in my raid array. I didn't notice that I had done this until the next morning when my server wouldn't boot, and came up with the generic error

> Waiting for device /media/STORAGE.
Continue waiting, or press S or M etc.I turned it off, found the loose cable, and plugged it back in, restarted the computer, still unable to find the device, so went into the manual recovery section. I accessed mdadm, and left it for 8 hours to rebuild the broken array.

Now, it still won't boot. I have used a liveCD and can see the array fine, but it cannot seem to find the partition on there.

To further complicate matters, the home folders are stored on the array, so I am unable to actually launch the system at all.

Does anyone have any suggestions on how to recover the data? Or, how I can move the home folder location back to the system drive, so I can actually boot into the system to try further commands.

Many Thanks

Alexander



Specs:
4 x 1TB Hitachi sata drives in Raid5 array
1 x 40GB samsung ide system drive
1GB ram
2.4GHz P4 processor
Ubuntu Server Edition 10.04

---

### Post by fjgaude on 2010-07-06
Seems like you are in a heap of trouble... when you boot using a LiveCD can you then load **mdadm** and run this command:

```
sudo mdadm --assemble --scan
```

After that will this work:

```
sudo mdadm -D /dev/mdxx
```

You might have to download and install mdadm while using the Live CD.

---

### Post by al090187 on 2010-07-06
Many thanks for your reply. A heap of trouble is an understatement!

> **fjgaude said:**
> Seems like you are in a heap of trouble... when you boot using a LiveCD can you then load **mdadm** and run this command:

```
sudo mdadm --assemble --scan
```After that will this work:

```
sudo mdadm -D /dev/mdxx
```You might have to download and install mdadm while using the Live CD.

The above method for assembling the array is the way I got it to sync after I replaced the drive. The detail command gives the following info.


> ubuntu@ubuntu:~$ sudo mdadm --assemble --scan
ubuntu@ubuntu:~$ sudo mdadm -D /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Sat Jul  3 23:22:10 2010
     Raid Level : raid5
     Array Size : 2930287488 (2794.54 GiB 3000.61 GB)
  Used Dev Size : 976762496 (931.51 GiB 1000.20 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Jul  5 22:33:36 2010
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 809e5bef:0ea34369:cf127344:71531497
         Events : 0.25

    Number   Major   Minor   RaidDevice State
       0       8       32        0      active sync   /dev/sdc
       1       8       64        1      active sync   /dev/sde
       2       8       16        2      active sync   /dev/sdb
       3       8       48        3      active sync   /dev/sdd
The array itself seems fine. Attached is a screenshot of the Disk Utility, showing the "Unknown Filesystem" on the array. It was ext4 before.

Any further advice? Or on how to move the home folder location?

---

### Post by fjgaude on 2010-07-06
I'm not sure what file utility you are using to test the array. Most do not understand arrays at all. The image you attached is too small for me to read.

While in LiveCD you can make a partition on your system disk and then copy the contents of your /home there. But I still think you have to then correct your **/etc/fstab** file so the OS knows where to load the files.

Look in /fstab file and notice what it is trying to do to load the OS and the /home directory. Copy and paste the fstab to your next post here.

Since your array is solid there is hope to get it all running as you wish once again.

---

### Post by al090187 on 2010-07-06
The picture I uploaded was wrong. I have just changed it for one you should be able to read.

The fstab doesn't seem to load a /home directory

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=54d8aac9-cbf6-4ccf-9218-dfcee0636c8b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=4c3c49bb-8982-4d0c-877b-773f8ca636e6 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/md0  /media/STORAGE  ext4  nosuid,uhelper=devkit,nodev  0  0

If I remember rightly, I changed the location of the home folders individually using Webmin. Basically, the hard drives came from a stand alone NAS, and there were folders on the drives with everyones stuff in. Webmin allowed me to change the home location, so the files were easily accessible again from the samba shares, as they were before. 

I think we need to figure out how to tell the computer there is a partition on the drive, without reformatting it.

---

