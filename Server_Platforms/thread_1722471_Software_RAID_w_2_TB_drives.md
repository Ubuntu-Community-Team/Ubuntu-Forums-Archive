---
title: "Software RAID w/ 2 TB drives"
date: 2011-04-05
forum: Server Platforms
---

### Post by putz3000 on 2011-04-05
I have an HP ProLiant ML110 G6 server.  I actually have two of these.  The first one I originally setup using 4 x 1 TB HD's using a combination of software RAID 1 & 5. OS install went just fine.

I then was told the server supports 2 TB drives so on server #2 I installed same brand and series of HD as server #1, but 2 x 2 TB drives.  I am attempting to setup with Software RAID 1, two partitions one for swap and one for the system.  I go through the Ubuntu instructions just like I did on the first server, but if I change the partition to be "physical volume for RAID" then I am no longer allowed to set the boot flag to yes.  It refuses.  I have wasted time talking to HP, I have tried different partition sizes, moved drives to working server, reset bios defaults...Nothing seems to work.

There is a Bios update, but even HP tells me that the update does not address the issue I am having.  

Is there a reason that software RAID wouldn't allow the boot flag to be set on a 2 TB drive?  Is there something about these ML110 G6 servers I should be looking at?  Server settings appear to be the same between server #1 (working) & Server #2 (not working).  This is an entry level server so just built in SATA controller.

---

### Post by putz3000 on 2011-04-06
Does this need to get moved to another thread? No one knows about any software RAID limitations?

---

### Post by psusi on 2011-04-06
The boot flag only has meaning to Microsoft OSes; ignore it.

---

### Post by ian dobson on 2011-04-06
Hi,

I have something similar to you. I have 4 2Tb drives each partitioned with a 20Gb for boot/root and the rest for data. Boot is RAID1 and Data is RAID5.

Just use fdisk to create your RAID1 partition as a type FD (Linux RAID). and use it. Linux doesn't care about the boot flag. Just make sure grub is loaded onto all your boot drives.

Regards
Ian Dobson

---

### Post by psusi on 2011-04-06
> **ian dobson said:**
> 
I have something similar to you. I have 4 2Tb drives each partitioned with a 20Gb for boot/root and the rest for data. Boot is RAID1 and Data is RAID5.


Why not put the whole thing on the raid5?

---

### Post by ian dobson on 2011-04-06
> **psusi said:**
> Why not put the whole thing on the raid5?

Hi,

This server has grown over the last 3 years, and at the beginning grub 0.97 didn't support booting from a RAID5 array. Maybe grub2 supports it, but I don't have the time to play about/never touch a running system.

Regards
Ian Dobson

---

### Post by putz3000 on 2011-04-07
I pushed through the install and got almost complete, but GRUB refuses to install on the drive.  I assume it cannot install on the master boot record because of no boot flag?

---

### Post by putz3000 on 2011-04-07
Any idea's how I can get grub installed and operational? Now I can't boot to OS since there is no Grub guiding the boot up.  

This project has completely screwed with me/wasted tons of time!

---

### Post by Vegan on 2011-04-07
You will need a RAID card with a BIOS on it that supports GPT disk partitions, then you can have an array > 2 TB which is the MBR limit.

---

### Post by psusi on 2011-04-07
> **Vegan said:**
> You will need a RAID card with a BIOS on it that supports GPT disk partitions, then you can have an array > 2 TB which is the MBR limit.

BIOS does not, and need not understand GPT.

To install grub-pc ( bios boot machines ) on GPT, you need to create a small ( 1mb ) bios boot partition.

---

### Post by ian dobson on 2011-04-08
> **putz3000 said:**
> I pushed through the install and got almost complete, but GRUB refuses to install on the drive.  I assume it cannot install on the master boot record because of no boot flag?

What message does grup display when it "refuses" to install?

Regards
Ian Dobson

---

### Post by putz3000 on 2011-04-08
> **ian dobson said:**
> What message does grup display when it "refuses" to install?

Regards
Ian Dobson

Ian, sorry, I would have to go all the way through the installer again - which is what I will probably have to do any how.  If that happens again I will write it down.

---

### Post by putz3000 on 2011-04-08
So if it is an issue of installing on Guid partitions, is this an issue with the Ubuntu installer - a setting I need to change? Is it the physical drive themselves or a bios setting in the main board?  How do I change that?

It doesn't seem to matter what size the partition is, I am unable to make the boot flag on.  What I am trying to do is RAID 1 everything so that it can easily operate if one drive fails or even  move the drives to another box if need be.

Corporate wants software RAID, so hardware is not an option for me.  I would prefer two 2 TB drives than a more convoluted four 1 TB solutions.

When asked if I wanted to install GRUB to the MBR, should I have just said no or would that have also prevented it from installing and booting normal?

---

### Post by srs5694 on 2011-04-08
putz3000,

As ian dobson has said, Linux ignores the boot flag, so you don't need to worry about it.

If you still have some sort of problem, you really must more clearly describe your partitioning system and the nature of the problem. There are at least three ways to do it (more if you get into needlessly complex ways or methods that combine RAID with LVM):


[list]
[*]Partition the physical drives (splitting /dev/sda, /dev/sdb, etc. into /dev/sda1, /dev/sda2, /dev/sdb1, and so on), merge some of these partitions into RAID devices (/dev/md0, /dev/md1, etc.), and put filesystems on these RAID devices.
[*]Partition the physical drives as just described, or perhaps into a single partition per drive (/dev/sda1, /dev/sdb1, and so on), merge these partitions into one or more RAID devices (/dev/md0, and possibly more), and then partition the RAID device(s) (/dev/md0p1, /dev/md0p2, etc.).
[*]Use the physical drives (/dev/sda, /dev/sdb, etc.) directly (without partitions) as the basis for a RAID configuration, probably resulting in a single /dev/md0 that you then partition into /dev/md0p1, /dev/md0p2, etc.
[/list]


There's also the issue of Linux software RAID vs. motherboard software RAID (aka "FakeRAID"). The former is the preferred solution for a Linux-only computer, but motherboard software RAID may be required if you're dual-booting with something else. I have only passing knowledge of motherboard software RAID, but I know that devices get combined and named differently if you use it.

