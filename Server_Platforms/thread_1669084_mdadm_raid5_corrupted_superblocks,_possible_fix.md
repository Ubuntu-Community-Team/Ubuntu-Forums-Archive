---
title: "mdadm raid5 corrupted superblocks, possible fix?"
date: 2011-01-17
forum: Server Platforms
---

### Post by zurishmi on 2011-01-17
I have a server that was originally running a healthy functional 3 disk raid5 with mdadm.  I added 2 disks to the array, and told it to grow.  Hardly 2 minutes into the reshape, my computer experienced an unrelated hard crash, and I was forced to reboot it.  My goal here is to gain access to the data on that array.  Any reader might also want to know that I have a full backup of the disk images of all 5 disks in my raid, so that any thing that "may" work I am happy to try, as I run no risk of further damaging my array.

Now I have a strange state:
2 drives report the correct raid superblocks, indicating the 5 disk setup, and the fact that it is mid-reshape.
2 drives seem to have missed a memo, and have slightly outdated superblocks, indicated a 3 disk array with 1 spare (somehow got written halfway through the original grow)
The last drive may be entirely corrupted due to something I did (stupid in hindsight).  Hopefully as this is a raid5 setup, that is not a problem.

I've read the entire mdadm man page and a LOT of forums, and see two possible solutions here, neither of which I can figure out how to do.

1. I find a means to copy the correct superblocks (while being properly adjusted) to the 2 drives with outdated superblocks, then assemble my array out of the 4 good drives, I can copy my data onto a backup, allowing me to rebuild the array correctly from scratch, and copy it back.  I am fairly certain that the 2 drives with outdated superblocks have the correct data otherwise.

2. Find a way to tell mdadm to assemble an array using the superblock data from a specific drive, ignoring if the others match.  Note, this is roughly the same as #1.


If for some reason I do not understand, these are clearly impossible, I am left with a different approach:

I can construct a previous raid with --assume-clean, that is > 99% clean, with a small bit of corruption due to the small bit of reshaping that took place.  Unfortunately that leaves this setup unmountable because the corruption is at the beginning of the drive.  I think I understand that there exist tools that can look through a drive or partition, and try to recover files and file fragments they think were previously there, without filenames.  This would actually be mostly acceptable, although not ideal.  If I were to do this, do people have specific suggestions of tools that do this that they have liked or are very nice to use?

---

### Post by frostschutz on 2011-01-17
Your raid died in mid grow (that's a worst case scenario) and in addition to that you wiped one of the drives? That's worse than worst case. Ugh.

Forget the wiped drive as it's useless. So basically since it was in the middle of regrowing, your actual data  will be in the first n bytes of the 5 disk raid 5, and the last (total-n) bytes  will be in the original 3 disk raid 5. The size of n depends on where the grow was interrupted.

So you have two raids, one raid 5 with 3 disks (one missing if one of them is the wiped drive), and one raid 5 with 5 disks (again with the wiped drive missing). Start both of those with your original mdadm superblock version, chunk size, and --assume-clean. Make a copy of both (for the 5 disk raid, only the size of the original raid needs to be copied). Find the intersection point. Put the two images together and there you go.

If you had partitions or LVM on this RAID, you may be able to rescue data without putting the two together, just by starting LVM from a backup of the LV layout. You may be able to read an entire LV if it was completely before or after the point of interruption. You can find backups of the LVM layout in the raw data of either raid.

Good luck... in the future make backups first :)

---

### Post by zurishmi on 2011-01-17
Wow, thanks for the quick response!  It's good to have confirmation that the grow works the way I suspected.  However, I hadn't even thought of doing what you suggested, mostly because I didn't know such a thing was possible.  Any specific suggestion of how I might go about finding the intersection and combining images, or know where I might find a guide?

You may have guessed correctly that I neither used LVM or partitions on the raid itself.

---

### Post by frostschutz on 2011-01-17
It may not actually work that way. It's just worth a try. Read the GROW section of the mdadm manpage. There's also this passage:

