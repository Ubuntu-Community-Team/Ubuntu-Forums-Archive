---
title: "ext2/ext3/ext4 driver for Windows 8"
date: 2012-11-02
forum: Windows
---

### Post by wesli_1 on 2012-11-02
Hi

Just wondering if there is a ext2/3/4 driver available that works on Windows 8?

I have tried [http://www.ext2fsd.com/](http://www.ext2fsd.com/) but it does not (yet) support Windows 8.

30mins of google searching has been absolutely fruitless.

Cheers,
Wesli_1

---

### Post by papibe on 2012-11-02
Thread moved to **Other OS/Distro Talk **.

---

### Post by oldfred on 2012-11-03
I would not write from Windows as it does not support ownereship nor permissions. I think some of the drivers were read only.

We normally suggest a separate NTFS data shared partition. The Linux NTFS driver exposes all the Windows files including the normally hidden ones. Better to set the Windows system or c: drive as Read Only and use a shared data partition for any data you may want in both systems.

Be careful of Windows fast boot.

WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by kiyop on 2012-11-03
1 minutes googling has found:
[http://www.forumswindows8.com/general-discussion/can-windows-8-read-files-ext3-partitions-621.htm#post13853](http://www.forumswindows8.com/general-discussion/can-windows-8-read-files-ext3-partitions-621.htm#post13853)
[http://sourceforge.net/projects/ext2read/](http://sourceforge.net/projects/ext2read/)

---

### Post by mips on 2012-11-04
You can try [http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

Even though it does not mention Win7 or Win8 I know it works in Win7.

---

### Post by monkeybrain2012 on 2013-07-16
Why would you even want to access Linux file system form Windows? Windows needs to be quarantined.

---

### Post by Op3rat0r on 2013-08-07
Hi,

ok long long ago. But I tried to install Ext2fsd on my Windows 8 and everything ist OK ;)
Only compatibility mode to Windows 7 and a restart.
From then on I can read and write to my Ext2 formated HDD.

Have fun

> **wesli_1 said:**
> Hi

Just wondering if there is a ext2/3/4 driver available that works on Windows 8?

I have tried [http://www.ext2fsd.com/](http://www.ext2fsd.com/) but it does not (yet) support Windows 8.

30mins of google searching has been absolutely fruitless.

Cheers,
Wesli_1

---

### Post by jspencerseiler on 2014-01-02
I cannot find anything either, if you manage to find something workable let me know please.

> **kiyop said:**
> 1 minutes googling has found:
[http://www.forumswindows8.com/general-discussion/can-windows-8-read-files-ext3-partitions-621.htm#post13853](http://www.forumswindows8.com/general-discussion/can-windows-8-read-files-ext3-partitions-621.htm#post13853)
[http://sourceforge.net/projects/ext2read/](http://sourceforge.net/projects/ext2read/)


These didn't provide workable solutions.

---

### Post by Bucky Ball on 2014-01-02
Shared NTFS partition best, as suggested. The rest is flaky and always have been (although some people seem to get a result). Development of such a thing for Win8? Hmm.

---

### Post by ahobo on 2014-01-08
Run it in Compatibility Mode -- Windows 8 can use Windows 7 drivers.

Right click > Properties > Compatibility (Tab) -- Checkbox, and select Windows 8.
After the installation, I went into C:\Program Files\Ext2fsd installation folder, and did the same for the Ext2Mgr.exe file, and also selected "Run as Administrator" at the bottom.
After you the install, you will probably have to reboot to get it to recognize.
Otherwise, it works fine for me in 8.1

---

### Post by usuarioforos on 2014-01-12
Hi ahobo, please can you confirm in the first step the file in that you do "[COLOR=#000000]Run it in Compatibility Mode -- Windows 8 can use Windows 7 drivers." and what program you execute?
[/COLOR]

Thanks

---

### Post by Bucky Ball on 2014-01-12
> **Bucky Ball said:**
> Shared NTFS partition best, as suggested. The rest is flaky and always have been (although some people seem to get a result). Development of such a thing for Win8? Hmm.

If you're working with anything other than EXT2 partitions this could be probematic. Could be problematic anyway.

---

### Post by usuarioforos on 2014-01-12
Hi, I can solve yet. Only is for test, I have to modify a file in a ext2 USB memory with linux for after boot of this usb memory. I have to do the modify of this file with Windows tools, there aren´t the same tool for linux.

If works, always will be in te usb for boot, not is important information but is the fastest method for do this test.

For things like this it is practical can be it so. After boot with linux all process will be do with Linux directly, **but sometimes when the utils is in windows you is needed to use this workarounds becouse not is possible from other way**. If this could be problematic you can uninstall the ext2 after do the change you need.

I can´t do becouse I had downladed the zip file (I not like the installers) so I can´t change the compatibility mode, but with .exe installer, works good, only you have to download the .exe version  [Ext2Fsd-0.51.exe (1.0 MB)]("http://sourceforge.net/projects/ext2fsd/files/latest/download?source=files") and then to the process that say Ahobo:

> Right click > Properties > Compatibility (Tab) -- Checkbox, and select Windows 7.
After the installation, I went into C:\Program Files\Ext2fsd installation folder, and did the same for the Ext2Mgr.exe file, and also selected "Run as Administrator" at the bottom.

After you the install, you will probably have to reboot to get it to recognize.
Otherwise, it works fine for me in 8.1

Regards

---

### Post by arekram on 2014-01-15
Hi, I found a tool that works on Win 8.1. 
[http://www.paragon-software.com/home/extfs-windows/](http://www.paragon-software.com/home/extfs-windows/)

you need to register before using it.

---

### Post by Dave_Burton on 2014-08-10
> **usuarioforos said:**
> ...only you have to download the .exe version  [Ext2Fsd-0.51.exe (1.0 MB)]("http://sourceforge.net/projects/ext2fsd/files/latest/download?source=files") and...

A new version 0.52 of Ext2FSD was released May 11, 2014.  The first improvement listed in the change log is "[COLOR=#333333]Feature: Windows 8 supported."

[/COLOR]See: [http://www.ext2fsd.com/](http://www.ext2fsd.com/)

---

### Post by Bucky Ball on 2014-08-10
***Thread closed.***

Well old thread. Info given now may be irrelevant. Things change in the world of technology. Best bet? EXT* has never really worked well in Win. You can trick it, but not native, only ever going to be a workaround (unless there is some miraculous change of heart regarding MS and open-source). 

As suggested, if dual-booting and wanting to share a partition, just create an NTFS partition and job done. Good luck to all. ;)

---

