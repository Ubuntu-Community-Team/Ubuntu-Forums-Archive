---
title: "PP in SSD: Do we have any current/important issue?"
date: 2011-11-09
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by effenberg0x0 on 2011-11-09
I'll be moving my current install of PP later today. From: WD SATA 3.0 1TB HDD To: Corsair Sata 3.0 120GB SSD.

I never player with SSD in Linux. I'm thinking about just booting the machine to a Clonezilla CD and go from there. I'll be alright with the aligning ssd partitions thing, copying stuff, recreating grub, fstab, etc. And there are many tutorials online so no probs there. 

The thing is I clearly remember seeing some thread that pointed out Oneiric had issues with  SSD during the last development cycle, but I can't find it. I can't remember if it was just someone complaining about having to manually edit fstab to add trim support via discard mount option or if it was something important.

I was just wondering if we currently have any relevant issue regarding the use of SSD in PP. Is anyone using it?

Thanks,
Effenberg

**EDIT: **Yes, I'll backup all the data (to a network drive) before procedure :)

---

### Post by Harry33 on 2011-11-09
There are at least these threads about 11.10 installation on SSD:

1 . [http://ubuntuforums.org/showthread.php?t=1860020&highlight=SSD](http://ubuntuforums.org/showthread.php?t=1860020&highlight=SSD)

2. [http://ubuntuforums.org/showthread.php?t=1862333](http://ubuntuforums.org/showthread.php?t=1862333)

I also remember reading here a thread about speed issues with SSD; not being fast enough compared to the specs.

---

### Post by ronacc on 2011-11-09
I have been running ubuntu maveric (64bit) on an SSD for about a year with no issues  except that it boots so fast that I can't finish pouring my morning coffee before its at desktop .

---

### Post by effenberg0x0 on 2011-11-09
> **ronacc said:**
> I have been running ubuntu maveric (64bit) on an SSD for about a year with no issues  except that it boots so fast that I can't finish pouring my morning coffee before its at desktop .

Thanks Ronacc, I read those threads and a lot of others. In Oneiric, people are most of all confused about the real need to align and implement mount parameters to avoid the SSD from wearing out fast. But there are consistent mentions to under spec speeds. I have attached the drive to the destination PC and mounted as secondary, just to test it. 

Curiously, these potential speed issues seem to not affect us (probably cause were on a newer Kernel?). Speeds seem pretty ok (amazing actually, in comparison to standard Sata 3.0 HDD).

I'm gonna part the thing properly, grub it, make it primary and rsync or dd the old stuff to it. I'll report any thing I find that could relate to these Oneiric issues, but I'm under the impression the thing is working perfectly out of the box in our Ubuntu+1 setup...

---

### Post by Xgen on 2011-11-09
I have a one year old 80 gb SSD as my primary drive running Maverick, Natty, Oneiric and Precise. It was recognized with no problems and I partitioned it like a normal hard drive with no extra settings. I use Burg as my boot loader and all start under 10 seconds from the menu.

---

### Post by tekstr1der on 2011-11-09
> **effenberg0x0 said:**
> I'm gonna part the thing properly, grub it, make it primary and rsync or dd the old stuff to it. I'll report any thing I find that could relate to these Oneiric issues, but I'm under the impression the thing is working perfectly out of the box in our Ubuntu+1 setup...

It sounds like you are aware of the various methods to employ in optimizing your SSD experience. Proper alignment happens automagically these days during partitioning at install time with a 1 MiB offset, so that should not be an issue, but I'd still verify it with parted.

It also sounds like this is a single disk, not a raid, and is not encrypted? Therefore you don't need to worry about passing trim/discard through device-mapper. This functionality has just gained support as of 3.1.x kernel. Cryptsetup now has this ability:

> Support --enable-discards option to allow discards/TRIM requests. 

    Since kernel 3.1, dm-crypt devices optionally (not by default) support block discards (TRIM) comands. 

    If you want to enable this operation, you have to enable it manually on every activation using --enable-discards 

    cryptsetup luksOpen --enable-discards /dev/sdb test_disk

    WARNING: There are several security consequences, please read at least
    [http://asalor.blogspot.com/2011/08/trim-dm-crypt-problems.html](http://asalor.blogspot.com/2011/08/trim-dm-crypt-problems.html)
    before you enable it. 

Other than the partition offset, discard flag in fstab, and optionally noatime/relatime flags in fstab, I can't think of anything else you need to tweak from the default setup to have a happy healthy SSD.

---

### Post by ubuntukid on 2011-11-09
I'm just going to jump in here :P. I was considering replacing the HDD in my laptop with an SSD come June (that's when I'll have the money for it). Is 12.04 expected to work well with ssd in the sense that I can just install it and everything should work well or will we still be using the command line to optimize it? I'm not much of a command line user myself.

---

### Post by effenberg0x0 on 2011-11-09
> **ubuntukid said:**
> I'm just going to jump in here :P. I was considering replacing the HDD in my laptop with an SSD come June (that's when I'll have the money for it). Is 12.04 expected to work well with ssd in the sense that I can just install it and everything should work well or will we still be using the command line to optimize it? I'm not much of a command line user myself.

As far as could see in very previous testings, even Oneiric is handling SSDs well. It's installer is dealing with the aspects of alignment properly. From then on, from the OS perspective, it's just a standard disk: Install your stuff, use it normally. 

I think this speed issues people sometimes mention on Oneiric are probably write-speed low performance due to wrong attempts at manually aligning the partitions, maybe some forgotten and wrong /etc/fstab parameters and/or old and non-updated kernel versions. 

It looks like a proper install, fully updated, handle things ok.

---

### Post by effenberg0x0 on 2011-11-09
> **Xgen said:**
> I have a one year old 80 gb SSD as my primary drive running Maverick, Natty, Oneiric and Precise. It was recognized with no problems and I partitioned it like a normal hard drive with no extra settings. I use Burg as my boot loader and all start under 10 seconds from the menu.

I'll have to fiddle a little as my current main and only HDD in this machine is using more space then fits the ssd (120GB). I'm guessing you're keeping your home directory at another physical drive, in order to fit that many distros, and it's packages, in 80GB? I'll keep a 1TB standard HDD for $HOME.

> **tekstr1der said:**
> It sounds like you are aware of the various methods to employ in optimizing your SSD experience. Proper alignment happens automagically these days during partitioning at install time with a 1 MiB offset, so that should not be an issue, but I'd still verify it with parted.

It also sounds like this is a single disk, not a raid, and is not encrypted? Therefore you don't need to worry about passing trim/discard through device-mapper. This functionality has just gained support as of 3.1.x kernel. Cryptsetup now has this ability:

Other than the partition offset, discard flag in fstab, and optionally noatime/relatime flags in fstab, I can't think of anything else you need to tweak from the default setup to have a happy healthy SSD.

Yes, these are exactly the options I'm considering. I'll be doing the &#7765;artitioning manually, as instead of going through a clean install I am actually moving a working install from one traditional HDD to the SSD. I'll not go for encryption and RAID because I have a server (Ubuntu too) that acts as a storage in the LAN. So the machines can mainly just hold the OS, some stuff you are currently working at $HOME, etc, but backups and important stuff are inside each users directory in the smb network, running on a large RAID60 (LVM, with encryption, etc). As the speeds are viable under a Gigabit LAN, most users dropped local backups.

---

### Post by effenberg0x0 on 2011-11-11
This is just an update to close the issue (and in case users search this forum section for info regarding support for SSD in PP).

I have tested both a migration from fully updated PP from standard HDD to SSD and a fresh install to SSD. It worked perfectly in both cases. Reinstalling does takes care of alignment properly, but fstab is mounted with "defaults" only. So one should manually add the adequate mount options for sdd preservation (the relevance of these options in current hardware / drivers is a point of long discussion anyway). 

There's no speed issue in PP, as measured using standard methods (hdparm, palimpsest, bonnie, dd, etc). Benchmarking results of these apps are coherent with SSD specs.
 
****

---

### Post by Jordanwb on 2011-11-22
I'd suggest using rsynd or cp rather than dd because the former operate at the file system layer while the last operates on the block layer. If you use dd, the SSD thinks that all the blocks are in use and has a harder time performing its garbage collection routines. You'd need to update grub and edit /etc/fstab

---

### Post by teh603 on 2011-11-22
No mention of using ext2 or disabling ext4 journaling to preserve the SSD, or was that covered somewhere else?

---

### Post by effenberg0x0 on 2011-11-22
> **Jordanwb said:**
> I'd suggest using rsynd or cp rather than dd because the former operate at the file system layer while the last operates on the block layer. If you use dd, the SSD thinks that all the blocks are in use and has a harder time performing its garbage collection routines. You'd need to update grub and edit /etc/fstab

grub/mount: Of course, that's implicit. My purpose of the thread, when I started it, was to grab opinions/ understand if, in terms of kernel support / drivers / sata3+ssd support, the issues frequently reported (slow r/w, sata failure/resync, etc) were real or just a result of the average-user lack of skills/anxiety. And the answer is #2: Ubuntu support is perfect in OO (and thus PP).

dd: Curiously matches Bonnie results. Very similar. When I used it, I deliberately wanted to test speed using different block sizes, to tune FS properly. For the 1:1 copy, I initially wanted to bind the device to /dev/raw(n), but since it's deprecated, for the sake of simplicity, I booted to Clonezilla and went for a coffee :) For larger devices, critical data, like duplicating raid disks, I also rely on dd. It's rare for me to trust cp -axR when it comes to larger amounts of data. I find rsync to be slower and got used to applying it only to lan/wan syncing. It's a matter of old habits I guess. cp probably is very reliable.

---

### Post by effenberg0x0 on 2011-11-22
> **teh603 said:**
> No mention of using ext2 or disabling ext4 journaling to preserve the SSD, or was that covered somewhere else?

I didn't wanted to go ext2. I chose the advantages of ext4, but disabled journaling. Now, if the next reply say that ext4 minus journaling = ext3 I'll answer RTFM :)

Seriously: I evaluated the controller specs, updated it's BIOS, tested proper block sizes and alignments, went for ext4, tuned the FS to it, disabled journaling, activated trim, moved swap to my ram disk etc. Performance is good for an average SSD (2x 120GB Sata 3 Corsair Force 3), I don't have any complain.

---

### Post by cometdog on 2011-11-28
> **effenberg0x0 said:**
> grub/mount: Of course, that's implicit. My purpose of the thread, when I started it, was to grab opinions/ understand if, in terms of kernel support / drivers / sata3+ssd support, the issues frequently reported (slow r/w, sata failure/resync, etc) were real or just a result of the average-user lack of skills/anxiety. And the answer is #2: Ubuntu support is perfect in OO (and thus PP).


Hmmm...  Just having installed OO myself, I wouldn't agree that support is perfect.  I have a pair of SSDs and wanted to set them up with LVM striping, since TRIM is still unsupported with RAID.  As far as I can tell, LVM striping can't be set up with the alternate installer (or at least it does not seem to be made clear if it is in fact doing so).  So this left me to do my partitioning and LVM setup manually, outside of the installer.  I'm pretty sure I didn't get the partitions aligned properly, but I'm also not sure how to tell whether I did.  In any case my shiny new SSDs look slower than they probably should through hdparm.  I hope that in PP we can have an LVM striping option in the installer.

---

### Post by effenberg0x0 on 2011-11-28
You do realize that you are talking about support for SSDs under raid under LVM specifics, in a forum section about Ubuntu+1, but you seem to be using Oneiric Oncelot? I'm confused by that.

> **cometdog said:**
> Hmmm...  Just having installed OO myself, I wouldn't agree that support is perfect.  I have a pair of SSDs and wanted to set them up with LVM striping, since TRIM is still unsupported with RAID.  As far as I can tell, LVM striping can't be set up with the alternate installer (or at least it does not seem to be made clear if it is in fact doing so).  So this left me to do my partitioning and LVM setup manually, outside of the installer.  I'm pretty sure I didn't get the partitions aligned properly, but I'm also not sure how to tell whether I did.  In any case my shiny new SSDs look slower than they probably should through hdparm.  I hope that in PP we can have an LVM striping option in the installer.

It's not Ubuntu related. Any distro that uses MDADM for RAID won't support Trim. Read this, from Neil Brown, creator/developer of developer of mdadm: [http://permalink.gmane.org/gmane.linux.raid/34479](http://permalink.gmane.org/gmane.linux.raid/34479)

I'm not even sure mdadm knows the technology of the disk it is using. I would expect discard initiatives to come from the FS. 

There's one workaround: MDTRIM: [https://github.com/Cyberax/mdtrim/](https://github.com/Cyberax/mdtrim/)

But dmraid supports trim. See [http://www.ocztechnologyforum.com/forum/showthread.php?82648-software-RAID-LVM-TRIM-support-on-Linux](http://www.ocztechnologyforum.com/forum/showthread.php?82648-software-RAID-LVM-TRIM-support-on-Linux) and [http://docs.redhat.com/docs/en-US/Red_Hat_Enterprise_Linux/6/html/Storage_Administration_Guide/newmds-ssdtuning.html](http://docs.redhat.com/docs/en-US/Red_Hat_Enterprise_Linux/6/html/Storage_Administration_Guide/newmds-ssdtuning.html)

> **cometdog said:**
> 
 I'm pretty sure I didn't get the partitions aligned properly, but I'm also not sure how to tell whether I did.
I would check this out before even thinking so much about trim support.
> **cometdog said:**
> 
In any case my shiny new SSDs look slower than they probably should through hdparm

HDParm is not a good test for SSDs. But is a good tool to tweak one. Study it's man pages.

Also, check the speed of your SATA link. I use Corsair Force 3 disks on Ubuntu and easily reach spec speed. But my controller is a SATA3, recognized as one, SATA3 cables specific cables, etc.

[09:05 PM][ahsl:AL-DESK:~/dev/citrix/effenberg-patch-]
$ cat /var/log/dmesg | grep -i "SATA Link up"
[    2.544149] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.544174] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)

If you really wanna tweak the SSDs, you gotta think about readahead, block sizes, alignment, etc. It's not easy, there's still no out-of-the-box solution for tweakers that need maximum performance, etc. It demands some reading and tinkering.

---

### Post by teh603 on 2011-11-28
So how much of this matters if I just want to replace my HD with an SSD and I'm not especially worried about tweaking the living (bleep) out of it?

---

### Post by effenberg0x0 on 2011-11-28
> **teh603 said:**
> So how much of this matters if I just want to replace my HD with an SSD and I'm not especially worried about tweaking the living (bleep) out of it?

Do a fresh install of Ubuntu OO in it. It will be properly aligned. 
Edit one single file after boot (/etc/fstab) and add the "discard" option, like this:

UUID=yayayayayayayayaya   /   ext4   defaults,noatime,**discard**,errors=remount-ro   0   1

And use it normally. All the terror about trim, performance, etc will continue for a while, but modern drives and controllers already have embedded fixes for problems that were serious by the end of 2009 / beggining of 2010. It's not an issue anymore. If you do no tweak, still you will have am incredible gain in speed and your HDD will last 5 years or more. 

Changes to kernel and File System will continue to happen every now and then, and some of them will improve support for SSD. But current support works to specs for a domestic user. 

Problems arise if you want to be sure your 10TB SSD storage will pay off the money you spend on it (ROI) in your Data Center. Then you make your supplier sign a contract with an SLA and that's it.

---

### Post by Alan F on 2011-12-21
> **effenberg0x0 said:**
> ............, moved swap to my ram disk etc................

What is the logic of moving swap to a ramdisk? 

I can understand moving temp files to ramdisk to reduce wear on an SSD but surely it is better to turn swap off, or reduce swapability to force retention of files in RAM?

---

### Post by zika on 2011-12-21
> **Alan F said:**
> What is the logic of moving swap to a ramdisk? 

I can understand moving temp files to ramdisk to reduce wear on an SSD but surely it is better to turn swap off, or reduce swapability to force retention of files in RAM?Hm, that reminds me of one conversation on very old BBS in early 80's when I replied to a similar question: it is just like making a new storage within Your apartment in order to make it more spacious... ;)
A simple „swapoff -a“ is much „better“... ;)

---

### Post by effenberg0x0 on 2011-12-21
> **zika said:**
> Hm, that reminds me of one conversation on very old BBS in early 80's when I replied to a similar question: it is just like making a new storage within Your apartment in order to make it more spacious... ;)
A simple &#8222;swapoff -a&#8220; is much &#8222;better&#8220;... ;)
> **Alan F said:**
> What is the logic of moving swap to a ramdisk?

I can understand moving temp files to ramdisk to reduce wear on an SSD but surely it is better to turn swap off, or reduce swapability to force retention of files in RAM?
SSD wear is really not an issue in this case cause it's not my infrastructure. I couldn't care less. If the thing melts the supplier will have to install a new one in 4 hours, meanwhile I'll be downstairs having a coffee and smoking :)
> **zika said:**
> Hm, that reminds me of one conversation on very old BBS in early 80's when I replied to a similar question: it is just like making a new storage within Your apartment in order to make it more spacious...
A simple &#8222;swapoff -a&#8220; is much &#8222;better&#8220;... 
It depends on the machine I'm using and for what. Most of the time, I run with no swap at all and 16GB of RAM. But most software users will swap, or would appreciate an app that swapps nicely without becoming unusable, crashing. I can, for example, limit the machine RAM to see how swapping affects the performance of an application, within desired metrics, and plot that to a chart. Within this curve, you can calculate an area of viability, that defines minimum specs for the current code. That is dramatically affected by some factors and not by others and few are the "general rules", it depends heavily on testing. For example, swapping impact on application usability when using common disks (HDD, SSD), Sata Version (Sata 2, Sata 3), CPU/BUS Speed, etc. You can find an average that can realistically be considered the minimum and recommended specs for some application. But for a software user, it probably makes no sense at all. That's it basically.

---

