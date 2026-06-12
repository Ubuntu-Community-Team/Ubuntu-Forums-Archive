---
title: "Help with boot failure to win 7 boot repair disk wont work"
date: 2017-03-06
forum: Windows
---

### Post by berrio on 2017-03-06
Hi there,  I need help very badly, I am trying to boot to my win 7 but it wont work.
 I get goint to the help system repair window but it doesnt fix anything, i have tried to restore my system to an earlier point, twice, but it doesnt work. I tried next to use command prompt to restore my bootloader, using bootedit.exe /fixmbr and then bootsec.exe /nt60 all /force and last bootrec.exe /rebuildbcd but its no use I get coming back to the window, cant even reboot to safemode either. Finally i dl the boot repair disk and use it to try to repair my bootloader but still cant get into my windows. I have recently installed this Win 7 like 7 days ago. I had before another win 7 but it got corrupted and I choos to install a fresh one. I also ha a winXP before but sinds I installed this last win 7 I haven been able to boot there either. 
I leave you the paste url link: [http://paste.ubuntu/com/24127424](http://paste.ubuntu/com/24127424)

Please help!

thanks

HA Berrio

---

### Post by RobGoss on 2017-03-06
Is this a dual boot system with **Ubuntu**? I notice you did not mention anything about Ubuntu being installed on your system

---

### Post by berrio on 2017-03-06
No I have not linux OS installed, I had Win 7 and Win XP only

---

### Post by oldos2er on 2017-03-06
Moved to *Other OS, Windows*

---

### Post by oldfred on 2017-03-07
Boot-Repair is not a Windows repair tool, primarily for Linux. It can do some minor fixes to Windows like install a Windows type boot loader and turn on chkdsk flag.
Better to use Windows repair tools.

It looks like you did most of the typical Windows repairs.
Did you run chkdsk on all 3 NTFS partitions? You can only do that from a Windows repair or installer's repair console in Windows.

       [http://www.sevenforums.com/tutorials/666-advanced-boot-options.html](http://www.sevenforums.com/tutorials/666-advanced-boot-options.html)
[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)
[URL="https://support.microsoft.com/en-us/kb/927392/"]https://support.microsoft.com/en-us/kb/927392/

[/URL]
 Make your own Windows 7 repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm) 

[URL="https://support.microsoft.com/en-us/kb/927392/"]
[/URL]

---

