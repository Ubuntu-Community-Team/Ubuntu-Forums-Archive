---
title: "Problems post linux installation"
date: 2017-05-04
forum: Ubuntu/Debian BASED
---

### Post by bobbybka on 2017-05-04
This is a bit of a long shot but this forum is pretty active so i decided to post here.

I've been trying to install kali linux along side windows 7 dual boot for the past few days and by now have half broken my system.
I first tried installing linux on a separate partition on my hard drive that had windows on it, but that never worked
After using a partitioning tool to merge all the gigs on my hard drive back, it effectively broke windows, and on bootup i got an error on a black screen that said something like "cant read disk"
I happened to have a second hard drive with nothing on it and tried installing kali there and thats how im typing this now, it worked.
however i have no idea how to boot up back from the windows hard drive and get that "cant read disk" error again.
I wish to recover the windows 7 side of my computer and set up the dual boot system I've been trying to get working.

I'm sure i left out alot of important details pertaining to explain the issue, and i apologize for my ignorance, I'm very new to the Linux world, if you need any specific info about my system or such, of course ask

---

### Post by wildmanne39 on 2017-05-04
*Thread moved to **Ubuntu/Debian BASED**.*

---

### Post by oldfred on 2017-05-04
That is mostly a Windows issue. 
You probably need to use your Windows repair disk's repair console to fix Windows.
After any resize it also needs chkdsk, which you can only run from Windows, not any Linux.

       Windows Repair Console ------------
f8 to get to repair install screen, if you can start to boot
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
[http://www.sevenforums.com/tutorials/666-advanced-boot-options.html](http://www.sevenforums.com/tutorials/666-advanced-boot-options.html)
[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)
[https://support.microsoft.com/en-us/kb/927392/](https://support.microsoft.com/en-us/kb/927392/)

Once you get Windows working, you should be able to update grub to include it in its menu. But best to keep Windows boot loader on Windows drive and grub on Linux drive. Do not know Kali but with Ubuntu you would do this:
sudo update-grub

---

### Post by oldos2er on 2017-05-05
> **bobbybka said:**
> I've been trying to install kali linux along side windows 7 dual boot

Have you seen [http://docs.kali.org/introduction/should-i-use-kali-linux](http://docs.kali.org/introduction/should-i-use-kali-linux), specifically 

"As the distribution&#8217;s developers, you might expect us to recommend that  everyone should be using Kali Linux. The fact of the matter is, however,  that Kali is a Linux distribution specifically geared towards  professional penetration testers and security specialists, and given its  unique nature, it is **NOT** a recommended distribution if  you&#8217;re unfamiliar with Linux or are looking for a general-purpose Linux  desktop distribution for development, web design, gaming, etc." ?

---

### Post by bobbybka on 2017-05-05
yes i am fully aware this is a bad idea but I'm determined to see it through.

---

