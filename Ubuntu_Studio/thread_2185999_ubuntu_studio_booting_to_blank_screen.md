---
title: "ubuntu studio booting to blank screen"
date: 2013-11-05
forum: Ubuntu Studio
---

### Post by anilkumar212005 on 2013-11-05
Ubuntu studio 12.04.3 was working fine until yesterday morning, i shut it down successfully and evening when i turn it on i am unable to see login window or any message (just blank screen) (shift or ctrl+alt+del no use) , bios is loading, i can see harddrive in bios but i have no idea what is causing this problem i dont know if somebody have experienced the same problem but unable to find answers anywhere else on internet. my computer specs as follows

intel core 2 duo, 32 bit, dg33fb motherboard

Please somebody let me know step by step to fix this issue.

---

### Post by Bashing-om on 2013-11-05
anilkumar212005; Hi ! Welcome to the forum .

Let's see what we can do to isolate the problem.
Can you boot to the grub menu ?
From a cold start, soon as the bios screen clears, depress and hold the shift key -> Grub boot menu (???);
Else, will have to resort to the liveDVD to see what the status of your operating system is.

[INDENT][INDENT]where there are solutions there are no problems
[/INDENT][/INDENT]

---

### Post by anilkumar212005 on 2013-11-05
@Bashing om, thanks for your reply, i tried it couple of times couldnt get to the grub boot menu. i have live usb stick, please let me know the next step?

---

### Post by Bashing-om on 2013-11-05
anilkumar212005; OK, plan B.

Boot the liveDVD/USB to "try ububtu" mode.
Show us what we are working with partition/booting wise with the output of terminal codes:
```

sudo fdisk -lu
sudo parted -l
sudo parted /dev/sda unit s print

```

then additional advise is pending to install grub onto the proper place.

[INDENT][INDENT]we can do this
[/INDENT][/INDENT]

---

### Post by anilkumar212005 on 2013-11-05
Hi Bashing om,

Thanks for your swift response,
i followed the procedures as given, 
-----------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------
ubuntu-studio@ubuntu-studio:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e6306

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   968542207   484270080   83  Linux
/dev/sda2       968544254   976771071     4113409    5  Extended
/dev/sda5       968544256   976771071     4113408   82  Linux swap / Solaris

Disk /dev/sdb: 4016 MB, 4016046080 bytes
255 heads, 63 sectors/track, 488 cylinders, total 7843840 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcad4ebea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb4   *          63     7843839     3921888+   b  W95 FAT32
-----------------------------------------------------------------------------------------------------
ubuntu-studio@ubuntu-studio:~$ sudo parted -l
Model: ATA WDC WD5000AADS-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system  Flags
 1      1049kB  496GB  496GB   primary                boot
 2      496GB   500GB  4212MB  extended
 5      496GB   500GB  4212MB  logical


Model: JetFlash Transcend 4GB (scsi)
Disk /dev/sdb: 4016MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 4      32.3kB  4016MB  4016MB  primary  fat32        boot
-----------------------------------------------------------------------------------------------------
ubuntu-studio@ubuntu-studio:~$ sudo parted /dev/sda unit s print
Model: ATA WDC WD5000AADS-0 (scsi)
Disk /dev/sda: 976773168s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start       End         Size        Type      File system  Flags
 1      2048s       968542207s  968540160s  primary                boot
 2      968544254s  976771071s  8226818s    extended
 5      968544256s  976771071s  8226816s    logical
-----------------------------------------------------------------------------------------------------
-----------------------------------------------------------------------------------------------------

500Wdc is my primary drive where ubuntustudio is loaded onto it.

Please guide me to the next step.

---

### Post by Bashing-om on 2013-11-05
anilkumar212005;

All looks straight forward. nothing exotic and no Windows. - and no errors !
What results from the liveDVD;

Boot the liveDVD, soon as the bios screen clears depress the shift key -> language screen, escape key to accept the default -> boot options screen.

choose "boot from first hard drive".

Perhaps all we need to do is (re-)install grub onto the SDA drive.

[INDENT][INDENT]it is all a process
[/INDENT][/INDENT]

---

### Post by anilkumar212005 on 2013-11-05
well i have installed applications and few personal files are lying on my desktop. please let me know how to reinstall grub

---

### Post by Bashing-om on 2013-11-05
anilkumar212005;

Sure ! I will .. 
Tell me first that "boot from first hard drive" from the liveDVD is successful // that test for me that there is no underlying file problems and all we are looking at is a booting issue.

edit: Sorry that I was so unclear in my last.

