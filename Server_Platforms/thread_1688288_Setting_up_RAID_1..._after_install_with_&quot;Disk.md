---
title: "Setting up RAID 1... after install with &quot;Disk Utility and mdadm&quot;"
date: 2011-02-15
forum: Server Platforms
---

### Post by F35 on 2011-02-15
Since I needed to create some RAID 1 file services after I installed Ubuntu 10.10, I looked at "DISK UTILITY" found under menu SYSTEM | ADMINISTRATION | DISK UTILITY.  

It gave a view of the hard drives I have installed.  I also found it has in its menu the following:  FILE | CREATE | RAID ARRAY.

So, it appeared this would be an easy way to set up RAID.  However, I discovered that I must first have mdadm installed.  With that installed, I was able to set up partitions.

However, the path to setting my RAID 1 up was still a little unclear and after re-boot am experiencing the following problems:
[INDENT]
[LIST=1]
[*]In Nautilus, under Computer, I can see the RAID 1.  It even has a "1" in the lower right corner of the icon.  When I double-click on the icon, I am challenged to provide password.  No what I intended...I intended on just opening into the RAID 1 files.
[*]Once I enter password, I get error "Unable to Start Location  Failed activating drive."
[*]I go to "Disk Utility" under Local Storage and Multi-Disk Devices and I can see my RAID 1 Array.  I click on it and the information in the right panel says "Start RAID Array" as the only button.  It should be started.
[*]Clicking on "Start RAID Array", I am again required to enter password.  Once through I get an error that says "Error Starting RAID Array    Error assembling array:  mdadm exited with exit code 1: mdadm no recogniseable superblock on /dev/sda2 mdadm: /dev/sda2 has no superblock - assembly aborted.
[/LIST]
[/INDENT]My assumption is "has no superblock" means I didn't setup partitions correctly.  What went wrong?

---

### Post by F35 on 2011-02-15
In Disk Utility, I go to Local Storage and PATA Host Adapter and see my 2 2 TB drives.  They are both set up the same.  They are partitioned and the graphic of the drive storage space is labeled "RAID Component".    At the top, PARTITIONING is "Master Boot Record".  Partition Type is "Linux RAID autodetect (Oxfd).

This is not a partition that has Ubuntu loaded, therefore it does not need to boot, but my intention is that the file service provided by this RAID 1 partition will be accessible to anyone on my network when the Ubuntu 10.10 machine is restarted and automatically rebooted.

I have missed something in the partitioning by using Disk Utility (rather than using the command line instructions I have seen elsewhere).  That being said, those instructions did not seem applicable since I just recently added these hard drives and I don't intended them to hold an Operating System which requires boot.  

If I go back to the start and disassociate these drives from the RAID array, using Disk Utility, what should I do to properly partition them to get superblock installed as well?

---

### Post by spindoctor64 on 2011-03-26
I'm having the same problem.  Any resolution yet?

---

### Post by AbeFM on 2011-06-05
Looking at [http://blog.rogersoles.com/technology/ubuntu-raid-creation/](http://blog.rogersoles.com/technology/ubuntu-raid-creation/) I think the suggestion is to tell the standard utils to go look for it - basically, nothing is mounted.

I assume by now you all have this figured out. I'll be doing the same if Disk Utility ever finished recovering my empty raid. I guess I have to figure out where to make suggestions, because it seems to me "create-and-format" should be an option, then there's no need to recover anything, you could do it at format time.

---

