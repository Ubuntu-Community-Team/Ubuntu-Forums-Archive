---
title: "I'm having permission problems with my external :("
date: 2010-11-08
forum: Security
---

### Post by helios16v on 2010-11-08
I just had it all working on my laptop with Ubuntu 10.10 but now I'm on my Desktop PC I just finishing putting together so I can put all of my old IDE hard drive data onto this external.

First off I'm trying to copy all of the files off of the external onto my Desktop PC 500 GB internal hard drive so I can format the external from Extended(Journaled) to FAT so my windows computers can read it too.

When I do this:
```
gksu nautilus
```
Then I try to change the ownership of the files and it then pops up and tells me
> 
**The owner could not be changed.**
Sorry, could not change the owner of "iPhone Pictures": Error setting owner: Read-only file system

I then tried this:
```
sudo chown -R stranger:stranger '/media/500 GB'
```
After that was finished I closed Terminal and tried to copy a previously locked file over and then I get this error.
> **Error while copying "Picture_001.JPG".**
There was an error copying the file into /media/Bruno/External Backup/ipod back up/Folder/Pictures/iPhone Pictures.
*Show more details*
Error opening file: Permission denied

I need some way to force an open permission to allow any computer or user to gain access to this hard drive with read and write access too.

Please help, I just want to get all of the files off of the external so I can format it to FAT then put all the files back on along with the files on my other 9 IDE hard drives I want to get rid of :P

-Ben

---

### Post by SeijiSensei on 2010-11-08
Usually a file system is marked "read-only" by mount when it finds errors in the structure.  I'm not sure what you mean by "Extended(Journaled)".  Do you mean it's an ext3 or ext4 filesystem?  If so, leave the device unmounted and run "sudo fsck /dev/sdX1" from a Terminal replacing "X" with the letter used to reference the device.  For instance, if it's the only other drive on the system it will probably be /dev/sdb1.  (This assumes the device has just one partition.  If it has multiple partitions, you'll need to use 2, 3, etc. instead.  You can look at the partition structure with "sudo fdisk /dev/sdb".)

---

### Post by helios16v on 2010-11-08
Extended(Journaled) is the default format for OSX because this external drive was originally used for backing up my old Powerbook G4. So when I got the thing I formatted it on my mac and it just did that be default, not really thinking at the time that Extended(Journaled) doesn't work with windows..

-Ben

---

### Post by SeijiSensei on 2010-11-08
Maybe this will help?

[http://viaforensics.com/computer-forensics/how-to-mount-mac-os-x-hsf-partition-in-linux.html](http://viaforensics.com/computer-forensics/how-to-mount-mac-os-x-hsf-partition-in-linux.html)

---

