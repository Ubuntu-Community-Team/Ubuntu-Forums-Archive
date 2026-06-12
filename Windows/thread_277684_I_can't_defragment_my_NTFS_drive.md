---
title: "I can't defragment my NTFS drive"
date: 2006-10-15
forum: Windows
---

### Post by CSMatt on 2006-10-15
I can't seem to be ale to defragment my NTFS partition with Windows Disk Defragmenter.  When I try, it sticks at 1%, even after an hour of waiting.  I had resized the partition using GParted earlier, but did not defragment it prior to resizing mainly both because I found out that this was recommended after I had resized the partition and because I resized the partition just after setting up the computer for the first time on Windows XP and I assumed that the drive was defragmented by the OEM before shipment.  I think this might be a consequence of me not defragmenting the partition prior to resizing it.  If it is, is there any way I can fix it without reformatting?  If a reformat is necessary, can I use a disk cloning program to back up and them restore the files on the partition?

Also, the partition is about 80 GB, so is it possible that I just haven't waited long enough?

---

### Post by Polygon on 2006-10-15
you might want to ask this on a windows forum as most of the people here use ubuntu and therefore dont need to defragment their drives ^^

anyway, the defragment should not take that long. When i defrag mine, it takes like 3 minutes to get going and then it starts showind a progress bar on the bottom of the window showing what its moving around and stuff

do you have at least 15% free on the drive before you defragment? I think it will yell at you if you dont, but make sure

and if that doesnt help... maybe the resizing screwed soemthing up...

---

### Post by Littleweseth on 2006-10-15
When you resized the NTFS partition, windows probably really didn't like it - i'm not sure, but gparted might not be that good at resizing NTFS partitions.

Expecially since it's a new install, defrag should take < 5 minutes.

---

### Post by mozetti on 2006-10-15
CSMatt,

Every computer is different, and I think Littleweseth is pulling that "<5 minutes" comment out of thin air. Every computer is different, and using gparted for the re-size may have made things a little funky.

The Windows Defrag tool will tell you if something is wrong (most times, at least), so I'd just start it up and let it run while you're doing something off the computer for awhile.

Also, make sure you have all your programs closed, and close as many programs running in the system tray (by the clock) as you can.

---

### Post by CSMatt on 2006-10-15
I always run Windows Disk Defragmenter in Safe Mode, so I don't think it's an outside process.

Are there any good free NTFS error checkers out there?  I tried using CHKDSK, but it evidentially did not detect anything wrong.

---

### Post by PriceChild on 2006-10-15
*Moves to Other OS talk*

---

### Post by CSMatt on 2006-10-16
Well, I just tried defragmenting again and it seems that all is well.  I think it turns out that the process is so slow that it is negligable in one hour alone.  I started defragmenting at about 4:00 PM EDT today.  When I left my computer the process was at 15%, I assume it is at 18% now and will finish at about noon tomorrow.

Whoever said that defragmentation takes 5 minutes must have a very small hard drive.  I'm just grateful that Extended 3 is journalized.

---

### Post by Reshin on 2006-10-18
Also, windows's own defragmenter **sucks**. I'm using O&O Defrag Trial and I'm loving it. Too bad it's commercial...

---

### Post by ShadowVlican on 2006-10-19
> **CSMatt said:**
> Well, I just tried defragmenting again and it seems that all is well.  I think it turns out that the process is so slow that it is negligable in one hour alone.  I started defragmenting at about 4:00 PM EDT today.  When I left my computer the process was at 15%, I assume it is at 18% now and will finish at about noon tomorrow.

Whoever said that defragmentation takes 5 minutes must have a very small hard drive.  I'm just grateful that Extended 3 is journalized.
unless your drive was HEAVILY fragmented, it DOES take 5 minutes :twisted: (well not literally, but NOWHERE near as slow as your experience)

i defrag every week, so only takes around 5 minutes for my 1.2TB RAID5 volume

---

### Post by RJARRRPCGP on 2006-11-28
> **Littleweseth said:**
> When you resized the NTFS partition, windows probably really didn't like it - i'm not sure, but gparted might not be that good at resizing NTFS partitions.

Expecially since it's a new install, defrag should take < 5 minutes.