The implications of each approach are different. Without precise knowledge of how your system is set up, advice will be vague or stand a high probability of leading you astray because the advice-giver will make an incorrect assumption.

For starters, you could type the following command and post its output:

```

sudo fdisk -lu

```

That will show us the MBR partition tables on all your disks and RAID arrays. Additional diagnostic commands may be required depending on what that one shows.

---

### Post by psusi on 2011-04-08
Since you seem to have missed it before:

> **psusi said:**
> 
To install grub-pc ( bios boot machines ) on GPT, you need to create a small ( 1mb ) bios boot partition.

---

### Post by putz3000 on 2011-04-11
OK, there have been a couple of requests that I will try to answer.

1) What am I trying to do / how am I trying to build this server. I am following the Ubuntu Server Guide instructions ([https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html](https://help.ubuntu.com/10.04/serverguide/C/advanced-installation.html)).  I want to have two 2 TB hard drives with two partitions - a 16 GB Swap & the remainder for everything else.  Both partitions as RAID 1.

2) I have also been asked for the output from the "fdisk -lu" command.  Here it is:

```
ubuntu@ubuntu:~$ sudo fdisk -lu

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  3907029167  1953514583+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  3907029167  1953514583+  ee  GPT


```

So, it does appear that my drives are set to GUID.  Does anyone know if I can un-set them for GUID?  Also, towards the end of the initial install when Ubuntu 10.10 wanted to install GRUB, I was given a choice. I selected MBR install (I think).  If I would not have done that would I still have needed a separate partition other than the two I created?

Also, there has been two posts telling me to create a 1MB MBR partition I think.  the problem I have with that is that I so far the size of the partition does not seem to matter for the boot flag.  Also, I want this as simple as possible and as mobile / fail over safe as possible.  If a drive crashes I want the second one to be operational with little impact as possible.  If motherboard chokes, I want the ability to move the drives to another machine and power it on.

I am sorry if my information is frustrating, over all I am still pretty "noob" which is not helping me any.  But thank you for everyone's patience and willingness to help.

---

### Post by srs5694 on 2011-04-11
Yes, you've got a GPT configuration. Try posting the following output:

```

sudo parted /dev/sda unit s print
sudo parted /dev/sdb unit s print

```

That will show us your GPT partitions. Depending on your configuration, it may be feasible to convert from GPT to MBR using my [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) software -- see the [Converting from GPT to MBR](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr) section of its documentation; however, there are likely to be other solutions, and GPT has some advantages over MBR, so I'm reluctant to recommend you do that.

> Also, there has been two posts telling me to create a 1MB MBR partition I think.

I think these were referring to a [BIOS Boot Partition,](http://grub.enbug.org/BIOS_Boot_Partition) not an MBR partition. You can create such a partition using GNU Parted, GParted, gdisk, or some other tools, provided you've got enough free space on the hard disk. It *should not* have its "boot flag" set, in libparted terminology, and in fact, doing so would be an *error*. GRUB can often install on a GPT disk without a BIOS Boot Partition, but it's more reliable when it's got one, and sometimes it refuses to boot without one. Thus, I recommend you put your efforts into creating such a partition and re-installing GRUB. Note that the BIOS Boot Partition can be tiny (as small as about 32KiB), so chances are you'll be able to squeeze one in there somehow.

Another point: Under MBR, Linux ignores the boot flag, so you can ignore it, too. Under GPT, what libparted-based tools call the "boot flag" is in fact the partition type code for an EFI System Partition (ESP). If you've got an EFI-based computer, you need one of these to boot; but if you've got a BIOS-based computer, you don't need an ESP, and attempting to set the "boot flag" on anything that's not an ESP will cause problems. Thus, I strongly encourage you to not attempt to set the "boot flag" on anything, since doing so will likely just cause more problems.

This brings up another point, though: Is your computer BIOS-based or EFI-based? Most computers today are BIOS-based, but some EFI-based machines are starting to appear. A few can boot in either way. Ubuntu support for EFI-based computers is still pretty weak, but it should improve with 11.04. The BIOS Boot Partition I've just described is necessary only on BIOS-based computers, as you might expect. If you're in doubt about this BIOS/EFI issue, consult your documentation or contact the computer's manufacturer.

---

### Post by Vegan on 2011-04-11
I have tried 10.10 with a few machines and its hit and miss whether it likes a given RAID card for boot or not.

I have some Adaptec cards that it likes fine but I do not have any recent models to try yet.

---

### Post by putz3000 on 2011-04-13
```
 ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print
Model: ATA ST32000644NS (scsi)
Disk /dev/sda: 3907029168s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start      End          Size         File system     Name  Flags
 1      2048s      31250431s    31248384s    linux-swap(v1)        raid
 2      31250432s  3907028991s  3875778560s                        raid

ubuntu@ubuntu:~$ 
```

```
 ubuntu@ubuntu:~$ sudo parted /dev/sdb unit s print
Model: ATA ST32000644NS (scsi)
Disk /dev/sdb: 3907029168s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start      End          Size         File system     Name  Flags
 1      2048s      31250431s    31248384s    linux-swap(v1)        raid
 2      31250432s  3907028991s  3875778560s                        raid

ubuntu@ubuntu:~$ 
```

---

### Post by srs5694 on 2011-04-13
I recommend you download my [GPT fdisk (gdisk and sgdisk)](http://www.rodsbooks.com/gdisk/download.html) program, install it, and then run the following commands:

```

sudo sgdisk -t 1:8200 /dev/sda
sudo sgdisk -t 1:8200 /dev/sdb
sudo sgdisk -a 8 -n 3:64:2047 /dev/sda
sudo sgdisk -t 3:ef02 /dev/sda

```

These commands fix a couple of problems with your current configuration:


[list]
[*]The first partition on each disk is part of a RAID configuration, but they're identified as swap partitions. Since swap doesn't normally need the protections of RAID, I'm guessing these should be regular swap partitions. The first two commands (with "8200" in them) do this. OTOH, if these really *should* be RAID partitions, and you're using /dev/md0 (or whatever the equivalent RAID device is) directly for swap, you should *not* run the first two of my commands.
[*]The last two of my commands create a new BIOS Boot Partition in the free space at the start of the first drive. (There's no need to create such a partition on the second drive, although you could if you wanted to -- just duplicate those commands but substitute "/dev/sdb" for "/dev/sda".)
[/list]


Once you've done that, re-install GRUB (or the whole Ubuntu) to /dev/sda. With any luck it'll all begin working. If not, post back with more details, including whether you're installing directly to the RAID device (/dev/md0 or /dev/md1) or partitioning it (creating /dev/md1p1, /dev/md1p2, etc.).

---

### Post by putz3000 on 2011-04-13
> **srs5694 said:**
> 
Once you've done that, re-install GRUB (or the whole Ubuntu) to /dev/sda. With any luck it'll all begin working. If not, post back with more details, including whether you're installing directly to the RAID device (/dev/md0 or /dev/md1) or partitioning it (creating /dev/md1p1, /dev/md1p2, etc.).

So you are saying I should create 3 partitions, one swap, one boot and one for everything else? Is the boot partition only for Grub and nothing else?  To allow for degraded RAID, I should install GRUB on the second drive as well correct?

---

### Post by rubylaser on 2011-04-13
opps, wrong thread :)

---

### Post by psusi on 2011-04-13
You don't need a /boot partition.

---

### Post by srs5694 on 2011-04-13
> **putz3000]So you are saying I should create 3 partitions, one swap, one boot and  one for everything else? Is the boot partition only for Grub and nothing  else?  To allow for degraded RAID, I should install GRUB on the second  drive as well correct?[/quote]

Yes, although I personally would split up the "everything else" into separate partitions for root (/) and /home.

The BIOS Boot Partition is used only by GRUB. I suppose for your scenario you might want to create it on both disks, then copy its contents from one to the other after installation (since it's not part of the RAID configuration and thus not automatically copied):

```

sudo dd if=/dev/sda3 of=/dev/sdb3

```

Change the partition numbers if you use something other than /dev/sda3 for the BIOS Boot Partition.

[QUOTE=psusi said:**
> You don't need a /boot partition.

The partition in question is a BIOS Boot Partition, not a Linux /boot partition. On a BIOS-based computer with GPT, a BIOS Boot Partition is recommended, although sometimes you can get away without one. (Putz3000's problem seems to be that he's not so lucky as to fall in this category.)

---

### Post by psusi on 2011-04-14
> **srs5694 said:**
> then copy its contents from one to the other after installation (since it's not part of the RAID configuration and thus not automatically copied):

You don't want to mess with the bios boot partition.  Let grub manage it; it will make sure it is correct when it installs to the disk.

---

### Post by srs5694 on 2011-04-14
> **psusi said:**
> then copy its contents from one to the other after installation (since  it's not part of the RAID configuration and thus not automatically  copied):[quote=srs5694]You don't want to mess with the bios boot partition.  Let grub manage it; it will make sure it is correct when it installs to the disk.[/QUOTE]

The point is that this is a RAID 1 configuration, the intent being to enable the system to boot should a drive fail. Since the BIOS Boot Partition is *not* part of the RAID configuration, that intent will be at least slightly defeated if you leave it entirely to GRUB to manage it; you must manually copy the contents of the BIOS Boot Partition from one drive to another if you expect to be able to boot from the second drive should the first one fail.

---

### Post by psusi on 2011-04-14
> **srs5694 said:**
> The point is that this is a RAID 1 configuration, the intent being to enable the system to boot should a drive fail. Since the BIOS Boot Partition is *not* part of the RAID configuration, that intent will be at least slightly defeated if you leave it entirely to GRUB to manage it; you must manually copy the contents of the BIOS Boot Partition from one drive to another if you expect to be able to boot from the second drive should the first one fail.

I understand the intent; grub must be installed to both disks.  Manually copying the bios boot partition will not help if it fails to do this, since the MBR must also be updated.  If you run dpkg-reconfigure grub-pc it will allow you update the list of disks grub should be installed to, and reinstall it there.

---

### Post by srs5694 on 2011-04-14
> **psusi said:**
> I understand the intent; grub must be installed to both disks.  Manually copying the bios boot partition will not help if it fails to do this, since the MBR must also be updated.  If you run dpkg-reconfigure grub-pc it will allow you update the list of disks grub should be installed to, and reinstall it there.

As Homer Simpson would say: d'oh! I completely forgot about the code in the MBR. You're right. It might make sense to create the BIOS Boot Partition on the second drive, but there's not much point in copying it over unless you also copied over the MBR code. This is possible, but it adds to the risk factor. It might be better to just have a copy of [Super GRUB 2 Disk](http://www.supergrubdisk.org/) on hand to boot in case of a catastrophic failure of the boot disk; that should enable booting and re-installing GRUB without too much hassle.

---

### Post by putz3000 on 2011-04-17
OK, this is driving me nuts. First, I am sorry to everyone for my lack of Linux knowledge/comfort-ability. I do thank everyone for trying to help me. Frustratingly for me, this thread has at times appeared to have turned into a debate over a need for a boot partition.

From what I can tell, I do not need a separate boot partition.  And from what I can tell from my own experimenting, creating a separate boot partition would not work unless I kept it off of the RAID1 configuration.

So the question is still how to install and use Ubuntu Server 10.04.1 on two 2TB Seagate Enterprise HD's split into two partitions both of which are RAID1.

I have bought more than one HP ProLiant ML110 G6 server. Supposedly identical hardware and from what I can tell, they look that way. Each system came with a default 160GB Seagate HD which I pulled out and replaced with my drives.  In my first system I installed four 1TB Seagate Enterprise HD's. that set I did partition into three partitions, SDx1 - Swap, SDx2 - boot, SDx3 - / (or /var, don't remember off hand).  The first two partitions were set to RAID1 with two spares. the third partition was set to RAID5. I had no problems with this setup and was able to mark SDx2 with the boot flag as instructed by the official Ubuntu 10.04 Server guide.

In the new system, I wanted to simplify things by using two 2TB HD's split into two partitions - swap and /.  So far this has not worked. I am unable to mark a partition with the boot flag. I believe when Grub installs it looks for the boot flag to know where to install, but I could be wrong. Since everyone keeps telling me I do not need the boot flag I have attempted two installs without it. No matter what, even though in the RAID config I have marked SDA2 & SDB2 with a mount point of "/" Grub still fails during install.  I am not even able to manually tell it where to install.  I get the following error message during the install:

[!!] INSTALL THE GRUB BOOT LOADER ON A HARD DISK
Unable to install Grub in /dev/sda
executing 'grub-install /dev/sda' failed
This is a fatal error

So here are the basic instructions from Ubuntu server Guide I have been trying to follow.  Following this is a recent test I did and the results that may or may not be significant.

1) Select Manual as the partition method.

2) Select the first hard drive, and agree to "Create a new empty partition table on this device?".

3) Select the "FREE SPACE" on the first drive then select "Create a new partition".

4) Next, select the Size of the partition. This partition will be the swap partition, and in general rule for swap size is twice that of RAM. Enter the partition size, then choose primary, then Beginning.

5) Select the "Use as:" line at the top. by default this is "Ext4 journaling file system", change that to "physical volume for RAID" then "done setting up partition".

