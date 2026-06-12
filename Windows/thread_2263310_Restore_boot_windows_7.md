---
title: "Restore boot windows 7"
date: 2015-01-31
forum: Windows
---

### Post by kvin2 on 2015-01-31
Hi,

i would like to restore the default mdr of windows 7, but it dose not work. If i restore grub it work's.
See the boot repaire log :
[http://paste.ubuntu.com/9963290/](http://paste.ubuntu.com/9963290/)

Thx!

---

### Post by oldfred on 2015-01-31
Moved to Other OS.

Can you boot Windows from grub? Grub only boots a working Windows.

But your Summary report shows a Windows boot loader which should directly boot Windows. 
Can you press f8 from BIOS to get into Windows repair console and run Windows repairs 3 times?

---

### Post by kvin2 on 2015-01-31
Yes i can on windows boot from grub, and i have try windows repair 3 time, but it dose not work.
Thx

---

### Post by oldfred on 2015-01-31
Then what is the problem?
If grub boots Windows, then the Windows boot loader in the MBR should boot Windows.

Or did you let Boot-Repair move boot flag from sda1? 
Windows boot loader uses boot flag. Grub does not.

---

### Post by kvin2 on 2015-02-01
I don't sur i handustand your question. (Sorry i'm french and don(y speek very well english)
I juste launch boot repaire et configure it to set boot windows.
When i do it at boot it stay blick on a black screen.

---

### Post by oldfred on 2015-02-01
There is a French forum, which you may understand a bit more. Not sure how active it is.
 French Forums
 [www.ubuntu-fr.org](www.ubuntu-fr.org)

Grub only boots working Windows. And Boot-Repair can only do minor fixes to Windows, like a Windows type boot loader in MBR.
You really need a Windows repairCD or flash drive or your original Windows install DVD if you have one.

      
 How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

