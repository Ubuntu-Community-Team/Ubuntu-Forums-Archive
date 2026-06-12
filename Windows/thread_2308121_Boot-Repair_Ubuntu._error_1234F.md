---
title: "Boot-Repair Ubuntu. error: 1234F"
date: 2015-12-31
forum: Windows
---

### Post by 14309128 on 2015-12-31
So I use a Dell Inspiron 15-3521 that uses Windows 8. I took care of the PXE-E61 error by disabling NIC. Then the next error that I also had with PXE-E61 is: 1234F, which I don't know how to fix. I followed the instructions to use Boot-repair through my working Ubuntu 14 live CD, and clicked Recommended repair. but it still didn't work after a reboot, and gave me the same 1234F error.

[http://paste.ubuntu.com/14309128/](http://paste.ubuntu.com/14309128/)


  How to do this? I don't understand the paste report.

  
I also have Hirens boot CD, if somehow I can use that????

---

### Post by oldfred on 2015-12-31
Is this a Windows only system? I do not see any Linux partitions.

Boot-Repair is primarily for Linux systems. It can only do very minor fixes to Windows systems. 
You normally use your Windows repair CD or flash drive to fix Windows issues and may get better help on a Windows forum. Some of us do dual boot and may be able to offer some suggestions.

You have installed testdisk boot loader (an old BIOS boot) to MBR. But your system is UEFI and you should make sure you always only boot in UEFI boot mode. You will get errors if you boot in BIOS mode as that will never work.

Not sure sure what your error is. Boot-Repair does not use error numbers. May be UEFI or Windows?
You may have corruption on sda5 which should be your c: drive in Windows. You may need to run chkdsk which only can be run from Windows, not from Linux.

       [http://www.tenforums.com/](http://www.tenforums.com/)
[http://www.eightforums.com/](http://www.eightforums.com/)
[http://superuser.com/](http://superuser.com/)

[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options) 

Not sure if this is still the same in newer Windows or not:

 f8 to get to repair install screen, if you can start to boot
[http://www.sevenforums.com/tutorials/666-advanced-boot-options.html](http://www.sevenforums.com/tutorials/666-advanced-boot-options.html)

---

### Post by 14309128 on 2015-12-31
Yes, this computer that I am talking about is a Windows 8 only PC. No other OS's installed.
I guess a microsoft fourm would be more suitable for my problem.

And F8 does not work, for the newer Windows 8 PCs holding down shift is what google told me.
UEFI mode gave me a blank screen after the "preparing repair" both secure on/off modes. Also, after it a long of waiting on the screen, it gives a skyblue blackground with white grey text that says there is an error and has to restart. (can't read it though because it auto-restarts after 3 seconds)

Anyway, I am now attempting a chkdsk using "chkdsk C: /f /r /x[B]"  
[/B]Using Hiren's Boot CD, underneath mini XP mode.
I am receiving many "File record segment 2*xxxxxx* is unreadable."
UPDATE: I restarted after it finished and nothing happened, same 1234F error.

I did remember yesterday that I did mess with the testdisk mbr with Hiren's Boot CD because I thought that would work, so that may explain the old BIOS boot.

No luck.

---

### Post by oldfred on 2015-12-31
Moved to Windows sub-forum.

Not sure what else to suggest. 
In live Ubuntu is Disks and icon in upper corner is tools and Smart Data which you can use to see if hard drive is reporting major issues.

---