6) For the / partition once again select "Free Space" on the first drive then "Create a new partition".

7) Use the rest of the free space on the drive and choose Continue, then Primary.

8 ) As with the swap partition, select the "Use as:" line at the top, changing it to "physical volume for RAID". Also select the "Bottable flag:" line to change the value to "on". Then choose "Done setting up partition".

9) Repeat steps three through eight for the other disk partitions.

The next part of the instructions are for RAID configuration - all of which works as instructed to step by step.

My problem form the get go is tied to the partition instructions.  Those instructions worked (with same install disk 10.04.01) just fine in my first system that had four 1TB drives.  Granted, in that set I did have a boot partition, but it too was set as RAID1 - so the instructions still worked as described, just modified to meet more than a 2 disk RIAD1 system build.

They are not however, working for the two 2TB system build.  Steps 1 - 3 work. But my problems start with Step 4. I am able to select the size of the partition. But I am never EVER asked if it is a Primary or Logical partition. I am asked, after the size, if the partition should be beginning or end. So, with Step four parts 1 and 3 are an option, but part 2 is skipped all together.  I believe that is why I am not able to mark anything as bootable.  When the time comes in step 8 to select the "Bootable flag:", the screen just flashes but the option does not change to on.

Now, here is some information that I thought was strange. I have two 2TB drives. For partition 1 (SWAP) I set the partition size to 16 GB. The installer still shows 2TB for the remaining drive space. And, when I go to make the next partition, the installer shows 2TB. I had assumed the wizard was just rounding up visually for those of us noobs, but now I am not so sure the installer is properly allocating the amount of left over space.

