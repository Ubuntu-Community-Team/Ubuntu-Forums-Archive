---
title: "Troubles installing vista..."
date: 2008-09-11
forum: Windows
---

### Post by ursoouindio on 2008-09-11
Hello all,

 

I am having some big troubles installing Vista on my Dell Inspiron 1525 and I will try to explain it the best way. I suspect that maybe Ubuntu has something to do with it. My configuration is Core 2 Duo T7250, 4  GB ram and 160 GB 7200 rpm hard disk.

 

I was running Windows XP SP3 and Ubuntu 8.04, with 2 NTFS and 2 EXT3 partitions. At first, I created a primary partition C: with 10 GB and another partition (which I believe was logical) for my documents, D: with 100 GB. Then, installed Windows XP, without any troubles at all. Then installed Ubuntu, creating 2 partitions (primary ones, I believe) for the system and files occupying the last ~40 GB from my hard disk. Ubuntu also creates a menu on the system start to boot from it or from Windows (GRUB).

 

It was running fine, but I decided to give Vista a chance. Backed-up everything I got on the hard disk because I realized that I would need to change the sizes from the partitions C: and D:. So, installed Partition Magic and tried to resize C: to 20 GB and D: to 90 GB. It asked to reboot and then executed its work, but some error happened and it didn't work.

So, decided to just delete both NTFS partitions and create a new one, using Windows Vista disc.

Not luck.

I booted my notebook from Vista DVD, it reads the necessary files to begin, goes quickly through the green-passing-bar screen and to the "Vista-green-background" screen. I noticed that the mouse cursor should appear here but it doesn't. Some seconds later appears a window asking about the language and I don't have any way to interact with it. No mouse, no keyboard - no arrows, no Tab, no letters and even no NumLock change.

 

Tried it a couple of times but every time it was the same.

 

Returned to XP, did a quick look for on the web and it seemed that could be due to the partitions structure or something. So i thought that Ubuntu messed up this settings on my hard disk when I installed it. 

Didn't thought twice, restarted my pc, changed the SATA configuration on the Bios and booted from the Windows XP CD. On the formatting part, deleted everything. Created just one NTFS partition (I intend to create another one after successfully install Vista), occupying 120 GB, with 40 GB to further Linux installation.

 

Tried boot Vista installation again, with AHCI or SATA setting, but the result are exactly the same as before.

 

Next tried is to install Windows XP and run Vista installation from it.

Just finished to install XP and opened Vista setup (at this point, AHCI is disabled on the Bios). It now runs through step 1 (collecting information) and starts step 2. It copy the files and start to decompress it. It asks to restart and when it boots the installation, it quickly shows the "Blue screen of death". It says something about some error with incompatible hardware or error with the disk. The support code starts with ***STOP: 0X0000007B.

 

With a rest of  patience, I decided to load the new XP and install all the drivers, including the AHCI. Changed the Bios from SATA to AHCI and tried again to run Vista setup from XP but the result was the same as the last.

 

Then, picked up Ubuntu cd and installed on the end of the hard disk. I am using it right now, but have a windows frankenstein on the rest of my hard disk. 

 

At this point, I can delete any partition (start from scratch) on this laptop in order to get Vista and Ubuntu working. 

 

My major question is why it freezes like that when trying to install Vista booting from its DVD. I believe it should not happen like this and the only differential I got over "normal" pcs is Ubuntu. 

I would like to delete all the partitions and start over again like I did on the middle of the description above. Then, I would install Ubuntu again. But any other suggested procedure is welcome!



Thank you very much to everyone that read it all, I believe that people with more experience installing Vista on this kind of computers can help. I never installed Vista on any PC, just on virtual machines.

 

Best regards,
Marco

---

### Post by Izek on 2008-10-17
Windows XP Install CD **will** freeze if your [Master Boot Record]("http://en.wikipedia.org/wiki/Master_boot_record") is different than it would expect (not sure why Vista would). Ubuntu installs a different MBR it seems and Ubuntu's partition editor will NOT remove the MBR. You can get around it by using [Darik's Boot and Nuke](http://en.wikipedia.org/wiki/Darik%27s_Boot_and_Nuke) to wipe the entire drive and clear the MBR. I had to do it every time I wanted to go from X/Ubuntu to Windows XP on my laptop, not sure about your machine though.

---

