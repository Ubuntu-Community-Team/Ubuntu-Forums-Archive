---
title: "Windows 8.1 bcd missing, cannot boot to windows"
date: 2014-07-11
forum: Windows
---

### Post by mttspierings on 2014-07-11
Hi,

I was playing around with ubunutu 14.04, I ended up dual booting it with windows 8.1. But it did not boot into Ubuntu from the boot loader.
So I removed the partitions for Ubuntu and tried to repair the mbr for windows 8.1 using easy bcd.
Now the boot for windows is gone and I cannot load into windows.

I have tried running the boot repair from ubuntu but that didnt fix it.
I do not have the recovery disk as this was a pre installed windows 8.1. 

Is there anything else I can do? Or will I have to replace windows 8.1 with Ubuntu 14.04?

edit: [http://paste.ubuntu.com/7782313](http://paste.ubuntu.com/7782313)

Thanks,
Matthew

---

### Post by yancek on 2014-07-11
Windows 8 has added some complexity to dual booting and you have to deal with uefi, the Secure Boot option as well as Fast boot.  There are a number of posts here dealing with it so you might search for some or google those terms.  How did you try to use EasyBCD?  It's been a while since I've used it but I remember it needing to be on the windows partition.  Does it even work with windows 8?

Did you not have an option to create a Recovery CD when you first booted windows 8?  I've not used it outside a Virtual Machine.  I have windows 7 which did prompt to create a Recovery CD on the first boot.  I suppose you do not have an installation DVD for windows?  Do you still have the Ubuntu installation medium to use to get info on your computer to post here for assistance?

---

### Post by oldfred on 2014-07-12
Moved to Other OS since only Windows issues.

You cannot fix most Windows issues from Linux. You need the Windows repair flash drive.
Boot-Repair is really more for Linux based systems and only can do a few minor fixes to Windows.

       Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

With UEFI both Windows boot files & Ubuntu&#8217;s boot coexist in the efi partition. You should have just been able to select Windows in UEFI menu with secure boot on or off and booted directly into Windows.
EasyBCD is not required for UEFI systems, other than it may be able to repair a BCD or run chkdsk.

They know more about Windows here:

 [http://www.eightforums.com/](http://www.eightforums.com/)

      
 Repair BCD
[https://neosmart.net/EasyBCD/](https://neosmart.net/EasyBCD/)

And sometimes these are suggested.

 EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)
[http://www.partitionwizard.com/partitionmanager/partition-fix.html](http://www.partitionwizard.com/partitionmanager/partition-fix.html)

My last Windows was XP two years ago, so cannot help directly other than suggesting what others have used.

---