Here is my test:

I took the original 160Gb Seagate drives that came in these two servers and I installed them. When I got to the partitioning instructions form the official install guide, guess what? they all worked - 100% of them. Set the boot flag? No problem! Same qty partitions. I even made my swap size the same 16 GB and the system correctly allocated the remaining amount of drive space. Step four asked me if the partitions were primary or logical and I was able to select the "Bootable flag:" to on.

So, any ideas? How can I get the option of primary/logical which I am pretty sure will solve my boot flag/grub install issue?

---

### Post by psusi on 2011-04-17
It sounds like you have created a GPT partition table instead of an MSDOS one.  Either start over and create an MSDOS partition table, or create a third partition ( on all disks, as small as you can, 1mb is more than enough ) and set the boot flag on that.

---

### Post by srs5694 on 2011-04-17
> **putz3000 said:**
> So the question is still how to install and use Ubuntu Server 10.04.1 on two 2TB Seagate Enterprise HD's split into two partitions both of which are RAID1.

That's *not* a configuration that will work, especially not with GPT. It's got several problems, although only the first is a show-stopper:


[list=1]
[*]The BIOS Boot Partition ***must not be*** a RAID partition. Period. IIRC, you said you want to configure it this way because management insists on RAID 1. If your management is so brain-dead as to insist that every partition be RAIDed, then you have no choice but to abandon GPT in favor of MBR. This is possible right now, with the disks you've got, but may not be in the future, when drives get a little bit bigger.
[*]GRUB works best on BIOS-based computers with GPT disks if it has a BIOS Boot Partition. Sometimes you can get around this requirement, but not always.
[*]Although you *can* put swap space in a RAID 1 partition, doing so will degrade performance for very little reason. By its very nature, swap space is temporary, so if it gets trashed it's not as big a deal as if a file on a filesystem gets trashed. I don't know enough about how swap on RAID 1 responds to various types of disk errors to say if there's much advantage to doing it that way from a reliability point of view. Personally, I wouldn't do it this way; I'd just create two ordinary (non-RAID) swap partitions, one on each drive. Each swap partition can be a bit smaller this way, too.
[*]If I understand your configuration correctly, you're talking about a single filesystem for everything -- both system files and user files. IMHO, this is a mistake. You should have, at a minimum, a root (/) filesystem and a /home partition, at least if it'll be a workstation or something else with much in /home. If not (say, if it's a Web server), you should split off whatever directory is appropriate (perhaps /var). You *can* do it all on one filesystem, but separating system files from user files offers extra flexibility when it comes to upgrading the OS, performing backups, and so on.
[/list]


> I am unable to mark a partition with the boot flag. I believe when Grub installs it looks for the boot flag to know where to install, but I could be wrong.

I've written this several times before in this thread. Please forgive me if I sound frustrated, but:

***[SIZE=4]YOU DO NOT NEED A BOOT FLAG ON ANY PARTITION IN YOUR SETUP, AND WITH A GPT DISK A "BOOT FLAG" _CANNOT_ BE SET ON A RAID PARTITION[/SIZE]***.

> Since everyone keeps telling me I do not need the boot flag I have attempted two installs without it. No matter what, even though in the RAID config I have marked SDA2 & SDB2 with a mount point of "/"

I'm unfamiliar with how the Ubuntu installer interacts with RAID, but with other Linux versions I've installed on RAID systems, you'd specify the single RAID device (as in /dev/md0 or whatever), not the underlying devices (/dev/sda2 & /dev/sdb2 or whatever).

> Grub still fails during install.  I am not even able to manually tell it where to install.  I get the following error message during the install:

[!!] INSTALL THE GRUB BOOT LOADER ON A HARD DISK
Unable to install Grub in /dev/sda
executing 'grub-install /dev/sda' failed
This is a fatal error

As I've written before, this is probably because of the lack of a BIOS Boot Partition. You can create one by creating a small (32KiB to 1MiB) partition and flagging it as "bios_grub" in GParted or by using gdisk and giving the partition a type code of EF02. See [this page](http://grub.enbug.org/BIOS_Boot_Partition) for details.

(BTW, GParted and other libparted-based tools do a poor job of conveying the nature of the underlying GPT data structures. This, I believe, is part of your problem in your insistence on looking for a way to set the "boot flag." The libparted-based tools make it look like it ought to be possible, but it's not. GPT fdisk (gdisk) presents the GPT data structures as they are, and so is less likely to mislead you in this way. OTOH, gdisk, is a text-mode tool without a pretty GUI, so it's likely to be harder to use if you're used to GParted. What GParted calls the "boot flag" and the "raid flag" are, on GPT disks, two different and mutually exclusive partition type codes. Setting them both would be like trying to cram two SUVs into a single parking space. Under MBR, the "boot flag" is independent of the RAID partition type code, so they can both be set simultaneously, but this isn't true under GPT.)

So here are the basic instructions from Ubuntu server Guide I have been trying to follow.  Following this is a recent test I did and the results that may or may not be significant.

> 8 ) As with the swap partition, select the "Use as:" line at the top, changing it to "physical volume for RAID". Also select the "Bottable flag:" line to change the value to "on". Then choose "Done setting up partition".

