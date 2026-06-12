---
title: "Help WIth Repairing File System"
date: 2019-05-01
forum: Ubuntu/Debian BASED
---

### Post by ivan23m on 2019-05-01
My system wouldn't read a few DVDs so I tried to check the file system for errors but it wouldn't unmount. After that, I forced it to check and got this message:

```


ivan23m@ivan23m-desktop:~$ sudo su
[sudo] password for ivan23m: 
root@ivan23m-desktop:/home/ivan23m#  umount /dev/sda 
umount: /dev/sda: not mounted
root@ivan23m-desktop:/home/ivan23m# fsck /dev/sda
fsck from util-linux 2.27.1
e2fsck 1.42.13 (17-May-2015)
/dev/sda is in use.
e2fsck: Cannot continue, aborting.


root@ivan23m-desktop:/home/ivan23m# fsck -nf /dev/sda
fsck from util-linux 2.27.1
e2fsck 1.42.13 (17-May-2015)
Warning!  /dev/sda is in use.
ext2fs_open2: Bad magic number in super-block
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sda

The superblock could not be read or does not describe a valid ext2/ext3/ext4
filesystem.  If the device is valid and it really contains an ext2/ext3/ext4
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
 or
    e2fsck -b 32768 <device>



```. 

I have two questions, first, how to unmount the drive so I don't have to force check, and second, what does the message I got after force check mean?

---

