---
title: "New Linux User Has Backup Questions"
date: 2010-08-19
forum: System76 Support
---

### Post by ShowMeGrrl on 2010-08-19
I have recently switched to a Linux computer as my main desktop computer after years of using Windows. I have the System76 Wild Dog. I need to set up a backup system for my computer. I was thinking of using the Simple Backup software for backup, but I read the Ubuntu community documentation and now think that might not be the best, since a lot of what I will be backing up are music and photos, which will not benefit from the compression that Simple Backup uses. So now I am thinking Grsync might be the best. 

I am looking for a backup system that is easy and reliable and that will preserve my data in case of a hard drive failure or other data loss emergency. What I really want is to never have to think about backup once I set it up and yet feel that my data is safe and secure. I am not looking for a whole-system imaging- or clone-type backup.

I am thinking of using a USB 2.0 external hard drive as the place to keep the backup, because it seems as if it would be simpler to do than installing an internal hard drive. (I dread opening up my computer box.)  I have some questions:

1) Is Grsync plus an external USB 2.0 hard drive a reasonable way for me to go?

2) What kind or brand of external hard drive would be compatible with my Wild Dog? My Wild Dog has the 64-bit Lucid Lynx 10.04 OS, an Ext4 file system and an ATA WDC WD1001FALS-00J7B0 hard drive. 

3) What size external drive should I get for backup?  My Wild Dog's hard disk is 1 TB in size.

4) Will I have to do any formatting or partitioning or configuring other scary stuff after I get the drive? Of course, it would be wonderful if I could just buy the drive and the USB cable, plug it in and just start backing up to it. Somehow I fear that it is going to be more complicated than that.

---

### Post by isantop on 2010-08-19
I've never used Grsync, so I can't comment on it. It should be okay. If you don't have tons of data to backup, I could recommend a service like Ubuntu One. You have 2 GB free, or 50 or ten bucks a month. You just pick what gets synced, and it syncs it. It also has the added advantage of being a syncing system too, so you may be able to benefit from that.

Your Wild Dog should be compatible with most External Hard Drives. The backup software included with most of them is designed for windows, so it's mostly useless, but the drive should work fine.

The drive will need to be as big as the data you want to back up. 500 GB should be more than enough for at least a long while, or you can buy a 1 TB drive and be completely future proof.

You shouldn't have to do any formatting unless you have files larger than 4 GB. Most external USB devices are formatted with FAT 32, which implses this limit, but you may be able to find one that is formatted with ntfs. If you can't, Ubuntu has a GUI utility you can use to easily format the disk's partition as ext4, or another format of your choice.

---

### Post by ShowMeGrrl on 2010-08-19
> You shouldn't have to do any formatting unless you have files larger than 4 GB. Most external USB devices are formatted with FAT 32, which implses this limit, but you may be able to find one that is formatted with ntfs. If you can't, Ubuntu has a GUI utility you can use to easily format the disk's partition as ext4, or another format of your choice.

I don't believe I have any files larger than 4GB. I get the impression from your response here that there is not any problem backing up from an Ext4 file system to a FAT 32 filesystem?

---

### Post by brokenromeo on 2010-08-19
I use Ubuntu One to sync my important files and documents, and I use Clonezilla and an external USB drive to make an image of my harddrive once a month or so, that way if something happens I can restore my whole system from the image file...I have a dual boot system, so that makes it very easy to restore both OS's and all applications and documents I had to the point of taking the image...

---

### Post by isantop on 2010-08-19
> **ShowMeGrrl said:**
> I don't believe I have any files larger than 4GB. I get the impression from your response here that there is not any problem backing up from an Ext4 file system to a FAT 32 filesystem?
That's correct, there should be no problems. Linux will automatically translate for the difference.

---

### Post by stillnotcool on 2010-08-19
> **ShowMeGrrl said:**
> I have recently switched to a Linux computer as my main desktop computer after years of using Windows. I have the System76 Wild Dog. I need to set up a backup system for my computer. I was thinking of using the Simple Backup software for backup, but I read the Ubuntu community documentation and now think that might not be the best, since a lot of what I will be backing up are music and photos, which will not benefit from the compression that Simple Backup uses. So now I am thinking Grsync might be the best. 

Boy am I glad to see this thread.  I've just spent months working out an adequate backup solution for my Ubuntu setup, and I'm happy to share with you what I've learned through the entire process.  My setup is similar to yours -- while I use a notebook computer with Ubuntu 10.04.1, I store large amounts of data on an external hard disk (formatted hfs+, so it can interoperate with Macs and with other devices I own), and I back up all my data to a second external hard disk.

> **ShowMeGrrl said:**
>  I am looking for a backup system that is easy and reliable and that will preserve my data in case of a hard drive failure or other data loss emergency. What I really want is to never have to think about backup once I set it up and yet feel that my data is safe and secure. I am not looking for a whole-system imaging- or clone-type backup. 

Neither was I, which is why some of the suggestions I encountered (CloneZilla, etc.) weren't for me.  I tried the following solutions:

1) Simple Backup Suite
2) Back in Time
3) Deja Dupe

... and here were the problems:

1) Terribly confusing to set up; compression is lost on my large files; doesn't use Rsync (I don't think)

2) Terribly buggy; while a good substitute for Apple's Time Machine (appealing to me because I just switched from a Mac), this program oddly decided to take complete snapshots of my entire disk whenever it felt like doing so, quickly depleting the storage space on my external drive

3) Terribly simple; this application only allows you to back up and restore single "images" of all the files/folders you have it back up (i.e., to restore ONE file, you're obligated to restore ALL your files from a certain backup ... why restore all 250GB of my data when I only need a 2KB text file?)

> **ShowMeGrrl said:**
>  I am thinking of using a USB 2.0 external hard drive as the place to keep the backup, because it seems as if it would be simpler to do than installing an internal hard drive. (I dread opening up my computer box.) 

I do the same thing, and have never regretted it.

> **ShowMeGrrl said:**
>  I have some questions:

1) Is Grsync plus an external USB 2.0 hard drive a reasonable way for me to go?

2) What kind or brand of external hard drive would be compatible with my Wild Dog? My Wild Dog has the 64-bit Lucid Lynx 10.04 OS, an Ext4 file system and an ATA WDC WD1001FALS-00J7B0 hard drive. 

3) What size external drive should I get for backup?  My Wild Dog's hard disk is 1 TB in size.

4) Will I have to do any formatting or partitioning or configuring other scary stuff after I get the drive? Of course, it would be wonderful if I could just buy the drive and the USB cable, plug it in and just start backing up to it. Somehow I fear that it is going to be more complicated than that.

1) Yes.  This is the solution I finally hit on -- after about two months of toying with options/combinations.  Grsync is powerful, flexible, and it uses the tried-and-true Rsync as its backend.  You can combine Grsync with cron jobs to automate backups, but I am terrible at this sort of thing and have resorted to backing up manually -- which I've found I like much better than automated backups (Time Machine was always making copies of things I didn't want, at times I didn't want it to).

2) I use Western Digital Elements drives.  For large capacity drives from this company, check out the "SE" models, which are USB powered.

3) Buy the largest drive you can afford and grow into it.  Your backup drive should have more space than your "source" drive, but 1.5TB drives are expensive.