If Windows gets furious, that means the HDD is corrupted!

Because I can resize partitions just fine with Partition Magic 8.0.

It's likely that the HDD has bad sectors.

Please check the event log!

---

### Post by rosegarden78 on 2008-03-24
> **CSMatt said:**
> I can't seem to be ale to defragment my NTFS partition with Windows Disk Defragmenter.  When I try, it sticks at 1%, even after an hour of waiting.  I had resized the partition using GParted earlier, but did not defragment it prior to resizing mainly both because I found out that this was recommended after I had resized the partition and because I resized the partition just after setting up the computer for the first time on Windows XP and I assumed that the drive was defragmented by the OEM before shipment.  I think this might be a consequence of me not defragmenting the partition prior to resizing it.  If it is, is there any way I can fix it without reformatting?  If a reformat is necessary, can I use a disk cloning program to back up and them restore the files on the partition?

Also, the partition is about 80 GB, so is it possible that I just haven't waited long enough?

If you only use Windows on your internal HDD try this link:
[http://www.fs-driver.org/](http://www.fs-driver.org/)
This will extend your OS to include the ext2 and ext3 file system.  Anyway...

NOTE: You cannot defragment Linux/EXT filesystems with Windows software.

I use Ubuntu Studio as my host and VirtualBox standard edition to run Windows XP.  I have a 160GB SimpleTech USB drive.  I formatted it with gparted, cfdisk and mkdosfs.  I enabled USB support from the article here.  Windows would not recognize my NTFS/FAT32 drive from Linux.
[http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html](http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html)

Defragging the internal static file system or fstab is beyond the scope of this article, but requires that you boot Ubuntu with VirtualBox and XP directly off USB disk.  The internal disk cannot be mounted if you want to change it.  If Windows is installed to internal disk then it will defrag itself.  If you boot off USB you need to find out how to make the drive visible inside VirtualBox.  XP Home is programmed to deny installation to USB while Microsoft publishes a USB version to well-qualified customers.  The only way to use XP is with Ubuntu USB running VirtualBox.

NOTE: Copying boot sector also copies disk size - only reliable way is to let Windows CD partition for you.
Attempt to connect the USB drives to VirtualBox.  Sometimes you need to try three times. If you have a valid disk backup all data to it from the faulty disk.  You can then use the valid disk to copy the boot sector.  The command is "dd if=/dev/sdb of=/dev/sdc bs=512 count=1" when you are certain SDB is a valid disk and SDC is faulty.

To determine which device is which, use these commands:
"ls /dev/sd*" - SDA is usually filesystem, so SDB would be first usb disk, SDC would be second device, etc.  when in doubt reboot with all devices unplugged.  Then plug in the first device and check "ls /dev/sd*" followed by the second device.  

Then use this command to double-check the device letters.
"nano /etc/mtab"

IF YOU HAVE ANY DOUBT ABOUT WHICH DRIVE LETTER TO USE - STOP IMMEDIATELY !
For more information about DOS USB Bootable Drive see this article:
[http://www.aselabs.com/articles.php?id=243](http://www.aselabs.com/articles.php?id=243)

The drive must have a Windows-formatted boot sector. You don't have any Windows-compatible disks lying around.  All you have is your Windows CD.  Now you have to format external HDD from USB.  Otherwise the disk will not show up in VirtualBox.  Set your computer to boot from USB.  Insert Windows CD and use partitioner to delete all then create a new partition.

But what if Windows STILL won't put a boot sector or MBR from the CD?  That's because installation refuses to touch an existing boot sector.  It will only create a partition in this case.  First, you need to do a low level format of your device.  

"sudo dd if=/dev/zero of=/dev/sdb bs=512 count=1" (1 block)
"sudo dd if=/dev/zero of=/dev/sdb bs=512 count=8" (8 blocks)
"sudo dd if=/dev/zero of=dev/sdb bs=512" (whole device)

This is because "gparted" or "cfdisk" does not create an MS-compatible boot sector.  Hence Windows cannot detect the device when you plug in.  If the first command doesn't work try the second and finally the third.  At some point XP installation will create partition but say it cannot install to location.  That's OK.  You zeroed out your device and XP installed a compatible boot sector and/or MBR.

Once your device is connected to VirtualBox you can use defrag.  Make sure you let Windows format the disk in NTFS and give it a nice label.  There used to be a program available called dklite7.exe or Diskeeper Lite from the company that made defrag for Windows but I think it's trial version now.  

If you have Studio Box off-line might stick with Windows only version, because dklite.exe installs a Windows Service which will interrupt audio recording.  Whatever you do keep "Shell Hardware Detection" service running or Windows will de-activate your installation.  You can access the list by typing "msconfig" from Start Menu Run.  Here is the list of services required to keep the virtual machine alive as a studio box: 

Windows Audio
COM+ System Application
DCOM Server Process Launcher
IMAPI CD-Burning COM Service
Plug and Play
Remote Procedure Call (RPC)
Remote Procedure Call (RPC) Locator
SHELL HARDWARE DETECTION
Universal Plug and Play Device Host
Windows Audio
Windows Installer

Always make a backup of your VDI file and keep a change log!  If you want to tweak XP some more try Control Panel - System and turn off the following:
System Restore - off
Automatic Updates - off
Error Reporting - no critical alerts or logs
Remote Desktop Connection - disable
System Startup - no failure logs
Performance - no effects for best performance
Swap File - disable or use on flash stick until needed - causes fragmentation and tuning problems

Don't forget to run "msconfig" and disable all services except those listed above.  Then run regedit look for the key called "enablePrefetcher" and change to 0.  Then delete the Windows folder called Prefetch.  If you don't need a Studio Box then leave all services intact.  Just run defrag program frequently to keep disk in shape.  Smaller disks run faster in virtual mode than larger disks.  For optimum speed use a 32GB FAT32 format when you install your virtual computer.  Once you activate your machine you cannot change the memory or video card settings or services.  Make sure you use at least 256MB with 8MB for graphics.

And yes my external HDD is 160GB and only has 20GB on it.  I did the steps above and Ubuntu had no problem automatically mounting NTFS.  But when I went into VirtualBox and started XP defragmenter half of the 20GB was red (fragmented) and placed at the center of the drive.

Defrag is moving all 20GB to the beginning of the drive, and removing fragments on the way.  It took an hour just to copy the data from the old drive.  So you can imagine how long it might take to copy and paste all over again.  Plus the computer has to figure out where to put all the stuff!

So yes it's normal to take hours or days.

Related articles:
[http://ubuntuforums.org/showthread.php?t=708426&highlight=ntfs+format](http://ubuntuforums.org/showthread.php?t=708426&highlight=ntfs+format)
[http://ubuntuforums.org/showthread.php?p=4578974#post4578974](http://ubuntuforums.org/showthread.php?p=4578974#post4578974)
[http://ubuntuforums.org/showthread.php?p=4579361&posted=1#post4579361](http://ubuntuforums.org/showthread.php?p=4579361&posted=1#post4579361)

---

### Post by CSMatt on 2008-03-29
I actually ditched the computer in question about a year ago for a new one (albeit for unrelated reasons), so I don't have this problem anymore.  But thanks anyway.

---

### Post by hhhhhx on 2008-03-29
> "And even though the computer was off and unplugged, an image stayed on the screen.  It was, *the Windows logo!*" - Bender 			nice sig.  lol

---

### Post by CSMatt on 2008-03-30
Nice avatar.  lol

---

### Post by articpenguin on 2008-06-18
I use jkdefrag. its fast although it takes 6 hours well thats because i have 1.5Million files most of them are flightgear. My system feels a lot more fast with jkdefrag than the bare bone version of diskeeper that is included with windoze xp. dot get me started with vistas defragger.

---

### Post by ComputerGeek31618 on 2008-06-24
Keep in mind that you need a few gigabytes of free space so the disk has somewhere to write when it defragments.  Witout that, it won't even try.  Also, the more is on the disk in the first place, the more time it takes to write them all into a block.  And the more free space is on the drive, the more drfragmenting it can do at once, and the less time it takes.  For example, defragging 30gigs on a 40gig disk at my house takes a few hours.  Defragging 60 gigs on my 300gig disk takes about 45 minutes.  Availible RAM, HDD speed (I/O and RPM), CPU speed, and amount of fragmentation are all other factors that affect defragmentation time.

---

