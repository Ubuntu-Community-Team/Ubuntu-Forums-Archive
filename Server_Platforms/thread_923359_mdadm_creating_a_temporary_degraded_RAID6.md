---
title: "mdadm creating a temporary degraded RAID6?"
date: 2008-09-18
forum: Server Platforms
---

### Post by plonka2000 on 2008-09-18
Hi all,

I'm looking at creating a RAID6 with 4 drives initially (I know, its not worth running RAID6 in 4 drives, might as well run RAID0+1 or RAID10, I did my reading but I plan to expand soon).

The reason I need to do this is because I only currently have 3 drives usable... All the rest have the data that I want on my RAID6 array. I also plan over the coming months to expland this array somewhat.

So will I be able to create an partially degraded array using the command:

```
mdadm --create /dev/md0 --level=raid6 --raid-devices=4 /dev/sda1 /dev/sdb1 /dev/sdc1 missing
```

Then after my array is created and I've ported as much data over as possible (I assume 2 equal drives worth), can I then put my additional drives in and grow my array onto them?

I would also appreciate some advice on the correct way to do this and the correct commands please.

Thanks all.

---

### Post by fjgaude on 2008-09-18
I see no reason why what you are wanting to do will not work. Sure, but make sure you let the array fully build before putting the filesystem on it using this:

```
sudo watch /proc/mdstat
```

After it finsihed, mkfs:

```
sudo mkds -t ext3 /dev/md[n]
```

```
sudo watch /proc/mdstat
```

Mount the array to a mountpoint you have created. Then you can add the files to it. Also you can add a line in /etc/fstab to auto mount the array.

Here's things to read, study about using software raid:

[http://shsc.info/LinuxSoftwareRAID](http://shsc.info/LinuxSoftwareRAID)
/usr/share/doc/mdadm/FAQ.gz  and md.txt.gz
[http://blog.tcg.com/tcg/2006/04/recovering_raid.html](http://blog.tcg.com/tcg/2006/04/recovering_raid.html)

Let us know how things are going.

---

### Post by plonka2000 on 2008-09-18
Hi and thanks for your help.
I really appreciate it.

I did as follows:
```
mdadm --create /dev/md0 --level=raid6 --raid-devices=5 /dev/sda1 /dev/sdb1 /dev/sdc1 missing missing
```
...and my array is built.
I'm a little concerned as I'm running 5 instead of 4 as I originally planned which means I'm running fully degraded, because I want to port 2 disks in as soon as the data is copied from them... So naturally I'm extra paranoid and want to get this just right first time.

**FYI: I built my 'first' 3 disks into a RAID5 yesterday, and after much thinking I thought a RAID6 would be better as my primary concern is redundancy.**

The result of my using:
```
watch cat /proc/mdstat
```
...gave this output (With nothing changing/updating).

```
Every 2.0s: cat /proc/mdstat                            Thu Sep 18 16:25:09 2008

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [ra
id10]
md0 : active raid6 sdc1[2] sdb1[1] sda1[0]
      1465151808 blocks level 6, 64k chunk, algorithm 2 [5/3] [UUU__]

unused devices: <none>
```

Because I used the same disks to build my RAID5 yesterday, is it not going to rebuild now that I'm using the same disks for a RAID6 now? I cant see the same building output when using 'watch' that I did yestersay.

I'm just concerned if the array is ready and stable.

Also, I'm a little confused which command to use to get my disks /dev/sdd and /dev/sde into my (degraded) array. do I just do the *mdadm --grow* command to get my last 2 initial disks into the array?

Thanks again.

[I]Edit:
The command I used for my filesystem before mounting /dev/md0 to /raid was:
```
mkfs.xfs -f /dev/md0
```
I assume that is an acceptable command to use XFS?[/I]

---

### Post by fjgaude on 2008-09-18
You might wish to first stop the array, un-mount it and then for the two drives that might be, or have been, part of the array to zero their superblocks:

```
sudo mdadm --zero-superblock /dev/sd[n]
```

If the drives turn out being busy, then fail and remove them:

```
sudo mdadm /dev/md0 --fail /dev/sd[n]
sudo mdadm /dev/md0 --remove /dev/sd[n]
```

Also after drives are added to expand an assay you need to use resize:

```
sudo resize2fs /dev/md[n]
```

I believe that command resizes to the max block size... have to read the man pages for it to know for sure, especially if it handles xfs filesystem. [It doesn't, only ext3]

Please study the reference material I posted... there is so much to learn, and so much that can be done that makes recovery difficult if not impossible.

Also, from here on out backups are indicated as necessary... I use three, one online, near-line, and off-line. For important data backups are demanded.

---

### Post by plonka2000 on 2008-09-18
Hi again,
I've gone through doing this a few times now and the same result comes back each time.

I stopped the array, zeroed the superblocks of each drive's partition 1 and then recreated it.

For some reason, mdadm does not seem to be regenerating the array.

I also seem to be getting an I/O error that I was not getting before:
```
root@soundwave:~# sudo mdadm --create --verbose /dev/md0 --level=6 --raid-devices=4 /dev/sda1 /dev/sdb1 /dev/sdc1 missing
mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 64K
mdadm: size set to 488383936K
mdadm: RUN_ARRAY failed: Input/output error
mdadm: stopped /dev/md0
```

Any ideas?

---

### Post by plonka2000 on 2008-09-18
Hi again,
From what I can tell, the RAID6 is working fine in degraded mode even though it hasnt gone through a complete rebuild.

I have looked through the official docs as well as the link you kindly provided but I cannot find a command to force a complete resync. Do you know of one?

I have gone back and again zeroed all my superblocks and recreated my RAID6. Here is my mdadm monitoring output:
```
root@soundwave:~# mdadm --manage --stop /dev/md0
mdadm: stopped /dev/md0
root@soundwave:~# mdadm --zero-superblock /dev/sda1
root@soundwave:~# mdadm --zero-superblock /dev/sdb1
root@soundwave:~# mdadm --zero-superblock /dev/sdc1
root@soundwave:~# mdadm --create /dev/md0 --level=raid6 --raid-devices=5 /dev/sda1 /dev/sdb1 /dev/sdc1 missing missing
mdadm: array /dev/md0 started.
root@soundwave:~# mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Thu Sep 18 21:53:32 2008
     Raid Level : raid6
     Array Size : 1465151808 (1397.28 GiB 1500.32 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 5
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Sep 18 21:53:32 2008
          State : clean, degraded
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 64K

           UUID : 6c8d5e8e:c8ccfded:1a7f0e04:078bab31
         Events : 0.1

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1
       3       0        0        3      removed
       4       0        0        4      removed
root@soundwave:~# watch cat /proc/mdstat
```

It shows as clean and mounted, but obviously degraded.
Am I safe to assume that this is acceptible to use from here on?

Thanks again.

---

### Post by plonka2000 on 2008-09-19
I've been having some serious issues remounting my RAID6 and making it stick. I think for some reason the superblock is not clearing even though it is not erroring anymore.

---

### Post by fjgaude on 2008-09-19
I guess I'm confused on what you are doing... you have three drives in a raid6 array... with two others that are to go into it?

I'm not sure you can assemble a raid6 with only three drives, with two missing. Seems like it should be okay.

Now the two drives that are to go into the array, have you added them yet?

Have you lost any important data?

Sorry, I'm in and out and don't have that much time to be at the computer.

---

### Post by plonka2000 on 2008-09-19
Hi again, and its cool, I really appreciate your time.
I'm working nights at the moment so I'm able to work on this throughout the night tonight. :)

From what you said, I think you understand what I'm trying to do.

I want to create a RAID 6 from 5 drives, but only 3 are currently available.

I havnt wiped and added the 2 last drives yet, as I'm confused as to whats happening with my array and why /dev/md0 doesnt seem to build/sync when I create it. Data loss is my nightmare at the moment, but I right now have nowhere to backup the 1TB of data currently on the 2 500GB disks not initially in the array.

I've read through various mdadm manuals and howtos and it doesnt state anywhere how to force a rebuild of the array. I'm wondering if the array will just not bother to rebuild/resync until I add the last 2 drives to make a complete array?
All the guides I have seen just assume things are building correctly.

This **assumption** would make sense a bit because the parity in RAID 6 would occupy the equivalent storage space of 2 drives from the array, right? So if 2 drives were missing, mdadm may not see the point in building until the last 2 drives are added...

I dont like making assumptions.
The problem is, I cant see anything to prove this guesswork wrong.

---

### Post by plonka2000 on 2008-09-19
Ok, so here is the train of thought that I think I should follow when creating an array... I need some validation here to see if I'm doing this correctly or if I'm missing something or doing something wrong.

*FYI, all actions are run as root.*
**First, I zero all the disks:**
```
#mdadm --zero-superblock /dev/sda1
#mdadm --zero-superblock /dev/sdb1
#mdadm --zero-superblock /dev/sdc1
```

**next, I format each partition with XFS:**
```
#mkfs.xfs /dev/sda1 -f
#mkfs.xfs /dev/sdb1 -f
#mkfs.xfs /dev/sdc1 -f
```

**next, now that I know all partitions are ready and formatted, create array:**
```
#mdadm --create /dev/md0 --level=raid6 --raid-devices=5 --chunk=128 /dev/sda1 /dev/sdb1 /dev/sdc1 missing missing
```

At this point the array should start syncing/building as far as I know, but it doesnt.
**The only output I get is:**
```
#watch cat /proc/mdstat
Every 2.0s: cat /proc/mdstat                            Thu Sep 18 16:25:09 2008

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [ra
id10]
md0 : active raid6 sdc1[2] sdb1[1] sda1[0]
      1465151808 blocks level 6, 128k chunk, algorithm 2 [5/3] [UUU__]

unused devices: <none>
```
**and:**
```
root@soundwave:~# mdadm --detail /dev/md0
/dev/md0:
        Version : 00.90.03
  Creation Time : Thu Sep 18 21:53:32 2008
     Raid Level : raid6
     Array Size : 1465151808 (1397.28 GiB 1500.32 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 5
  Total Devices : 3
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Sep 18 21:53:32 2008
          State : clean, degraded
 Active Devices : 3
Working Devices : 3
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 128K

           UUID : 6c8d5e8e:c8ccfded:1a7f0e04:078bab31
         Events : 0.1

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1
       3       0        0        3      removed
       4       0        0        4      removed

```
**Then after the array is 'built' I'm supposed to format the Filesystem before mounting:**


As far as I can tell, this is the correct process to follow to build a proper array.

**Some questions I have:**
(1)A particular howto/manpage I read said that I should be marking/formatting each drive partition (/dev/sda1, etc) as 'fd' or 'RAID Autodetect' instead of XFS/EXT3. Is this correct, o it would look like this?:
```
root@soundwave:~# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0305dfe3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   fd  Linux raid autodetect
```

(2)The /dev/md0 is supposed to come up at boot, right?
It doesnt, but I cant find anywhere to troubleshoot this.

(3)Is there a way to force a resync with a fully built array, nevermind with a partially built one? I cant seem to find reference to it. IF i use *--force* during creation with *mdadm --create* (Which I tried) should it force a full build regardless?

(4)Is it possible that my superblocks are not zeroing correctly?
How can I verify this? Again I cant find any reference apart from a vague thread on this forum which mentioned the tool ***blockdev***?

---

### Post by fjgaude on 2008-09-19
> Some questions I have:
(1)A particular howto/manpage I read said that I should be marking/formatting each drive partition (/dev/sda1, etc) as 'fd' or 'RAID Autodetect' instead of XFS/EXT3. Is this correct, o it would look like this?:
Code:
root@soundwave:~# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0305dfe3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   fd  Linux raid autodetect

Yes, I do it with **cfdisk**... I think it's okay to do it with **gparted**. But even then, the only reason for that is when you are using the --scan command. This command is very useful. Have you looked at your /etc/mdadm/mdadm.conf file to see what it is like now?

> (2)The /dev/md0 is supposed to come up at boot, right?
It doesnt, but I cant find anywhere to troubleshoot this.

It only comes up automatically if you have a line in /etc/fstab file that mounts it to your mountpoint during boot.

> (3)Is there a way to force a resync with a fully built array, nevermind with a partially built one? I cant seem to find reference to it. IF i use --force during creation with mdadm --create (Which I tried) should it force a full build regardless?

Not to my knowledge... during create the array is build, period. What you do trying to do is out-of-the-mainstream.

> (4)Is it possible that my superblocks are not zeroing correctly?
How can I verify this? Again I cant find any reference apart from a vague thread on this forum which mentioned the tool blockdev?

If you don't get a drive or array busy message then the superblocks have been zeroed correctly.

You are trying to create a raid6 array, which requires four drives, and the two missing are not being handled correctly by mdadm. That's about all I can think of.

Let's go over why you wish raid6. Two drives can fail... with modern drives this is likely not to ever happen. Your CPU, motherboard, etc., will likely fail long before two drives fail. Try, as a test, creating a raid5 with three drives and two missing, and see what happens.

---

### Post by plonka2000 on 2008-09-19
Ok, I've tried something a little different with what seems to be good results. Today, I totally reinstalled my server from scratch and got it up and running, and installed just mdadm and webmin (I've been using Webmin for remote admin, and from my experience now and in the past, I think its a top quality piece of software!).

FYI: Reinstalling the entire server wasnt a big problem since nothing is 'live' on it, and its still just basic services (That was the point of this server, simple and easy to replace. The main complicated and voilatile stuff will be in Virtual Machines which will run on top of it stored on the RAID6 which will grow much bigger than 5 disks... Hence RAID6).

Anyway, I tried something different after reinstalling.
Installed just the basic system, mdadm and webmin and used Webmin from my workstation to create my 'Linux RAID' partitions, **THEN** went to remote SSH console and used the following:

```
root@soundwave:~# sudo mdadm --create --verbose /dev/md0 --level=6 --chunk=256 --raid-devices=5 /dev/sda1 /dev/sdb1 /dev/sdc1 missing missing
mdadm: layout defaults to left-symmetric
mdadm: size set to 488383744K
mdadm: array /dev/md0 started.
```
I got the RAID running now, then went back to Webmin and formatted **/dev/md0** as ext3:
*FYI: I really want to use XFS but it doesnt seem to be an option in Webmin, so I'm trying the safe ext3 route for now.*
```
**Executing command** mkfs -t ext3 /dev/md0 ..

mke2fs 1.40.8 (13-Mar-2008)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
91578368 inodes, 366287808 blocks
18314390 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=4294967296
11179 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
	32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
	4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
	102400000, 214990848

Writing inode tables:     0/11179... etc... 11179/11179
Creating journal (32768 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 20 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.

.. command complete.
```

**FYI: I've attached a pic of how my RAID6 now looks in Webmin (Webmin_01.jpg).**

Webmin is reporting everything as ok, and shows that the array is degraded. I'm feeling a lot more comfortable about this now.
I'm going to plug my other 2 drives in now and start porting the data over.

---

### Post by plonka2000 on 2008-09-19
Further to that, I reinstalled xfsprogs:
```
sudo apt-get install xfsprogs
```

AND 'SGI' turned up as an option for me to format the /dev/md0 device. I've since formatted it (Via Webmin) to XFS and its all good running XFS now too. :)
Here is my output:
```
**Executing command** mkfs -t xfs -f /dev/md0 ..

meta-data=/dev/md0               isize=256    agcount=32, agsize=11446528 blks
         =                       sectsz=4096  attr=0
data     =                       bsize=4096   blocks=366287808, imaxpct=25
         =                       sunit=64     swidth=192 blks, unwritten=1
naming   =version 2              bsize=4096  
log      =internal log           bsize=4096   blocks=32768, version=2
         =                       sectsz=4096  sunit=1 blks, lazy-count=0
realtime =none                   extsz=786432 blocks=0, rtextents=0

.. command complete.
```

This is looking good.
Gonna do a reboot to make sure everything comes up on boot as expected, then going to plug in additional drives and start porting over.:)

