---
title: "Invalid assembly of mdadm RAID array after reboot"
date: 2011-04-22
forum: Server Platforms
---

### Post by peterk2011 on 2011-04-22
Hi all,


I need your help to restore data on my home server. I was working on my server, the server was working ok, i had my volumes mounted and working fine. Then i decided to reboot the machine, and after reboot i noticed that my LVM2 data volume disappeared. :(
 

The configuration is: Ubuntu 10.04 lucid server, one 320GB sata disk (/dev/sda) with 3 partitions, /dev/sda1 as root, /dev/sda2 as swap, /dev/sda3 as home. The main data volume is a 5 disks software raid5 (/dev/sd[bcdef]1), and a LVM2 volume over this. The LVM uses a single pv, single vg and single lv using all available spaces on the raid volume. This was the configuration at least, because now, the LVM configuration just disappeared, pvscan, vgscan just don't see anything, like the lvm volume has never existed.
 

I suspect this is related to the raid volume not being assembled correctly, because altough the volume itself auto-builds up during boot, and mdadm reports it clean but i noticed a strange thing: instead of the original configuration, where the raid members were partitions (/dev/sd[bcedf]1 respectively), now mdadm assembles the volume out of disks, not partitions - except one disk. Look:


 
Before:
```

$ mdadm -Q -D /dev/md0
/dev/md0:
Version : 0.90
Creation Time : Mon Apr 18 12:55:03 2011
Raid Level : raid5
Array Size : 5860548608 (5589.05 GiB 6001.20 GB)
Used Dev Size : 1465137152 (1397.26 GiB 1500.30 GB)
Raid Devices : 5
Total Devices : 5
Preferred Minor : 0
Persistence : Superblock is persistent
Update Time : Fri Apr 22 00:35:22 2011
State : clean
Active Devices : 5
Working Devices : 5
Failed Devices : 0
Spare Devices : 0
Layout : left-symmetric
Chunk Size : 512K
UUID : 57b079c9:517e0846:b742ab4e:ff6d754c (local to host FileStation)
Events : 0.23986
Number Major Minor RaidDevice State
0 8 17 0 active sync [COLOR=red]/dev/sdb1[/COLOR]
1 8 33 1 active sync [COLOR=red]/dev/sdc1[/COLOR]
2 8 65 2 active sync [COLOR=red]/dev/sde1[/COLOR]
3 8 49 3 active sync [COLOR=red]/dev/sdd1[/COLOR]
4 8 81 4 active sync /dev/sdf1

```


 
After:
```

$ mdadm -Q -D /dev/md0
/dev/md0:
Version : 0.90
Creation Time : Mon Apr 18 12:55:03 2011
Raid Level : raid5
Array Size : 5860548608 (5589.05 GiB 6001.20 GB)
Used Dev Size : 1465137152 (1397.26 GiB 1500.30 GB)
Raid Devices : 5
Total Devices : 5
Preferred Minor : 0
Persistence : Superblock is persistent
Update Time : Fri Apr 22 20:19:29 2011
State : clean
Active Devices : 5
Working Devices : 5
Failed Devices : 0
Spare Devices : 0
Layout : left-symmetric
Chunk Size : 512K
UUID : 57b079c9:517e0846:b742ab4e:ff6d754c (local to host FileStation)
Events : 0.23986
Number Major Minor RaidDevice State
0 8 16 0 active sync [COLOR=red]/dev/sdb[/COLOR]
1 8 64 1 active sync [COLOR=red]/dev/sde[/COLOR]
2 8 32 2 active sync [COLOR=red]/dev/sdc[/COLOR]
3 8 80 3 active sync [COLOR=red]/dev/sdf[/COLOR]
4 8 49 4 active sync /dev/sdd1

```


 
Note: **The order of disks has changed after reboot!** Comparing disk ID-s, sdc became sde and vice-versa, and sdd became sdf and vice versa. Mdadm seem to correcly recognize these changes., because the members of the array swapped their order exactly as supposed to do. But instead of partitions, now, whole disks are being assembled... 


I tried to stop the array and assemble by hand, but no go:
 
```

$ mdadm --stop /dev/md0
mdadm: stopped /dev/md0
$ mdadm --assemble /dev/md0 /dev/sdb1 /dev/sde1 /dev/sdc1 /dev/sdf1 /dev/sdd1
mdadm: no RAID superblock on /dev/sdb1
mdadm: /dev/sdb1 has no superblock - assembly aborted

```


 
Command "mdadm --assemble /dev/md0" doesn't work also, there's no error message, it just quits and /proc/raidinfo doesn't report any array assembled.

But if i query sdb1 I got this:

 
```

/dev/sdb1:
Magic : a92b4efc
Version : 0.90.00
UUID : 57b079c9:517e0846:b742ab4e:ff6d754c (local to host FileStation)
Creation Time : Mon Apr 18 12:55:03 2011
Raid Level : raid5
Used Dev Size : 1465137152 (1397.26 GiB 1500.30 GB)
Array Size : 5860548608 (5589.05 GiB 6001.20 GB)
Raid Devices : 5
Total Devices : 5
Preferred Minor : 0
Update Time : Fri Apr 22 20:39:03 2011
State : clean
Active Devices : 5
Working Devices : 5
Failed Devices : 0
Spare Devices : 0
Checksum : fbc4cab9 - correct
Events : 23986
Layout : left-symmetric
Chunk Size : 512K
Number Major Minor RaidDevice State
[COLOR=red]this 0 8 16 0 active sync /dev/sdb[/COLOR]
0 0 8 16 0 active sync /dev/sdb
1 1 8 64 1 active sync /dev/sde
2 2 8 32 2 active sync /dev/sdc
3 3 8 80 3 active sync /dev/sdf
4 4 8 49 4 active sync /dev/sdd1

```


 
The superblock seems to be there but reports wrong members. All other disks reports the same, so all have their superblock info, and the same - wrong - device list of disks instead of partitions. Event counters equal on all disks, and all disks are clean and working, so no hardware problem.

I think the root of the problem is this mismatched assembly, because if I dump the first chunk of each raid member:

 
```
$ dd if=/dev/sdb1 of=/tmp/sdb1-dump bs=512K count=1
```


 
i can see the LVM metadata at the beginning of the /dev/sdb1 dump, and I can see almost the same data in the /dev/sdd1 chunk (i suppose this is the parity chunk). If I dump the same first 4 chunks out of /dev/md0, - correct me if i'm wrong, but I suppose - it should be a concatenation of the above chunks (except the parity). But I see some completely different data. I dumped the fist 6 megs out of /dev/md0, and around 5 meg into the file I see the LVM superblock info. Since I have created disk partitions starting from sector 2048:

 
```

/dev/sdb1 2048 2930277167 1465137560 fd Linux raid autodetect
/dev/sdc1 2048 2930277167 1465137560 fd Linux raid autodetect
/dev/sdd1 2048 2930277167 1465137560 fd Linux raid autodetect
/dev/sde1 2048 2930277167 1465137560 fd Linux raid autodetect
/dev/sdf1 2048 2930277167 1465137560 fd Linux raid autodetect

```


 
it makes sence, because 5x2048x512 is about 5MB. This indicates the same problem: 
the raid array assembled incorrectly.

 
So, the question is, how can I correct this situation? As you see, the metadata on the disks already contain invalid member info (disks instead od partitions), so I need to correct them for sure. One solution I can think of is doing a "mdam --create /dev/md0 -l 5 n 5 --assume-clean" and specifying the members in correct order, but this is quite drastic, I would like to find a less dangerous option.


 
Please help me solve this, thanks.

---

### Post by peterk2011 on 2011-04-22
Btw, worth to mention that I have forgot to remove a USB key from the server while rebooted... Maybe this is the reason for the changed device names, and maybe mdadm couldn't handle this situation correctly. 
 
But why it has written the wrong suberblock info to the drives already? :confused: I have not even tried to mount the volume yet (there is nothing to mount atm), so the suberblocks suppose to be untouched .... - or not ?

---

### Post by dtfinch on 2011-04-22
Sounds similar to this thread [http://ubuntuforums.org/showthread.php?t=1729459](http://ubuntuforums.org/showthread.php?t=1729459) , related to having partitions that extend to the very end of the disk and using 0.90 metadata, except that their partition tables were wiped out by mdadm while yours seem mostly intact, apart from mdadm not seeing a superblock on sdb1, which could happen if you recreated them and the ended up slightly smaller than before.

If not for the further issue if mdadm not seeing the superblocks on the partitions anymore, I would have suggested changing the "DEVICE partitions" line of mdadm.conf to say "DEVICE /dev/sd??", which would exclude the full disks.

If it did wipe your partitions and you recreated them, and they turned out smaller than before, maybe you could use sfdisk with the -d option to backup the partition layout of the one disk that was unaffected, and use it recreate the layout on the other disks.

In the future you could use a different metadata format or create slightly undersized partitions to avoid this problem.

---

### Post by peterk2011 on 2011-04-22
Ok, solved. :D Phewwww.....
 
I took a risk and issued the above mentioned "mdadm --create" command, and - thanks god -, it re-created the array with the correct layout. The LVM subsystem immediately noticed the pv,vg and lv, I could moount (read only first), and everything seem fine. :P
 
The exact command i issued was:
 
```

$ mdadm --create /dev/md0 --assume-clean --level=5 --raid-devices=5 --metadata=0.9 /dev/sdb1 /dev/sdc1 /dev/sde1 /dev/sdd1 missing

```
 
Notice the "missing" entry at the end. Maybe the "--assume-clean" switch is enough to force mdadm to **NOT start** a resync/recovery task on the array once created, but I was not 100% sure about this. I wanted to check/test my data integrity before letting mdadm do any write job on the array, so I took the safer way and specified only 4 devices out of the 5, adding a "missing" device at the end. This resulted a degraded - but otherwise fully working - array, and because of the degraded state, I could be sure that there will be no resync/recovery job starting. Then, after I have checked that my data is intact, I simply issued a
```
$ mdadm --add /dev/md0 /dev/sdf1
```
adding the final disk back to the array. This of course triggered a resync, but it's better than an incorrectly recovered array if i did something wrong.
 
Conclusion:
The origin of this whole mess of course was the pendrive that i have left plugged in the server during reboot. This scrambled the sata drives in a way that mdadm couldn't handle, and resulted in an incorrectly assembled array. I guess, the problem was that in /etc/mdadm/mdadm.conf I had
```
DEVICE partitions
```
which - according to the man page - instructs mdadm to scan devices returned by "cat /proc/partitions". This returns partitions but also returns whole drives too. So, to make sure this will never happen again, i have modified the config file and specified each device one by one:
```
DEVICE /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1 /dev/sdg1
```
 
I have added /dev/sdg1 to the end of the list even if it does not exist, to make sure that if a pendrive or an external disk becomes one of the sd[bcdef] device in the future - pushing the last raid disk to be /dev/sdg1 - it will be scanned.
 
 
I think I definitely found a mdadm bug, so I plan to report this - once I figure out how & where to report such bugs. ;)

---

### Post by peterk2011 on 2011-04-22
> **dtfinch said:**
> If not for the further issue if mdadm not seeing the superblocks on the partitions anymore, I would have suggested changing the "DEVICE partitions" line of mdadm.conf to say "DEVICE /dev/sd??", which would exclude the full disks.
 
Thanks for your response, and advice. This was the first that came in my mind too, but your solution is way better. I'll modify it right away. :)
 
To be honest, i am not familiar with the inside work/logic of mdadm, I just saw the results and tried to figure out what happened. In my case, mdadm didn't touch the partition table, but happily overwrote the raid superblocks with incorrect member data, while tried to figure out the changed layout on boot. Apparently, it tried to be too smart in my case, giving up assembling the volume would have been a better choice imho. But as i said, i'm not familiar with the inside logic of it, so it could be that this is inevitable using v0.9 superblock and whole-disk-size partitions.
 
Btw, I used v0.9 metadata for purpose. I read somewhere that with never version of superblocks it is not possible to re-create the the array in the way I just did, because with never versions, mdadm either creates a different size array or overwrites the filesystem metadata at the beginning. So I thought I leave this safe door open for rescue operations. I think i need a good reading on mdadm docs, so next time i will not only think that I know what i'm doing but actually do know. ;)

---

### Post by peterk2011 on 2011-04-23
Well, my saga continues. :(
 
As i wrote, I have successfully rebuilt my array using the above "mdadm --create" command, and it was working fine - in a degraded state of course. Then, I added the last, missing disk back by issuing:
```
$ mdadm --add /dev/md0 /dev/sdd1
```
 
And i guess i shouldn't have done this... Everything looked OK while it was re-syncing:
```
$ mdadm -Q -D /dev/md0
/dev/md0:
  Version : 0.90
  Creation Time : Fri Apr 22 23:32:01 2011
  Raid Level : raid5
  Array Size : 5860548608 (5589.05 GiB 6001.20 GB)
  Used Dev Size : 1465137152 (1397.26 GiB 1500.30 GB)
  Raid Devices : 5
  Total Devices : 5
  Preferred Minor : 0
  Persistence : Superblock is persistent
  Update Time : Sat Apr 23 01:04:48 2011
  State : clean, degraded, recovering
  Active Devices : 4
  Working Devices : 5
  Failed Devices : 0
  Spare Devices : 1
  Layout : left-symmetric
  Chunk Size : 512K
  Rebuild Status : 16% complete
  UUID : 7b3e0e42:3ab4e527:b742ab4e:ff6d754c (local to host FileStation)
  Events : 0.18
  Number   Major   Minor   RaidDevice State
      0       8       17        0      active sync   /dev/sdb1
      1       8       65        1      active sync   /dev/sde1
      2       8       33        2      active sync   /dev/sdc1
      3       8       81        3      active sync   /dev/sdf1
      5       8       49        4      spare rebuilding   /dev/sdd1

```
 
but once it finished, the array became a mess (i didn't reboot, and didn't do anything related to md0, it just became like this once the rebuild finished):
```
$ mdadm -Q -D /dev/md0
/dev/md0:
  Version : 0.90
  Creation Time : Fri Apr 22 23:32:01 2011
  Raid Level : raid5
  Array Size : 5860548608 (5589.05 GiB 6001.20 GB)
  Used Dev Size : 1465137152 (1397.26 GiB 1500.30 GB)
  Raid Devices : 5
  Total Devices : 5
  Preferred Minor : 0
  Persistence : Superblock is persistent
  Update Time : Sat Apr 23 11:22:48 2011
  State : clean, FAILED
  Active Devices : 3
  Working Devices : 4
  Failed Devices : 1
  Spare Devices : 1
  Layout : left-symmetric
  Chunk Size : 512K
  UUID : 7b3e0e42:3ab4e527:b742ab4e:ff6d754c (local to host FileStation)
  Events : 0.142
  Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       0        0        1      removed
       2       8       33        2      active sync   /dev/sdc1
       3       8       81        3      active sync   /dev/sdf1
       4       0        0        4      removed
       5       8       49        -      spare   /dev/sdd1
       6       8       65        -      faulty spare   /dev/sde1

```
 
So apparently the rebuild process failed big time. Disk /dev/sdd1 became spare and /dev/sde1 became faulty. I stopped the array, and tried to create again (as i did above), but mdadm complained that /dev/sde1 is invalid. So I tried to include /dev/sdd1 and leave out /dev/sde1 from the create command, and it worked:
 
```
mdadm --create /dev/md0 --assume-clean --level=5 --raid-devices=5 --metadata=0.9 /dev/sdb1 missing /dev/sdc1 /dev/sdf1 /dev/sdd1
```
 
The array came up and looks fine (checked, the data is intact):
```
$ mdadm -Q -D /dev/md0
/dev/md0:
  Version : 0.90
  Creation Time : Sat Apr 23 11:45:14 2011
  Raid Level : raid5
  Array Size : 5860548608 (5589.05 GiB 6001.20 GB)
  Used Dev Size : 1465137152 (1397.26 GiB 1500.30 GB)
  Raid Devices : 5
  Total Devices : 4
  Preferred Minor : 0
  Persistence : Superblock is persistent
  Update Time : Sat Apr 23 11:46:24 2011
  State : clean, degraded
  Active Devices : 4
  Working Devices : 4
  Failed Devices : 0
  Spare Devices : 0
  Layout : left-symmetric
  Chunk Size : 512K
  UUID : ad774bc1:ba23b9d2:b742ab4e:ff6d754c (local to host FileStation)
  Events : 0.4
  Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       1       0        0        1      removed
       2       8       33        2      active sync   /dev/sdc1
       3       8       81        3      active sync   /dev/sdf1
       4       8       49        4      active sync   /dev/sdd1

```
 
So, instead of rebuilding /dev/sdd1, I guess mdam actually re-synced /dev/sde1... Thanks god, I had all 5 disks clean before this mess happened, so I still have 4 intact disks. But now, /dev/sde1 is junk, so I have only 4 good drives and I definitely can't afford to loose any more drives...
 
My first question is what could have been wrong with first recovery attemp? Is it possible, that this happened because I've just simply added back the missing drive without cleaning/wiping it fist? I suspect that the drive still contained the old superblock info, with higher event counter. Could this lead to this failure even if that superblock has nothing to do with the new array (so mdadm supposed to overwrite it)?
 
The second question is the more important: How can I be **absolutely sure**, that this will not happen again, so if I add a new drive, the **new drive will by synced** and not one of the existing ones? Is it enough if i wipe everything from /dev/sde1?
 
Can I be sure that if an array is clean and degraded, and I add a new - completely empty - drive to the array, then existing drives will not be touched, and the new drive will be synced? Can I be sure about this if I created the array with "--assume clean" either? Btw, is there any difference between a newly created array and a pre-existing array that has been -recreated with "--assume-clean"? So is there anything that would make an "mdadm --add" command work on a newly created array but make the same command fail on a re-created array (assuming that the array is indeed clean and data is intact)?
 
Thank you for your help.

---

### Post by dtfinch on 2011-04-23
Did it log anything sde or mdadm related to /var/log/messages?

---

### Post by peterk2011 on 2011-04-23
> **dtfinch said:**
> Did it log anything sde or mdadm related to /var/log/messages?
 
You're spot on again, dtfinch. I was too quick with my judgement, there was nothing wrong with mdadm & the resync, the problem was a I/O error on sde1 (which became sdc1 again since then - i love this scambling game) during the process. The disk had a few unreadable sectors reported by smartd. 
 
I reallocated them with hdparm and doing a full surface rewrite/scan atm. I'll wait for it to finish to decide if i can add it back to the array. I'll be back with the results. Thank you for your assistance!

---

### Post by peterk2011 on 2011-04-24
Ok, the full surface scan finished without errors, and s.m.a.r.t info looks OK. Current_Pending_Sector count (which was 5 before scan) is zero again and there is no reallocated sectors so i suppose the write operation on these sectors have successfully corrected them. So i decided to re-add the disk to the array, it's better than leaving the array degraded for a few days. It's resyncing now.
 
I will closely monitor this disk in the upcoming days/weeks to see it works fine. This array will be a 7 disks RAID6 array in a few days - maybe weeks - time, so it will soon have 2 disks redundancy. If the disk will not show further signs of failing, i might leave it in there. I'll decide it later.
 
Thank you dtfinch for your helpful comments again. I mark this thread solved, i hope i don't halloo too early / am indeed out of the wood. ;)

---

### Post by AllGamer on 2011-04-27
I've very much the same or similar problem, some how after a failed driver update my OS HDD became unbootable, so i simply went ahead and reinstalled ubuntu as it was a quick thing to do via USB key.

but to my surprise after the system came up, and installed **mdadm** back, it was... it still having trouble mounting the volume.

I'm able to assemble them just fine, but it is unable to mount the volume, with this error:

**Error mounting volume**
An error ocurred while performing an operation on "on SATA" (whole-disk volume on 6.0 TB RAID-5 Array): Filesystem driver not installed

then on **Details** it shows:
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/md0, missing codepage or helper program, or other error
in some cases useful info is found in syslog -try dmesg | tail or so

and if i run **dmesg |tail** i get this output:

[66085.733117]  disk 0, o:1, dev:sdb
[66085.733119]  disk 1, o:1, dev:sdd
[66085.733122]  disk 2, o:1, dev:sdc
[66085.733125]  disk 3, o:1, dev:sde
[66085.733186] md0: detected capacity change from 0 to 6001196531712
[66085.733912]  md0:
[66109.049472] EXT3-fs error (device md0): ext3_check_descriptors: Block bitmap for group 1934 not in group (block 0)!
[66109.112479] EXT3-fs (md0): error: group descriptors corrupted
[66682.927915] EXT3-fs error (device md0): ext3_check_descriptors: Block bitmap for group 1934 not in group (block 0)!
[66682.991996] EXT3-fs (md0): error: group descriptors corrupted



the mdadm RAID5 when it was working the volume was formatted to EXT3
the volume name is "on SATA"

is there any way to fix this and rescue my data?



--- additional info ---
inside the **mdadm.conf** the only important line is this:

ARRAY /dev/md0 level=raid5 num-devices=4 UUID=1cd3c907:5ebd7927:310b5b34:c3d51354

all the other lines are default



--- out put from mdadm ---
sudo mdadm -Q -D /dev/md0
/dev/md0:
```

        Version : 00.90
  Creation Time : Tue Mar 15 19:12:55 2011
     Raid Level : raid5
     Array Size : 5860543488 (5589.05 GiB 6001.20 GB)
  Used Dev Size : 1953514496 (1863.02 GiB 2000.40 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Wed Apr 27 22:13:54 2011
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 1cd3c907:5ebd7927:310b5b34:c3d51354
         Events : 0.48

    Number   Major   Minor   RaidDevice State
       0       8       16        0      active sync   /dev/sdb
       1       8       48        1      active sync   /dev/sdd
       2       8       32        2      active sync   /dev/sdc
       3       8       64        3      active sync   /dev/sde

```

---

### Post by AllGamer on 2011-04-28
if i try to force it to start it shows me this

sudo mdadm -C /dev/md0 --assume-clean --level=5 --raid-devices=4 /dev/sdb /dev/sdc /dev/sdd /dev/sde
```

mdadm: /dev/sdb appears to contain an ext2fs file system
    size=1565576192K  mtime=Wed Apr 20 21:28:16 2011
mdadm: /dev/sdb appears to be part of a raid array:
    level=raid5 devices=4 ctime=Tue Mar 15 19:12:55 2011
mdadm: /dev/sdc appears to be part of a raid array:
    level=raid5 devices=4 ctime=Tue Mar 15 19:12:55 2011
mdadm: /dev/sdd appears to be part of a raid array:
    level=raid5 devices=4 ctime=Tue Mar 15 19:12:55 2011
mdadm: /dev/sde appears to contain an ext2fs file system
    size=1297138688K  mtime=Wed Apr 20 21:28:16 2011
mdadm: /dev/sde appears to be part of a raid array:
    level=raid5 devices=4 ctime=Tue Mar 15 19:12:55 2011

```
Continue creating array? y
mdadm: array /dev/md0 started.

---

### Post by peterk2011 on 2011-05-01
> **AllGamer said:**
> if i try to force it to start it shows me this
 
sudo mdadm -C /dev/md0 --assume-clean --level=5 --raid-devices=4 /dev/sdb /dev/sdc /dev/sdd /dev/sde

 
Do you know the exact order in which the disks were added to the array? The query in your first post indicated sdb sdd sdc sde, but for the create command here, you used sdb sdc sdd sde order.
 
It is possible, that during ubuntu reinstall, your drives have been swapped and got different labels - just like in my case. If you don't know the original order, try the above create command with different driver order, then try to mount the array after each try. There are 24 possible variations, you should eventually find the right order.

---

### Post by AllGamer on 2011-05-02
thanks for the idea, but no luck, i kind of tried most likely combinations, and it was a pain in the back, as i had to kept issue these commands to reset it

sudo mdadm /dev/md0 --stop
sudo mdadm --zero-superblock /dev/sd[bcde]

and sometimes it might even lock up even when stopped, and i had to reboot the whole server, to try the next combination

mdadm: Couldn't open /dev/sdb for write - not zeroing
mdadm: Couldn't open /dev/sdc for write - not zeroing
mdadm: Couldn't open /dev/sdd for write - not zeroing
mdadm: Couldn't open /dev/sde for write - not zeroing

sudo mdadm -C /dev/md0 --assume-clean --level=5 --raid-devices=4 /dev/sdb /dev/sde /dev/sdc /dev/sdd
sudo mdadm -C /dev/md0 --assume-clean --level=5 --raid-devices=4 /dev/sdb /dev/sde /dev/sdd /dev/sdc
sudo mdadm -C /dev/md0 --assume-clean --level=5 --raid-devices=4 /dev/sdb /dev/sdc /dev/sdd /dev/sde

i'm sure i'll eventually find it if i keep trying, but the data wasn't that important anyways, those were mostly stuff i can mostly recover from other sources (backups, online, CD, DVD, etc) knowing the **insecure nature of mdadm**, i only saved TEMP data on that RAID, like non important VMware projects, ISOs, and other big chunk temp outdated files.

the mdadm write performance was not the greatest, i've got 3 other FakeRAID in the same server, and those have way better I/O performance for write intensive applications like VMware and alikes.

so, i've pretty much decided to format the whole thing, and simply create everything from scratch, and this time i'll make sure to create some partitions on it, instead of using the full disk

**as it appears to be a known issue and prone to corrupt the super-blocks and/or the RAID partition table when the RAID itself uses 100% of each disk without a partition on each disk**

---

### Post by yanaek on 2011-11-29
I had similar problem recently. I started upgrade to Ubuntu 11.10, there were some messages like "error: Found two disks with the index..." which I ignored (after mdadm upgrade, during grub upgrade) and after reboot I ended up with mdadm not seeing partitions, but using whole disks as array members.

Unfortunately I didn't notice that while plymouth was loading, and it suggested me to fix errors on FS, preventing mounting /home dir.
Not being aware of mdadm problems (I noticed this after next reboot) I accepted fsck changes and ... it destroyed my filesystems , hundreds of Gigabytes of data.

If I saw this thread before using fsck... damn.

---

