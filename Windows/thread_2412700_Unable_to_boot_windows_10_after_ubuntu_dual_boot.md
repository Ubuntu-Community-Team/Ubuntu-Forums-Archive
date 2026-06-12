---
title: "Unable to boot windows 10 after ubuntu dual boot"
date: 2019-02-16
forum: Windows
---

### Post by jjjustin321 on 2019-02-16
Hi, I recently dual booted my PC with Ubuntu and Windows 10, and now Windows 10 will not start.  I tried to reset it with keep all files, but the reset failed as well.  I also tried to use bootrec commands in the command prompt in recovery mode, but I could not get administrator access and it said that no administrator accounts were available on the PC.  I used boot repair and this is the link it generated for me: [http://paste.ubuntu.com/p/CfDtG5fwCd/](http://paste.ubuntu.com/p/CfDtG5fwCd/)
If anyone can help, I'd be really grateful!

---

### Post by yancek on 2019-02-16
> Hi, I recently dual booted my PC with Ubuntu and Windows 10, and now Windows 10 will not start

Did the dual boot ever work or do you mean you attempted to install Ubuntu on the same machine/drive as windows?

> tried to reset it with keep all files, but the reset failed as well. 

Exactly how did you try to reset?

> I also tried to use bootrec commands in the command prompt in recovery mode, but I could not get administrator access and it said that no administrator accounts were available on the PC.

That seems odd, I mean the part about no administrator accounts being available.  When you get the command prompt in the windows menu and right click to select 'run as administrator', is that when you see the warning?  Did you install windows 10 or was it pre-installed from the factory?


Your boot repair output shows you have windows boot code in the MBR but it also shows that you have UEFI installs of both windows and Ubuntu so the code in the MBR is not necessary.  The EFI partition has correct EFI files for both systems.  Use GParted from the Ubuntu install DVD/USB and check to see that sda1 is marked as boot/active, disable Secure Boot in the BIOS and check to see that Legacy/CSM boot is disabled in the BIOS and try booting again.  If you have a Boot Option to boot from EFI file available on boot, make sure to select the grubx64.efi file.

---

### Post by oldfred on 2019-02-16
Are you trying to boot Windows via grub or directly from UEFI?

Grub only boots working Windows, so when Windows has issues, you need to see if you can boot from UEFI directly and maybe f8 into internal repair console. Or use your Windows repair flash drive to make Windows repairs.

---

### Post by Mark Phelps on 2019-02-16
When you did the prep for the dual boot, did you allow the installer to shrink the Windows partitions to create the unallocated space? If so, that was your mistake as that often results in corruption of the Windows filesystem -- making it very difficult, after that, to repair Windows because it will no longer boot.

Also, you said you did a reset with the option to keep all files. Maybe we're mixing terms here, but there is no such thing in Windows. There is a REFRESH, which keeps SOME of the files, but it only retains apps that were installed from the Windows Store; all other apps are removed.  There is a Factory Reset, but that removes everything.  There is a Repair-Install, and that will keep all the data, settings, and apps -- but that has to be run from INSIDE Windows, it can not be run if you boot from the Windows media.

Also, a failed Reset leaves the PC with a corrupted Windows filesystem, so you will have to repair it using something else.

You would probably do best, since these are MS Windows issues, to post your issues on a Windows forum -- like Tenforums.com (for Windows 10).

---

### Post by oldfred on 2019-02-16
Moved to Windows sub-forum.

---

