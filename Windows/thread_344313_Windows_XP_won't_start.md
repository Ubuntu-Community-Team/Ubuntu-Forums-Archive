---
title: "Windows XP won't start"
date: 2007-01-22
forum: Windows
---

### Post by le_vainqueur on 2007-01-22
I'm not sure if this is where I should put this thread, so please feel free to move it as you see fit.

I have been dual booting for the past 3 or so months with Ubuntu Edgy and Windows XP with little difficulty.  I have two hard drives, one 40GB as a Windows hd, and one 160GB with a 40GB Linux partition and a 120GB shared partition.  

Today I was ripping a CD in Windows when my computer froze.  I tried  CTRL-ALT-Del several times waiting for several minutes each time.  There was absolutely no detectable response, so I reset my computer manually.  When Windows tried to restart, it only got as far as the Windows loading screen with the scrolling bar, and then restarted again.  It gave me the opportunity to start in safe mode (3 options), with the last known configuration, and normally.  I tried all of them, and they each had the same effect.  When I tried to start in safe mode the loading stopped on the prompt

> multi(0)disk(0)rdisk(0)partition(1)\WINNT\SYSTEM32\DRIVERS\agp440.sys

Then it restarted as with the other options.  This led me to believe that there was an error loading my video card.  I removed the video card, and tried restarting...same effect.  I also tried to remove the Linux hard drive and restart, but that didn't work either.  Fortunately I can still run Ubuntu without complication.  

Any advice?

---

### Post by Coelocanth on 2007-01-22
[Check This](http://support.microsoft.com/kb/324764) from the Microsoft Help and Support site.

Sounds like a driver issue.

---

### Post by le_vainqueur on 2007-01-22
Thanks for the link.  I have already run into a problem, though, that I experienced during other troubleshooting.  Step 1 calls for inserting your Windows XP disk.  Well, I inserted my restore disk from Gateway, and tried to navigate through it.  I tried to find some way to repair Windows, essentially.  The problem is, when I try to go into the Windows installation menu (which I assume is the equivalent of inserting an XP disk) it tells me that I cannot do this since my file system is NTFS.  This strikes me as odd since my computer was NTFS by default.  I have never changed it.  The menu says that I must first erase the disk, since it is NTFS, before I can continue.

On another note, I have come across another error while trying some things of my own.  The error is:

> UNMOUNTABLE_BOOT_VOLUME

TECH. INFO:
***STOP: 0x000000ED (0x82F65849, 0xC0000006, 0x00000000, 0x00000000)

---

### Post by riven0 on 2007-01-22
Agh! I hate stop errors. They were the bane of my existence. :evil: 

It's incredibly strange that your XP CD is telling you it can't repair because of the NTFS format. XP *is* based on NTFS! What is it talking about???

In either case, when you get to the main menu, select **To setup Windows XP now, press ENTER**. Now accept the EULA, then it will take you to the installation screen. Choose your partition and hit **R**. It should start the repair as long as there is nothing wrong with the cd.

---

