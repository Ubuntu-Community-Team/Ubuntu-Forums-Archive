---
title: "Software RAID-5 Installer issue."
date: 2007-04-18
forum: Server Platforms
---

### Post by n00tz on 2007-04-18
alright, I'm tying to install Ubuntu Server (Dapper 6.06 LTS & I've tried Edgy also) I've never tried to use the Software RAID before, but here's my problem:
I get to the Disk partitioner --> Configure software RAID .. I Create the MD device as a RAID 5 on all 6 of my SCSI disks (no spares) and finish. it restarts the partiioner... and I tell it to guided partition the RAID device.. I tell it to erase the entire disk and install how it wishes..

I get this message after it appears to format the ext3 at / and the swap:  > Error informing the kernel about modifications to partition /dev/md/0p1 -- invalid argument. This means linux won't know about any changes you made to /dev/md/0p1 until you reboot so you shouldnt mount it or use it in any way before rebooting

It does this with the 2 partitions the installer makes automagically (Physical at / and swap inside a Logical partition).

I can tell it to ignore or cancel or go back... if I ignore them it just says that formatting as ext3 failed.

Anyone tried this before and know of the work around? I'm not afraid to Alt+F2 and work in the command line for a resolution.

I've attempted to fdisk /dev/md0 and make the partitions there (successfully, I might add) but then I can't format them because mke2fs doesn't see a device at /dev/md0p1 (as is listed when I fdisk -l). I'm stumped.

---

### Post by PhragMunkee on 2007-04-18
Am I correct in thinking that you can't install to a software RAID 5?  That means you would have to put the kernel and drivers/modules on the RAID and you can't load the RAID without the kernel and you can't load the kernel without the RAID?

Instead, would it be possible to sacrifice a small amount of space on one of the drives (which means it applies to all of the drives) for a /boot partition?

What all is required in order to set everything up on a software RAID?  I think what he is wanting to do is have all of /home, /usr, /var, /etc, etc. in a safe, redundant array.

And, being his coworker across the hall, I know he has an old IBM 4-way 700 MHz server with 6 18.2 GB SCSI drives on a plain old SCSI controller (no hardware RAID).  Maybe that'll help in solving his problem?

---

### Post by n00tz on 2007-04-19
that would be correct ^

I'm currently attempting to try the /boot idea by separating .2G off of the 18.2G drives. I'll post a followup edit to this message if all is well.

==EDIT==

I have it working. I went through and used FDISK to make all 6 drives look like this:

1st partition 200M linux raid autodetect (RAID1) /boot
2nd partition 168M linux swap / solaris  SWAP
3rd partition (remaining) linux raid autodetect (RAID5) /

i set up the partitions according to their purpose using manually edit partition table, and everything went without a hitch.

I hope this helps someone in the future.

---

