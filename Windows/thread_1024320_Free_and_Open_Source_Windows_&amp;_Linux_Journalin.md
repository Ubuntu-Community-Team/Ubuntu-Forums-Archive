---
title: "Free and Open Source Windows &amp; Linux Journaling File System"
date: 2008-12-28
forum: Windows
---

### Post by Grant A. on 2008-12-28
Does anyone know if there is a Free and Open Source Journaling File System that works 100% on both Windows and Linux? The ext2 driver totally ignores ext3's journal.

---

### Post by jrusso2 on 2008-12-29
This filesystem does not exist.  Windows can only be installed on NTFS or FAT 32 which is not recommended.  NT used to be able to be installed on the OS/2 filesystem HPFS but this was eliminated.

---

### Post by Grant A. on 2008-12-29
Well, I meant is there was a driver where I could use a Journaling Filesystem for files that would work in both Windows and Linux, not install the OS to it.

---

### Post by jrusso2 on 2008-12-30
You can read and write to NTFS from Linux with NTFS 3G or write from WIndows to ext 3 
[http://tombuntu.com/index.php/2008/03/19/four-applications-for-accessing-ext3-partitions-from-windows/](http://tombuntu.com/index.php/2008/03/19/four-applications-for-accessing-ext3-partitions-from-windows/)

---

### Post by fiddler616 on 2008-12-30
There's a driver for using Ext* in Windows--Google lin2fs, I think it is. The problem is that you can't boot off it--it needs to boot to load the driver, and to boot it needs the driver, which it doesn't have because...you get it. I suppose if you were really into this, you could make an NTFS boot-only partition, and keep all your apps/documents on Ext3, but I'm pretty sure there's a speed decrease.

---

### Post by Schok on 2009-01-04
I got the software Ext IFS and installed it in windows so i can read and write on my seperated /home partition from my ubuntu 8.10. The thing is, when i try to view the partition from "My Computer" there's an error that says:

 &#8220;The disk in drive X: is not formatted. Do you want to format it now?&#8221;

What should i do? According to the link given above, thru the comments, a guys said my ubuntu wasn't properly shut down. It was and i restarted a couple of times already. Is there any other way before I try out other softwares?

btw ive tried mountdiag.exe but it just loaded for 1 sec before it disappears..

---

### Post by cardinals_fan on 2009-01-04
It's really a shame.  I've been messing with XP lately, and my biggest gripe is the awful file systems.

---

