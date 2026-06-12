---
title: "Boot repair disk didn't solve my problem"
date: 2019-02-25
forum: Windows
---

### Post by squareroot4 on 2019-02-25
I am not good at this kind of things. My laptop won't boot because of disk problems. The problem occured after my laptop's power ran out while doing windows updates. I waited 6-7 hours for the "repairing disk error, this might take over an hour" but nothing has changed. I downloaded the boot repair disk, i followed the instructions step by step but after the reboot it made things worse. By that i mean now when i open my pc the screen goes black at the moment when the windows logo should pop up. There also is no cursor on the screen. Maybe you guys can help me

 [Http://paste.ubuntu.com/p/HFDdYF3kYM/](Http://paste.ubuntu.com/p/HFDdYF3kYM/)

---

### Post by Autodave on 2019-02-25
This is not an area where Windows repair is done.  My suggestion would be to reinstall your Windows.  Or, give Ubuntu a try!

---

### Post by oldfred on 2019-02-25
Moved to Windows sub-forum, since Windows issues.

You are showing major issues on your NTFS partition sda2.
You may need to run chkdsk multiple times and not interrupt it or let power fail. the chkdsk does not fix all errors on every pass.
Any time you have a power failure or any other interruption why system is writing data, you will get corruption and need to run repairs.

You may be able to boot into recovery mode as your Windows boot partition shows. Otherwise you have to use your Windows repair/recovery drive.
       f8 to get to repair install screen, if you can start to boot
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
[http://www.sevenforums.com/tutorials/666-advanced-boot-options.html](http://www.sevenforums.com/tutorials/666-advanced-boot-options.html)
[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)
[https://support.microsoft.com/en-us/kb/927392/](https://support.microsoft.com/en-us/kb/927392/) 
    
You do have this?
       Make your own Windows 7 repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm) 
            Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

