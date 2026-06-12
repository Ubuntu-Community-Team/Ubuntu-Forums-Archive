---
title: "Partition  problem while trying to reinstall Windows 7"
date: 2013-12-02
forum: Windows
---

### Post by evacide on 2013-12-02
I had only Ubuntu on my drive and now I'm trying to delete the partitions and reinstall Windows. Somehow my partitions got messed up and my other drive with all backup files is stuck underneath an extended partition. Is there any way to get it and the other free space out without losing data? I'm stuck using the LiveCD right now. I've attached a screenshot too, thanks!

tldr: get /sda5 out from underneath /sda3 so I can create a partition up top for Windows

---

### Post by ajgreeny on 2013-12-02
Do you want to remove ubuntu completely or did you want a dual boot setup?

You seem to have deleted all your ubuntu partitions unless you had an ntfs data partition, sda5; or was that partition your backup?  However you certainly have no OS partition for ubuntu now as that would be ext4 filesystem.

What exactly did you do, and what do you think was originally your ubuntu OS partition, as it may be possible to get it back again if you have a need for it.

If you want a windows only system now you can shrionk the extended partition sda3 by grabbing its left hand end and moving it to the right.  That will remove the unallocated space from the extended partition, and add it to the unallocated 287MB at the start of the drive.
You should then be able to install Windows into the partition at the start of the drive, and it will find the ntfs partition automatically

---

### Post by oldfred on 2013-12-02
Moved to OtherOS since Windows issues.
If you have partitions on drive you need a primary NTFS partition with the boot flag for Windows to install. 
Some have had to reformat with Windows install as the gparted install does create a XP type NTFS partition. Windows still should install and convert that to a Windows 7 type NTFS partition. 
If unallocated space Windows will want to create two primary partitions as it also creates a small 100MB boot partition. That boot partition is not required but is standard with Windows 7 so you could encrypt the main install.

---