4) No, but you may wish to (and it's not scary, trust me!)  As mentioned upthread, files larger than 4GB won't transfer to a FAT32 drive (the default for WD drives); however, I use Ubuntu's disk utility (in System < Administration) to format the external drive as Ext4 before performing my initial backup.  This means I am copying files from an hfs+ drive to an ext4 drive on a daily basis.  I have had no issues with this.

Please keep us posted on your progress.  I completely understand how difficult finding a backup solution can be for a new Ubuntu user, and I'm happy to help in any way I can.  I do wish Ubuntu would ship with a solid solution already in place, but, alas, it does not.

---

### Post by ShowMeGrrl on 2010-08-20
Thanks much to isantop and Semiotic Robotic for very helpful info! I guess I will go forward with my plan and start looking for an external hard drive.

---

### Post by gamerchick02 on 2010-08-20
ShowmeGrrl;

I have a Western Digital 250 gb passport drive I picked up that I use for backups.

I use BackInTime (available in the repos) every week and run a snapshot to the external.  I'm not sure if I can compress (aka .tar) the files with BackInTime or not.

It's been working well for me.  Tomorrow I plan to install a 500 gb drive in my Pangolian and reinstall everything.  I might need to upgrade my eternal to a 1 tb drive or something if I accumulate more data.

Amy

---

### Post by PabloH on 2010-08-20
A word of caution concerning the FAT32 usb partition. While you can copy your data to it, it will not preserve linux/unix file attributes and permissions. That is ok for photos and what not, but if you do a raw copy of system files to FAT32 and then back again-- you are not likely to have a working system. You should be fine if you tar them up first. 

I would make sure whatever backup program you use takes this into account. Otherwise, I would reformat the usb drive to something else. An additional advantage to reformatting is that you can choose to encrypt the drive with something like LUCs. That way, if the drive is stolen or lost-- you don't have to worry about the average person getting your information off it (without knowing the passphrase). The disadvantage is that you can no longer use the drive with windows machines (unless they have GNU utilities installed that can read ext3, etc).

---

### Post by ShowMeGrrl on 2010-08-21
> **PabloH said:**
> A word of caution concerning the FAT32 usb partition. While you can copy your data to it, it will not preserve linux/unix file attributes and permissions. That is ok for photos and what not, but if you do a raw copy of system files to FAT32 and then back again-- you are not likely to have a working system. You should be fine if you tar them up first. 

I would make sure whatever backup program you use takes this into account. Otherwise, I would reformat the usb drive to something else. An additional advantage to reformatting is that you can choose to encrypt the drive with something like LUCs. That way, if the drive is stolen or lost-- you don't have to worry about the average person getting your information off it (without knowing the passphrase). The disadvantage is that you can no longer use the drive with windows machines (unless they have GNU utilities installed that can read ext3, etc).

Well, this is total news to me -- and good to know. I do not intend to encrypt my data as this will not be a portable drive and I am not particularly worried about hiding the data. 

However, I sure don't like the idea of losing the linux file attributes and permissions, etc. So I guess I need to buck up and try to reformat the drive to ext4 and hope that does not prove to be too messy or dangerous a process.

I intend to install WindowsXP using Virtual Box on my Wild Dog. Will I have any problems backing up some of my Windows data on the external drive along with my Linux data? I'm not talking about system files so much as application data (e.g. Quicken) and ordinary files such as .jpgs and .html and .txt and .doc and .pdf.

If I reformat the external drive to ext4, does that mean I won't be able to store backed up data from the Windows virtual machine on it? Would I be able to first transfer the Windows files and folders over to my Linux system and then back up from there to the ext4 filesystem on the external drive? 

I lack experience and knowledge about virtualization and about backups and external drive filesystems, so as you can see, I am a little confused here.

---

### Post by PabloH on 2010-08-22
> **ShowMeGrrl said:**
> Well, this is total news to me -- and good to know. I do not intend to encrypt my data as this will not be a portable drive and I am not particularly worried about hiding the data. 

However, I sure don't like the idea of losing the linux file attributes and permissions, etc. So I guess I need to buck up and try to reformat the drive to ext4 and hope that does not prove to be too messy or dangerous a process.

I intend to install WindowsXP using Virtual Box on my Wild Dog. Will I have any problems backing up some of my Windows data on the external drive along with my Linux data? I'm not talking about system files so much as application data (e.g. Quicken) and ordinary files such as .jpgs and .html and .txt and .doc and .pdf.

If I reformat the external drive to ext4, does that mean I won't be able to store backed up data from the Windows virtual machine on it? Would I be able to first transfer the Windows files and folders over to my Linux system and then back up from there to the ext4 filesystem on the external drive? 

I lack experience and knowledge about virtualization and about backups and external drive filesystems, so as you can see, I am a little confused here.

It should be no problem to put ext4 on the drive. I have done it plenty of times. To do so simply plug in the usb disk. Then right click on the icon for the usbdisk that will appear on the desktop and select format. It should give you ext2 and ext4 as options.

Once you format it, it won't mount in windows anymore. However, there are open source file system readers that you can install in windows that will work with it. I have not used them, so I cannot comment on them. I would not recommend using them in this situation, as there is an easier way.

If you want to look them anyway, one such product is:
[http://www.ext2fsd.com/](http://www.ext2fsd.com/)

You asked about copying your files to linux first, then moving them onto the usbdisk. You could do that, but that is a PITA as well. 

VirtualBox lets you use directories and mounts from your linux computer on the Windows VM. These are shared mounts. The easiest way to get to your usbdisk from windows is to share a directory on your usbdisk with the windowsVM via shared mounts. This will be much easier than trying to get the WindowsVM to mount the usbdisk inside virtualbox. By using the shared mounts you will be able to access the disk from Linux or Windows at the same time.

Your usb disk will likely get mounted in Ubuntu Linux as follows:

/media/someusbdiskname/

In your case, you will probably want to create a directory for your linux machine to rsync to, say "linuxcomputer"-- and then another one for windows to sync to, say "windowsVM". Of course, these should be owned by you and not root.

So you will have something like:

[LIST]
[*]/media/someusbdiskname/linuxcomputer/
[*]/media/someusbdiskname/windowsVM/
[/LIST]

Now, you simply tell VirtualBox to share /media/someusbdiskname/windowsVM with your windows virtual machine. You can then copy your windows files to this directory and rsync your linux files to the linux directory. 

To see how to use shared folders between a Ubuntu host and a windows guest in VirtualBox:

[http://www.youtube.com/watch?v=75FeKOkpSKk](http://www.youtube.com/watch?v=75FeKOkpSKk)

---

### Post by ElSlunko on 2010-08-22
I've used backintime and it's been a very reliable horse for me. I've never had a problem or complication with it and have been able to restore my /home directory after breaking my system when I was doing things I shouldn't have been doing (Damn idle hands!).

---

### Post by stillnotcool on 2010-08-22
> **PabloH said:**
> It should be no problem to put ext4 on the drive. I have done it plenty of times. To do so simply plug in the usb disk. Then right click on the icon for the usbdisk that will appear on the desktop and select format. It should give you ext2 and ext4 as options. 

I'd like to second this suggestion for you, SMGrrl.  In the past, I have used Ubuntu's built-in "Disk Utility" for formatting purposes, but using the right-click context menu will also work for you quite well.  Like you, I am a cautious, inexperienced Linux user, so I'd like to share one more experience with you before you reformat your external drive.

Each time I've formatted my external hard disk as ext4, the formatting process has taken a fairly long time.  I'm comparing this interval with my experiences on Mac OS and Windows, where formatting can take under one minute with the FAT32 or HFS+ filesystems.  However, when formatting large capacity drives (500GB, 750GB) with ext4, I've had to wait nearly ten minutes or the formatting to complete.  Don't panic!  Nothing is wrong.  The drive WILL format and everything will be fine.  I just wanted to share this point of caution with you, because it's something that threw me for a loop the first time I tried what you're about to attempt.

---

### Post by VastOne on 2010-08-22
> **ShowMeGrrl said:**
> I have recently switched to a Linux computer as my main desktop computer after years of using Windows. I have the System76 Wild Dog. I need to set up a backup system for my computer. I was thinking of using the Simple Backup software for backup, but I read the Ubuntu community documentation and now think that might not be the best, since a lot of what I will be backing up are music and photos, which will not benefit from the compression that Simple Backup uses. So now I am thinking Grsync might be the best. 

I am looking for a backup system that is easy and reliable and that will preserve my data in case of a hard drive failure or other data loss emergency. What I really want is to never have to think about backup once I set it up and yet feel that my data is safe and secure. I am not looking for a whole-system imaging- or clone-type backup.

I am thinking of using a USB 2.0 external hard drive as the place to keep the backup, because it seems as if it would be simpler to do than installing an internal hard drive. (I dread opening up my computer box.)  I have some questions:

1) Is Grsync plus an external USB 2.0 hard drive a reasonable way for me to go?

I use Grsync exclusively over an ssh connection to another computer transferring large amounts of music and data everyday.  It is by far the best backup for my needs and I would highly recommend it.

---

### Post by d3v1150m471c on 2010-08-22
an external HD, cronjob, and the native cp command ( or even rsync ). that's all you should really need.

---

### Post by ShowMeGrrl on 2010-08-23
> You asked about copying your files to linux first, then moving them onto the usbdisk. You could do that, but that is a PITA as well. 

VirtualBox lets you use directories and mounts from your linux computer on the Windows VM. These are shared mounts. The easiest way to get to your usbdisk from windows is to share a directory on your usbdisk with the windowsVM via shared mounts. This will be much easier than trying to get the WindowsVM to mount the usbdisk inside virtualbox. By using the shared mounts you will be able to access the disk from Linux or Windows at the same time.

Your usb disk will likely get mounted in Ubuntu Linux as follows:

/media/someusbdiskname/   etc. etc.


Thanks, Pablo. Huge help!

---

### Post by stillnotcool on 2010-08-23
> **VastOne said:**
> I use Grsync exclusively over an ssh connection to another computer transferring large amounts of music and data everyday.  It is by far the best backup for my needs and I would highly recommend it.

I don't mean to hijack the thread, but could you detail the commands/parameters/arguments you use to accomplish this (backing up files via ssh) with Grsync?  It's something I've been wanting to try.

---

### Post by VastOne on 2010-08-23
> **SemioticRobotic said:**
> I don't mean to hijack the thread, but could you detail the commands/parameters/arguments you use to accomplish this (backing up files via ssh) with Grsync?  It's something I've been wanting to try.

Sure - 

Assuming you already have an SSH connection. 

The default ssh port is 22 and I do not like to use that so I changed mine to 92

In Grsync I had to add this to the Advanced Options

-e "ssh -p 92"

-p indicates my port of 92

If you have not changed your default ssh port it would then be 

-e "ssh -p 22"

Everything else in Grsync is self explanatory... But let me know if you need more info

Here is a screen shot

---

### Post by stillnotcool on 2010-08-24
> **VastOne said:**
> Everything else in Grsync is self explanatory... But let me know if you need more info

Great!  And a follow-up: How does Grsync know where to put the files when it makes the connection?  Does it look for a specific directory or does it create the directory you've specified above?  Thanks in advance.

---

### Post by VastOne on 2010-08-24
> **SemioticRobotic said:**
> Great!  And a follow-up: How does Grsync know where to put the files when it makes the connection?  Does it look for a specific directory or does it create the directory you've specified above?  Thanks in advance.

Very good question...

Take a look at the attached picture...

The top is the source in this synchronization that I have setup

The bottom (192.168.40.134:/media/storage/Music) is what I want synchronized on the other side.  And that location is a valid location, so you just have to make sure you are reaching out to a valid location.

So, you can set it up to do whatever you want it to do...

If you wanted your /Home to be copied over for example, you just choose it and where you want it on the other side...

You can Select Open to choose...

I would recommend you do some test copies to get the feel of it and go from there..

You will pick it up in a heartbeat once you see what is going on.

---

### Post by stillnotcool on 2010-08-24
Thanks.  I'll give this a shot soon and report back.  My apologies once again for briefly hijacking the thread.

---

### Post by ShowMeGrrl on 2010-08-29
OK, I got my new USB Western Digital 1.5TB Elements external drive and plugged it in. It was recognized just fine.

I opened the disk utility and tried to set up an EXT4 partition, but after a minute or two, my Wild Dog froze. I started over and successfully set up a 200GB NTFS partition and then tried to set up an EXT3 partition to fill out the rest of the drive. Once again, the system froze.

I would estimate I made four or five attempts to format the drive to EXT4 or EXT3 and each time, my machine froze up. (Most of these failed attempts were before I set up the NTFS partition, but at least one was after I set up the NTFS partition.)

Any ideas of what is going on or what my next steps should be?

---

### Post by PabloH on 2010-08-30
I don't think you are doing anything wrong. It sounds like you have a dud machine to me. Lockups are not normal. If there was a problem with the program-- only it should become unresponsive-- not the whole machine.

---

### Post by isantop on 2010-09-01
I wouldn't say a dud machine. It may be a problem with your installation of the disk utility. You can try GParted, which comes on the LiveCD and is available from the repositories, which should be able to do it just fine.

---

### Post by ShowMeGrrl on 2010-09-01
I tried using gparted to format the 1.13tb remaining on the disk (I earlier had successfully created a 258gb NTFS partition using Disk Utility.) Unfortunately, in the middle of using gparted to format the remaining 1.13tb as ext4, my system froze.

Any ideas?

---

### Post by VastOne on 2010-09-01
> **ShowMeGrrl said:**
> I tried using gparted to format the 1.13tb remaining on the disk (I earlier had successfully created a 258gb NTFS partition using Disk Utility.) Unfortunately, in the middle of using gparted to format the remaining 1.13tb as ext4, my system froze.

Any ideas?

My inclination is that this is a hard drive failure. I would recommend that you return and replace it. I have had the same experiences with brand new drives and they were bad.

---

### Post by ShowMeGrrl on 2010-09-02
OK, after getting system freezes while using the Disk Utility gui and the gparted gui, I am now trying to format the drive using the terminal window. 

The goal is to format an external Western Digital Elements 1.5TB drive. The first partition is NTFS and is 258 GB in size. It seems to be working OK.

I am trying now to format the remaining part of the drive (1.13TB) as ext4. This is what I have been having trouble doing.

The first part (the NTFS partition) is known as sdb1. The second part that I am now trying to format is known as sdb2. 

(The sda partitions refer to my internal hard drive, which I am definitely NOT trying to format!)

Here are the commands I have typed in at the terminal and the responses:

```
username-desktop:~$ sudo umount /dev/sdb2
[sudo] password for username: 
umount: /dev/sdb2: not mounted
username-desktop:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006d56c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      121359   974810546+  83  Linux
/dev/sda2          121359      121602     1952037    5  Extended
/dev/sda5          121359      121602     1952036+  83  Linux

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 1500.3 GB, 1500299395072 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x43dce222

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      182402  1465136127+  ee  GPT
username-desktop:~$ mkfs.ext4 /dev/sdb2
mke2fs 1.41.11 (14-Mar-2010)
mkfs.ext4: Permission denied while trying to determine filesystem size

```

I am kind of stuck and don't know what to do to get this external hard drive formatted so that I can proceed to set up a backup system for my new Linux box. Any help appreciated. I am getting rather frustrated. BTW, the Disk Utility reports that the drive is "healthy."

---

### Post by jdb on 2010-09-02
> **ShowMeGrrl said:**
> 
I am kind of stuck and don't know what to do to get this external hard drive formatted so that I can proceed to set up a backup system for my new Linux box. Any help appreciated. I am getting rather frustrated. BTW, the Disk Utility reports that the drive is "healthy."

This thread sheds some light:
[http://ubuntuforums.org/showthread.php?t=643534]("http://ubuntuforums.org/showthread.php?t=643534")

The name of the "GNU parted" application is just "parted", it should already
be on your machine.

I've never used it but it has a man page
```
man parted
```

jdb

---

### Post by ShowMeGrrl on 2010-09-02
Thanks, jdb. I am thinking I may have made a mistake in using the GUID partitioning table and should have gone with Master Boot Record instead. (It was described in rather unflattering terms -- "a number of limitations with respect to number of partitions and size of disk" -- so I went with GUID, though I didn't really know anything about either. Turns out that MBR will work for me.)

So it seems that I should start over from scratch with the partitioning and select MBR. My question is how do I start over from scratch? Do I just delete the ntfs and other partition and then I am back at square one and can start partitioning again and select MBR this time?

---

### Post by srs5694 on 2010-09-02
Your problem has nothing to do with MBR vs. GPT, and changing to MBR will not help. You just need to include "sudo" before your mkfs.ext4 command, thus:

```

sudo mkfs.ext4 /dev/sdb2

```

---

### Post by ShowMeGrrl on 2010-09-02
> **srs5694 said:**
> Your problem has nothing to do with MBR vs. GPT, and changing to MBR will not help. You just need to include "sudo" before your mkfs.ext4 command, thus:

```

sudo mkfs.ext4 /dev/sdb2

```

Well, you're at least partly right. I typed the code you suggested (i.e., with the 'sudo') and it did start formatting, and I did not get the "permission denied" rejoinder. However, then my system froze again. I had to do a hard reset/reboot.

The reason I think the GUID vs. MBR might be a problem is that fdisk does not support GUID. And Wikipedia says this about the GUID Partition Table: "As of 2010, support for GPT among common systems is limited" Mightn't a system protest if you're trying to format a partition that was created using a non-supported partition table?

---

### Post by isantop on 2010-09-02
In disk utility, there is an option to "Format Drive".Make sure it's format drive and not format volume. This should allow you to setup an MBR partition table.

---

### Post by srs5694 on 2010-09-02
> **ShowMeGrrl said:**
> Well, you're at least partly right. I typed the code you suggested (i.e., with the 'sudo') and it did start formatting, and I did not get the "permission denied" rejoinder. However, then my system froze again. I had to do a hard reset/reboot.

The reason I think the GUID vs. MBR might be a problem is that fdisk does not support GUID. And Wikipedia says this about the GUID Partition Table: "As of 2010, support for GPT among common systems is limited" Mightn't a system protest if you're trying to format a partition that was created using a non-supported partition table?

No. First, fdisk is a separate utility that's uninvolved in creating a filesystem, so fdisk's lack of support for GPT has nothing to do with a system that freezes up when you try to create a filesystem on a GPT disk. Other utilities, such as GNU Parted and gdisk, *do* support GPT. The Linux kernel *does* support GPT (at least, if compiled with GPT support, which is true of Ubuntu's kernel). I've got several systems running with GPT disks, and they're all fine. The Linux kernel has had GPT support since 2001 or thereabouts, so this isn't exactly brand-new stuff. The mkfs utility and its helpers don't know a thing about partition tables; they just work with the device files (/dev/sda1, etc.) provided by the kernel.

Second, the Wikipedia entry's reference to limited GPT support should not be taken to mean that GPT support in Linux is buggy. The Wikipedia reference to limited support is referring to the fact that many OSes don't support GPT at all (many versions of Windows prior to Vista, OS/2, BeOS, etc.), and some don't support all GPT features (for instance, Windows won't boot from GPT on BIOS-based computers). Linux's support for GPT is actually quite good.

I recommend you post the output of parted or (if it's installed) gdisk on the disk, to verify that the GPT data structures are intact. Either of these commands should do it:

```

sudo gdisk -l /dev/sdb
sudo parted /dev/sdb print

```

Even if the GPT data structures are intact, the fact that the system is freezing up when you try to create a filesystem on a disk that doesn't contain the OS screams "hardware fault" to me. You can of course try converting from GPT to MBR (GNU Parted, GParted, and gdisk will all do this), and there's little reason to *not* try this; however, I'd be suspicious if you could use the disk with MBR but not GPT. It could be there's still a problem with the disk, but it's just been masked by the subtle changes that the partition table conversion created.

Another thought: There are utilities that will report the SMART diagnostics on a drive. One is smartctl, but it's a text-mode tool. I don't recall the names of the GUI tools for this, offhand, but they do exist. These tools will tell you whether the drive has detected any problems itself.

---

### Post by ShowMeGrrl on 2010-09-02
Thanks much srs5694! Here is the output you asked for:

```


username-desktop:~$ sudo parted /dev/sdb print
[sudo] password for username: 
Model: WD Ext HDD 1021 (scsi)
Disk /dev/sdb: 1500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name        Flags
 1      17.4kB  258GB   258GB   ntfs
 2      258GB   1500GB  1243GB               Linux-Ext4


```

> Even if the GPT data structures are intact, the fact that the system is freezing up when you try to create a filesystem on a disk that doesn't contain the OS screams "hardware fault" to me. You can of course try converting from GPT to MBR (GNU Parted, GParted, and gdisk will all do this), and there's little reason to not try this; however, I'd be suspicious if you could use the disk with MBR but not GPT. It could be there's still a problem with the disk, but it's just been masked by the subtle changes that the partition table conversion created.

Another thought: There are utilities that will report the SMART diagnostics on a drive. One is smartctl, but it's a text-mode tool. I don't recall the names of the GUI tools for this, offhand, but they do exist. These tools will tell you whether the drive has detected any problems itself.
    	
The Disk Utility that comes with Ubuntu (System-> Administration -> Disk Utility) appears to have these SMART diagnostics. It reports that the drive is "healthy." I clicked on the "SMART Data" button, which is supposed to allow me to "View SMART data and run self tests." When I did this, the report was that everything was either "good" or N/A. 

I will attach a screenshot of the Disk Utility panel showing the external drive and its partitions.

---

### Post by srs5694 on 2010-09-02
Your partition table looks OK, as far as I can tell from the summary output. Here are some more ideas and suggestions:


[list]
[*]It's possible that the drive is OK but that either the connection to the computer is weak (bad cable, cable coming loose, etc.) or that electronics in the interface is bad. This wouldn't turn up in the SMART tests, but it could still cause problems that could result in a system hang. If the drive's cable can be completely replaced, try doing so. Also, try plugging it into a different USB port. If it's connected via a hub, connect it directly to the computer.
[*]Try typing "sudo dd if=/dev/sdb2 of=/dev/null". This command will take a long time to complete, but it will read every byte from the suspect partition. If the system hangs, then you know that something very basic is wrong. If not, then it could be something higher-level or related to writes (more on that shortly). Note that there may be an error message when it finishes the job; just check the reported statistics about how many bytes were copied to be sure it read the whole partition.
[*]If the system hangs during the previous test, try "sudo dd if=/dev/sdb of=/dev/null" (the same command, but using /dev/sdb rather than /dev/sdb2). If this command also hangs, you can rule out the partition table as a cause, with 100% certainty, since this command transfers data from the entire drive, without the intervention of the partition table.
[*]If the system didn't hang, try this: "sudo dd if=/dev/zero of=/dev/sdb2". This fills /dev/sda2 with 0 values. *Be very careful to specify /dev/sdb2 correctly!* If you mistype the partition ID, you'll destroy whatever partition you specify. (I'm assuming it's OK to wipe out that partition, since it presumably contains no data.) As with the previous couple of commands, this one will take quite a while to complete -- perhaps several hours.
[*]You could try using a recent version of my GPT fdisk (gdisk) to convert from GPT to MBR form non-destructively. (Download the latest version [here.](https://sourceforge.net/projects/gptfdisk/files/) The 0.5.1 version that's in Ubuntu's repository is old enough that it's got limited support for the GPT-to-MBR conversion.) To do this, launch the program ("sudo gdisk /dev/sdb"), type "r" to get to the recovery & transformation menu, and type "g" to do the conversion. You'll get the chance to tweak the conversion. You'll probably want to change the type code for /dev/sdb2, so type "2" and then "t" and then "83". Then type "0" to accept the changes and confirm by typing "y". This will convert non-destructively to MBR. To be sure the system is using the new MBR partition table, unplug the drive and then plug it back in. If you subsequently try creating a filesystem and the computer still hangs, you can be 100% certain that the problem is not GPT-related.
[/list]

---

### Post by ShowMeGrrl on 2010-09-02
> You could try using a recent version of my GPT fdisk (gdisk) to convert from GPT to MBR form non-destructively. 

What do you  mean by "non-destructively"? Do you mean without data loss? I don't really have any data on this drive (just one non-important text file), so I do not mind losing all the data.

Or are you saying that to reformat and use MBR this time, that would be harming the drive in some way?

---

### Post by ShowMeGrrl on 2010-09-02
> If the system didn't hang, try this: "sudo dd if=/dev/zero of=/dev/sdb2". This fills /dev/sda2 with 0 values. Be very careful to specify /dev/sdb2 correctly! 

Do you really mean "This fills /dev/sda2 with 0 values"? or do you mean sdb2? I think sda2 is my internal hard drive. I don't really want to mess with it.

---

### Post by srs5694 on 2010-09-02
> **ShowMeGrrl said:**
> What do you  mean by "non-destructively"? Do you mean without data loss? I don't really have any data on this drive (just one non-important text file), so I do not mind losing all the data.

Correct; the partitions will be preserved and their data will remain intact, just converted from GPT to MBR form.

> [Quote]If the system didn't hang, try this: "sudo dd if=/dev/zero of=/dev/sdb2". This fills /dev/sda2 with 0 values. Be very careful to specify /dev/sdb2 correctly!Do you really mean "This fills /dev/sda2 with 0 values"? or do you mean sdb2? I think sda2 is my internal hard drive. I don't really want to mess with it. [/quote]Yes, I meant "/dev/sdb2" in all three places. Sorry about the typo!

---

### Post by ShowMeGrrl on 2010-09-03
OK, here is the latest.

Using gparted, I created a new MBR partition table. I then created a ~250GB ntfs partition. That was successful. 

As an experiment, I tried formatting the other 1+tb partition as ntfs also. It worked quickly and flawlessly. So I had two ntfs partitions and the entire drive was allocated.

The problem, of course, is that I don't want that second partition to be ntfs.

I deleted that second partition and then tried another experiment: To create a small ext4 partition: ~50GB. That worked. That was fine as a test, but I did not want a 50GB partition, so I deleted it.

I next tried a 300GB ext4 partition. System froze.

I took it down to ~200GB ext4 partition -- that worked. 

So I now had as sdb1 a 255GB ntfs partition and as sdb2 a ~200GB ext4 partition. I was able to mount these and copy and paste files into them, etc.

I next tried to create a 250GB ext4 partition. That worked. That was sdb3.

MBR allows a maximum of 4 partitions. I tried to do 275GB for the 4th partition. That failed (system froze). I tried 250GB again and this time, unfortunately, that failed (system froze). I took it down to ~200GB. That worked.

So I now have one ntfs partition and three ext4 partitions. 

I didn't really want three ext4 partitions but the worst part is that 580GB of my external drive is still unallocated and I can't use that unallocated space because I am at the max of 4 partitions. 

This is better than where I was at the last few days of not seeming to be able to get any ext4 partitions, but it's far from ideal.

This is a bug of some kind, but exactly what, I don't know.

---

### Post by srs5694 on 2010-09-03
I'm skeptical that it's a bug; or if it is a bug, it's interacting with your hardware. Think of all the systems on which >250GB ext4 partitions have been created. If there were a bug in the filesystem creation tools that caused *all* such filesystem creation efforts to fail, then you'd be seeing bug reports all over the place.

My suggestion at this point is to return the drive and get another model. This is a weird problem and there's clearly a hardware component to it. (I can't guarantee that a new drive would fix the problem; it could be rooted in the USB controller on your computer, for instance.)

Failing that, try recreating your big partition and creating another Linux-native filesystem on it, like XFS or JFS, rather than ext4fs. If it succeeds, that will work just as well. A caution: If the drive is failing because of, say, extended periods of data transfer, then you'll soon run into problems when you try to store large files on the drive, no matter what filesystem you're using. In fact, this could even happen with your relatively small partitions. Try storing a big file, like a ~4GB DVD image file, on the disk and see if it fails.

---

### Post by jdb on 2010-09-03
> **ShowMeGrrl said:**
> 
MBR allows a maximum of 4 partitions. I tried to do 275GB for the 4th partition. That failed (system froze). I tried 250GB again and this time, unfortunately, that failed (system froze). I took it down to ~200GB. That worked.

So I now have one ntfs partition and three ext4 partitions. 


You can make one of the 4 partitions an extended partition.
You can put as many partitions as you want in an extended partition.
for example:
```
11:45:15 /root fdisk -l /dev/sdb

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009a0f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         131     1052226   83  Linux
/dev/sdb2             132       36161   289410975   83  Linux
/dev/sdb3           36162       54176   144705487+  83  Linux
/dev/sdb4           54177       60801    53215312+   5  Extended
/dev/sdb5           54177       55481    10482381   83  Linux
/dev/sdb6           55482       56786    10482381   83  Linux
/dev/sdb7           56787       58091    10482381   83  Linux
/dev/sdb8           58092       59396    10482381   83  Linux
/dev/sdb9           59397       60801    11285631   82  Linux swap / Solaris
11:45:41 /root 

```

I guess the question is, will it let you make the extended partition as big as the remainder of the disk.

jdb

---

### Post by ShowMeGrrl on 2010-09-03
> **srs5694 said:**
> I'm skeptical that it's a bug; or if it is a bug, it's interacting with your hardware. Think of all the systems on which >250GB ext4 partitions have been created. If there were a bug in the filesystem creation tools that caused *all* such filesystem creation efforts to fail, then you'd be seeing bug reports all over the place.

My suggestion at this point is to return the drive and get another model. This is a weird problem and there's clearly a hardware component to it. (I can't guarantee that a new drive would fix the problem; it could be rooted in the USB controller on your computer, for instance.)

Failing that, try recreating your big partition and creating another Linux-native filesystem on it, like XFS or JFS, rather than ext4fs. If it succeeds, that will work just as well. A caution: If the drive is failing because of, say, extended periods of data transfer, then you'll soon run into problems when you try to store large files on the drive, no matter what filesystem you're using. In fact, this could even happen with your relatively small partitions. Try storing a big file, like a ~4GB DVD image file, on the disk and see if it fails.

Interesting observation about the likely problems storing large files on the drive. I wouldn't be surprised if you're right about that.

A friend of mine did some Googling on this problem and came up with a theory that seems to fit the facts pretty well.

I plan to try her suggested fix (disabling automount) after the Labor Day weekend. I will let you know how it turns out. Here is what she had to say:

> I did some googlng this morning, and saw that some people have run
into problems where they've partitioned a disk, it's unmounted, and
then they go to format it but the OS fires off automount to mount it
as it is being formatted, and the formatting tool goes nuts and
consumes 100% of the CPU and freezes the system.

This fits what you've seen pretty nicely -- you're formatting, and
around 300G in to the process, automount wakes up and does its thing,
and makes gparted/mkfs suck up 100% of the CPU and freeze up your
system, but there's no kernel panic in the logs. It also takes
ext3/ext4 off the hook, which comports with my biases about
filesystem/mkfs solidness. So I'm liking this theory.

The way
to test this hypothesis is to disable automount and format a big chunk
of that drive. 

Many people recommend running gparted as part of a stripped-down
rescue disk boot; my guess is that most of those rescue OSes don't
have automount as part of the OS, so that's why it's more stable.



This could explain why I was able to format that big 1+ TB chunk in ntfs with no problem. For whatever reason, the ntfs formatting happened in a flash. The ext4 formatting was much slower. So under her theory, you could say that the ntfs formatting was completed before automount kicked in, while the ext4 formatting was unable to complete before automount started up.

---

### Post by ShowMeGrrl on 2010-09-03
> I guess the question is, will it let you make the extended partition as big as the remainder of the disk.

Yes, I was thinking the same thing. The way it has been going, I would guess, no. But I should try it and see.

---

### Post by VastOne on 2010-09-03
> **ShowMeGrrl said:**
> Interesting observation about the likely problems storing large files on the drive. I wouldn't be surprised if you're right about that.

A friend of mine did some Googling on this problem and came up with a theory that seems to fit the facts pretty well.

I plan to try her suggested fix (disabling automount) after the Labor Day weekend. I will let you know how it turns out. Here is what she had to say:



This could explain why I was able to format that big 1+ TB chunk in ntfs with no problem. For whatever reason, the ntfs formatting happened in a flash. The ext4 formatting was much slower. So under her theory, you could say that the ntfs formatting was completed before automount kicked in, while the ext4 formatting was unable to complete before automount started up.


A simple solution would be to boot to a LiveCD and try to format there as I am 99% sure automount is disabled then.

---

### Post by CharlesA on 2010-09-03
You don't need to worry about it automounting from my experience.

I've formatted 4 USB HDDs ranging in size from 1.5TB to 2TB from Ubuntu desktop without any problems. As long as it's not mounted to begin with, it'll work fine.

---

### Post by ShowMeGrrl on 2010-09-03
Re: my comment that ntfs formatting happened in a flash, while the ext4 formatting seemed to go much more slowly.

Here was a comment from earlier in this thread (first or second page) from Semiotic Robotic:

> Each time I've formatted my external hard disk as ext4, the formatting process has taken a fairly long time. I'm comparing this interval with my experiences on Mac OS and Windows, where formatting can take under one minute with the FAT32 or HFS+ filesystems.

---

### Post by CharlesA on 2010-09-03
Don't forget with EXT3 and 4, it has to create the journal, which can take a bit of time.

---

### Post by srs5694 on 2010-09-03
The hypothesis that the problem is due to the automounter interfering with the filesystem creation process is plausible, so I'll back off on my suggestion that it's a hardware problem. Using an emergency boot disc to do the filesystem creation should certainly prevent interference, so VastOne's suggestion makes sense.

If you do successfully create a filesystem, I recommend rebooting and copying as large a file as you can to test sustained throughput, just in case there's a hardware problem or some other problem specific to your normal system (a kernel bug, say).

As to the size of an extended partition, it can be as large as desired, up to 2 TiB or the maximum size on the disk. You do have to have at least one free primary partition "slot" in which to create it, though. Of course, if you can create your big filesystem by booting an emergency disc, this is largely moot; you can use two primary partitions, one primary and one extended partition with one contained logical partition, or one extended partition with two contained logical partitions, as you see fit. There are very few advantages or disadvantages to any of these configurations. You could also go back to GPT and be rid of the primary/extended/logical distinction, at least on that drive.

---

### Post by ShowMeGrrl on 2010-09-08
Here is an update on where I stand in trying to format my external Western Digital 1.5TB Elements hard drive. 

As you may recall, my desire is to have one partition formatted as ntfs at about 250GB and a second partition formatted as ext4 that would fill the remainder of the drive -- so about 1.25TB.

I am using a Master Boot Record (MBR) partition scheme because Internet research showed that WindowsXP cannot deal with GUID. (My experience has borne that out: My Windows VM could not access the drive until I changed the partition scheme from GUID to Master Boot Record. Then Windows was able to access it.)

So far I have been able to create ntfs partitions of any size without a problem. But I have been unable to create ext4 partitions larger than about 250GB without my system freezing up. The result is that more than 500GB of my external drive is unformatted and of no use, because MBR allows a maximum of 4 partitions.

In formatting the drive, I have used Ubuntu's Disk Utility, the gparted program, and parted in the terminal. None of them has been successful in creating the large ext4 partition; they have all produced system freezes.

I am new to formatting and partitioning, so I will have to study up on extended vs primary vs logical partitions to see whether I could create a large extended partition to use up the entire drive that way.

Still, the question remains why can I not format the 1.25TB free partition as a regular primary ext4 partition? I should not be having this problem! It's not as if I'm doing something extreme or unusual.

As I reported a couple days ago, my friend turned up a problem some people were having of automount kicking in during formatting, causing the formatting tool to go nuts and
consume 100% of the CPU and freeze the system. That seemed to fit the facts of my situation. Based on that diagnosis, she thought  disabling automount might solve my problem.

We did that this evening. Unfortunately, it did not work. We disabled automount and then used Disk Utility to try to format that remaining 1.25TB free partition as ext4. The system froze.

We then booted up a systemrescuecd into the CD drive and ran the mke2fs command (This is part of the e2fsprogs utililty, which apparently is a bit more modern and capable than parted at formatting drives.). Trying this offered two benefits: one was to try something other than parted to do the formatting and the other was to do the formatting from a liveCD rather than from within the OS. 

Unfortunately, the formatting process came to a halt during writing of inode tables at the 877/9278 point. Thus, it seemed to have the same lack of success as the other prior approaches.

I then ran memtest86+ on my computer for 3 to 4 hours to make sure my RAM is OK. After 3 passes, it showed 0 errors. Complete pass.

Now my friend has taken my Western Digital external drive and will try to format it using her Linux machine. (I'm not sure which version of Ubuntu she is running -- I'll have to find that out.) I will report the results after she has tried that.

Depending on how that turns out, I will try to run the "sudo dd if=/dev/sdb2 of=/dev/null" tests you suggested, srs5694.

---

### Post by srs5694 on 2010-09-08
Sorry to hear you're still having problems. Given your results with System Rescue CD, which AFAIK has no active automounter, it's looking again like a hardware fault to me. You could try another filesystem (XFS, say), but given the issues you've had, I wouldn't really trust that even if you successfully created the filesystem.

As to one other question, MBR is limited to four *primary* partitions. You can have an arbitrary number of *logical* partitions in a single extended partition (which counts as one of the primary partitions). I've put about 20 partitions on an MBR disk in this way with no problems. As with using XFS or some other filesystem, though, I wouldn't trust that disk with multiple partitions, given its flakiness when you try to create a single big filesystem.

---

### Post by ShowMeGrrl on 2010-09-09
OK, here are the results from my friend's attempt to format my Western Digital 1.5TB Elements external hard drive using machines other than mine:

> Test #1. Formatted 1.1TB partition with 64-bit Mac OS via Disk Utility
to HFS+ successfully.

Test #2. Deleted partition, added new partition and formatted to ext4
successfully using 0.5.1 gparted on a 32 bit 10.04 Ubuntu Live CD.
Mounted, created file, opened it, deleted it. Unmounted partition,
deleted it.

Test #3. Added new partition and formatted it to ext4 successfully on
32 bit Ubuntu 9.10, native install, using gparted v. 0.4.5. Mounted
it, copied lots of files to it, opened some of them, deleted them.

>From these results, I conclude that there is nothing wrong with your
external drive. My guess is that the problem is either with the
particular version of gparted and/or its dependent packages. Maybe
it's strictly a 64-bit version problem -- that would explain why I
couldn't google up much in the way of similar bug reports. There might
not be many 64-bit Ubuntu users out there; I noticed that the download
site discourages 64-bit for daily desktop usage.


She is going to partition the drive for me. I hope that I won't have any trouble using it for backup. I previously was able to copy files to both the ntfs and ext4 partitions, though they were small files. I didn't try anything ambitious.

My Wild Dog is a 64-bit machine and it is my main computer, so I can't really avoid "daily desktop usage." Not sure what she was referring to there. So far, this is the only problem I have had that I have been unable to solve. Most of the other problems I've had are just part of my learning curve and I've been able to get past them. (However, I still must run my computer with desktop effects turned off in order to prevent crashes -- some kind of bug with the nvidia driver.)

Thank you all for your help and interest. It certainly helped keep my spirits up! And I learned a lot too!

---

### Post by VastOne on 2010-09-09
> **ShowMeGrrl said:**
> OK, here are the results from my friend's attempt to format my Western Digital 1.5TB Elements external hard drive using machines other than mine:



She is going to partition the drive for me. I hope that I won't have any trouble using it for backup. I previously was able to copy files to both the ntfs and ext4 partitions, though they were small files. I didn't try anything ambitious.

My Wild Dog is a 64-bit machine and it is my main computer, so I can't really avoid "daily desktop usage." Not sure what she was referring to there. So far, this is the only problem I have had that I have been unable to solve. Most of the other problems I've had are just part of my learning curve and I've been able to get past them. (However, I still must run my computer with desktop effects turned off in order to prevent crashes -- some kind of bug with the nvidia driver.)

Thank you all for your help and interest. It certainly helped keep my spirits up! And I learned a lot too!

She was referring to Ubuntu's web site and it's statement on 64 bit which has been debunked every which way from here to Eden.  She also says that there may not be many 64 bit users "out there" which is a false assumption based on that misleading information.

Did you ever try to do anything with this from a Ubuntu Livecd boot?  I was curious about the results of that.

---

### Post by ShowMeGrrl on 2010-09-09
> Did you ever try to do anything with this from a Ubuntu Livecd boot? I was curious about the results of that.

My friend's Test#2 was from a Ubuntu Livecd boot. Also, I tried to partition from a systemrescuecd live CD boot, and that failed.

---

### Post by VastOne on 2010-09-09
> **ShowMeGrrl said:**
> My friend's Test#2 was from a Ubuntu Livecd boot. Also, I tried to partition from a systemrescuecd live CD boot, and that failed.

If you did it with an Ubuntu Livecd and it failed and she did it with the same Livecd then it would suggest that the connection from your to your hard drive would be the issue, either in the port or the cabling.

---

### Post by ShowMeGrrl on 2010-09-09
Well, if I did it from a 32-bit LiveCD and it worked, that wouldn't rule out that the problem was with the 64-bit version of parted, would it?

---

### Post by VastOne on 2010-09-09
> **ShowMeGrrl said:**
> Well, if I did it from a 32-bit LiveCD and it worked, that wouldn't rule out that the problem was with the 64-bit version of parted, would it?

Are you saying you did it with a 32 bit Ubuntu Livecd and it did work?

---

### Post by srs5694 on 2010-09-09
The System Rescue CD is a 32-bit build, so the fact that you got a failure when you used that nixes the idea that it's a 64-bit issue.

The big variable that's left is the hardware, although it's looking more like a hardware failure in the cabling or your computer's USB controller than in the hard drive itself. Have you always plugged the drive into the same USB port on the computer? If so, try another one. Did your friend use the same USB cable you used? If not, the cable could be faulty. If the problem is the USB circuitry on the motherboard, the easiest solution is to install a plug-in USB card to supplement or replace the motherboard's USB circuitry. (This assumes you've got a desktop system with at least one free slot; if it's a laptop or if you don't have any free slots, you'll have a harder time replacing the USB circuitry.)

---

### Post by VastOne on 2010-09-09
> **srs5694 said:**
> The System Rescue CD is a 32-bit build, so the fact that you got a failure when you used that nixes the idea that it's a 64-bit issue.

The big variable that's left is the hardware, although it's looking more like a hardware failure in the cabling or your computer's USB controller than in the hard drive itself. Have you always plugged the drive into the same USB port on the computer? If so, try another one. Did your friend use the same USB cable you used? If not, the cable could be faulty. If the problem is the USB circuitry on the motherboard, the easiest solution is to install a plug-in USB card to supplement or replace the motherboard's USB circuitry. (This assumes you've got a desktop system with at least one free slot; if it's a laptop or if you don't have any free slots, you'll have a harder time replacing the USB circuitry.)

Was just about to reply word for word with what you just said and I could not have said it any better.

Process of elimination is the key to successful troubleshooting.

---

### Post by ShowMeGrrl on 2010-09-09
My friend used the same cable I used. I did try a different USB port and it didn't make a difference. I have lot of USB devices (mouse, keyboard, two printers and a scanner) and none of them is having problems, so I doubt there is a problem with the USB controller.

Could there be a compatibility issue of Western Digital Elements drive and Ubuntu 64-bit?

---

### Post by CharlesA on 2010-09-09
> **ShowMeGrrl said:**
> My friend used the same cable I used. I did try a different USB port and it didn't make a difference. I have lot of USB devices (mouse, keyboard, two printers and a scanner) and none of them is having problems, so I doubt there is a problem with the USB controller.

Could there be a compatibility issue of Western Digital Elements drive and Ubuntu 64-bit?
Shouldn't be a compability problem. It would just see it as a hard drive.

---

### Post by VastOne on 2010-09-09
> **ShowMeGrrl said:**
> My friend used the same cable I used. I did try a different USB port and it didn't make a difference. I have lot of USB devices (mouse, keyboard, two printers and a scanner) and none of them is having problems, so I doubt there is a problem with the USB controller.

Could there be a compatibility issue of Western Digital Elements drive and Ubuntu 64-bit?

Have you seen [_[COLOR="Red"]this thread?[/COLOR]_]("http://ohioloco.ubuntuforums.org/showthread.php?p=9823822")

---

### Post by ShowMeGrrl on 2010-09-10
> Have you seen this thread? [http://ohioloco.ubuntuforums.org/showthread.php?p=9823822](http://ohioloco.ubuntuforums.org/showthread.php?p=9823822)

Yes, I have seen that thread, but it kind of re-states the problem, which is that I could format partitions as ntfs but not as ext4. The question is why can I not format partitions as ext4? Actually, I could format them as ext4 but only smallish partitions of around 250GB or less.

I did find that I could not mount the drives in my Windows VM as long as the partition scheme was GUID. Once I changed the scheme to Master Boot Record (which is MS-DOS), I was able to mount them in Windows. However, I still was not able to format a large partition as ext4.

The ntfs formatting was almost instantaneous. The ext4 formatting was slow and then crashed before completing.

My friend, as I described above, WAS able to do the ext4 formatting on different machines. The question is why was she able to format it and not I on my Linux 10.04 64-bit OS?

---

### Post by VastOne on 2010-09-10
> **ShowMeGrrl said:**
> Yes, I have seen that thread, but it kind of re-states the problem, which is that I could format partitions as ntfs but not as ext4. The question is why can I not format partitions as ext4? Actually, I could format them as ext4 but only smallish partitions of around 250GB or less.

I did find that I could not mount the drives in my Windows VM as long as the partition scheme was GUID. Once I changed the scheme to Master Boot Record (which is MS-DOS), I was able to mount them in Windows. However, I still was not able to format a large partition as ext4.

The ntfs formatting was almost instantaneous. The ext4 formatting was slow and then crashed before completing.

My friend, as I described above, WAS able to do the ext4 formatting on different machines. The question is why was she able to format it and not I on my Linux 10.04 64-bit OS?

Somewhere in the hardware of the machine lies the issue, IMHO. If you have already systemically eliminated every variable (cable, slots, bios state, bios update, particles of dust, etc etc) then I would suggest a bug report detailing the issue with a 64 bit and this drive. But before that I would really really try to find someone with the same drive and using Ubuntu and on 64 that is having the same problem you are having.  I cannot see you being on a little island all by yourself as this is a popular drive and Ubuntu 64 is a popular distro.

---

### Post by ShowMeGrrl on 2010-09-10
> Somewhere in the hardware of the machine lies the issue, IMHO. If you have already systemically eliminated every variable (cable, slots, bios state, bios update, particles of dust, etc etc) then I would suggest a bug report detailing the issue with a 64 bit and this drive. But before that I would really really try to find someone with the same drive and using Ubuntu and on 64 that is having the same problem you are having. I cannot see you being on a little island all by yourself as this is a popular drive and Ubuntu 64 is a popular distro.

I'm too much of a newbie to want to mess around with my BIOS or the innards of my computer, at this stage. It must be something about my machine (which is new), but I don't know what. If I learn anything more as I go along, I will update here.

---

### Post by PabloH on 2010-09-10
If you still want to find out what is going on, I would bypass this whole formatting thing and write directly to the disk using dd as previously recommended on page 4. 

This will generate lots of IO-- which is what the ext4 formatting utility is doing when the computer hangs. This will show if the hang is caused by a hardware issue triggered by heavy prolonged IO (which I suspect it is) or if there is something fishy going on with the disk partitioning and formatting utilities (not so likely).

Of course, this will destroy all data on the disk.

something like: dd if=/dev/null of=/dev/sdb

Where sdb is the usb disk and not a hard drive you have data on that you care about. You could substitute sdbX where X is number of the big partition containing ext4. After you are done, you will have to re-partition whatever you dd'ed. If your computer locks up doing this, then it is most certainly not the partitioning tools, but some hardware issue triggered by heavy I/O to this disk.

---

### Post by CharlesA on 2010-09-10
> **PabloH said:**
> If you still want to find out what is going on, I would bypass this whole formatting thing and write directly to the disk using dd as previously recommended on page 4. 

This will generate lots of IO-- which is what the ext4 formatting utility is doing when the computer hangs. This will show if the hang is caused by a hardware issue triggered by heavy prolonged IO (which I suspect it is) or if there is something fishy going on with the disk partitioning and formatting utilities (not so likely).

Of course, this will destroy all data on the disk.

something like: dd if=/dev/null of=/dev/sdb

Where sdb is the usb disk and not a hard drive you have data on that you care about. You could substitute sdbX where X is number of the big partition containing ext4. After you are done, you will have to re-partition whatever you dd'ed. If your computer locks up doing this, then it is most certainly not the partitioning tools, but some hardware issue triggered by heavy I/O to this disk.

This would be a good test, that's for sure. At the very least, it would stress test the machine.

I'd also suggest running memtest86+ on the machine.

---

### Post by srs5694 on 2010-09-10
> **ShowMeGrrl said:**
> My friend used the same cable I used. I did try a different USB port and it didn't make a difference. I have lot of USB devices (mouse, keyboard, two printers and a scanner) and none of them is having problems, so I doubt there is a problem with the USB controller.

Could there be a compatibility issue of Western Digital Elements drive and Ubuntu 64-bit?

It is *not* a 64-bit issue specifically; the fact that you couldn't create an ext4 filesystem on the 32-bit SystemRescueCd (as described in [post #49 in this thread](http://ubuntuforums.org/showpost.php?p=9819891&postcount=49)) proves this. Unless you've got some reason to think that the failure under SystemRescueCd was fundamentally different from the failure under your normal Ubuntu install, chasing the 64-bit bug hypothesis at this point is a waste of time.

It could be a USB hardware or low-level driver issue, despite the fact that you've got other USB devices that work. This is because the problem turns up when creating an ext4 filesystem, which involves a lot of I/O. Keyboards and mice produce tiny amounts of I/O by comparison. Printers and scanners produce more, but probably not as much as creating a big ext4 filesystem. Some hardware and driver faults only turn up when they're put under heavy load, so it's entirely plausible that the hardware or driver is flaking out on you. As I suggested earlier, and as PabloH also suggested, using dd to read and/or write large amounts of data to the drive could test this hypothesis. (It's conceivable that a flaw would only turn up with interleaved reads and writes, though, which the suggested dd test won't do.)

It could also be that the problem is one of an interaction of the USB interface on the hard disk with the USB controller in the computer. They're both supposed to follow the USB specification, but if one deviates just a little bit, you could be getting problems that manifest as the failures you're seeing. I've seen this sort of device-to-device incompatibility many times in the past, although not this *specific* pattern. The closest might be an adapter to connect a PATA disk to a computer's USB port, which produces random disconnects on one of my computers, but works fine on others. (Come to think of it, though, if I were to try massive I/O on that disk, it's conceivable that the random disconnect would freeze the system, as you're seeing.)

Another thought that occurs to me is that it might be a power supply issue. Does the drive have an AC adapter "brick?" I've heard that some such devices can be sensitive to very minor fluctuations in the power coming through the wall socket, which can result in momentary USB disconnects. If this is the case, it might have affected you but not your friend because the tests were done in different locations; your power might be a little less stable than your friend's power. If this is the problem, connecting the drive's power brick to a power stabilizer or UPS might improve matters. OTOH, such power fluctuations are likely to be random, and it sounds like your failures are very predictable, so I think this hypothesis is rather unlikely, although not entirely impossible.

My suggestion to you is to do one of two things:


[list=1]
[*]Buy a plug-in USB controller for your computer and connect the hard disk to it rather than to the computer's standard USB port. There's a good chance that this will solve the problem, whether it's a bad USB controller or a controller/disk incompatibility. If the board you buy happens to use the same model controller as the old one, though, the problem might persist.
[*]Return the disk to the store and buy a new one from a different manufacturer. This will only fix the problem if the root cause is hardware-to-hardware incompatibility; if your computer's USB controller is buggy, you'll need to bypass it, as in suggestion #1.
[/list]


Of course, it won't hurt to do tests with dd. If dd doesn't fail or crash the system, then that's rather puzzling, since the range of hypotheses would be pretty narrow and weird -- namely, specific *patterns* of I/O would be triggering the problem, rather than just massive *amounts* of I/O; or it could be a power line issue, as just outlined.

One other test you can try is this: At a shell prompt, type "dmesg" and note the last messages, then plug in the drive, wait about 15 seconds, and type "dmesg" again. You'll see new messages related to the insertion of the drive. For instance, here's what I get when I connect a USB flash drive to one of my systems:

```

[3845923.667043] usb 2-4: new high speed USB device using ehci_hcd and address 5
[3845923.784340] usb 2-4: configuration #1 chosen from 1 choice
[3845923.784747] scsi9 : SCSI emulation for USB Mass Storage devices
[3845923.784969] usb-storage: device found at 5
[3845923.784972] usb-storage: waiting for device to settle before scanning
[3845928.784751] scsi 9:0:0:0: Direct-Access              USB_DRIVE        1.00 PQ: 0 ANSI: 2
[3845928.784930] sd 9:0:0:0: Attached scsi generic sg3 type 0
[3845928.785291] usb-storage: device scan complete
[3845928.787230] sd 9:0:0:0: [sdc] 31576064 512-byte logical blocks: (16.1 GB/15.0 GiB)
[3845928.787725] sd 9:0:0:0: [sdc] Write Protect is off
[3845928.787727] sd 9:0:0:0: [sdc] Mode Sense: 23 00 00 00
[3845928.787729] sd 9:0:0:0: [sdc] Assuming drive cache: write through
[3845928.791601] sd 9:0:0:0: [sdc] Assuming drive cache: write through
[3845928.791605]  sdc: sdc1 sdc2
[3845930.878566] sd 9:0:0:0: [sdc] Assuming drive cache: write through
[3845930.878569] sd 9:0:0:0: [sdc] Attached SCSI removable disk

```

Now wait a while longer -- maybe a few minutes -- and type "dmesg" again. If you see more messages relating to that drive, post them here. It could be that the drive is disappearing from the USB subsystem or is otherwise misbehaving, and the dmesg output may provide clues about what's going on.

---

### Post by ShowMeGrrl on 2010-09-10
Status report. I did a big copy (3 folders totaling about 68GB) to the big ext4 partition on the Western Digital Elements external hard drive. The copy proceeded normally. 

> One other test you can try is this: At a shell prompt, type "dmesg" and note the last messages, then plug in the drive, wait about 15 seconds, and type "dmesg" again. You'll see new messages related to the insertion of the drive. For instance, here's what I get when I connect a USB flash drive to one of my systems: . . .Now wait a while longer -- maybe a few minutes -- and type "dmesg" again. If you see more messages relating to that drive, post them here. It could be that the drive is disappearing from the USB subsystem or is otherwise misbehaving, and the dmesg output may provide clues about what's going on.

OK, I ran this test. Here is the output after I plugged the drive in. (There was no change in the message after I waited a few minutes after that.):

> [29807.035007] usb 1-1.3: new high speed USB device using ehci_hcd and address 5
[29807.157029] usb 1-1.3: configuration #1 chosen from 1 choice
[29807.207197] Initializing USB Mass Storage driver...
[29807.207396] scsi6 : SCSI emulation for USB Mass Storage devices
[29807.207591] usb-storage: device found at 5
[29807.207594] usb-storage: waiting for device to settle before scanning
[29807.207606] usbcore: registered new interface driver usb-storage
[29807.207658] USB Mass Storage support registered.
[29812.194321] usb-storage: device scan complete
[29812.195284] scsi 6:0:0:0: Direct-Access     WD       Ext HDD 1021     2002 PQ: 0 ANSI: 4
[29812.195899] sd 6:0:0:0: Attached scsi generic sg2 type 0
[29812.196866] sd 6:0:0:0: [sdb] 2930272256 512-byte logical blocks: (1.50 TB/1.36 TiB)
[29812.197823] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[29812.197828] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[29812.199561] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[29812.199566] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[29812.199571]  sdb: sdb1 sdb2
[29812.258820] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[29812.258825] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[29812.258830] sd 6:0:0:0: [sdb] Attached SCSI disk
[29812.763246] EXT4-fs (sdb2): mounted filesystem with ordered data mode

Now I'm going to try reformatting the Western Digital external hard drive off a 32-bit Ubuntu Lucid LiveCD. I will let you know how that works.

After that I will try the dd tests and let you know how they go.

It is tempting to say the external hard disk is working now that my friend has formatted it, so I'm just going to move ahead and start using it for backup. However, I do want to get to the bottom of this and find out what is causing the problem. Thus, I will delay moving ahead and try to do the suggested diagnostics (as long as I don't need to mess with the BIOS or go into the innards of my machine!).

---

### Post by ShowMeGrrl on 2010-09-11
Well, I'm happy to report an interesting development: success!

I booted off the Ubuntu 10.04 32-bit LiveCD on my Wild Dog. I then used the Disk Utility to format my Western Digital Elements external disk. I used a Master Boot Record scheme. I created one ntfs partition of ~250GB and a second ext4 partition of ~1.2TB.

The formatting went smoothly. No problems. 

I had to do some fumbling around afterwards to change the permissions on that drive. Strangely, I was shown as owner of the ntfs partition, while '999' (whoever that is) was shown as owner of the ext4 partition.

At any rate, I then tested out the two partitions, first making surse that I could see the two partitions in Linux and see the ntfs partition in my Windows VM. I then did a Grsync backup to ntfs from within Windows and to the ext4 from within Linux. 

Everything worked.

Sooooo, does this suggest that the 64-bit OS is the issue?

By the way, the Disk Utility gives various info about the Western Digital Elements external drive. One piece of info it gave was that the firmware dates to 2002. I suppose that might be a factor in compatibility with more modern systems?

---

### Post by srs5694 on 2010-09-11
I suspect the firmware date is in error. In 2002, disk hardware was so different from what it is today that I can't imagine firmware written in 2002 being useful today.

The fact that you were able to create the filesystem using a 32-bit Ubuntu disc is odd, given that the 32-bit System Rescue CD disc you tried earlier failed. If your initial failures are due to an obscure (*very* obscure, given that 64-bit installations are quite common) 64-bit bug, you'd still have to explain that System Rescue CD failure. Occam's Razor says the two failures are likely to have the same cause. Thus, at the moment, I suspect an intermittent hardware fault -- perhaps a weak connection on the USB port. You could test this by trying to format it again with your 64-bit installation, without touching the disk hardware. Whether you want to go to this effort is of course up to you.

---

### Post by ShowMeGrrl on 2010-09-11
> **srs5694 said:**
> I suspect the firmware date is in error. In 2002, disk hardware was so different from what it is today that I can't imagine firmware written in 2002 being useful today.

The fact that you were able to create the filesystem using a 32-bit Ubuntu disc is odd, given that the 32-bit System Rescue CD disc you tried earlier failed. If your initial failures are due to an obscure (*very* obscure, given that 64-bit installations are quite common) 64-bit bug, you'd still have to explain that System Rescue CD failure. Occam's Razor says the two failures are likely to have the same cause. Thus, at the moment, I suspect an intermittent hardware fault -- perhaps a weak connection on the USB port. You could test this by trying to format it again with your 64-bit installation, without touching the disk hardware. Whether you want to go to this effort is of course up to you.
The Disk Utility says "Firmware Version: 2002" so maybe it's kind of a base of 2002 but it's been tweaked since then.

The failure that I had on the System Rescue CD may have been slightly different. The failure that I always got when trying to format from within my desktop 64-bit OS was a system freeze -- no mouse or keyboard input. Hard reboot required. With the System Rescue Disk, the formatting operation stopped after a while. The cursor was still blinking and my friend just declared that it seemed not to be working, so we powered down.

I will try to reformat as you propose later today.

---

### Post by ShowMeGrrl on 2010-09-12
> vThe fact that you were able to create the filesystem using a 32-bit Ubuntu disc is odd, given that the 32-bit System Rescue CD disc you tried earlier failed. If your initial failures are due to an obscure (very obscure, given that 64-bit installations are quite common) 64-bit bug, you'd still have to explain that System Rescue CD failure. Occam's Razor says the two failures are likely to have the same cause. Thus, at the moment, I suspect an intermittent hardware fault -- perhaps a weak connection on the USB port. You could test this by trying to format it again with your 64-bit installation, without touching the disk hardware. Whether you want to go to this effort is of course up to you.

Well, srs5694, I thought you were being a little stubborn in declining to accept the OS theory, but you are right on the money. I did as you suggested and tried to format the external drive again with my 64-bit installation, without touching the disk hardware. Guess what? It worked! 

It formatted beautifully and everything is working as it is supposed to.

I am at a loss. I am also hopeful that nobody will suggest any more tests!

It must be, as you suggested, "a weak connection on the USB port."

Thanks for all the collaboration and help! I learned a lot and everything seems to be working properly. (I don't think I'll be unplugging the drive -- for a while at least.)

---

### Post by srs5694 on 2010-09-12
That weak connection is troublesome. The difficulty is that there are several possible causes, including a weak trace on the motherboard, a bad cable, or bad connections in the drive itself. Does the drive have a completely removable cable, or is it permanently attached on the drive end? If it's removable, you might consider swapping in a new cable at the earliest possible time, in case it's just a bad cable. I'd like to suggest again, however, that you return the drive -- but I'll modify my earlier suggestion to say that it should be OK to replace it with the same make and model drive. Replacing the drive in this way will fix two of the three possible problem sources, and at little or no cost to you, assuming the drive is within the return period from the retailer. If you have problems with the replacement drive, then you'll know something's wonky with your computer's USB subsystem, and you can supplement that with a plug-in card. (Such adapters are pretty inexpensive; see [this search at NewEgg,](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&DEPA=0&Order=BESTMATCH&Description=pci+usb+card&x=0&y=0) for instance -- most are priced between $8 and $20.)

---

### Post by ShowMeGrrl on 2010-09-12
Status report. Overnight I did a complete backup of my Home folder, including all the hidden files, to the Western Digital Elements external drive, using the free, open-source Grsync backup software. About 72GB. It worked beautifully. 

I love the Grsync program. It does exactly what I want it to do and is dead simple to use. You have the option to encrypt the files but I did not choose to do so. I can access the files on my external drive the same way I access them on my main machine. In other words, the backup is not encased in some weird form or code that requires me to "restore" it using a special program. Grsync simply copies it onto the external hard drive. You are given the choice of retaining permissions, ownership, etc. of the files.

When you make a change to a file or folder and then do your next Grsync backup, it copies only the changes, so you don't have to repeat full backups. It's very efficient. 

And, by the way, there is a Grsync version for Windows, so I am also able to use the program within my Windows VM. It seems to work the same as the Linux version. They both work very well from what I can tell.

srs5694, I'm inclined to live with the USB issue for now. I'm just too tired to want to continue to hassle with it, to go to the trouble to mail back the drive and possibly fight with the retailer, to postpone my backup and thus the transition to my new machine. Even worse, to get a replacement drive that has all the same problems -- maybe even different problems -- all over again. It gives me a bad headache even to think of it. My drive and backup are working splendidly. I want to move forward. I accept that I may run into some USB problem later. Fine. At least it's later! ;-) 

BTW, the drive has a completely removable cable. I did notice that its connection at the drive end is a little loose.

From the look of those plug-in cards, I'd have to open up the machine and install them myself. The idea of opening up my computer is alarming to me.

---

### Post by stillnotcool on 2010-09-14
> **ShowMeGrrl said:**
> I love the Grsync program. It does exactly what I want it to do and is dead simple to use. You have the option to encrypt the files but I did not choose to do so. I can access the files on my external drive the same way I access them on my main machine. In other words, the backup is not encased in some weird form or code that requires me to "restore" it using a special program. Grsync simply copies it onto the external hard drive. You are given the choice of retaining permissions, ownership, etc. of the files.

Isn't it the best?  You've precisely identified one of the primary reasons this is the only backup software I will use: no crazy formats, containers, or lock-ins.  Glad the suggestion worked for you.  Best of luck -- and sleep soundly knowing your data is secure!

---

### Post by VastOne on 2010-09-14
> **SemioticRobotic said:**
> Isn't it the best?  You've precisely identified one of the primary reasons this is the only backup software I will use: no crazy formats, containers, or lock-ins.  Glad the suggestion worked for you.  Best of luck -- and sleep soundly knowing your data is secure!

It is one of the very best.  I work with a lot of ppl on backup and disaster recovery process, and using grsync is a critical piece of the puzzle.  It makes rsync livable and the incremental copies keeps my data safe and secure in a short period of time.

---

### Post by Eyore15 on 2010-09-16
> **brokenromeo said:**
> I use Ubuntu One to sync my important files and documents, and I use Clonezilla and an external USB drive to make an image of my harddrive once a month or so, that way if something happens I can restore my whole system from the image file...I have a dual boot system, so that makes it very easy to restore both OS's and all applications and documents I had to the point of taking the image...

I didn't find clonezilla in the repositories; is there another imaging program that anyone can recommend that IS housed in the repositories?

---

### Post by PabloH on 2010-09-17
> **Eyore15 said:**
> I didn't find clonezilla in the repositories; is there another imaging program that anyone can recommend that IS housed in the repositories?

gddrescue and good old dd work ;)

---

### Post by Eldera on 2010-09-17
[quote=eyore15]I didn't find clonezilla in the repositories;[/quote]

For more on clonezilla here is a link

[http://www.clonezilla.org/](http://www.clonezilla.org/)

One downloads an iso image, burns a live CD, and uses clonezilla while booted from the CD.

---

