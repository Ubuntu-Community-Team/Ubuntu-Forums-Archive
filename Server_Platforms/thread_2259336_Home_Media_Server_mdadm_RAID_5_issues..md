---
title: "Home Media Server mdadm RAID 5 issues."
date: 2015-01-03
forum: Server Platforms
---

### Post by cfrieler on 2015-01-03
Greetings!
First, let me be clear - I know just enough about Linux to be truly dangerous.
I built a server three years ago for home use - Ubuntu 12.04 with a 3ware RAID controller
and 8 - 2TB drives. I set up SAMBA for access from several Win7 systems and my WD TVLive, 
and all was good until we ran it out of space.

I recently built a new server on 14.04 with a Supermicro AOC-SAT2-MV8 controller and 
8 - 4TB WD Red drives.  I configured a single RAID5 volume with mdadm and it formatted in ext4 to >28TB.  
I won't say that configuring SAMBA to provide accessible shares for my collection of Win7 systems was 
trouble-free, but it has worked for the last two months.

We had a power bump this AM, and I have been fighting for 8 hrs now to fix the problems. 
When the server was rebooted, it had an error message on the screen;
"An Error occurred while mounting /mnt/(volume UUID)"
 with the options Skip or Manual.

Selecting Skip allowed the system to boot, but it failed to auto-mount the RAID5 volume. 
Logging on to the desktop, a simple right click > Mount appears to do nothing. 
I started GParted and was able to mount the volume, although it complained that every
one of the eight drive's GPT table was corrupted (separate popup dialog for each) 
"but the backup copy was usable". 

I am deathly afraid of loosing the data on this volume, because I have hundreds of hours 
of labor invested, and no backup for a good portion of it.  Fortunately, when mounted all 
the data appears intact on the volume.

I seem to remember these "corrupted GPT table" messages from when I first set up the 
volume and thought it was just an incompatibility between GParted and mdadm. 
Can anyone confirm that? 

mdstat reports...
md0 : active raid5 sdi[8] sdh[6] sdg[5] sdb[0] sde[3] sdf[4] sdd[2] sdc[1]
27348210176 blocks super 1.2 level 5, 512k chunk, algorithm 2 [8/8] [UUUUUUUU]

Is there a utility that can check the GPT tables on RAID volumes?

After mounting, none of the SAMBA shares are functional. It appears that GParted 
mounted the volume at /mnt, instead of at /media/username as SAMBA expected. 
And after a reboot, the system still fails to auto-mount the volume.

I have been through everything I could turn up through Google in the last 8 hours, 
and am still confused.

Is there a good troubleshooting guide for mdadm?
What is the correct utility to use to check the file system on this volume?
Can anyone point me one or more steps in the right direction?
Thanks for any advice, 
cfrieler

---

### Post by cfrieler on 2015-01-03
I've "solved" my own problem by casting a wider search net and finding a previously 
discussed work-around this long running bug....

[https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/1011257](https://bugs.launchpad.net/ubuntu/+source/gnome-disk-utility/+bug/1011257)

A little pathetic that this has persisted through five releases and still bites users. 
I guess if I weren't such a noob it would be obvious?
So much for "just works".

---

### Post by MAFoElffen on 2015-01-03
Working a lot with things (mdadm, hard-ware raid, LVM, etc)... and now going back to school to document my skills and certificatons: "RAID is not a substitute for backups."

If you are using RAID, and like living on the edge... the #1 problem I see here and help people with, is recovering a RAID Array, (were they don't have a backup)... and the filesystem was not closed gracefully. 

Biggest prevention for that is a UPS. Doesn't have to be big. Just enough so the system and filesystem can finish any commits and shutdown gracefully. I don't know how much that would save so many from so much grief.

---