[I]Edit:
I've rebooted and everthing seems to have come up as expected.
I've attached a pic from Webmin of the mount points. The RAID **/dev/md0** is come up on **/raid** just fine and is showing 1.37TB as I was hoping. 

Time to shut down and plug in the other 2 disks.[/I]

---

### Post by fjgaude on 2008-09-19
Fine... one way or another, eh? webmin has been an option that many have used with success. I'll start recommending it to folks.

Let us know if everything is in fact okay as you add more drives.

---

### Post by plonka2000 on 2008-09-19
> **fjgaude said:**
> Fine... one way or another, eh? webmin has been an option that many have used with success. I'll start recommending it to folks.

Let us know if everything is in fact okay as you add more drives.

Yep, so far so good...
Next:
-Get my data ported from both additional drives.
-Add the drives into the array and verify the array integrity.
-Add samba for LAN access/backups.
-Add VMWare for My project VMs.
(I'm in the VMWare Server 2.0 testing program)

Provided the array works and doesnt destroy my 1TB of data (I'm still sweating about that possibility), I dont see much else going wrong except maybe VMWare Server v2 having install issues, which I noted from their notes.

I've also been trying to keep track of as much as possible and I've made many many notes. Maybe I may write up my own howto after all this is done.

**SOmething else:**
Can you help me with the correct commands to add my 2 disks into the array as the missing disks? Do I just do an ***--add*** command or is there something else?
Also, should I add them one at a time and rebuild the array onto them or add both at once?

Thanks for all your help.
I really appreciate it no end.

---

### Post by fjgaude on 2008-09-19
It's been a long time since I added a drive to an existing array. If memory serves, I had a three-drive array, and wanted to add one drive. I did this:

```
sudo mdadm --grow --raid-devices=4 /dev/md0
```

That added one drive. For you, you would do this twice or go to 5 right off.

On the other hand, you might simply try the --add command, since you have already stated that the array is 5 drives, two missing.

The thing that concerns me is the /etc/mdadm/mdadm.conf file... what it shows now for ARRAY and what it should show after you have made the drive additions. Please look at the file, notice what it says, then do the add.

Gosh, the more I think of what you are doing the more thoughts come to mind. The three-drive array you have now, is there good data on them? I see, your issue is you don't have enough drives in hand to do this the normal way. Question, can you copy a file to the existing array and read the file?

Maybe webmin is your easy way to add drives, partitions.

As a reminder, always, no matter what, have backups of your important data. A raid array is not sufficient... many of us know this from the hard knocks of experience. Especially if you are in business of making a living out of all of this. I nornally have three backups, online, near-line, off-line. If you have data on those two disks you are to copy over and add to the existing array, I'd wait until I get two new drives to add to the array... but it's up to you.

You will have little trouble with VMware... it is a solid program which I've used for over two years now. Notice my signature. <grin>

---

### Post by plonka2000 on 2008-09-19
I know what you mean, I've been thinking about all the possibilities as to why things have been happening the way they have and I have come to a few educated guesses.

Firstly, the reason the array isn't building (Remember this is a guess) is because its not physically possible. If parity is to be maintained for 2 drives in a 5 drive RAID6 array which is degrades by 2 drives, how is it supposed to store parity? It doesnt physically have the storage for the parity, so I think it will build parity when 1 or 2 drives are added, bringing it upto 4/5 (Partially degraded) or 5/5 (Totally clean).

Secondly, the first *guess* is assuming mdadm was written that intelligently, which so far it seems it has been. One of the ways I think I can verify this is try and scrounge up as much random storage I can, and make a backup of as much as I can of one of the 'missing' drives (500GB worth of data), then ***--add*** it to the array and watch what happens. If all goes well and the array is then built onto that disk, then I can simply ***--add*** the final 'missing' disk and have a complete array again. If I'm wrong, either the parity wont work and the whole array will appear to run fine and not be running fine, or it will just fall over and die, possibly corrupting the data on all the drives involved.

As far as I can tell, because I'm monitoring the data migration quite closely, all the data seems to be moving over quite fine. Its also readable from the array (Which I have shared read-only using samba). There are no problems accessing anything yet (That a local ***chmod 777*** wont fix).

I got the contents of my /etc/mdadm/mdadm.conf file but it doesnt look to be much help:
```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays

# This file was auto-generated on Fri, 19 Sep 2008 20:14:47 +0100
# by mkconf $Id$
```

It looks pretty untouched to me, but I'm not entirely sure what an *untouched* mdadm.conf should look like really.

FYI: I'll be up all night as I'm working all night on other things too, though I doubt that at 2am you're still waking.

Also, I'm aware of multi-level backups and in fact I'm quite paranoid about it myself. I'm looking at this as my first stage of a bigger backup plan. This is a location that my other systems will be mirroring/syncing to, so its an online backup for other locations. As for offline backups, I keep the most important things offline as well already.

The main point of this being a Linux based RAID6 is because its expandable and portable (I can build a new/bigger/badder server and move my disks there if need be, but I think I can fit 10 disks into my current setup).

---

### Post by fjgaude on 2008-09-19
Okay, but from your mdadm.conf file I can't see how the array was created. The key line is missing; here's that line from my file for my four-drive raid5:

```
# definitions of existing MD arrays
ARRAY /dev/md32 level=raid5 num-devices=4 UUID=bc41e255:0b455fd4:4aef2e68:cb22f42a
```

Well, for raid6 there are two writes that are on all drives in the array, so that two can fail and the array runs along but no data is lost.

As long as you can successfully write to the existing three-drive array I guess everything is okay. **mdadm** is matural, coming really from the Linux raidtools of years ago.

Add one drive and watch what happens with watch /proc/mdstat, after you have removed as much data as possible from the added drive.

Good luck, take to you tomorrow morning.

---

### Post by plonka2000 on 2008-09-21
Ok, this saga isnt quite completed yet, but I have some answers and some things have happened, good and bad. I also had a chance to mess with the array and point out some things that others may want to know about, including yourself fjgaude.

Firstly, **the array failed**, and I lost 500GB of data.
Luckily, I made a back up of essentials, which was about 400GB worth of it... So no panic there, at least not this time.

I do think I know what happened for people who try this approach in the future. The bottom line is, **it works if it is done to the letter and is done incrementally.**

My array failed after I ported just under 1TB of data over from the 2 NTFS drives (Took a long time) and restarted the system to be again sure the RAID6 array would come back up. It didnt come back up.
The reason my array failed I suspect is because (After backing up to another system over LAN) I added the next disk **/dev/sdd1** into the array and then removed it a few second later.
I removed it by first failing it, so the system would know, then removing it as a resource.
**[COLOR="Red"]FYI: DO NOT DO THIS![/COLOR]** Although my array carried on working, I suspect some of the parity data was reconfigured for the new drive and was therefore missing.

Moral of that story, even though your array will still continue working live if a drive is added then removed, it will not start again if it is stopped, until that drive is then re-added so that the 3-with-2-missing to 4-with-1-missing rebuild can complete.

When the system was restarted, **/dev/md0** would not come up again and so after the initial shock and widened my eyes, I investigated. :-k It seemed that the superblock of **/dev/sda1** was somehow wiped (I suspect by mdadm itself as part of the user-aborted rebuild operation). When I tried to **--assemble** or **--build**, it refused, claiming there is no valid superblock data on **/dev/sda1**, when there clearly was before.

I then did an identical rebuild (3 out of 5 drives, fully degraded) and ported over a few GB of data from the last remaining NTFS drive **/dev/sde1** and added **/dev/sdd1** back in as I did before. I let the rebuild complete and looked at my output for monitoring. It listed:
```
#watch cat /proc/mdstat
Every 2.0s: cat /proc/mdstat                            Sun Sep 21 17:37:34 2008

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid6 sda1[0] sdd1[3] sdc1[2] sdb1[1]
      1465151616 blocks level 6, 128k chunk, algorithm 2 [5/4] [UUUU_]

unused devices: <none>
```

For comparison here is a copy of the fully degraded output:
```
#watch cat /proc/mdstat
Every 2.0s: cat /proc/mdstat                            Thu Sep 18 16:25:09 2008

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid6 sdc1[2] sdb1[1] sda1[0]
      1465151808 blocks level 6, 128k chunk, algorithm 2 [5/3] [UUU__]

unused devices: <none>
```

So it looks like an **--add** command will add the drive as spare then automatically add it to the array to fill one of the missing 2 drives. This is good news at least.
**The main reason I was worried and needed to know what would happen here**, was because when building a 5-drive and fully degraded (2 drives missing) RAID6, the array does not 'build'; Its just there, ready to rock running in fully degraded mode. I think this supports my educated guess about the parity earlier. It cant generate parity, because there is no additional parity on a fully degraded RAID6, therefore it will build when 1 or 2 drives are added.

**_Obviously, I cannot confirm if the same array failure will occur if adding then removing the 2nd missing disk, but I can only *GUESS* that it would continue to work considering there should be enough parity spread across the other 4 present drives to allow it._** Also, this is the way RAID6 was designed; to withstand a simultaneous 2-drive failure or have 1 fail while the array is recovering from 1 failure.
_I still wouldnt do it though._

---

### Post by fjgaude on 2008-09-21
Thanks for your input... we have stated to always let things finish before starting the next step... yep, two parity writes to each drive in raid6.

Adding a drive in puts it into a spare mode... not into a expand the array size mode.

What you are doing I've never done, and hope I never have to.

New versions of mdadm 2.6.3, all the way to 2.6.7 that's in beta now, should be coming into Ubuntu to help pervent issues when stopping an array while it is still in re-sync modes.

Most of my knowledge about mdadm comes from testing two, three, and four drives in raid0, 1, and 5 modes. With the reliability of drives I never saw a need for raid6.

Keep us informed about your doing.

---

### Post by plonka2000 on 2008-09-23
Well all seems to be going well so far.
I still havnt added the last drive yet, as that is the no-going-back stage for me as it means to backup and revert to anything else is out of the question at that point, unless I rip 2 disks out and run this whole RAID6 process backwards.

I've migrated my data over and kept backups still. At the moment I'm just sitting on it to see how it pans out for a bit.

Now there is something I wanted to throw out there to find out.
I noticed that my RAID6 is a LOT slower than my RAID5 on the same hardware. I'm sure it cant be just down to the additional parity overhead.

I was getting superfast 40-50MB/sec over my gigabit LAN before all of this using RAID5, but now I can barely scrape 8MB/sec.

Can you assist me with working out if this is just the speed that RAID6 runs at, or if there is something I can work out.

I also wondered if this was to do with running in degraded mode, but I figured that it shouldnt run this slowly.

Thanks again.

---

### Post by fjgaude on 2008-09-24
The speed of a raid6 is n-2 times the number of drives in the array. For example, if each drive has 70 MB/sec throughput, then a six-drive array should have 240 MB/sec. This is only true if the controller has the throughput, which is true for PCI-E and -X, but not for straight PCI.

When I stop one drive in my four-drive raid5 array and it runs degraded, the throughput goes down to that of two drives, i.e., 140 MB/sec.

I would say you have something else going on with that 8 MB/sec issue.

---

### Post by plonka2000 on 2008-09-24
From what I have been reading online, I get the feeling that RAID5 with mdadm is a lot more optimised that RAID6 with mdadm. This troubles me quite a bit but I'm currently in a unique position in that I can further test this before settling.

I'm keen on RAID6 (Very keen) because of the redundancy but if this is the level of performance I will be getting, then I may have to rethink.

This is my current throughput:
```
root@soundwave:~# hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   2604 MB in  2.00 seconds = 1302.06 MB/sec
 Timing buffered disk reads:  276 MB in  3.02 seconds =  91.52 MB/sec
root@soundwave:~# hdparm -tT /dev/sdb

/dev/sdb:
 Timing cached reads:   2228 MB in  2.00 seconds = 1114.27 MB/sec
 Timing buffered disk reads:  250 MB in  3.00 seconds =  83.28 MB/sec
root@soundwave:~# hdparm -tT /dev/sdc

/dev/sdc:
 Timing cached reads:   2204 MB in  2.00 seconds = 1101.43 MB/sec
 Timing buffered disk reads:  272 MB in  3.02 seconds =  90.20 MB/sec
root@soundwave:~# hdparm -tT /dev/sdd

/dev/sdd:
 Timing cached reads:   2304 MB in  2.00 seconds = 1151.76 MB/sec
 Timing buffered disk reads:  234 MB in  3.01 seconds =  77.85 MB/sec
root@soundwave:~# hdparm -tT /dev/sde

/dev/sde:
 Timing cached reads:   2250 MB in  2.00 seconds = 1125.41 MB/sec
 Timing buffered disk reads:  244 MB in  3.02 seconds =  80.91 MB/sec
root@soundwave:~# hdparm -tT /dev/sdf

/dev/sdf:
 Timing cached reads:   2156 MB in  2.00 seconds = 1078.00 MB/sec
 Timing buffered disk reads:   56 MB in  3.06 seconds =  18.30 MB/sec
```

Let me explain the current layout of my disks.
I have 1 onboard Intel ICH7 SATA-II 4-Port controller (_/dev/sda_+_sdb_+_sdc_+_sdd_) and a single 2-Port Sil3512 RAID-I card in a PCI slot that currently has 1 port used (Effectively _/dev/sde_).

_/dev/sdf_ is a 4GB USB key that Ubuntu itself is installed on and also the boot drive.

Considering I should be getting throughput of 2 drives at least, then I dont know whats happening. Here is the bandwidth output of _/dev/md0_:
```
/dev/md0:
 Timing cached reads:   2250 MB in  2.00 seconds = 1125.10 MB/sec
 Timing buffered disk reads:  364 MB in  3.00 seconds = 121.21 MB/sec
```

As far as I can tell, this is below normal but considering overheads should be sustainable.

Why then am I getting horrible transfers over my gigabit LAN?
I would expect to get 30MB/sec as a bare minimum for an unsaturated home gigabit LAN.

As far as I know, write speeds will be somewhat reduced due to parity, but do you have any idea I should expect? (I ultimately mean by pushing data from my Windows workstation to the server)

Maybe since I now have 4 drives available and reliable temporary backup, I should re-make a 4-Drive-only RAID5 and test that throughput then recreate a 4-Drive-only RAID6 and compare?

Thanks for all your help.

---

### Post by plonka2000 on 2008-09-24
FYI: I've never liked using the 2-Port Sil3512 PCI card.
I have planned to swap out the motherboard in my server with the one in my Vista workstation, which currently has 8 onboard SATA-II ports. It will mean I dont need to buy a SATA-II card too.

---

### Post by fjgaude on 2008-09-24
I would expect to get up to 110MB/sec down a gigabit LAN, with large-file transfers.

I see your drives are in the over-70MB/sec range meaning they are new, very new. Good!

Here's my run using hdparm, with Xigmatek DHT-S1283 cooler, CPU at 4.0GHz (9 x 445), memory at 1066MHz (2.4 * 445) (FSB 4 x 445 = 1780 MHz) 2/26/08, fan at 908 RPM; no-load, temp=23C; under max load, temp=42C, fan=1167 RPM; VCore=1.38/1.36v, **four-drive raid5**:

```
root@sunshine:/home/frank# hdparm -tT /dev/md32
/dev/md32:
 Timing cached reads:   19216 MB in  2.00 seconds = 9622.09 MB/sec
 Timing buffered disk reads:  638 MB in  3.01 seconds = 212.01 MB/sec
```

You might try the test of four drives with raid6 and see just how fast it is. If your controller for the four drives is PCI, and it might be with the ICH7 set, then 110MB/sec is all you can hope for, even through the drives would permit 160MB/sec or so with raid6 and your fast drives.

As said before, I know nothing of raid6 with mdadm... never saw the need. I did play around with arrays that are madeup of arrays: three-drive raid5 that uses three, three-drive arrays, nine total drives. Worked great under mdadm. <smile>

Keep us informed as to your doings.

---

### Post by plonka2000 on 2008-09-24
Now you have piqued my interest!
YEah the drives are new indeed... The first 3 new ones are Samsung SAMSUNG HD502IJ's, and the last 2 are SAMSUNG HD501LJ's.

I know theyre fast drives and I love the Samsung Spinpoints Drives.
They have exceeded all my expectations in all uses not just in my server, but we used 4 of them at work also in a Netgear ReadyNAS... Sooo sweet.

I'm currently rebuilding my array into a 4-Drive RAID6.
I'm using a 64K chunk size, which I think is the mdadm default, although for some reason, Webmin defaults to a 4kB chunk size. :confused:
I've experimented with chunk size using all the way upto a 256kB chunk at one point, which was interesting with latrge writes but was not very effective for streaming, strangely.

Any thoughts on chunk size again?
I'm guessing you use the default 64kB?

After this, I want to setup a 4-Drive RAID5 and test that also so we can all see the benefits or not of doing this.

The specs of my server are not stellar but more than enough to do what I want:

Core2duo E6300 1.83GHz, 3GB RAM @DDR2 PC2-5300/667, Gigabyte GA-945P-S3 Motherboard.

Current progress:
```
Every 2.0s: cat /proc/mdstat                                  Wed Sep 24 22:16:51 2008

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid6 sdd1[3] sdc1[2] sdb1[1] sda1[0]
      976767872 blocks level 6, 32k chunk, algorithm 2 [4/4] [UUUU]
      [=>...................]  resync =  9.1% (44874420/488383936) finish=119.0min speed=62068K/sec

unused devices: <none>
```

---

### Post by fjgaude on 2008-09-24
For my work I've tried 64K and 128K for chunk without noticing any difference. Using 64K now...

Do let us know the results of your tests...

---

### Post by plonka2000 on 2008-09-25
ok, so I ran a few basic disk array tests.

I've been remoting home from work all day, taking results then setting the build off again. I must say, Webmin makes mdadm RAID management so easy.

I formed a RAID6 array with 4 drives, with chunk sized of 32K, 64K and 128K and I did a basic hdparm -tT on each configuration.
I ran it twice from 64K and 128K to make sure results were consistent in this test.

The results are below:

**RAID6 32K**
```
/dev/md0:
 Timing cached reads:   2420 MB in  2.00 seconds = 1209.68 MB/sec
 Timing buffered disk reads:  290 MB in  3.00 seconds =  96.56 MB/sec
```

**RAID6 64K**
```
/dev/md0:
 Timing cached reads:   2502 MB in  2.00 seconds = 1251.49 MB/sec
 Timing buffered disk reads:  300 MB in  3.01 seconds =  99.58 MB/sec

/dev/md0:
 Timing cached reads:   2486 MB in  2.00 seconds = 1242.71 MB/sec
 Timing buffered disk reads:  312 MB in  3.01 seconds = 103.56 MB/sec
```

**RAID6 128K**
```
/dev/md0:
 Timing cached reads:   2464 MB in  2.00 seconds = 1232.01 MB/sec
 Timing buffered disk reads:  244 MB in  3.02 seconds =  80.75 MB/sec

/dev/md0:
 Timing cached reads:   2490 MB in  2.00 seconds = 1245.51 MB/sec
 Timing buffered disk reads:  250 MB in  3.02 seconds =  82.89 MB/sec
```

The results dont seem that different.
Maybe my onboard ICH7 is PCI limited? I would have thought it would have been put on the PCI-E bus.

So now I'm forming a 4-Drive RAID5 to see the difference.
This should take less time than RAID6 forming as less parity to setup...

```
Every 2.0s: cat /proc/mdstat                                       Thu Sep 25 18:11:51 2008

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdd1[3] sdc1[2] sdb1[1] sda1[0]
      1465151808 blocks level 5, 32k chunk, algorithm 2 [4/4] [UUUU]
      [==>..................]  resync = 10.1% (49455744/488383936) finish=96.6min speed=75709K/sec

unused devices: <none>
```

---

### Post by fjgaude on 2008-09-25
If you can't get above about 110MB/sec with a four-drive raid5 array then you know you are on the PCI bus with the controller. That ICH7 chipset is old, but I don't recall just how old and when Intel switched to having their ATA controllers running off the PCI-E. I have ICH9 on my MB and have the block design of the chipset showing how the controllers run off the PCI-E X1 bus. Wish it was X4 but not so.

The PCI-E X1 is said by Intel to have a bandwidth of 500MB/sec. I've seen tests with raid arrays showing it will go to 450MB/sec contoller, drive, array throughput.

Glad to see you doing all this testing. I'll likely start again when I get one more 120MB/sec Seagate, 320G drive... Should have it next week. Will use it for booting. Right now I use a WD Raptor, 36G, very quick, and fast too. If it doesn't boot faster than I'll use it as online backup for my array.

---

### Post by plonka2000 on 2008-09-25
RAID5 basic test have completed.

it loosmlike the reduced parity does bring some performance in terms of disk reads at least.

**RAID5 32K**
```
/dev/md0:
 Timing cached reads:   2482 MB in  2.00 seconds = 1240.92 MB/sec
 Timing buffered disk reads:  476 MB in  3.01 seconds = 158.37 MB/sec

/dev/md0:
 Timing cached reads:   2464 MB in  2.00 seconds = 1231.99 MB/sec
 Timing buffered disk reads:  480 MB in  3.01 seconds = 159.68 MB/sec
```

**RAID5 64K**
```
/dev/md0:
 Timing cached reads:   2474 MB in  2.00 seconds = 1236.90 MB/sec
 Timing buffered disk reads:  534 MB in  3.00 seconds = 177.75 MB/sec

/dev/md0:
 Timing cached reads:   2438 MB in  2.00 seconds = 1218.81 MB/sec
 Timing buffered disk reads:  544 MB in  3.00 seconds = 181.28 MB/sec
```

**RAID5 128K**
```
/dev/md0:
 Timing cached reads:   2454 MB in  2.00 seconds = 1226.84 MB/sec
 Timing buffered disk reads:  466 MB in  3.00 seconds = 155.12 MB/sec

/dev/md0:
 Timing cached reads:   2462 MB in  2.00 seconds = 1231.22 MB/sec
 Timing buffered disk reads:  470 MB in  3.01 seconds = 156.06 MB/sec
```

From what I can see here, in terms of small file reads, 64K is about the sweet spot. I will be dumping large media backups on here made of mostly large 800MB-2GB files each.

perhaps a RIAD5 with a 128K or even 256K chunk size would be better suited for me after all... Although I'm a paranoid individual so the thought of RAID5 (Single redundancy) leaves me a little concerned at the back of my mind. I honestly didnt think the overhead of RAID6 was as severe as it seems here though.

On the good news, however, it looks as though my ICH7 isnt PCI limited. :)

This is all basic testing though, what I should really be doing is taking different sized files like 1 divx movie of about 700MB, 1 mp3 of about 5MB and 1 random install .exe of ~100MB and measure the transfer times over my LAN to my RAID array for each file.
If you're considering taking this testing further or doing any of your own maybe this would be a stewp in the right direction?

---

### Post by fjgaude on 2008-09-26
Good to see the high througput, PCI-E for ICH7. Learn something new everyday, eh?

Using **hdparm** for testing is about the simplest thing we can do... I have sent and received big files down the LAN, disk to disk, etc., and have quit testing. Use Gkrellm for measurements. For what I do raid 64K chucks seen about right.

I've found that routers can be up and down when it comes to file transfer times... can't say which brand would be best. I'm satisfied with what I have now, Linksys. My next upgrade will be four drives of the latest vintage, 120MB/sec or so throughput. Don't wish to spend the money just yet though.

Keep up the good work.

---

