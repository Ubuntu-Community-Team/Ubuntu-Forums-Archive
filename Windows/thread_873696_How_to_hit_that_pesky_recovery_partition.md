---
title: "How to hit that pesky recovery partition"
date: 2008-07-29
forum: Windows
---

### Post by Mgiacchetti on 2008-07-29
[http://www.youtube.com/watch?v=yVIBj336FVQ](http://www.youtube.com/watch?v=yVIBj336FVQ)

Using WinRar, navigate to the Recovery Partition, and backup the following files (add to archive = C:\recoverybackup.rar).

Folder.htm
Desktop.ini
Protect.ed
Autorun.inf

Now that you have them backed up, go ahead and delete them from the recovery partition.

Now you should be able to access the recovery partition, and all of its contents.


Your preinstalled drivers are loaded in the \I386\DRV folder and your preinstalled applications are in the \I386\APPS folder.

-------------------------------------------
In case you have messed up your [MBR](http://en.wikipedia.org/wiki/Master_boot_record) and need to use the restore option and are unable to access the [recovery partition](http://en.wikipedia.org/wiki/Recovery_Partition) from F10/F12 boot option, follow these instructions:

If you don't have a working Windows Installation, you will need a windows XP disk and (**[COLOR=Red]not someone else's[/COLOR]**[COLOR=Red][COLOR=Black]) [/COLOR][/COLOR]key **[COLOR=Red]you cannot use the key on the side of the pc unless you have an OEM install disk for the version of windows you have[/COLOR]**, yep to make f10 work again, you need to install xp twice, lol.  

**[COLOR=Blue]MAKE SURE TO[/COLOR] [COLOR=Red]COMPLETE THIS TUTORIAL[/COLOR], [COLOR=Blue]IT WILL RESTORE THE[/COLOR] [COLOR=Red]ORIGINAL OEM SOFTWARE[/COLOR] ([COLOR=Blue]piracy is theft[/COLOR] and you dont wanna be caught stealing an os that didn't come on your pc do you?)**


If you have a working windows install. Reboot into "safe mode with command prompt" (F8) in command prompt, navigate to the recovery partition 

While in the recovery partition, navigate to "MiniNT\system32" type "Restore.exe" and press enter. 

When the program completes restart the PC.

You should now be able to [COLOR=Red]!!PRESS F10/F12!![/COLOR] at boot to [COLOR=Red]!!COMPLETE THE RECOVERY PROCESS!![/COLOR], as the above WILL NOT completely recover the PC to factory defaults because the partition is active, this will however fix your MBR so you can boot into the recovery partition and [COLOR=Red]fully restore the PC[/COLOR]. 

Thank you WinRar!

---

### Post by Joeb454 on 2008-07-29
Moved to Windows Discussions :)

---

