---
title: "Howto: Use ntfsresize+fdisk to resize a partition with bad sectors"
date: 2009-08-19
forum: Tutorials
---

### Post by LindaBW on 2009-08-19
I have successfully used ntfsresize and fdisk to shrink my Windows partition on a hard drive that has bad sectors.  I am new to partitioning, but the following steps worked for me, so maybe they will help someone else.  Many sites warn that these operations are risky and may result in losing all the data on your hard drive, so be sure to back up whatever you want to save if you try this.

My goal was to dual boot with Ubuntu 9.04 and Windows XP (I had only Windows XP).  I followed the instructions at [https://help.ubuntu.com/9.04/switching/dualboot-procedure.html](https://help.ubuntu.com/9.04/switching/dualboot-procedure.html).  On Step 6 of that page, I wanted to reduce the size of my Windows partition, but size was not given as an option.  (The partitioner listed the "space in use" on my Windows partition as "unknown".)  I exited the installation process.

Seeking a more informative partitioning tool, I downloaded pmagic-4.3.iso from partedmagic.com.  This Live CD contains a number of useful partitioning tools such as GParted, ntfsresize, and fdisk(8), which I used.  Booting from the CD, I opened GParted, right-clicked on my Windows partition, and selected the "information" option.  It told me that GParted had detected bad sectors on this partition, but if I wanted to resize this partition anyway, I could return to Windows, run 'chkdsk /f /r', reboot twice, and then use ntfsresize with the --bad-sectors option.

The first time I ran CHKDSK, it seemed to do nothing and found no bad sectors.  But then I ended up running it again later (after compressing old files and defragging), and CHKDSK ran for maybe an hour, so long that I didn't watch the whole thing.  All I could find afterward was a summary of its log (stored in the "Event Manager"), in which it reported there were indeed 4 bad sectors, but didn't say anything about whether it had "repaired" them.  I decided to proceed with the resize.

The man page of ntfsresize ([http://man.linux-ntfs.org/ntfsresize.8.html](http://man.linux-ntfs.org/ntfsresize.8.html)) tells me that the proper way to do this is shrink the filesystem with ntfsresize, and then use fdisk(8) to change the size of the partition to match the new filesystem, but doesn't say how.

The best source I found about how to use ntfsresize+fdisk to resize a partition was in the Parted Magic documentation: [http://partedmagic.com/documentation/120-cli-partitioning.html](http://partedmagic.com/documentation/120-cli-partitioning.html).  Another good (if awfully formatted) guide is at [http://crashrecovery.org/CrashRecoveryKit/iso/2.4.21/HOWTO.ntfs.html](http://crashrecovery.org/CrashRecoveryKit/iso/2.4.21/HOWTO.ntfs.html).  I also benefitted from [http://ubuntuforums.org/archive/index.php/t-1069748.html](http://ubuntuforums.org/archive/index.php/t-1069748.html).  Now here is what I did.

Boot the machine from the Parted Magic CD.  Open a Terminal (find it in the main menu).  I want to know what Parted Magic calls my hard drive so I type:

```

root@PartedMagic:~# fdisk -l

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x40000000

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1          10       80293+  de  Dell Utility
/dev/hda2   *          11        4864    38989755    7  HPFS/NTFS

```The answer is "/dev/hda".  Now in my case there are two partitions, and the Windows one is called: "/dev/hda2".  I ask ntfsresize how much it thinks I could shrink the Windows partition, including the --badsectors option since I know my disk has that problem:

```

root@PartedMagic:~# ntfsresize -i --bad-sectors /dev/hda2
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/hda2
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 39925506560 bytes (39926 MB)
Current device size: 39925509120 bytes (39926 MB)
WARNING: This software has detected that the disk has at least 1 bad sector.
WARNING: Bad sectors can cause reliability problems and massive data loss!!!
Checking filesystem consistency ...
100.00 percent completed
Accounting clusters ...
Space in use       : 16866 MB (42.2%)
Collecting resizing constraints ...
You might resize at 16865632256 bytes or 16866 MB (freeing 23060 MB).
Please make a test run using both the -n and -s options before real resizing!

```In theory, I could resize to 16866 MB, but this is just an estimate.  Playing it safe, I decide to resize to 19000MB.  I want to make sure there are no unexpected problems so I do a test run of the filesystem resize operation (the --no-action prevents it from changing anything, the -b is short for --bad-sectors):

```

root@PartedMagic:~# ntfsresize --no-action -b --size 19000M /dev/hda2
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/hda2
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 39925506560 bytes (39926 MB)
Current device size: 39925509120 bytes (39926 MB)
New volume size    : 18999992832 bytes (19000 MB)
WARNING: This software has detected that the disk has at least 1 bad sector.
WARNING: Bad sectors can cause reliability problems and massive data loss!!!
Checking filesystem consistency ...
100.00 percent completed
Accounting clusters ...
Space in use       : 16866 MB (42.2%)
Collecting resizing constraints ...
Needed relocations : 972361 (3983 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
Updating $BadClust file ...
Updating $Bitmap file ...
Updating Boot record ...
The read-only test run ended successfully.

```Since the process was successful in theory, now I do it for real.  This is the step that is dangerous to my data:

```

root@PartedMagic:~# ntfsresize -b --size 19000M /dev/hda2
ntfsresize v2.0.0 (libntfs 10:0:0)
Device name        : /dev/hda2
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 39925506560 bytes (39926 MB)
Current device size: 39925509120 bytes (39926 MB)
New volume size    : 18999992832 bytes (19000 MB)
WARNING: This software has detected that the disk has at least 1 bad sector.
WARNING: Bad sectors can cause reliability problems and massive data loss!!!
Checking filesystem consistency ...
100.00 percent completed
Accounting clusters ...
Space in use       : 16866 MB (42.2%)
Collecting resizing constraints ...
Needed relocations : 972361 (3983 MB)
WARNING: Every sanity check passed and only the dangerous operations left.
Make sure that important data has been backed up! Power outage or computer
crash may result major data loss!
Are you sure you want to proceed (y/[n])? y
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
Updating $BadClust file ...
Updating $Bitmap file ...
Updating Boot record ...
Syncing device ...
Successfully resized NTFS on device '/dev/hda2'.
You can go on to shrink the device for example with Linux fdisk.
IMPORTANT: When recreating the partition, make sure that you
  1)  create it at the same disk sector (use sector as the unit!)
  2)  create it with the same partition type (usually 7, HPFS/NTFS)
  3)  do not make it smaller than the new NTFS filesystem size
  4)  set the bootable flag for the partition if it existed before
Otherwise you won't be able to access NTFS or can't boot from the disk!
If you make a mistake and don't have a partition table backup then you
can recover the partition table by TestDisk or Parted's rescue mode.

```Now the filesystem has been resized to 19000MB.  (I can type 'disktype /dev/hda' for information confirming this).  I ask fdisk for the partition table so I can read the current settings:

```

root@PartedMagic:~# fdisk -l

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x40000000

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1          10       80293+  de  Dell Utility
/dev/hda2   *          11        4864    38989755    7  HPFS/NTFS

```For my Windows partition, the starting cylinder is 11, the partition type is 7 (NTFS), and the bootable flag is on.  I am going to edit the partition table and replace the entry for the Windows partition with a new entry that makes the partition smaller, but otherwise identical to the old one.  I enter the fdisk dialogue:

```

root@PartedMagic:~# fdisk /dev/hda

The number of cylinders for this disk is set to 4864.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

```I delete the Windows partition, in my case partition 2:

```

Command (m for help): d
Partition number (1-4): 2

```Then I make a new partition.  It is a primary partition, partition number 2 (like the old one).  The default starting cylinder was the correct value in this case, 11.  For the size, I specify 19000M, the same value I shrank the filesystem to.  (I saw ntfsresize round that requested size down, and fdisk round it up, so the filesystem was correctly contained inside the partition.):

```

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 2
First cylinder (11-4864, default 11): 11
Last cylinder, +cylinders or +size{K,M,G} (11-4864, default 4864): +19000M

```Set the type to 7, as it was before:

```

Command (m for help): t
Partition number (1-4): 2
Hex code (type L to list codes): 7
Changed system type of partition 2 to 7 (HPFS/NTFS)

```Next I want to make sure the partition is still marked as bootable, so I check the table:

```

Command (m for help): p

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x40000000

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1          10       80293+  de  Dell Utility
/dev/hda2              11        2433    19462747+   7  HPFS/NTFS

```It isn't listed as bootable, so I use the 'a' command to toggle the bootable flag:

```

Command (m for help): a
Partition number (1-4): 2

```Now I type 'w' to save the new partition table and exit.

```

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.

```Then I shut down Parted Magic and rebooted into Windows to let it run its checks and make sure everything was ok.  All was well, so I tried again with the Ubuntu install process, and the install CD was able to find the newly freed space on my drive and automatically put Ubuntu there and set things up for dual boot.  Now I have a successfully dual booting machine despite bad sectors.

Thanks to everyone out there who put up enough information that I was able to do it eventually!  I hope this post might speed up the process for someone else.

---

### Post by craig.o on 2009-09-29
Linda;

Thanks for the detailed instructions.  

My friend's Dell is in the same condition: it has bad blocks and we want to install Ubuntu.  I'm undecided though, about the best way to go forward.  It'll either be the method you outline here or, we'll bite the bullet and buy a new disk.

Considering that chkdsk finds bad blocks on practically each run and, that ntfsck isn't yet available, I'm leaning towards just getting a new disk.  

Did you ever run chkdsk (w/the repair flag) since the two times you list in your post?  Reason I ask is that I'm curious as to how you're judging the disk's durability...

thanks again,
-Craig

---

### Post by LindaBW on 2009-10-03
Hi Craig,

I did go ahead and run chkdsk again just now to see what would happen, and it found nothing (but also seemed to check nothing -- it took less than a second to run once I restarted the computer).  I don't know what that means.

However, to answer your other question, everything I have read suggests that there is no effective way to judge a disk's durability.  Once a disk gets a bad sector, it could die within a few days or months, or it could keep lasting for years, and both possibilities frequently happen.  Right now I just burn CD backups of anything I would be upset to lose.

I wish I could be of more help!

Yours,
Linda

---

### Post by phineas.milne on 2009-10-25
Linda,

Thank you for the directions. I followed the instructions very carefully. When i restarted i got a message saying no operating system. did anything like this happen to you? did you have to boot of the original os disk?:confused:

-phineas.milne

---

### Post by LindaBW on 2009-10-25
Hi Phineas,

Nothing like that happened to me.  One thing to check is to make sure you have the "boot" flag on for the Windows partition.  To check this, enter fdisk, and type "p" to see the partition table.  The second column in the partition table is the "Boot" column.  If a partition has an asterisk in this column, it means the partition is bootable.  If there is no asterisk, you can use the "a" command to toggle the flag as described above.

If the boot flag is already on, I don't have any more ideas for what might be wrong -- I'm a novice at this myself.  If you have a log of the actions you took, posting that might help a more experienced user diagnose the problem.  (If you didn't know, it's very easy to preserve logs of your command line operations before you exit Parted Magic and lose everything.  Just open a text editor in the Parted Magic OS (it has one), copy paste everything from your terminal into that, and then save the file to an external disk such as a flash drive.)

Linda

---

### Post by phineas.milne on 2009-10-25
Thanks Linda!

I only had one partition to start with so that might have been it. thank you for your help!

---

### Post by funkiwan on 2009-12-17
What an incredibly helpful post. I was in the same boat (bad sectors, trying to resize XP so I could perform a dual boot) and these instructions worked perfectly. I had only one partition. Thanks!

---

### Post by rdr94117 on 2010-01-22
I had exactly the same situation, followed these instructions exactly, and it worked perfectly. Thank you, thank you! 

I would never have successfully navigated all those command lines without this guide. Hard to believe in this day and age that there's not an intuitive user interface for this operation.

---

### Post by Paul Crawford on 2010-05-13
Just a couple of comments to add to this:
(0) If you can, make a full disk back-up before doing anything! Tedious, and needs another disk, but very wise if there is anything of value on the one you are about to play with.

(1) If your disk is flaky, **DO NOT DEFRAG** or compress anything until you have done the full chkdsk surface scan! In fact, before any re-size I would suggest you do a full surface scan just in case. That should take an hour or so. If not, try again!

(2) If you get a brief message when Windows boots to the effect it can't lock or gain exclusive access to the disk for checking, be very worried. Typically it means you have a root kit infection and they are terribly difficult to remove from 'inside' an infected OS. You really need to be able to AV scan the disk from a clean computer.

While clam is free and useful as a LINUX AV, I found it gave some suspect warnings (possible false positives), so it good to have a 2nd opinion with AVG/Avast or similar. 

(3) How long a disk will live with errors is anybody's guess. If you can look at the SMART status, I think the default Palimpsest disk utility in 10.04 gives this, but be aware that not all BIOS enable this by default (or can report it at all). GSmartMon is the other tool I have used for SMART queries in the past. Sometimes you need to consider removing the disk and mounting it as 2nd disk in another PC if there is no SMART support (also for AV cleaning).

Some external disk USB caddies report SMART status, but most do not.

(4) If your disk is clean, then there is a simple tool in gparted to do all of this, where it falls over is dealing with the potentially serious issue of a failing disk. This article is really for those who understand enough to take that decision.

Whether the disk is reported good or bad makes little difference in a sense, as you should have a regular backup! Sooner or later you will have a HDD die, or accidentally delete something, or (mostly Windows) have malware or a bug wipe data. **Be prepared!**

---

### Post by MWola on 2011-01-28
Dear Linda,

Thank you for your post.  I was trying to install Ubuntu 10.10 alongside Windows XP on my Dell XPS M1330 without deleting Windows from the system.  However, I ran into a problem.  Upon first starting up the Ubuntu live CD or using GParted the disk drive corresponding to the one in which Windows was located had a warning.  It said that I had a bad sector and to run Windows 'chkdsk /f /r' and reboot twice.  I did this and Windows found no errors, but it did not go away.  When I used 'ntfsresize -b' I was successful.  I did not have to run the Parted Magic CD.  I simply used the terminal in the Ubuntu live CD and using the 'ntfsprogs' package ran 'ntfsresize.'   I then ran 'fdisk' the way you had outlined (and thank you for pasting the output of the terminal!!!!!). 

I only had one difference from what you posted - when I made the new partition it asked for the starting sector, not starting cylinder.  However, running 'fdisk -u', in a separate terminal, yielded the partition table with the sizes in sectors and not cylinders.

Everything else went just as the terminal "screenshots" you posted and was smooth sailing.  I can now dual boot Windows XP and Ubuntu 10.10 and all is right in the universe.  Thanks for posting this!!!!!  You saved me many hours of headaches and computer woes.

---

### Post by Arleas on 2011-01-30
> **LindaBW said:**
> Hi Phineas,

Nothing like that happened to me.  One thing to check is to make sure you have the "boot" flag on for the Windows partition.  To check this, enter fdisk, and type "p" to see the partition table.  The second column in the partition table is the "Boot" column.  If a partition has an asterisk in this column, it means the partition is bootable.  If there is no asterisk, you can use the "a" command to toggle the flag as described above.

If the boot flag is already on, I don't have any more ideas for what might be wrong -- I'm a novice at this myself.  If you have a log of the actions you took, posting that might help a more experienced user diagnose the problem.  (If you didn't know, it's very easy to preserve logs of your command line operations before you exit Parted Magic and lose everything.  Just open a text editor in the Parted Magic OS (it has one), copy paste everything from your terminal into that, and then save the file to an external disk such as a flash drive.)

Linda

Thanks a lot. It's partitioning now. Hopefully I won't get a boot error, but either way your tutorial helped me out.

Thanks again!

---

### Post by dieter-erich on 2011-02-27
Hi,
   scanning these posts I wondered whether anybody has seen the following problem and found a solution or can explain what is happening:

I am having some inconsistencies when running my Vaio Laptop under WinXP and/or under Wubi 10.04.2 (double boot). Chkdsk does not find any error but gparted and ntfsresize complain about at least 2 defective sectors. I did as indicated in these posts (i.e. run chkdsk /r /f twice on c: and d: and also run ntfsresize with the parameters set to correct bad sectors) but the error shown in gparted did not go away. I also run the Seegate HD tool under WinXP and it did not report any HD error. So, is there a defective sector or not?
Thanks for hints, DE

---

### Post by szechman on 2012-07-19
This worked great but it seems to be a lot of steps and a lot of things to keep track of. I found a much simpler way and it can all be done through gparted. I cannot take credit for this but I have tested it and it works great.

BE CAREFUL AS THIS DISABLES THE BAD SECTOR CHECK!

Basically, you create an executable bash script which adds the --bad-sectors option to the original ntfsresize program. You can follow these general steps:
 
[LIST=1]
[*]Locate the **ntfsresize** executable (for the GParted live CD it will be in **/usr/bin**, for Parted Magic it is in **/usr/sbin**). (/sbin for ubuntu)
[*]Rename it to **ntfsresize.orig**.
[*]Create a new bash script at the same location named **ntfsresize**. (See below for what you should put in this script.)
[*]Use chmod to ensure the new script is executable (**chmod 755** will do the trick).
[*]Run GParted as normal.  It will ignore the bad sector(s).
[/LIST]
 In the bash script itself, you’ll want to add these two lines:
 #!/bin/bash
exec ntfsresize.orig --bad-sectors "$@"


I did all the moving and script creating with the sudo command as to keep permissions as root.


Now I don't even have to think about it, I just launch gparted and no bad sector error.

---

### Post by Analogon on 2012-07-24
LindaBW:

I can't thank you enough for this wonderful and helpful posts. Three years later it's still useful. I had problems too with a bad sector, so Gparted wouldn't work at all. Your guide was of invaluable help, since I didn't want to deal with ntfsresize or fdisk, since it seemed too difficult. Your guide gave me confidence.

But, as MWola, I'd like to do some remarks, hoping this could help somebody else too. When creating the new partition in fdisk, the one with:

```

Command (m for help): n 
Command action
    e   extended 
      p   primary partition (1-4) 
p
Partition number (1-4): 2
First cylinder (11-4864, default 11): 11 
Last cylinder, +cylinders or +size{K,M,G} (11-4864, default 4864): +19000M
```

It asked me for sectors, not cylinders. People doing this should be very careful with this point. To my knowledge, by default the unit measure is given in sectors, until you specify it otherwise. If for some reason, in the step above fdisk ask you for an unit different than given in the partition table, as MWola suggest, open an alternate terminal (ctrl+alt+t) and type:

```
fdisk -l -u='sectors' 
```Or change 'sectors' for 'cylinders', as required, and copy the value. I was given and asked everything in sectors, so I didn't have that issue.

But what confused me is that when asked for the first sector,  the default given didn't correspond to the original partition table. This confused me a lot, and for a moment I thought of entering the default given. I realized there was a reason for you constantly keeping track of the original partition table, and I decided to enter the first sector given in the original partition table, NOT the default suggested. Everything else  went as shown, and now I'm typing this on my new Ubuntu system. Thank you so much.

In short. keep track of if fdisk is asking you for cylinders or sectors, and enter the first sector or cylinder for the required partition given in the ORIGINAL partition table, regardless of what fdisk may have as default.

---

