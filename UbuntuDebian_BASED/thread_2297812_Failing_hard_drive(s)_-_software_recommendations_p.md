---
title: "Failing hard drive(s) - software recommendations please"
date: 2015-10-06
forum: Ubuntu/Debian BASED
---

### Post by Archaeology_Student on 2015-10-06
Hi,

I have a hardware issue, and I hope that someone has the time to either offer help or point me in the right direction. 

I have four hard drives that are currently unable to mount and have failed or are failing (various noises upon powering on). 

I am using Elementary OS (which is based on ubuntu), and have read a few linux how-to tutorials on using fsck and attempted to use that command, and some other commands (e2fsck, mounting good boot sectors, etc.), as well as gparted, but I can't mount the drives :(

The drives were in a NASLite-M2 server (Tyan S2882-D Pro - 2 x 246 AMD Opteron CPUs, 12 GB ECC memory, etc.), and NASlite uses the EXT2 file system. NASLite offers the ability to fix the filesystem(s) for each drive, but the drives will no longer mount :( 

The failing drives are:

1) WD 120 GB EIDE
2) WD 500 GB EIDE
3) WD 500 GB EIDE (identical model as above)
4) Seagate 2 TB Green SATA drive

I have been looking at **two programs in linux called 'TestDisk' and 'GNU ddrescue'** as my last options to attempt to recover the data off of the hard drives. The hard drives contain a tonne of family photos, old family photo high res scans, and videos. 

Is there anything else I can try to attempt to recover? Would it matter if I were to use a ubuntu live CD vs a Knoppix, vs my install of Elementary OS?

I realize this is a lot of information, but I appreciate any and all feedback. Thank you!

---

### Post by matt_symes on 2015-10-06
OHi

Personally I would take the drives out the NAS and put them into another PC.

I would use ddrescue to image each entire drive, mount the partition in each image and attempt recovery on the image.

This is risky though because if the drive fails while ddrescue is running then you're looking at profession rescue service.

Look in dmesg and/or syslog and see what that makes of the drives.

You can use any Linux for this so use what you are most comfortable with.

Another option is spinwrite (spinright ? I forget the spelling) by Steve Gibson. Paid for software but has a good reputation. That was not an endorsement my me though.

See what others suggest and please make backups in future.

Kind regards

---

### Post by Archaeology_Student on 2015-10-06
Hi Matt, 

Thank you for the reply! I have removed the drives and have them hooked up with an external docking solution that allow both SATA and EIDE drives to be hooked up to my MacBook. I'm using VMware to run Elementary OS where I am working on fixing things. 

I will definitely run with the GNU ddrescue at this point and I will report back :)

Again, thank you for taking the time to reply.

---

### Post by weatherman2 on 2015-10-06
I would cut out the middleman and just boot Ubuntu on your Macbook - don't bother with the hassles the VMware step adds.  You can boot Ubuntu from a USB stick, assuming your Macbook is new enough.  I am not a Mac person but have booted Ubuntu successfully on 2010-era Macbooks quite easily.

First, I would assess each drive's S.M.A.R.T. health to try to figure out what state it is in.  Try GSmartControl to check S.M.A.R.T. status - though if you boot a live USB of Ubuntu, you will then need to install GSmartControl (enable the "universe" repository).

You may also need to add options to the smartctl command to access an external dock.  (There is a place to add this in GSmartControl, a graphical interface to smartctl.)  Try the options "-d sat" and "-T permissive"  (without the quotes).

If you can read the S.M.A.R.T. status at all, then the drive's control is alive.  If not, the controller may be dead so not even worth trying to access the drive.

If you read S.M.A.R.T. and it shows no errors, maybe there is no hardware problem with the drive.  if these are Windows(?) drives, you may need to run chkdsk from a Windows disc.  Don't bother with fsck unless these are actual Linux-formatted hard drives.

Or it may be as easy as mounting the partitions and copying the data to another drive.

If you see S.M.A.R.T. attributes like Pending Sectors > 0 (more than a few anyway) then I would try ddrescue, too.

---

### Post by Archaeology_Student on 2015-10-09
So far the only thing that has been working is GNU ddrescue. I am currently backing up one hard drive to a secondary hard drive (this one is a little bigger). 

I am using the 120 GB (dev/sdb) as the first test of the bad hard drives with ddrescue as the input, and a newer 160 GB (dev/sdc) hard drive as the output drive. 

So far I understand all of the commands except for one thing that has me scratching my head. Perhaps someone can clarify. 

One option is to use a command to duplicate the hard drive from to the other, and another option is to create a disk image file. Please see simplified examples below:

Duplicate hard drive command: sudo ddrescue /dev/sdb /dev/sdc rescue.log