> 
       When relocating the first few stripes on a RAID5, it is not possible to
       keep  the  data on disk completely consistent and crash-proof.  To pro&#8208;
       vide the required safety, mdadm disables writes to the array while this
       "critical  section" is reshaped, and takes a backup of the data that is
       in that section.  This backup is normally stored in any  spare  devices
       that  the  array  has, however it can also be stored in a separate file
       specified with the --backup-file option.  If this option is  used,  and
       the system does crash during the critical period, the same file must be
       passed to --assemble to restore the backup and reassemble the array.
That could've been a chance for you but I think with one drive wiped in addition to your problem, that's no good either. So... yeah. :-/

Still maybe worth checking if that backup is there somewhere on one of the spares - because if it is, it could save your filesystem... no clue how to actually find it, though. I'd probably have to read the source code how / where on the spares this is stored exactly.

What you need here, is some luck. :)

---

### Post by zurishmi on 2011-01-18
Some updates here:

the superblock on one of the drives that reports the correct array:

```
[FONT=Courier New][COLOR=#000000]/dev/sde:[/COLOR][/FONT][FONT=Courier New]
[/FONT] [FONT=Courier New][COLOR=#000000]          Magic : a92b4efc[/COLOR][/FONT][FONT=Courier New]
[/FONT] [FONT=Courier New][COLOR=#000000]        Version : 00.91.00[/COLOR][/FONT][FONT=Courier New]
[/FONT] [FONT=Courier New][COLOR=#000000]           UUID : e2960603:4ffeab9b:8c2f8abc:5b00dbde (local to host grape)[/COLOR][/FONT][FONT=Courier New]
[/FONT] [FONT=Courier New][COLOR=#000000]  Creation Time : Fri Dec 10 04:03:40 2010[/COLOR][/FONT][FONT=Courier New]
[/FONT] [FONT=Courier New][COLOR=#000000]     Raid Level : raid5[/COLOR][/FONT][FONT=Courier New]
[/FONT] [FONT=Courier New][COLOR=#000000]  Used Dev Size : 976758912 (931.51 GiB 1000.20 GB)[/COLOR][/FONT][FONT=Courier New]
[/FONT] [FONT=Courier New][COLOR=#000000]     Array Size : 3907035648 (3726.04 GiB 4000.80 GB)[/COLOR][/FONT][FONT=Courier New]
[/FONT] [FONT=Courier New][COLOR=#000000]   Raid Devices : 5[/COLOR][/FONT][FONT=Courier New]
[/FONT] [FONT=Courier New][COLOR=#000000]  Total Devices : 5[/COLOR][/FONT][FONT=Courier New]
[/FONT] [FONT=Courier New][COLOR=#000000]Preferred Minor : 1[/COLOR][/FONT][FONT=Courier New]

   [/FONT][FONT=Courier New][COLOR=#000000]Reshape pos'n : 2539776 (2.42 GiB 2.60 GB)[/COLOR][/FONT][FONT=Courier New]
[/FONT] [FONT=Courier New][COLOR=#000000]  Delta Devices : 2 (3->5)[/COLOR][/FONT][FONT=Courier New]

[/FONT] [FONT=Courier New][COLOR=#000000]    Update Time : Sat Dec 11 20:39:24 2010[/COLOR][/FONT][FONT=Courier New]
[/FONT] [FONT=Courier New][COLOR=#000000]          State : active[/COLOR][/FONT][FONT=Courier New]
[/FONT] [FONT=Courier New][COLOR=#000000] Active Devices : 4[/COLOR][/FONT][FONT=Courier New]
[/FONT] [FONT=Courier New][COLOR=#000000]Working Devices : 4[/COLOR][/FONT][FONT=Courier New]
[/FONT] [FONT=Courier New][COLOR=#000000] Failed Devices : 1[/COLOR][/FONT][FONT=Courier New]
[/FONT] [FONT=Courier New][COLOR=#000000]  Spare Devices : 0[/COLOR][/FONT][FONT=Courier New]
[/FONT] [FONT=Courier New][COLOR=#000000]       Checksum : 977eb8a4 - correct[/COLOR][/FONT][FONT=Courier New]
[/FONT] [FONT=Courier New][COLOR=#000000]         Events : 15303[/COLOR][/FONT][FONT=Courier New]

[/FONT] [FONT=Courier New][COLOR=#000000]         Layout : left-symmetric[/COLOR][/FONT][FONT=Courier New]
[/FONT] [FONT=Courier New][COLOR=#000000]     Chunk Size : 64K[/COLOR][/FONT][FONT=Courier New]

[/FONT] [FONT=Courier New][COLOR=#000000]      Number   Major   Minor   RaidDevice State[/COLOR][/FONT][FONT=Courier New]
[/FONT] [FONT=Courier New][COLOR=#000000]this     3       8       64        3      active sync   /dev/sde[/COLOR][/FONT][FONT=Courier New]

[/FONT] [FONT=Courier New][COLOR=#000000]   0     0       8        1        0      active sync   /dev/sda1[/COLOR][/FONT][FONT=Courier New]
[/FONT] [FONT=Courier New][COLOR=#000000]   1     1       8       17        1      active sync   /dev/sdb1[/COLOR][/FONT][FONT=Courier New]
[/FONT] [FONT=Courier New][COLOR=#000000]   2     2       8       81        2      active sync   /dev/sdf1[/COLOR][/FONT][FONT=Courier New]
[/FONT] [FONT=Courier New][COLOR=#000000]   3     3       8       64        3      active sync   /dev/sde[/COLOR][/FONT][FONT=Courier New]
[/FONT] [FONT=Courier New][COLOR=#000000]   4     4       0        0        4      faulty removed[/COLOR][/FONT]
```A few notes on the superblock here that a reader may notice:
1. The Used Dev Size is suspiciously only 1 TB, even though the 3 disk raid that was grown should have been using 2 TB (perhaps only part of the superblock got updated correctly).  I really don't know why this is, or how it might be affecting my later efforts.
2. The devices are in a strange order, and more importantly, 3 are partitions, and 1 is a raw drive.  This was a typo, but from what I understand doesn't actually matter.  I've been told recently the reason drives used in raids have a partition of type "Linux Raid Autodetect" is simply so that the beginning of the drive is not important data, as some software may occasionally alter what it thinks is a partition table (say... windows).  The raid actually had the devices in the order given here.