[SIZE=4]***DO NOT SET THE "BOOTABLE FLAG" ON ANY PARTITION IN YOUR CONFIGURATION!!! DOING SO MAKES THE PARTITION NO LONGER A RAID PARTITION!!!***[/SIZE]

> My problem form the get go is tied to the partition instructions.  Those instructions worked (with same install disk 10.04.01) just fine in my first system that had four 1TB drives.  Granted, in that set I did have a boot partition, but it too was set as RAID1 - so the instructions still worked as described, just modified to meet more than a 2 disk RIAD1 system build.

My suspicion is that the Ubuntu installer is using GPT by default on 2 TB disks but used MBR by default on the 1 TB disks. MBR supports a "boot flag" that's independent of the partition type code. GPT does not (or at least, not in a way that's mapped by GParted). GRUB also works best with a BIOS Boot Partition on GPT disks, but does not need such a partition on MBR disks.

> They are not however, working for the two 2TB system build.  Steps 1 - 3 work. But my problems start with Step 4. I am able to select the size of the partition. But I am never EVER asked if it is a Primary or Logical partition.

The primary/extended/logical distinction is a very old hack that's unique to MBR. GPT does not need it, since it was designed with support for a sufficient number of partitions from the start.

> Now, here is some information that I thought was strange. I have two 2TB drives. For partition 1 (SWAP) I set the partition size to 16 GB. The installer still shows 2TB for the remaining drive space. And, when I go to make the next partition, the installer shows 2TB. I had assumed the wizard was just rounding up

Yes, it's rounding up. 16 GB = 0.016 TB, so 2 TB - 16 GB = 1.984 TB, which rounds up to 2 TB or even 2.0 TB.

> So, any ideas? How can I get the option of primary/logical which I am pretty sure will solve my boot flag/grub install issue?

The primary/logical issue is ***unrelated*** to the issue of the "boot flag" issue. Please, *follow the advice you've already been given*. You may also want to read the Wikipedia articles on [MBR](http://en.wikipedia.org/wiki/Master_boot_record) and [GPT](http://en.wikipedia.org/wiki/GUID_Partition_Table) so that you'll have a better understanding of what the data structures are.

There are two ways for you to proceed:

Method 1:


[list=1]
[*]Proceed with the installation as you described, but follow the advice I've given you several times; specifically....
[*]Create a [BIOS Boot Partition](http://grub.enbug.org/BIOS_Boot_Partition) ("bios_grub flag," in GParted parlance) on the first disk, and
[*]Don't attempt to set the "boot flag!"
[/list]


If you try this method again and say you've tried to set the boot flag, I won't bother responding.

Method 2:


[list=1]
[*]Boot an emergency disk or Ubuntu live CD and use GParted or parted to create an *MBR* partition table and set up your partitions in that, rather than use the GPT that the Ubuntu installer is creating for you. In GParted, select Device -> Create Partition Table and, in the resulting dialog box, click Advanced and select "msdos" as the partition table type. (*Do not* use fdisk for this; as the disks already have GPT data, fdisk will leave some of that behind, which will cause further problems.)
[*]Reboot into the installer.
[*]When it comes time to deal with partitioning, use the custom option and use the partitions you created earlier. (Depending on how you do it, you might need to flag partitions as being RAID.) Do not let it create new partitions, or it might do so as GPT rather than as MBR.
[/list]


If you try this method, you'll be able to set the boot flag to your heart's content, but be aware that it does nothing.

Be aware that you'll be using GPT soon enough, since MBR can't cope with drives with more than 2^32 sectors (2 TiB when sectors are 512 bytes in size). Thus, you must learn about GPT now. It's really not that hard; you've just got to give up on preconceptions like what the "boot flag" means and the idea that the primary/extended/logical distinction is useful. Because of the latter, GPT is actually simpler than MBR, from a user perspective.

[quote=psusi]It sounds like you have created a GPT partition table instead of an  MSDOS one.  Either start over and create an MSDOS partition table, or  create a third partition ( on all disks, as small as you can, 1mb is  more than enough ) and set the boot flag on that.[/quote]

Actually, the BIOS Boot Partition should *not* have the "boot flag" (as reported by GParted) set; it should have the "bios_grub flag" set. What GParted calls a "boot flag" on GPT disks is actually a partition type code for an EFI System Partition, which is used on EFI-based computers, not BIOS-based computers.

---

### Post by psusi on 2011-04-18
> **srs5694 said:**
> Actually, the BIOS Boot Partition should *not* have the "boot flag" (as reported by GParted) set; it should have the "bios_grub flag" set. What GParted calls a "boot flag" on GPT disks is actually a partition type code for an EFI System Partition, which is used on EFI-based computers, not BIOS-based computers.

Ahh, right.  I was thinking the boot flag was the one translated to the grub bios boot partition; I forgot about EFI.

---

### Post by serge_o on 2011-04-23
Thanks for the answer. I had the same problem - running several servers with this config = 2*HDDs with RAID1.  as I tried it with 2TB it did not work (August 2010) but at that time this problem was not known here yet - I posted here on ubuntuforums in february and still there was no advice.

So you are the first one to give a good piece of advice, thanks.


One question though
you wrote:
> 

Although you *can* put swap space in a RAID 1 partition, doing so will degrade performance for very little reason. By its very nature, swap space is temporary, so if it gets trashed it's not as big a deal as if a file on a filesystem gets trashed. 

as far as I understand, if the drive goes bye-bye half of the swap is lost, correct?
if swap is used at the moment then the system has crashed, correct?
well if that is correct, than swap MUST be on RAID 1 or higher, or be disabled.
the whole RAID thing should result in a system which survives a hard drive failure...
going offline because of an absent memory page in the swap does not count as survive for me...

Am I wrong?


Well, thanks again for the advice - I will try this with the BIOS boot partition.

---

### Post by srs5694 on 2011-04-23
> **serge_o said:**
> as far as I understand, if the drive goes bye-bye half of the swap is lost, correct?
if swap is used at the moment then the system has crashed, correct?
well if that is correct, than swap MUST be on RAID 1 or higher, or be disabled.
the whole RAID thing should result in a system which survives a hard drive failure...
going offline because of an absent memory page in the swap does not count as survive for me...

Am I wrong?

Yes and no. Drives can fail in several different ways. If the whole drive dies, then yes, you'll lose half the swap space and I'd expect the result would be a system crash that might not occur if swap were in the RAID setup. This will not result in loss of filesystem data, though, except for whatever's not yet been flushed to the disk. If a single sector goes bad *in a swap partition*, then swap would be corrupted to a less extreme extent, but I'd expect the result would be similar to catastrophic loss of the drive. If data were *corrupted* in the swap space, though, the result would be hard to predict; it'd be the same as data corruption in memory. If swap were in a RAID 1 configuration, which is what's under discussion, the RAID tools would detect the difference, but I have no idea how they'd react. AFAIK, RAID 1 doesn't help you tell which of the two disks has correct data in this case.

Thus, overall it seems to me that putting swap in a RAID configuration might help you avoid a crash with certain types of disk failure; however, lots of things can cause a crash, so putting swap in a RAID 1 array won't make the computer crash-proof by any stretch of the imagination. Furthermore, you've got to balance the consequences of a *possible* crash against the *certain* consequences of degraded swap performance from putting swap in a software RAID 1 configuration. IMHO, RAID 1 is about protecting valuable system files from damage in case of a disk failure. If a disk fails, you'll almost certainly have downtime, even with RAID 1, so the possibility of a system crash is the least of your worries in that case. Also, note that you'd experience such problems only in the event of a catastrophic failure of the entire disk or bad sectors developing in the sectors consumed by the swap space. If the disk develops bad sectors, the probability of them occurring in the swap space is tiny. If there are no bad sectors but data corruption were to creep in, it's unclear to me which approach would be safer.

---

### Post by serge_o on 2011-04-24
> **srs5694 said:**
> Yes and no. Drives can fail in several different ways. If the whole drive dies, then yes, you'll lose half the swap space and I'd expect the result would be a system crash that might not occur if swap were in the RAID setup. This will not result in loss of filesystem data, though, except for whatever's not yet been flushed to the disk. 


the last part is very importan. there are users sending mail. accessing FTP, jabber, samba, etc.
a sudden system crash will SURELY result in some kind of filesystem corruption here or there. that is why...


> 
If a single sector goes bad *in a swap partition*, then swap would be corrupted to a less extreme extent, but I'd expect the result would be similar to catastrophic loss of the drive. If data were *corrupted* in the swap space, though, the result would be hard to predict; it'd be the same as data corruption in memory. If swap were in a RAID 1 configuration, which is what's under discussion, the RAID tools would detect the difference, but I have no idea how they'd react. 
AFAIK, RAID 1 doesn't help you tell which of the two disks has correct data in this case.


correct, RAID 1 is helpless if the data differ but both drives report OK. if one drive reports a failure then it is straightforward.


> 
Thus, overall it seems to me that putting swap in a RAID configuration might help you avoid a crash with certain types of disk failure; however, lots of things can cause a crash,

I would argue on this point, because HDDs are the most likely to fail. of course any part of a computer could fail any time - if it is not acceptable then we should use a professional storage with all paths doubled - but a processor gone awry is more rare than a crashing HDD.

HDDs fail statistically more often that any other part.
I for my servers can live with the probability of mMotherboard or CPU burning out - one cant help in this case.
But the probabilit of an HDD going away is too high for me.

so that is my opinion on this point about putting SWAP to RAID, but of course one should analyse his own system and make a qualified decision as to whether this choice is ok or not.

 so putting swap in a RAID 1 array won't make the computer crash-proof by any stretch of the imagination. Furthermore, you've got to balance the consequences of a *possible* crash against the *certain* consequences of degraded swap performance from putting swap in a software RAID 1 configuration. IMHO, RAID 1 is about protecting valuable system files from damage in case of a disk failure. If a disk fails, you'll almost certainly have downtime, even with RAID 1, so the possibility of a system crash is the least of your worries in that case. Also, note that you'd experience such problems only in the event of a catastrophic failure of the entire disk or bad sectors developing in the sectors consumed by the swap space. If the disk develops bad sectors, the probability of them occurring in the swap space is tiny. If there are no bad sectors but data corruption were to creep in, it's unclear to me which approach would be safer.[/QUOTE]

---

### Post by psusi on 2011-04-25
Yes, you should put the swap on raid-1 as well so the system doesn't crash if a drive fails.  Remember, the main purpose of raid is to keep the system up, not to protect data.  Raid is not a backup plan!

---

### Post by putz3000 on 2011-04-25
OK, first, thank you srs5694 for putting up with my frustrating lack of knowledge/bull headedness.  I won't attempt to explain anything as it won't lessen the frustration you have obviously had. I also want to thank psusi and serge_o for their input as well.

Now, for some follow-up questions:

Based on what I have read so far, it looks to me like the only way to do this is with 3rd party partitioning software, not the Ubuntu wizard.  Is that correct?

I will need to create at least 3 partitions - a SWAP partition, tiny partition to hold some boot files (does not sound like GRUB or the kernal is installed there?), and at least one more for OS/Data unless I want to further break that down as well.  Is that correct?

Creating the SWAP file as RAID 1 is possible although have to consider system performance versus degree of disaster protection being sought.

The BIOS partition cannot be RAID 1 at all, is that correct? This concerns me a bit as it would seem that I no longer will have the ability to have the system boot in a degraded RAID mode.  Also, it would seem that with out RAIDing the Boot partition I will have to manually install or update files when ever there is a kernel/GRUB update.  Is that a correct understanding, or are the files that are stationary in that little partition not something that is updated/ or updated unless a GRUB3 is released?  I guess I am assuming that what ever tiny files are placed in that partition are actually GRUB files - are they actually unrelated to GRUB?

So, if I use GParted to create my three partitions, then once they are created I can then boot with the Ubuntu install wizard.  When I get to the partition part, I would still select manual, but not change anything.  I would then go into the RAID configuration and mark which ever partition(s) I want for RAID.  Then continue on with the installation and in theory the system will be a working system complete with GRUB.  Is that correct?

---

### Post by srs5694 on 2011-04-25
> **putz3000 said:**
> Based on what I have read so far, it looks to me like the only way to do this is with 3rd party partitioning software, not the Ubuntu wizard.  Is that correct?

That's not technically correct, although I think your conception may be correct. I'm not sure if the partitioner in the Ubuntu installer can do absolutely everything required, but GParted, fdisk and GPT fdisk (gdisk) are all Linux tools that ship with Ubuntu, so I wouldn't describe them as "3rd party" tools. You'd use one or more of these tools to do the partitioning, either from the Ubuntu install CD in "live CD" mode or from another Linux emergency disc.

> I will need to create at least 3 partitions - a SWAP partition, tiny partition to hold some boot files (does not sound like GRUB or the kernal is installed there?), and at least one more for OS/Data unless I want to further break that down as well.  Is that correct?

Mostly correct, and I'd split the OS/data partition into at least two partitions, depending on your needs, as I described earlier in this thread.

The "tiny partition to hold some boot files" actually doesn't hold files per se; it holds part of the code that GRUB runs at boot time, but not in a filesystem. It's just raw machine code that the boot loader runs in as simple a way as it can manage.

> The BIOS partition cannot be RAID 1 at all, is that correct?

If you mean the BIOS Boot Partition, that's correct. (Please use the full and correct name for all partitions; that will minimize the probability of further confusion. At least once earlier in the thread you referred to this as the "boot partition," which a subsequent poster misunderstood to be a reference to the /boot partition, which it's not. The BIOS Boot Partition holds GRUB boot-time code that's executed immediately after the GRUB code in the MBR, whereas the /boot partition holds a Linux filesystem that in turn holds the kernel, initial RAM disk, and GRUB configuration files, among other things. Similar confusion can occur over other partition names if applied sloppily.)

> This concerns me a bit as it would seem that I no longer will have the ability to have the system boot in a degraded RAID mode.

Correct. There are manual ways around this, such as copying the contents of the BIOS Boot Partition and the MBR's boot code from one disk to another. If you don't apply these manual fixes, rendering the remaining disk bootable will be fairly easy -- it's just a matter of re-installing GRUB, which can be done in various ways but is quite straightforward if you know how.

Note that if you were using MBR rather than GPT, the same would be true; you'd need to duplicate the GRUB installation on both disks in one way or another. GPT simply puts a partition around the second-stage boot code, which GRUB on MBR places in a part of the disk that's officially unallocated.

> Also, it would seem that with out RAIDing the Boot partition I will have to manually install or update files when ever there is a kernel/GRUB update.  Is that a correct understanding, or are the files that are stationary in that little partition not something that is updated/ or updated unless a GRUB3 is released?

By "Boot partition," I'm assuming you mean the BIOS Boot Partition, not the /boot partition.

No, you shouldn't normally need to manually update anything when you install a new kernel or GRUB. The code in the BIOS Boot Partition doesn't change with kernel updates and might not change with GRUB updates, although it might under some circumstances.

> So, if I use GParted to create my three partitions, then once they are created I can then boot with the Ubuntu install wizard.  When I get to the partition part, I would still select manual, but not change anything.  I would then go into the RAID configuration and mark which ever partition(s) I want for RAID.  Then continue on with the installation and in theory the system will be a working system complete with GRUB.  Is that correct?
 
Yes.

---

### Post by collisionystm on 2011-04-25
> **putz3000 said:**
> I have an HP ProLiant ML110 G6 server.  I actually have two of these.  The first one I originally setup using 4 x 1 TB HD's using a combination of software RAID 1 & 5. OS install went just fine.

I then was told the server supports 2 TB drives so on server #2 I installed same brand and series of HD as server #1, but 2 x 2 TB drives.  I am attempting to setup with Software RAID 1, two partitions one for swap and one for the system.  I go through the Ubuntu instructions just like I did on the first server, but if I change the partition to be "physical volume for RAID" then I am no longer allowed to set the boot flag to yes.  It refuses.  I have wasted time talking to HP, I have tried different partition sizes, moved drives to working server, reset bios defaults...Nothing seems to work.

There is a Bios update, but even HP tells me that the update does not address the issue I am having.  

Is there a reason that software RAID wouldn't allow the boot flag to be set on a 2 TB drive?  Is there something about these ML110 G6 servers I should be looking at?  Server settings appear to be the same between server #1 (working) & Server #2 (not working).  This is an entry level server so just built in SATA controller.

Is it pure ignorance on my part, or does it just not make sense to break up a raid partition? Take advantage of your hardware and drives and do a RAID10 with 4x2tb. Then just do nightly backups to an external drive. There is no sense in creating a giant swap partition when I doubt ubuntu server would ever peak your ram enough to take advantage. I dunno. Call me crazy.

---

### Post by collisionystm on 2011-04-25
Oh and another thing. Make sure to run badblocks on your drives with a live cd. It will check for bad sectors. Its cheap insurance to check for future problems. If you have bad sectors toss the drive and get a new one. I have never had problems with drives that pass the test.

---

### Post by psusi on 2011-04-26
> **putz3000 said:**
> 
Based on what I have read so far, it looks to me like the only way to do this is with 3rd party partitioning software, not the Ubuntu wizard.  Is that correct?

You need to use the alternate installer for raid setups, not the livecd.  The alternate installer handles all of this just fine.

> **putz3000 said:**
> The BIOS partition cannot be RAID 1 at all, is that correct? This concerns me a bit as it would seem that I no longer will have the ability to have the system boot in a degraded RAID mode.  Also, it would seem that with out RAIDing the Boot partition I will have to manually install or update files when ever there is a kernel/GRUB update.  Is that a correct understanding, or are the files that are stationary in that little partition not something that is updated/ or updated unless a GRUB3 is released?  I guess I am assuming that what ever tiny files are placed in that partition are actually GRUB files - are they actually unrelated to GRUB?

Yes, the bios boot partition can not also be raid.  There is a configuration screen for where to install grub to.  It will list all of your disks and have a check box next to each.  If you check each of them ( and have created a bios boot partition on each ) then grub will be installed to each of them, and any one of them will be capable of booting.

Grub2 is technically still in beta and there no no plans for a grub3, but any time grub is updated, it will automatically reinstall to each of the disks you originally selected.

> **putz3000 said:**
> So, if I use GParted to create my three partitions, then once they are created I can then boot with the Ubuntu install wizard.  When I get to the partition part, I would still select manual, but not change anything.  I would then go into the RAID configuration and mark which ever partition(s) I want for RAID.  Then continue on with the installation and in theory the system will be a working system complete with GRUB.  Is that correct?

Use the installer to create the partitions, not gparted.  On each disk, create the 1 mb grub_bios partition, then your raid partitions, then make sure you tell grub to install to all of the disks.

---

### Post by paddygreenhood on 2011-07-26
Ok, have read this entire thread.
Would it not be sensible to amend the advanced installation guide [https://help.ubuntu.com/11.04/serverguide/C/advanced-installation.html](https://help.ubuntu.com/11.04/serverguide/C/advanced-installation.html)
to reflect this?
It's a long and winding road otherwise...

---

### Post by putz3000 on 2011-07-27
paddygreenhood: I completely agree. There is no excuse for it. I have been unable to update this post with a "How To" based on my experience, but I hope to do so in near future. Now that I know what I am looking for I want to see if it is even possible to setup and install using normal server install disk.  For my install I used the alternate disk, but the alternate disk installed desktop so after the install I then used the server disk to reinstall.  That worked because I had used the alternate disk to setup the partitions in the way Grub needed them.

---

### Post by TobyLL on 2011-12-17
Apologies for posting on an old thread, but I have been having had similar problems myself, and haven't found a step-by-step guide anywhere.

Having read through the forums, here is my attempt at a HOWTO for installing Ubuntu Server on disks large than 2TB.  These steps were all detailed by previous posters, so thanks are due to them for actually providing the answers.

I have tested the following steps on a HP ProLiant MicroServer N40L, with 2 x 2.5TB WD Caviar Green disks, using Ubuntu Server 10.04.3.

The text format below is copied from [https://help.ubuntu.com/11.04/serverguide/C/advanced-installation.html#software-raid](https://help.ubuntu.com/11.04/serverguide/C/advanced-installation.html#software-raid), as it is intended to be a replacement for that page for disks larger than 2 TB.

Follow the installation steps until you get to the *Partition disks* step, then:
[LIST=1]
[*]Select *Manual* as the partition method
[*]Make a note of the disk device names, they may be needed later, e.g. SCSI1 (0,0,0) (**sda**), SCSI2 (0,0,0) (**sdb**)
[*]Select the first hard drive, and agree to "Create a new empty partition table on this device?".
Repeat this step for each drive.
[*]Select the *"FREE SPACE"* on the first drive then select *"Create a new partition"*.
[*]Next, select the *Size* of the partition as 1 MB.
[*]Select the *"Use as:"* line at the top. By default this is *"Ext4 journaling file system"*, change that to "Reserved BIOS boot area".  *"Bootable"* should be *off* by default - leave it as off.  This partition does not need a mount point. Select "Done setting up partition". 
[*]Continue with swap and RAID partitioning as per [https://help.ubuntu.com/11.04/serverguide/C/advanced-installation.html#software-raid](https://help.ubuntu.com/11.04/serverguide/C/advanced-installation.html#software-raid)
[/LIST]
Note that during the 10.04.3 installation, a 1.0 MB FREE SPACE area appeared at the start of each of drive.  This didn't affect the install.

Continue install until the *Configuring grub-pc* screen prompts you to *Install the GRUB boot loader to the master boot record?*.  Select *Yes*.

After the installation has completed, and the machine has rebooted, login and run the following commands:
sudo grub-install /dev/sda
sudo grub-install /dev/sdb
(repeat for all disks in the system)

**Notes**
I attempted the above with Ubuntu Server 11.10, and although the install worked correctly, pulling one of the disks resulted in an unbootable system.  Although the GRUB menu appeared correctly, selecting any of the boot menu items resulted in an immediate reboot.  None of the menu items were editable.  I suspect that this was a problem with the GRUB setup in some way, but didn't probe any further.  Pulling the other disk worked, i.e. the unbootable system only occurred for one of the disks.

---

