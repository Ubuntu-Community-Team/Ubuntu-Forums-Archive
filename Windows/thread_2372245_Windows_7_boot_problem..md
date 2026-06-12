---
title: "Windows 7 boot problem."
date: 2017-09-22
forum: Windows
---

### Post by rdengle on 2017-09-22
Hello all I'm trying to fix a laptop for a friend. This is Windows 7 it will not boot used the boot repair tool said it repaired but still no dice. The error code is -xc000000e which I think is damaged system files it just came out of nowhere. The paste is:[ http://paste.ubuntu.com/25594657]("http://paste.ubuntu.com/25584657") she's trying to retrieve a doc any help would be super if email best: (email removed)Thanks!

---

### Post by oldfred on 2017-09-22
Removed email (forums are scanned and spammers may then get your email) & moved thread to Windows sub-forum.

Boot-Repair is primarily for repair of Linux systems. It can install a Windows type boot loader if that is the issue, but not much else.

Your link to Boot-Repair's summary report is not the report, please correct & the report may show something to help with using a Windows repair flash drive to fix Windows.

---

### Post by rdengle on 2017-09-22
I ran it three times.  In order, they were:  ([http://paste.ubuntu.com/](http://paste.ubuntu.com/)) 25594443/ then it went to 25594550, then the last said 255994657  I appreciate it muchly thank you.  I'm trying to find any kind of boot disk I can create for this system, it's a 2nd hand laptop she has and of course she has no product code for 7.

---

### Post by oldfred on 2017-09-22
One of those worked.
It showed Boot-Repair has installed syslinux boot loader which is a standard Windows type boot loader that should boot Windows.
And sda1 is NTFS boot partition with boot flag and the two Windows boot files/folders required to boot and sda2 is NTFS with main install.
So configuration looks ok.

Can you get into Windows internal repair console with f8 as it starts to boot?
       Windows Repair Console ------------
f8 to get to repair install screen, if you can start to boot
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
[http://www.sevenforums.com/tutorials/666-advanced-boot-options.html](http://www.sevenforums.com/tutorials/666-advanced-boot-options.html)
[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)
[https://support.microsoft.com/en-us/kb/927392/](https://support.microsoft.com/en-us/kb/927392/)

You also can create a Windows repair disk from another copy of Windows. I once used a Windows 7 repair flash drive on my XP install to run chkdsk. That did lead to some issues with incompatible NTFS boot sectors but that was also easily repaired. And version newer than Windows 7 should also work for Windows 7.

       
 [http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://windows.microsoft.com/en-us/windows-10/create-a-recovery-drive](http://windows.microsoft.com/en-us/windows-10/create-a-recovery-drive)
Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)
Manually create repair flash, shows files & locations
[http://www.7tutorials.com/create-usb-memory-stick-system-recovery-tools](http://www.7tutorials.com/create-usb-memory-stick-system-recovery-tools)

---

### Post by rdengle on 2017-09-22
OK F8 didn't work.  Unfortunately I don't have a copy of Windows 7 or any for that matter. ;(.  It just keeps prompting me to put in the installation disk (no gots) in order to run the repair tool. Only option given. I was able to get the boot order changed right now I have it as 1st notebook HD 2. Optical drive I can pick at will multiboot. So there is that. Then I tried a rescue disk I made from a program called Windows Boot Genius (Tenorshare) which looked like it had some things I could use but it froze right on the opening screen. That's it so far and again truly appreciate you putting your thoughts in. :)

---

### Post by Autodave on 2017-09-23
If you can either boot it into Linux by the internal HD or by a Linux boot disk, stick, you should at least be able to navigate then to the Windows partition and find and copy the doc she needs to a USB stick/external HD.

---