I tried your suggestion assuming that the reshape position given means that I should copy exactly 2539776 KiB from the beginning of the reformed (--assume-clean) 5 disk raid5, and put it into a temporary file on the now unused previously corrupted drive (I just ran fdisk then put a filesystem on it).  I then used --assume-clean again to reform the original 3 disk raid5, and copied the temporary file to the beginning of it (using dd both times).  Ideally, that raid should have all of the correct data except the first 2.6 GB.

Something here did not work, and I was left with a device that still was not mountable.  Maybe I'm missing something, or the reshape doesn't work exactly like that, or the reshape pos'n shouldn't be interpretted exactly like that (perhaps it means it wrote that much data to each device, instead of the raid as a whole?).  Also I'm fairly certain that amount of data is more than enough to exceed the critical first few stripes section that requires a backup file.

Another idea came to mind that would be nice to get some input about, as I do not understand enough to know if this is a possible option.  Is there a way to use fsck or another such utility to reconstruct a mountable filesystem out of an array, while ignoring the first 2.6 GB that are missing (such that I could access files that were in the later parts).  I have sufficient backup of most of the early files in my array.

---

### Post by zurishmi on 2011-01-20
I have succeeded in recovering all of my data, and found an excellent solution that seems not very well known.

It seems that even after trying to manually undo the mid-reshape as frostshutz suggested, I still had a small bit of corruption.   However, the real problem was that part of this was in the ext4 filesystem superblock, and this can be a real mess.  The solution to this is to tell it to use one of the many backup superblocks stored throughout the disk.  I found a guide here:  [[COLOR=#000099][FONT=Arial]_http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/_[/FONT][/COLOR]]("http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/")

Fsck was able to properly interpret the filesystem with a fully intact superblock, and only had to patch up some minor holes due to some corruption at the beginning.  I was left with almost everything intact.

---

