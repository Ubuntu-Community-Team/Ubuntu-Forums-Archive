---
title: "Ubuntu installer does not see windows 8.1 or free space."
date: 2013-09-19
forum: Ubuntu Development Version
---

### Post by Hewjr100 on 2013-09-19
Here is the situation, I have windows 8.1 build 9471 with a custom install.  Created only one partition which is c drive.  Shrunk partition by 160 GB.  Booted into ubuntu 13.10 daily 9/19 and selected install Ubuntu.  When the installer came up it did not see windows 8.1 or free space.  Just to make sure, I rebooted into live system and sure enough windows was there.  So why can't the initial boot into install option not see windows or free space.  Also tried to install from live, but nothing happens, click on install Ubuntu and the launcher icon just fades in and out, no installer window pops up.

 

 Henry

---

### Post by cariboo on 2013-09-19
Are you using the manual partitioner (something else)?

---

### Post by Hewjr100 on 2013-09-19
Don't think so, in live cd I just click on install ubuntu 13.10 icon both on launcher and desktop.

Henry

---

### Post by cariboo on 2013-09-19
You may want to try the manual partitioner, to see if your Windows partitions are detected properly, You can select by clicking Something Else.

---

### Post by Hewjr100 on 2013-09-19
Actually I went ahead and rebooted to install ubuntu, when I attempted to install I got a message about gpt and fake dos.  Windows can really get me peeved.  Anyway I ran gparted live and blew windows off.  Currently I am running ubuntu 13.10 only.

Tommorrow I wil try reinstalling windows and try again.  I beleive the problem is with windows 8 oem image, whenever I custom install windows 8.1 over windows 8, I get the gpt fake dos error message.  If I remember, last time this happened I installed windows 8.1 over ubuntu. This should solve the problem. Then I will be able to dual boot.

Henry

---

### Post by grahammechanical on 2013-09-20
It seems to me that you are having the usual sort of problems that people have when installing Ubuntu with Windows 8 pre-install. These issues may not specifically be 13.10 related. Is this the first time you have tried to install Ubuntu with Windows 8? There many threads in the other sections of the forums about doing this. There often are complications.

1) Fast boot needs to be turned off
2) If Windows boots in EFI mode, then Ubuntu has to be installed in EFI mode
3) Ubuntu 12.04.2; 12.10; 13.04 and 13.10  can install with secure boot enabled.
4) We must be using 64bit Ubuntu as the 32bit Ubuntu installer does not recognise EFI/UEFI

That is the little bit that I have picked up from reading those other threads.

Regards.

---