Create disk image command: sudo ddrescue /dev/sdb /dev/sdc/backup.image

Can someone explain why one would create an image versus an almost identical backup? What are the pros and cons to each method of the two mentioned (i.e., duplicate hard drive and create a disk image)?

Thank you.

---

### Post by weatherman2 on 2015-10-09
> **Archaeology_Student said:**
> So far I understand all of the commands except for one thing that has me scratching my head. Perhaps someone can clarify. 

One option is to use a command to duplicate the hard drive from to the other, and another option is to create a disk image file. Please see simplified examples below:

Duplicate hard drive command: sudo ddrescue /dev/sdb /dev/sdc rescue.log

Create disk image command: sudo ddrescue /dev/sdb /dev/sdc/backup.image

Can someone explain why one would create an image versus an almost identical backup? What are the pros and cons to each method of the two mentioned (i.e., duplicate hard drive and create a disk image)?

Thank you.

Do you have four spare disks?  If so, you could make ddrescue duplicates of each hard drive.

Or, if you have say a 1TB hard drive, you could make four images, all saved on this single 1TB hard drive, plus use the 1TB drive for other things if there is room left over on the 1TB.  But if you "duplicate" your failing drive (instead of making an image), you must devote the entire drive to the duplicate.

Once you make an image, you can restore it to any device you want, work with it, recover data, then restore a second image and work with it, etc.  Or, you may be able to mount the ddrescue images directly without even duplicating them to a device.

---

### Post by Archaeology_Student on 2015-10-09
Thank you for the reply Weatherman2,

So far out of the 120 GB I have rescued 120,034 MB (120 GB) and an errsize (error size) of 32,768 Bytes with 8 errors. 

my next task is to run the following commands

e2fsck -v -f /dev/sdc 

(**or could I get away with gparted instead of e2fsck?**)

mount -t ext2 -o ro /dev/sdc /mnt

I'm really hoping this works... I just do not want to see the errors I was getting before when trying to mount (mind you, that was with the original damaged hard drive).

---

### Post by Archaeology_Student on 2015-10-09
I should also add, that the other three failing hard drives are:

1) 500 GB
2) 500 GB
3) 1 TB

I'll perhaps make images of the remaining three and transfer them to my NASLite-M2 box as I have a 3 TB hard drive in there with 2 TB to spare!

---

### Post by Archaeology_Student on 2015-10-09
Well, I got it to finally work... took a few different commands, but in the end, what worked for the 120GB drive backup was the following...

I counldn't get the drive to mount or use e2fsck, as it kept giving me errors. 

I used the program called 'Testdisk'. I followed the simple instructions and alayzed the disk, and then because this was a ext2 system, I went to advanced in the Testdisk program and went to the MBR menu option. It told me to run the following command based on the MBR analysis:

fsck.ext2 -p -b 20480000 -B 4096 (device)

I ran that command, and was then prompted to use 'fsck' manually without -a or -p. I followed that and ran the same command without the -p and after about 20 minutes it corrected the drive and mounted it for me.

This has been a long three days for me, so I am glad I have had a trial by fire, and can now run through this again to refine and hone my hard drive rescuing skills *lol*

---

### Post by weatherman2 on 2015-10-09
I think the fact that you haven't done any S.M.A.R.T. analysis (?) to check the actual state of your drives is a bit risky.  If a drive is starting to fail, running fsck on it is not a great idea - better to make an image first with ddrescue.  A failing drive can get worse the longer you use it and make recovering data even harder.  But if the drive isn't really failing, feel free to run fsck and other utilities to your heart's content.

---

### Post by Archaeology_Student on 2015-10-11
> **weatherman2 said:**
> I think the fact that you haven't done any S.M.A.R.T. analysis (?) to check the actual state of your drives is a bit risky.  If a drive is starting to fail, running fsck on it is not a great idea - better to make an image first with ddrescue.  A failing drive can get worse the longer you use it and make recovering data even harder.  But if the drive isn't really failing, feel free to run fsck and other utilities to your heart's content.

Hi Weatherman2, 

I ran 'fsck' on the newer cloned drive as per 'testdisk' instructions after an analyis, not the original failing hard drive. 

With the remaining 500 GB, 500 GB, and 1 TB hard drives, I will be making images, not cloning the disk ;)

The original failing hard drives do not seem to want to mount under any OS, and they make some horrbile clicking noises where as they were quiet before they became unreadable/unmountable. On a side note, the 120GB failing drive was almost 16 years old!

Again, thank you for your help and input :)

---

### Post by coffeecat on 2015-10-13
> **Archaeology_Student said:**
> I am using Elementary OS

*Thread moved to **Ubuntu/Debian BASED**.*

---