[INDENT][INDENT]then it is nothing but a thing
[/INDENT][/INDENT]

---

### Post by anilkumar212005 on 2013-11-05
bashing om, i booted from live usb, did exactly as mentioned above,

Boot the liveDVD, soon as the bios screen clears depress the shift key  -> language screen, escape key to accept the default -> boot  options screen.
choose "boot from first hard drive".

its like a loop, goes back to language screen again and so on...
if this is ok i am up for next step.

---

### Post by Bashing-om on 2013-11-05
anilkumar212005. Nope, we got problems.
That "boot from first hard disk" should have booted you into the install.

Let's see if we can repair the file system.
from the liveDVD -> terminal:
terminal code:
```

sudo e2fsck -C0 -p -f -v /dev/sda1

```

If there are reported errors that the utility can not resolve, post the output and  we will change e2fsck's options.

[INDENT][INDENT]all we can do is try
[/INDENT][/INDENT]

---

### Post by anilkumar212005 on 2013-11-05
bashing om, 

here is the terminal's output

e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?
ubuntu-studio@ubuntu-studio:~$

---

### Post by Bashing-om on 2013-11-05
anilkumar212005; UnGood !

I am going to have to consider on this, as to what to do .. perhaps others in the meantime can offer some suggestions.

My present thought is to spare off the superblock.

It is to the point that my think-a-bility is impaired for this session. I will sleep on this and return on my morrow.

[INDENT][INDENT]we are not stone walled yet !
[/INDENT][/INDENT]

---

### Post by anilkumar212005 on 2013-11-05
bashing om, 
thanks for your help, sure, please get back to me by tommorrow.
i am open to any kind of help on this by anybody.

---

### Post by Bashing-om on 2013-11-06
anilkumar212005; Good morning !

I have not changed my mindset; but, verify my suspicion before proceeding to spare of to alternate blocks:
Post back the output of the simplified file system check command:

From the liveDVD: - Because; can not run a file system check on a mounted partition ! -
```

sudo fsck.ext4 -v /dev/sda1

```
I prefer to see this output as your system formats it, please copy and paste outputs between code tags:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

[INDENT][INDENT]where there is life there is hope
[/INDENT][/INDENT]

---

### Post by anilkumar212005 on 2013-11-06
[B]Bashing om, thank you for getting back to me, please let me know if this format is fine for you to view.

```
[/B]
e2fsck 1.42 (29-Nov-2011)
fsck.ext4: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?

```

---

### Post by Bashing-om on 2013-11-06
anilkumar212005; Thanks, much better readability wise !

OK, that seems to confirm we are dealing with a bad superblock.

Are there any spare viable blocks ?.. Let's see what might be:
```

sudo dumpe2fs /dev/sda1 | grep superblock
sudo dumpe2fs /dev/sda1 | grep -i backup

```

Depending on that output, we will restore the superblock from backup.

[INDENT][INDENT]There is still a possibility of life
[/INDENT][/INDENT]

---

### Post by anilkumar212005 on 2013-11-06
bashing om,

i executed the above given code and results are pasted here

```

--------------------------------------------
sudo dumpe2fs /dev/sda1 | grep superblock

ubuntu-studio@ubuntu-studio:~$ sudo dumpe2fs /dev/sda1 | grep superblock
dumpe2fs 1.42 (29-Nov-2011)
dumpe2fs: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Couldn't find valid filesystem superblock.
ubuntu-studio@ubuntu-studio:~$ 
--------------------------------------------
sudo dumpe2fs /dev/sda1 | grep -i backup

ubuntu-studio@ubuntu-studio:~$ sudo dumpe2fs /dev/sda1 | grep -i backup
dumpe2fs 1.42 (29-Nov-2011)
dumpe2fs: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
ubuntu-studio@ubuntu-studio:~$ 

-----------------------------------------

```

please walk me through the next step

---

### Post by Bashing-om on 2013-11-06
anilkumar212005; Yuk !
I have never encountered a situation like this !

This is what that output should have looked like:
```

sysop@1304mini:~$ sudo dumpe2fs /dev/sda1 | grep -i backup
[sudo] password for sysop: 
dumpe2fs 1.42.5 (29-Jul-2012)
Journal backup:           inode blocks
  Backup superblock at 32768, Group descriptors at 32769-32769
  Backup superblock at 98304, Group descriptors at 98305-98305
  Backup superblock at 163840, Group descriptors at 163841-163841
  Backup superblock at 229376, Group descriptors at 229377-229377
  Backup superblock at 294912, Group descriptors at 294913-294913
  Backup superblock at 819200, Group descriptors at 819201-819201
  Backup superblock at 884736, Group descriptors at 884737-884737
sysop@1304mini:~$ 

```

