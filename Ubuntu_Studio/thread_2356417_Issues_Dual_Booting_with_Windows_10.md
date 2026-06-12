---
title: "Issues Dual Booting with Windows 10"
date: 2017-03-23
forum: Ubuntu Studio
---

### Post by jawilson2405 on 2017-03-23
I installed Ubuntu Studio on my SSD with Windows 10. The two OS are on separate partitions. My problem is that when I boot, I don't have an option to load Windows. I'm willing to uninstall ubuntu and try again or uninstall it and then install on a separate SSD. 

How do I delete my ubuntu partition?

Is there another option?

---

### Post by ajgreeny on 2017-03-23
See **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 

**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system.

---

### Post by jawilson2405 on 2017-03-23
[http://paste2.org/EYy4kadw](http://paste2.org/EYy4kadw)

---

### Post by oldfred on 2017-03-23
Line 504:
> menuentry 'Windows 10 (loader) (on /dev/sda1)' -

That is  a grub menu entry to boot Windows, it will be near bottom of menu listing in grub.

If that entry does not work, you may have left Windows fast start up on which is hibernation.
Grub only boots working Windows, or Windows that does not need chkdsk nor is hibernated.

You need to have both Windows repair disk and Ubuntu live installer. 
Windows 10 will turn fast start back on with updates and may reset itself as default boot by reinstalling its boot loader to MBR.

If you cannot boot Windows from grub menu, install a Windows or Windows type boot loader into MBR and turn off fast start.
Then restore the grub2 boot loader to MBR.

       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System
[/URL]
 [http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://windows.microsoft.com/en-us/windows-10/create-a-recovery-drive](http://windows.microsoft.com/en-us/windows-10/create-a-recovery-drive) 

      
 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 
    [URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]
[/URL]

---