### Post by Bashing-om on 2019-05-01
ivan23m; Yuk :(

Scary situation.

the:
> 
Warning!  /dev/sda is in use.

indicates to me that you are attempting to run that file system check from the installation (hard drive); No can do !

What results when you run the file system check from a liveDVD(USB) ?

If still with "bad super-block" then yeah follow the checker's advise:
see:
[http://ubuntuforums.org/showthread.php?t=2177756](http://ubuntuforums.org/showthread.php?t=2177756)
as one good tutorial.

[INDENT][INDENT]these things happem
[/INDENT][/INDENT]

---

### Post by ivan23m on 2019-05-01
I don't know how to run a file check from a Live USB or DVD nor how to make one. Can you spell out the steps for me, I'm far from an expert in Linux?

---

### Post by Bashing-om on 2019-05-01
ivan23m; Sure !
we can do that :)

How did you do that initial install of ubuntu ?
What medium do you want to use to make the LIVE environment ?
what is the current installed release version ? As the LIVE medium must be the same, in this instance of running a file system check.

You are going to download the ISO file - verify the integrity
copy (burn) the .iso to the desired medium - verify the integrity
boot from the live environment
from terminal in the live mode run the file system checks ( fsck and/or e2fsck).

[INDENT]once you have done it a couple of times - ain't no big deal.[/INDENT]

---

### Post by ra7411 on 2019-05-01
Hook up your install usb or dvd (the one you used to install Ub), you may have to mess with your bios to get it to boot from the install disk, when it does choose "Try Ubuntu", you will get a generic ub screen running from the install disk.

-use the file manager to see if you can find and copy any unbacked up user files to a safe place. Any restore or re-install operation you may wind up doing, will wipe out existing files in the target partition.

-use the pre-installed DISKS program to evaluate drives and partitions, a drive must be unmounted (arrow symbol, square symbol means it's mounted) before doing analysis or repair operations.

-select the gears icon, select CHECK FILESYSTEM.

-if it's damaged try REPAIR FILESYSTEM, maybe it will fix things.

-another approach to partition / filesystem repair, with the problem drive unmounted (umount /dev/sdxy), open a terminal (Ctrl+Alt+T) and use "sudo fsck -f /dev/sdxy"  (x=hd letter, y=partition number) to force it look for problems past a cursory check. Use the installed Firefox browser to online search up various commands to use with "Linux fsck" - some of these can force certain operations that might cause additional problems, so be careful.

---

### Post by TheFu on 2019-05-01
One more thing.

sda is the entire drive and almost NEVER used that way in Linux.  Linux installs will **always** create at least 1 partition.  That would be sda1.  The second partition would be sda2 ... on a GPT partitioned disk, you can keep adding partitions, sda5, sda56, sda99, .... 

File systems go onto partitions, not disks.  The **lsblk** command will show how things are related, in a hierarchy tree.  Trying to run fsck on the entire disk is not a good thing.  FSCK - File System Check - is for file systems, not disks, not partition tables, just file systems.

Boot from any install media for the same release of Ubuntu you are running - the desktop/server part isn't important, just the 16.04 or 18.04 part is.  To make this, there are logs of tutors - [https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-ubuntu) - there are links on that page to the Windows and OSX versions of the tutorial too. Pick your poison.  Boot from this device (flash/optical), "Try Ubuntu", then open a terminal and run **fsck /dev/sda1** .  --force options should only be used when you 100% know exactly what you are doing. That applies with all commands. If you have 0.0000000001% uncertainty, verify first.

---

### Post by Rubi1200 on 2019-05-01
I have two comments to make.

1. you _cannot _run fsck on a mounted drive or partition, has to be from a liveCD/USB

2. why are you elevating to root > [COLOR=#000000][FONT=&amp]sudo su[/FONT][/COLOR] 

There is absolutely no need to do that and it is even more dangerous than just running with "regular" elevated privileges.

---

### Post by ivan23m on 2019-05-02
Thank you everyone for your help. What I did is I started the system via bootable DVD, I use Linux Zorin 12.4 Lite, and wrote a few commands in the Terminal the result of which is down below. It has also been suggested to click on gears icon and to 'use the pre-installed DISKS program to evaluate drives and partition'. I haven't found that option when clicking on gears icon so I've chosen the option SMART Data & Self-Tests' by clicking on the three dots above. Perhaps there are some relevant data there, what is obvious is that my hard disks are in a bad condition, see under "Type". I have three questions: 

1. Is any information here relevant to my reason for doing all of this in the first place which is the inability to read certain DVDs?
2. If necessary, how to proceed with file check in Terminal, should I use root privileges now when I started thesystem via DVD and clicked on 'Try Linux'?
3. Does the bad condition of the hard drives have anything to do with 1.?

I hope you won't mind having to read from pictures, it won't let me make screenshots in Try Mode and I can't copy from the Terminal cause the picture on the screen disrupts and I have to restart. That happens relatively often.

---

### Post by Rubi1200 on 2019-05-02
I don't know about others but the only screenshot I can see clearly is the first one from the terminal.

I might have tried Zorin once but that was probably years ago so here goes.

From the liveCD/USB open the terminal and run these commands to post here:

```
sudo fdisk -l
```

will show us the drives and partitions

Once we know the layout we can talk next steps.

---

### Post by ivan23m on 2019-05-02
Here are the screenshots you said you can't see, I am going to to the suggested now.

---

### Post by ivan23m on 2019-05-02
```


zorin@zorin:~$ sudo fdisk -l
Disk /dev/loop0: 1.3 GiB, 1388523520 bytes, 2711960 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/sda: 74.5 GiB, 80026361856 bytes, 156301488 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x43796552


Device     Boot     Start       End   Sectors  Size Id Type
/dev/sda1  *         2048 154300415 154298368 73.6G 83 Linux
/dev/sda2       154302462 156301311   1998850  976M  5 Extended
/dev/sda5       154302464 156301311   1998848  976M 82 Linux swap / Solaris




Disk /dev/sdb: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x9c3bafb3


Device     Boot Start       End   Sectors   Size Id Type
/dev/sdb1        2048 488394751 488392704 232.9G  7 HPFS/NTFS/exFAT
zorin@zorin:~$ 


```

---

### Post by Rubi1200 on 2019-05-02
Zorin is installed on sda1 with a swap partition, fine.

What are you using sdb, the 250GB drive for?

Unless you need it right now I would unmount/unplug it and then run this command:

```
sudo smartctl --quietmode=errorsonly --all /dev/sda1 > sda-smart.txt
```

This will check for SMART errors only on the 80GB drive and put the output in a text file which you can attach with the next post.

Thanks.

---

### Post by ivan23m on 2019-05-02
I do not use 250 GB disk, it's from a computer with Windows installed. I wanted to ask is there anything I should do before using it on Linux to make it compatible with but we can deal with that after this.

```


zorin@zorin:~$ sudo smartctl --quietmode=errorsonly --all /dev/sda1 > sda-smart.txt
sudo: smartctl: command not found
zorin@zorin:~$ 



```

Sda-smart text file is empty.

---

### Post by Rubi1200 on 2019-05-02
Two questions:

are you connected to the internet while on the live medium and is the Zorin partition encrypted?

---

### Post by ivan23m on 2019-05-02
First, yes, second, I don' t know the answer, you're gonna have to help me how to check that.

---

### Post by Rubi1200 on 2019-05-02
Since Zorin is based on Ubuntu I thought the smarttools would be installed...

In any event,

```
sudo apt-get install smartmontools --no-install-recommends
```

Once installed run the command again from my previous post with the text output.

Thanks.

---

### Post by ivan23m on 2019-05-02
There it is.

---

### Post by Rubi1200 on 2019-05-02
And if you run this now:

```
sudo fsck /dev/sda1
```

Are there still errors?

---

### Post by ivan23m on 2019-05-02
```


zorin@zorin:~$ sudo smartctl --quietmode=errorsonly --all /dev/sda1 > sda-smart.txt
zorin@zorin:~$ sudo fsck /dev/sda1
fsck from util-linux 2.27.1
e2fsck 1.42.13 (17-May-2015)
/dev/sda1: clean, 331422/4825088 files, 16016831/19287296 blocks


```

---

### Post by Rubi1200 on 2019-05-02
Well, the good news is the file system appears to be clean, so I do not think that is the issue.

How old is the 80GB drive? The images you posted earlier and the text output do not seem to indicate a drive that is immediately failing (but I may be wrong about that).

I definitely recommend backing up all your data if you are concerned about a possible HD failure.

Perhaps the errors you mentioned in the first post were caused by something else, like the DVD drive being damaged...not sure.

I need to get back to work now but will check in later and also see if others have something to add.

---

### Post by ivan23m on 2019-05-02
Thank you, you have spent a few hours with me on this, I appreciate your help very much. I still am not sure what is it about the DVDs not reading but because we managed to check the system, I'll mark it as solved. Maybe it'll help someone.

---

