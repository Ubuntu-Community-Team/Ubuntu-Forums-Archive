---
title: "BIG partition problems  :/"
date: 2020-05-26
forum: Ubuntu/Debian BASED
---

### Post by frvto on 2020-05-26
(SORRY if my inglish isn't the best)):P

Well, i just install Cinammon on a new C: partition (in the original i have WIndows 10), all normal and succesfull, automated instalation in new partition, Ubuntu running great
The problem beggins when i try to load WIndows Desktop

It's like the desktop never loads, just the wallpaper, not the icons, and when i pass the mouso pointclicker above the toolbar, the mouse shows the "loading" icon... and a hour pass and its the same 
First thing i though was I don't left enough hardrive space for the WIndows partition, so i use the "stand alone" version of CInammon burned in my pendrive, to see if i can provide more GB to that partition

AND , then comes another problem, wich i can't understand , but i have pics that im sure you guyz can help me read (take in count im not very skillfull)

[https://ibb.co/kDpLTGC](https://ibb.co/kDpLTGC)
[https://ibb.co/7YMymyS](https://ibb.co/7YMymyS)
[https://ibb.co/9b8dCJF](https://ibb.co/9b8dCJF)

I still can't load WIndows normally , i think i made something wrong to that partiotion of C:
and i really don't know what to do now
there's a D: partition with some work on it, just in case i save to a external device


I'm really sad cause all my professional music work i was doing it's on Windows, and installing all the software on Ubuntu is just gonna take me a lot of work and time i don't have
So, i really need to know how to repair Windows in order to load it again

***Really, thanks a lot, any help's gonna be very usefull***

---

### Post by dino99 on 2020-05-26
As the second screenshot says: the NTFS partition is inconsistent; please run 'chkdsk /f' to repair it.

As a general reminder, use windows tools on windows partition, and linux tool on linux partition; dont do mix ;)

---

### Post by slickymaster on 2020-05-26
Thread moved to **Ubuntu/Debian BASED** for a better fit

---

### Post by frvto on 2020-05-26
thanks !

---

### Post by frvto on 2020-05-26
ok
now, how can i run that on Linux?
i dunno how to acces Windows anymore   :/

---

### Post by CelticWarrior on 2020-05-26
> **frvto said:**
> ok
now, how can i run that on Linux?
i dunno how to acces Windows anymore   :/

You can't run it on Linux.
Windows file systems should only be managed/fixed in Windows with Windows tools.

If you need to recover your Windows you need Windows installation media. And even with that it may or may be recoverable. That's why everybody needs backups.

---

### Post by yancek on 2020-05-26
I don't understand what you mean in the second paragraph of your original post.  Drive partitions with drive letters such as C or D are windows filesystems.  Windows does not give labels to Linux fileystems and you should never try to install anything to a windows labelled partition from Linux.  I'm not really sure what you did though? Is that what you see when you boot windows?  Why did you need more hard drive space for windows?  You already have a windows UEFI installation.  And as stated above, you cannot repair the problems with the proprietary microsoft windows OS from any Linux so you need your windows installation media (which you are not likely to have with an OEM install) or use the recovery CD you made for it.  If you don't have either, you should be able to download it from the microsoft site or a windows site.  Take a look at the site at the link below which is the official Ubuntu documentation on dual booting UEFI with windows 10 and compare the instructions with what you did.  

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by frvto on 2020-05-26
Thanks yancek,

What i did is install Linux in a partition i create from C:  (a new one), then, when i open Windows, it doesn't load correctly .. meaby because i dont left space on that partition
When i try to fix it removing some space from the new partiotion to the original, there was some kind of "problem" GParted advise me , but i really don't know how to read (that was in the images links)

I'm gonna try windows in safe mode to run chkdsk /f  as dino says to see if that helps, and tell you what happen

thank you all

---

### Post by oldfred on 2020-05-26
While you have to use your Windows repair flash drive or installer to fix Windows, it also looks like you made it too small.
Windows NTFS needs 30% free to run well. At 10% free, it can take forever to run a defrag. You have even less.

Windows 10 repair disk
[https://askubuntu.com/questions/1156795/windows-hard-disk-read-only-now-windows-is-removed?noredirect=1#comment1925839_1156795](https://askubuntu.com/questions/1156795/windows-hard-disk-read-only-now-windows-is-removed?noredirect=1#comment1925839_1156795)
[https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html](https://www.tenforums.com/software-apps/27180-windows-10-recovery-tools-bootable-rescue-disk.html)
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)
Rescatux live cd with a grub restore option (through rescueapp) fixed it!
Will now repair Windows BIOS & UEFI
[https://askubuntu.com/questions/1058806/tried-to-install-both-windows-and-ubuntu-now-neither-will-boot](https://askubuntu.com/questions/1058806/tried-to-install-both-windows-and-ubuntu-now-neither-will-boot)

You may also have left Windows fast start up on. Then Linux will not correctly see the NTFS partition(s).
Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

---

