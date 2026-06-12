---
title: "Partition Mess"
date: 2016-09-22
forum: Windows
---

### Post by lfoggie1 on 2016-09-22
Hi guys,

I'm new here so apologies in advance for any rule-breaking, please be kind to me!

I installed Ubuntu for the first time having been a Windows user all my life. 

When installing Ubuntu from a USB I selected the option to partition the hard drive to have a separate partition for Ubuntu of 10GB (with plans to extend the size of the partition later). I tried to also create a swap partition of 2GB (which as far as I know now was unnecessary as I have 6GB of ram). The installation went smoothly and Ubuntu is running perfectly... And then I tried to boot up Windows which instantly tried to repair itself, diagnose itself, failed and offered options such as system recovery etc. So here I am knowing full well that I never should have touched the partitioning.

 I am an idiot.

If anyone can help me I'd be so grateful. Gpart has been useful in showing me that there are problems but I am not knowledgeable enough to know whether the problems are irreversible.

The following images I feel speak for themselves:

[[IMG]http://s26.postimg.org/bery8ro2t/ALl_drives.png[/IMG]]("http://postimg.org/image/bery8ro2t/")

[[IMG]http://s26.postimg.org/j8sju5vvp/Main_Partition.png[/IMG]]("http://postimg.org/image/j8sju5vvp/")

[[IMG]http://s26.postimg.org/ja2hnkxph/Main_Partition_2.png[/IMG]]("http://postimg.org/image/ja2hnkxph/")

[[IMG]http://s26.postimg.org/4s5afl6ed/MIcrosoft_Reserved_Partition.png[/IMG]]("http://postimg.org/image/4s5afl6ed/")

And here are two images showing the "Partition Types" of the two partitions for which GPart showed an error for: you can see that the larger of the two, the main partition on a Linux partition type...

[[IMG]http://s26.postimg.org/6l873wrl1/WIndows_as_LInux.png[/IMG]]("http://postimg.org/image/6l873wrl1/")

[[IMG]http://s26.postimg.org/b8e95oexx/MIcrosoft_Reserved.png[/IMG]]("http://postimg.org/image/b8e95oexx/")

I also tried using Boot-Repair to no effect. Here are the boot-repair diagnostics

[Before boot-repai]("https://paste2.org/57G7JfgL")r:

[After boot-repair]("https://paste2.org/vDDh6OFP"): 

The key to the problem may be something to do with "According to the info in the boot sector, sda4 has                             1701427363 sectors, but according to the info from 
                            fdisk, it has 1660155903 sectors."

What has happened? I tried not to mess the WINdows partitions up when I installed Ubuntu but to no avail... I cannot access my files.

I hope these changes are not irreversible but I am prepared to bear the full consequences of my idiotic actions should they prove to be so...

Thanks in advance.

Lewis.

---

### Post by oldfred on 2016-09-22
Links are not clickable.

You did not turn off Windows fast startup or its always on hibernation. That keeps all NTFS partitions mounted. The Linux NTFS driver will not mount hibernated or NTFS needing chkdsk.

You should be able to boot Windows directly from UEFI boot menu, often f10 or f12.
Turn off fast start up.

       Fast Startup off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.htmlold)

Did you install Ubuntu in UEFI boot mode?
       
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 

 Windows & grub often require some totally unformatted partitions like Windows system reserved. Gparted shows that as an error since not formatted, but it must be unformatted so ok.

Some work better with UEFI secure boot off, but keep UEFI boot on, not BIOS/CSM/Legacy.
       HP Check if Customized UEFI settings available like this  HP ProBook 4340
[URL="https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216"]https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216
[/URL]
 Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886) 

[URL="https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216"]
[/URL]

---

### Post by lfoggie1 on 2016-09-23
Hi oldfred,

Thanks for replying.

> **oldfred said:**
> Links are not clickable. 

Do you mean the boot-repair links? I'll fix them... You can see the pictures though right?

> **oldfred said:**
> Did you install Ubuntu in UEFI boot mode?

I installed Ubuntu as a UEFI boot, just like Windows is. I started up in UEFI firmware boot menu which showed Ubuntu UEFI and Windows UEFI boot menus along with another option which was something to do with EFI.

I tried to start the Windows UEFI boot menu to disable fast start but immediately the HP logo appears trying to repair and diagnose itself which results in failure and then a number of options like system restore etc. are available.

I am not sure that Windows was in fast startup mode as I'm sure I disabled it a while ago but maybe I'm wrong. In any case I cannot change it because as I said when I try to access the WIndows boot menu it immediately goes to the HP logo and trying to repair itself.

Your other links were informative but I can't really see anything that would help.

Since I did not make the boot-repair links clickable here is a part of it which I hope may tell us something:

"
sda3: __________________________________________________________________________

  
	    File system:       

 	    Boot sector type:  -

 	    Boot sector info: 

 	    Mounting failed:   mount: unknown filesystem type ''

  
	sda4: __________________________________________________________________________

  
	    File system:       ntfs

 	    Boot sector type:  Windows 8/2012: NTFS

 	    Boot sector info:  According to the info in the boot sector, sda4 has 
 	                       1701427363 sectors, but according to the info from 
 	                       fdisk, it has 1660155903 sectors.
 	    Mounting failed:   mount: unknown filesystem type ''
 	Failed to read last sector (1701427362): Invalid argument

 	HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,

 	   or it was not setup correctly (e.g. by not using mdadm --build ...),
 	   or a wrong device is tried to be mounted,
 	   or the partition table is corrupt (partition is smaller than NTFS),
 	   or the NTFS boot sector is corrupt (NTFS size is not valid).
 	Failed to mount '/dev/sda4': Invalid argument
 	The device '/dev/sda4' doesn't seem to have a valid NTFS.

 	Maybe the wrong device is used? Or the whole disk instead of a

 	partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
 	Failed to read last sector (1701427362): Invalid argument
 	HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
 	   or it was not setup correctly (e.g. by not using mdadm --build ...),
 	   or a wrong device is tried to be mounted,
 	   or the partition table is corrupt (partition is smaller than NTFS),
 	   or the NTFS boot sector is corrupt (NTFS size is not valid).
 	Failed to mount '/dev/sda4': Invalid argument
 	The device '/dev/sda4' doesn't seem to have a valid NTFS.
 	Maybe the wrong device is used? Or the whole disk instead of a
 	partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?"

I don't know if this is of relevance but in GPart the large Windows partition where all my files are is given as 791.62GB whereas the "disks" app on ubuntu reveals this partition to be 850GB.


Thanks oldfred, I hope I'm giving you the right information.

---

### Post by oldfred on 2016-09-23
I was able to load link, it just is that others may not. I use a valid link and change last chars to yours.

That it cannot see the NTFS partitions is either chkdsk or the hibernation in 99% of the cases.
Best to use your Windows repair/recovery flash drive:
 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options) 

Have you tried f8 when booting directly into Windows?

---

