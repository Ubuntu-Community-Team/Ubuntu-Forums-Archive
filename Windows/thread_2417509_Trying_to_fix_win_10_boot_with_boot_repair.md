---
title: "Trying to fix win 10 boot with boot repair"
date: 2019-04-23
forum: Windows
---

### Post by mpalenque on 2019-04-23
boot info was on another win8 which was deleted. not Its not booting and im trying to fix it.

[http://paste.ubuntu.com/p/yZSyg6RxGF/](http://paste.ubuntu.com/p/yZSyg6RxGF/)

---

### Post by mpalenque on 2019-04-23
Windows is installed on kingston SSD named sdd

---

### Post by oldfred on 2019-04-23
Moved to Windows sub-forum since no Linux.

Boot-Repair is for Linux systems, it can only do a few minor fixes for Windows.

Windows second install always puts its boot files in the first install. Windows boot files have to be in a primary NTFS partition with boot flag. But do not have to be in the separate Boot partition that Windows has used since Windows 7. You can have boot files in your main or c: drive partition, but have to have boot flag & it has to be a primary partition.
And you will have to run Windows repairs. as sdd1 is missing BCD configuration file which Boot-Repair cannot fix.

       Vista,  win7 and newer Windows in BIOS boot mode
  Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 

      
 How to: perform a repair upgrade using the Windows 10 ISO file
[URL="http://answers.microsoft.com/en-us/insider/wiki/insider_wintp-insider_install/how-to-perform-a-repair-upgrade-using-the-windows/35160fbe-9352-4e70-9887-f40096ec3085"]http://answers.microsoft.com/en-us/insider/wiki/insider_wintp-insider_install/how-to-perform-a-repair-upgrade-using-the-windows/35160fbe-9352-4e70-9887-f40096ec3085
      [/URL]
 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options) 
    [URL="http://answers.microsoft.com/en-us/insider/wiki/insider_wintp-insider_install/how-to-perform-a-repair-upgrade-using-the-windows/35160fbe-9352-4e70-9887-f40096ec3085"]
[/URL]

---

