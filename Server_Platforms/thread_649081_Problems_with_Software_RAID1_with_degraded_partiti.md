---
title: "Problems with Software RAID1 with degraded partition."
date: 2007-12-24
forum: Server Platforms
---

### Post by bobsta63 on 2007-12-24
Hi Guys/Gals

Just want some help with Software RAID1, I have just installed Ubuntu Server 6.06 on a Compaq DL320 Server and all appears to be fine except when I look at the RAID status on md0 it shows one of the harddrives (hdg1) as being removed (which it is not!) but if I check the status of the md1 it shows hdg2 as being 'active sync'. 

Here is the resault of command 'mdadm --query --detail /dev/md0'

[COLOR="YellowGreen"]root@enzo:~# mdadm --query --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Mon Dec 24 14:54:46 2007
     Raid Level : raid1
     Array Size : 48829440 (46.57 GiB 50.00 GB)
    Device Size : 48829440 (46.57 GiB 50.00 GB)
   Raid Devices : 2
  Total Devices : 1
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Mon Dec 24 17:12:07 2007
          State : clean, degraded
 Active Devices : 1
Working Devices : 1
 Failed Devices : 0
  Spare Devices : 0

           UUID : 8b178e4b:df67a834:38128267:61411a99
         Events : 0.934

    Number   Major   Minor   RaidDevice State
       0      33        1        0      active sync   /dev/hde1
       1       0        0        -      removed[/COLOR]


and here is the resault of running the command again (mdadm --query --detail /dev/md1) on the other mirrored partition (md1):

[COLOR="YellowGreen"]root@enzo:~# mdadm --query --detail /dev/md1
/dev/md1:
        Version : 00.90.03
  Creation Time : Mon Dec 24 14:54:54 2007
     Raid Level : raid1
     Array Size : 1951808 (1906.38 MiB 1998.65 MB)
    Device Size : 1951808 (1906.38 MiB 1998.65 MB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Mon Dec 24 15:15:26 2007
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 601defe0:77d368f2:18c6cef3:de67fb33
         Events : 0.4

    Number   Major   Minor   RaidDevice State
       0      33        2        0      active sync   /dev/hde2
       1      34        2        1      active sync   /dev/hdg2[/COLOR]

What I dont understand is I have just installed this RAID1 using the Ubuntu installer and surely it should be fine as I have only just installed Ubuntu Freshly? 

Any help/suggestions would be very much appreciated :)

Happy christmas to you all too :)

---

### Post by bobsta63 on 2007-12-24
Please guys anyone?

Im kinda stuck! lol - If you need more infomation (regarding setup) please just ask.

Thanks in advance,

Bobby

---

### Post by rsw686 on 2007-12-24
Could be a fluke why it was dropped. I would add it back and see if it happens again. If it does there is probably an issue on that section of the drive and it will need to be replaced.

---

### Post by bobsta63 on 2007-12-25
Hi rsw686

Thanks for the reply, Happy christmas by the way! :)

Is there anything I need to do to remove it... (Do I need to issue any commands before I open the server up and remove the drive) then power the server back up again, shutdown and re-add the disk?

So basically from the infomation I gave you it all seems fine then I suppose? So I should really try a new HDD,

Once again, Thanks for your help and have a great day.

Thanks mate,

Regards,
Bobby

---

### Post by salamba on 2007-12-25
Best to check your logs for errors relating to hdg or md devices.
If you're happy with the disk, you could just hot add the partition back into md0.  No need to shut down or anything like that.

mdadm /dev/md0 --add /dev/hdg1

(If you are sure this is the right partition to add - maybe check mdstat & fstab first)
'cat /proc/mdstat' to see the recovery,  and watch you logs for it to fail again.   As the previous reply said,  it's likely you've a problem with that drive though.

---

### Post by rsw686 on 2007-12-25
Yep just hot add the disk back with the command above. If you end up replacing it you will need to do the following.

Fail and remove both drives from the arrays
mdadm --fail /dev/md0 /dev/hdg1
mdadm --remove /dev/md0 /dev/hdg1

mdadm --fail /dev/md1 /dev/hdg2
mdadm --remove /dev/md1 /dev/hdg2

Shutdown machine and swap the drive

Boot the machine back up

Copy the partition table from the existing drive and remove the RAID block
sfdisk -d /dev/hde | sfdisk /dev/hdg
mdadm --zero-superblock /dev/hdg

Add the drive back to the arrays
mdadm --add /dev/md0 /dev/hdg1
mdadm --add /dev/md1 /dev/hdg2

Check the status and make sure they are resyncing
cat /proc/mdstat
mdadm --detail /dev/md0
mdadm --detail /dev/md1

If you boot off this drive you will need to setup grub on the drive as well. Even if you do not replace the drive you should do this. The installer only installs the grub config on the first drive. Should be similar to the below commands.

device (hd0) /dev/hdg
root (hd0,0)
setup (hd0)
quit

---

### Post by bobsta63 on 2007-12-26
Hi guys,

Thanks for your responses, I decided to reinstall Ubuntu yesterday as I didnt have any drives bigger than 50GB so I replaced both drvies with 2x 20GB and re-installed Ubuntu all is now working fine again, So I suppose it was a dodgey disk.

Just one more quick queston....

If I had a disk fail could I not just power off the server, place the failed disk with a brand new (clean) disk and then power back up again and the array will automatically partition and rebuild the disk? - Is that possible or would I still need to do the above mentioned tasks such as copy the partion table etc manually?

Regards,
Bobby

---

### Post by rsw686 on 2007-12-26
> **bobsta63 said:**
> Hi guys,
If I had a disk fail could I not just power off the server, place the failed disk with a brand new (clean) disk and then power back up again and the array will automatically partition and rebuild the disk? - Is that possible or would I still need to do the above mentioned tasks such as copy the partion table etc manually?

It doesn't work that way. How does the system know you want that disk to be used as part of the array. You could be adding that disk to backup data to. Dedicated RAID controller work like you state, but only disks being part of the array are plugged into them.

mdadm doesn't write partition tables since the arrays are just on a partition. You need to partition the disk first so that mdadm knows its boundaries.

The commands make sense if you use them a couple of times. What I did when I was testing it all out was to create a VMware guest with 6 drives. I practiced failing drives, adding them, growing the array, migrating from raid 1 to raid 5, etc. That way I am covered in any situation that arises.

---

### Post by bobsta63 on 2007-12-26
Yeah, I understnad :)

Think I will do what you did (played around with a load of VDisks in VMWare.

Thanks for all your help (rsw) - I gave you 'thanks'

Regards,
Bobby

---

