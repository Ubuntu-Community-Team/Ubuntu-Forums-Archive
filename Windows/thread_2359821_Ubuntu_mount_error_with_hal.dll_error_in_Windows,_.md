---
title: "Ubuntu mount error with hal.dll error in Windows, CMOS battery dead"
date: 2017-04-28
forum: Windows
---

### Post by capt.robovski on 2017-04-28
Hi there,

Newly registered but have been a longtime reader of these forums having used live cds for some time, and soon considering switch to dual booting (unfortunately need a couple of propriety programs which are industry standard).

At my parents' house I have an old Acer Aspire E300 desktop running Windows XP Home SP3. The machine hadn't been run for a few years but I've realised I didn't have full backups of key files like photos and documents (d'oh!) Earlier this week went round with a 1TB USB drive to copy things across and found the CMOS battery was dead - it didn't boot. I reset the clock in the BIOS and it booted into XP just like it had been run yesterday. After a few minutes idling at the desktop it showed a couple of warning dialogs. I went away for 10mins and came back to find a black screen with error message reading:

Windows could not start because the following file is missing or corrupt:
<Windows root>\system32\hal.dll.
Please re-install a copy of the above file.

Windows will now not boot. I then tried mounting the drive in Precise Puppy Linux, which did work after a warning about ntfs-3. However, the machine was so unresponsive it was unusable. I (probably impatiently) powered down - i tried to unmount the drive first but Puppy didn't respond to anything. 

I booted into a live DVD of Ubuntu 12.10 which I knew worked. I then got the following error when trying to mount either of the hdd partitions:

Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, 
Error mounting: mount exited with exit 13: ntfs_attr_pread_i: ntfs_pread failed: Input/output error
Failed to read NTFS $Bitmap: Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows then reboot into Windows twice. The usage of the /f parameter is very important! If the device is a SoftRAID/FakeRAID then first activate it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

This has given me more information than Windows, but as it's Ubuntu specific I thought I would ask here for some help diagnosing the error. I've seen some posts here about the hal.dll error when there's dual boot issues but I'm at a loss.

Basically, my goal now is to somehow mount the two partitions and copy data to the USB drive. I don't really mind how, I'm just concerned that the drive could be failing and that chkdsk might strain it further.

My thoughts are to either:

1. Use a SATA to USB adapter to run the drive on my working Windows 7 laptop.
2. Use a Windows 7 DVD on the XP machine to try and access the partitions via the restore>command line> notepad>explorer window trick
3. Use something like Testdisk to attempt recovery (that's the scariest option for me - technically minded person but not a whiz)

Any advice on how to resolve the error in Ubuntu (or windows)? If I can mount the drives it should be fine :) 

Thanks in advance

Rob

Edit: Added photos of the two error messages.

---

### Post by oldfred on 2017-04-28
Fix WinXP hal.dll 
[http://ubuntuforums.org/showthread.php?t=1410696](http://ubuntuforums.org/showthread.php?t=1410696)
Missing hal.dll not always missing, but other errors or boot.ini wrong partition 

You also may need chkdsk.

I once ran chkdsk from my Windows 7 repair flash drive (I did not have Windows 7) and it fixed more issues than the XP chkdsk.
But it converted the partition boot sector PBR to Windows 7 boot.
Inside the PBR is info on which file is used to boot. XP uses ntldr and Windows 7 or later in BIOS mode uses bootmgr.
I then reran the XP chkdsk and that fixed that issue.

XP is so obsolete that even the later Vista is now obsolete.

If you just want to access the data, once you run chkdsk from XP (and or 7), you should be able to mount the partition from an Ubuntu live installer.
Better to use Lubuntu as it is more lightweight. 
Or move drive to another newer system, and mount from there.

---

### Post by capt.robovski on 2017-04-28
Thanks for your help, oldfred, really clear and easy to understand too :)

Sounds good. I've found an XP iso I backed up years ago in my disc wallet so can try running chkdsk from the recovery console on that. My concern was based on posts read elsewhere that chkdsk puts a lot of strain on the drive, which worries me if the drive might be on its last legs. (I'm probably being paranoid, as I've run chkdsk just because in the past...!) 

What I find odd is that XP booted all the way to the desktop before it produced the error, so it probably isn't a boot issue here?

I tried Lubuntu 16.04 on the same multiboot disc as Puppy and it just had a black screen. I couldn't even get the accessibility icons and hit f6 for nomodeset options, which is odd as I've successfully used the iso to install it in a VM. I have an old Ubuntu 9.10 cd in thr wallet which was burned on the faulty machine, so that should be roughly as light as Lubuntu, given its age?

---

### Post by capt.robovski on 2017-04-28
Sorry was meant to ask a couple of other questions:

1. Does the mount error in Ubuntu give any clues to what has happened with the drive?
2. I'm thinking of buying a SATA to USB adapter to plug the drive into my working Windows 7 laptop. Should I run chkdsk before doing this, or is the fact that a working NTFS based system is trying to mount it likely to be enough?

---

### Post by yancek on 2017-04-28
> 
1. Does the mount error in Ubuntu give any clues to what has happened with the drive?

The two primary culprits in your situation are leaving a system hibernated which is the default for windows 8 and 10 and most windows users are unaware of this.  With xp, I very much doubt that is the problem and it is more likely a corrupt filesystem.  That cannot be fixed from Linux but since you have a windows CD/DVD, you can run chkdsk from that.  I don't really use windows but, if your xp filesystm is corrupt, booting and or mounting it from another windows system itself is not likely to resolve the problem.

---

### Post by oldfred on 2017-04-28
Really old drives have potential for failure.
The oil/grease in bearing starts to stick and other parts just do not work.
Or hard drive failure can be an issue.

Those that know always say to make an image copy of a drive (if possible) and only run repairs on the image.

If drive can be seen, you could you run tools that scan hard drive like photorec in Linux.
Some say the NTFS tools may work somewhat better on NTFS partitions.

---

### Post by capt.robovski on 2017-04-29
Thank you both for your help, much appreciated. I'm not able to access the pc until next week, so trying to get as much info as possible beforehand. As you can probably tell, I'm quite nervous about it!

Yep, I wondered about cloning the drive first using Clonezilla. Never tried cloning anything before, so couple of probably obvious questions:

1. The hard drive is (I think) 160GB, partitioned in half (worst case it's 200GB). I need to backup both partitions. If I clone the entire drive (device>device) will that copy everything, including the partitions?

2. The external USB drive I would be cloning to is also the one I'd need to backup/recover files to. It's 1TB. If I was to partition this drive first, could i clone the drive to a partition on the USB drive, thus allowing another partition for recovering data?

3. What's the reason for trying to recover data from the clone, rather than the original? Surely if anything goes wrong with the clone during recovery, the backup has gone?

Lastly (and this might be too hard to say), how long should I expect cloning to take if transferring is via USB2 and the original drive is a 13 year old 7,200rpm SATA drive?

---

### Post by oldfred on 2017-04-29
I have never done a clone either.
But I do not think you just want to clone the drive. You may convert your 1TB drive to a 160GB drive. Although you probably can then add partitions if partition table is not the damaged part of drive.

Most recovery suggestions that I have seen, use an image file and then work with that. But I have not saved notes, so do not know details.

I have run photorec and it took many hours and drive was not all that large.

---

### Post by capt.robovski on 2017-04-29
Old post here seems to suggest that as long as the external drive is partitioned ahead of time, it will not wipe the entire drive. 

Worst case scenario, I could backup to other types of drives like SD cards, just more labour intensive :)

Thanks again all for being patient with all my questions! Will give it a whirl next week and let you know what does/doesn't work.

---