I am stumped ! I could be mistaken .. those with greater experience may be able to offer better advise. but ! What I see is to backup what files you can, zero out that drive and try and (RE-)install. 

That is to the best of my knowledge. Wait though and see if anyone has an alternative,

[INDENT][INDENT]sometimes one has to bite the bullet
[/INDENT][/INDENT]

---

### Post by anilkumar212005 on 2013-11-06
bashing om,

i did a couple of search on internet stepped into this link
[http://ubuntuforums.org/archive/index.php/t-1245536.html](http://ubuntuforums.org/archive/index.php/t-1245536.html)
ran this command

```

ubuntu-studio@ubuntu-studio:~$ sudo mke2fs -n /dev/sda1
mke2fs 1.42 (29-Nov-2011)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
30269440 inodes, 121067520 blocks
6053376 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
3695 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
    4096000, 7962624, 11239424, 20480000, 23887872, 71663616, 78675968, 
    102400000

ubuntu-studio@ubuntu-studio:~$ sudo e2fsck -f -b 32768 /dev/sda1
e2fsck 1.42 (29-Nov-2011)
Error writing block 1 (Attempt to write block to filesystem resulted in short write).  Ignore error<y>? 

ubuntu-studio@ubuntu-studio:~$ 

```

any idea onto next step

---

### Post by Bashing-om on 2013-11-06
anilkumar212005; Hey !

You do good work !
Let's see what happens ! 
```

sudo fsck -b 32768 /dev/sda1

```
Which is the 1st backup superblock listed.

[INDENT][INDENT]worth now a shot
[/INDENT][/INDENT]

---

### Post by anilkumar212005 on 2013-11-06
bashing om,

tried this
```

ubuntu-studio@ubuntu-studio:~$ sudo fsck -b 32768 /dev/sda1
fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
Error writing block 1 (Attempt to write block to filesystem resulted in short write).  Ignore error<y>? 


```
any thoughts appreciated

---

### Post by Bashing-om on 2013-11-06
anilkumar212005; Well,

Let's try the command from the link that you found ( hey I did go look !)
```

sudo e2fsck -f -b 32768 /dev/sda1

```
Remember this method is interactive, most replies will be "yes" but user discretion is advised.

[INDENT][INDENT]I do hope for the best
[/INDENT][/INDENT]

---

### Post by anilkumar212005 on 2013-11-07
Bashing om,

Thanks for walking me through this tough situation, this fix worked and my computer is back in working stage. it was quite a learning curve on grub, its role and superblocks.
i found other useful links for people who are experiencing issues on grub and superblocks thought to share here

[http://askubuntu.com/questions/322070/how-can-i-fix-mounting-my-data-drive-after-a-crash](http://askubuntu.com/questions/322070/how-can-i-fix-mounting-my-data-drive-after-a-crash)
[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
[http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html](http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html)
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)
[http://animeshdas.wordpress.com/2009/11/18/data-recovery-from-corrupted-ext2ext3-filesystem-having-bad-superblock/](http://animeshdas.wordpress.com/2009/11/18/data-recovery-from-corrupted-ext2ext3-filesystem-having-bad-superblock/)
[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)
[http://www.admon.org/using-alternative-superblock-to-check-ext3/](http://www.admon.org/using-alternative-superblock-to-check-ext3/)
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)


i found this forum quite friendly and responsive, happy being a linux user.
thanks again to bashing om

---

### Post by Bashing-om on 2013-11-07
anilkumar212005; Great !
I am pleased that you have resolution - I had but one more thing to try as a means of last resort. Glad we did not have to - clearing the journal inodes !

For completeness of this awesome thread ->
Means of last resort :  based on consideration that all my data was already lost ->
 (remove the first inode)Clearing the journal inode !
```

sudo debugfs -w /dev/sda1
debugfs 1.41.11 (14-Mar-2010)
debugfs:  clri <8>
debugfs:  quit

```
Then I've launch fsck:
```

sudo fsck -yv /dev/sda1

```

Appreciate you sharing what you had researched ! This is open source at it's best ! 

@ anilkumar212005; Please mark this thread as solved as an aid to others seeking a solutioun and to keep the forum tidy. I look forward to reading you next time.

[INDENT][INDENT]open source, one for all and all for 1
[/INDENT][/INDENT]

---

