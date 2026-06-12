---
title: "Creating Partitions and FS on New External Drive"
date: 2016-12-30
forum: Virtualisation
---

### Post by AUDIOTEK on 2016-12-30
It's part of my Linux+ course how to partition create FS etc... from the command line mostly using fdisk.  I have a LaCie external HD that the Windows host machine sees no problem.  For now I run Ubuntu in GUI mode with VirtualBox so I can see what happens when you partition etc...   Problem is Ubuntu doesn't see that drive at all.  I'm using the Disk utility but nothing.   How can I force Ubuntu in CUI to see that external disk so I can use fdisk and practice?

---

### Post by oldfred on 2016-12-31
What version of Windows?
If Windows 8 or 10, it uses fast start up to make you think Windows boots faster when it really is just hibernation. But it leaves all NTFS partitions mounted. And hibernated/mounted NTFS or NTFS that needs chkdsk will not be seen by the Linux NTFS driver.

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions](http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions)

Note that only with 16.04 does fdisk support gpt partitioned drives. You have to use parted or gdisk if you have an older version of Ubuntu.

Windows 8 or 10 if from vendor is UEFI boot and then drive has to be gpt partitioned.
Also all drives over 2TB must be gpt partitioned. Ubuntu can use gpt for BIOS boot, but Windows only boots in BIOS mode from MBR (msdos) partitioned drives.

       
 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr) 
    
We recommend you only use Windows to shrink NTFS partitions.
You then use Linux tools to create new partitions, or repartition a drive.
Windows can convert a MBR drive to a proprietary dynamic partitioning scheme if you have used all 4 primary partitions.  And that is a one way conversion. Dynamic does notwork with Linux.
Gpt(GUID) partitioning does not have the 4 primary partition limit. 

Some more info:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

---

### Post by AUDIOTEK on 2016-12-31
Great thanks    I'm using Windows 7 and Ubuntu 16.10.

So what if this actual situation appears in a real life where a Linux machine cannot see a drive on a remote computer and the sysadmin has to format it??

What format should I format the external disk to so Ubuntu can see it?

---

### Post by ajgreeny on 2016-12-31
Also which version of VBox are you using and do you have the exact same version of VBox-guest-additions installed in the guest?

Do you have USB enabled in your guest?

---

### Post by AUDIOTEK on 2016-12-31
Enable USB Controller in Vbox is checked but all graeyd out  and selected to USB 1.1 (OHCI)

I also tried to format the LaCie drive on my standalone Ubuntu and I get    ERROR FORMATTING VOLUME
Error Synchronizing after formatting type "ext4": Timed out waitining for object (udisks-error-quark,0)  I might try a different drive

---

### Post by howefield on 2016-12-31
Thread moved to the "*Virtualisation*" forum.

---

