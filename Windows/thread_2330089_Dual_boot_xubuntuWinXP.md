---
title: "Dual boot xubuntu/WinXP"
date: 2016-07-07
forum: Windows
---

### Post by parasutist1 on 2016-07-07
Hi there,

got 200GB hdd. +- 150GB reserved via GParted for xubuntu 15.04. Another partition, +- 50GB, is formatted in ntfs. There i want to install Win XP - got iso.

But.

These methods i've tried:

Unetbootin - simply cannot boot, as there was nothing. 
Multiboot - after given command "boot" says that something must be done to the kernel, which i cannot find out at all, or it simply freezes
WinUSB - i can't even run this thing, simply nothing happens when trying to run
[http://askubuntu.com/questions/151073/how-to-create-windows-xp-liveusb-using-ubuntu-to-replace-it](http://askubuntu.com/questions/151073/how-to-create-windows-xp-liveusb-using-ubuntu-to-replace-it) - post from "upapilot" - when i select flash drive to boot i get only black screen with "_" flashing.

Is it only my programming noobiness what's causing the trouble? 

You, who actually reads this, can you help me, please?

---

### Post by uNoubu8a on 2016-07-07
Hi,

Sorry if I am misunderstanding your intentions:

[LIST]
[*][s]Do you plan to install Windows XP (note it is no longer receiving updates from Microsoft so this is not recommended) on the 50GB partition you have set aside on your HDD?[/s] - Obviously that is the goal, sorry :P
[*]You also mention you have an XP ISO.  Are you trying to create a bootable device using the Windows XP ISO?
[*]Where you able to successfully do all the steps in the askubuntu thread you posted to make a bootable Windows XP USB drive?
[/LIST]

I am unable to follow when you where getting which issues and what you where trying to do when you got them, sorry :confused:



Cheers
404

---

### Post by parasutist1 on 2016-07-07
1.: sure i do
2.: As i said, when i do the first method adviced: i copy the files from iso to that usb (just as-is, no single folder for everything, separated). Then i ran that command - returns "Windows 2000/XP/2003 master boot record successfully written to /dev/sdb". Then after booting that usb i got black screen with "_" flashing in upper left corner, nothing happens, it just keeps flashing 15+ minutes

Second method: WinUSB doesnt even start. 

Third method: alright, havent tried that, but i'm not rly sure it will lead to something, since i don't really get it. But will try it tommorow
Fourth method: alrdy got VM (win xp; from that iso, virtualbox) and it takes 20 minutes just to boot. And worked around shared folders, and got nothing at all, so i guess it won't work either 

Hope you somehow understand me :D

---

### Post by uNoubu8a on 2016-07-07
Hmmm... from what I can find online Windows XP doesn't officially support installation from USB and most methods (especially under Linux is reporting mixed results).  If you have access to a Windows machine you could try [Rufus]("https://rufus.akeo.ie/") which I saw mentioned as able to create a bootable Windows XP USB (it is an awesome application).

Most threads and links are older (as installing XP has fallen out of fashion) so perhaps there is a more up-to-date method available that I am not aware off.



404

---

### Post by yancek on 2016-07-07
The unetbootin home page specifically states that it will not work on "non-Linux" system which would include windows xp, of course.
Multiboot works with newer versions of windows, at least 8 and 10 and probably 7 although I haven't tried 7.  Doubt if it will work with xp and as stated above, I'm not sure it is even possible to boot xp from a usb.  You might find better info at the microsoft site or a windows forum.

---

### Post by oldfred on 2016-07-07
You cannot just copy files. You have to have formatted drive and installed Windows boot loader.
And Windows in BIOS mode only installs to MBR partitioned drives, and must installed into a NTFS formatted primary partition with the boot  flag.

XP also will not work with AHCI which now is really recommended. You may be able to find old AHCI driver somewhere and need to slipstream it into the install to use AHCI. Just about impossible to add driver after install.
My new SSD 4 or 5 years ago required AHCI, and I found XP did not work. Going into BIOS to turn that on/off became just too much so I then shut XP down. Best thing ever not to have XP.

---

### Post by parasutist1 on 2016-07-08
The fun part of this is, that i can't find my 16gb flash disk, so i can use only 4GB one :( And also, i actually never thought i will have ubuntu. My old disk with Win10 is working only when he wants to, so i had to get another. Tried installing Win7+8, but all installations failed with the same error, which i already tried to fix, but nothing happened at all..

---

### Post by oldfred on 2016-07-08
Some Windows links. If system runs Windows 10, may be best to stop fighting Microsoft and just install it, if you want or need Windows.
And XP is to the point of being dangerous to use on Internet. It has no updates and is the system that is attacked the most.

 How to: Create a Recovery Drive for reinstalling Windows 10 from Windows 10
[http://answers.microsoft.com/en-us/windows/wiki/windows_10-win_upgrade/how-to-create-a-recovery-drive-for-reinstalling/58df9c7d-84de-4652-9952-8bac34abc6c5](http://answers.microsoft.com/en-us/windows/wiki/windows_10-win_upgrade/how-to-create-a-recovery-drive-for-reinstalling/58df9c7d-84de-4652-9952-8bac34abc6c5)
Repair/backup/restore
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options) 
      
 Windows 10 ISO
[https://www.microsoft.com/en-us/software-download/windows10ISO](https://www.microsoft.com/en-us/software-download/windows10ISO)
Windows 10 repair disk
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)

---

