---
title: "Dual Boot and Microsoft kb3033929"
date: 2015-03-12
forum: Security
---

### Post by pfeiffep on 2015-03-12
Today my dual boot HP desktop needed 13 updates for Windows 7, subject failed to install.
After some research I found it's suspected that some dual boot Linux / Windows machines refused to install this update.
I also have a dual boot Dell laptop that installed this update successfully. 

Over all I'm not too worried about the failure on the HP since I don't use Windows 7 very often.

---

### Post by bashiergui on 2015-03-14
The best outcome for that one was it failed to install. The patch put some dual boot computers in endless reboot loops. Here's an unofficial workaround
[http://www.idigitaltimes.com/how-fix-windows-7-update-reboot-loop-problems-microsofts-kb3033929-patch-causing-422816](http://www.idigitaltimes.com/how-fix-windows-7-update-reboot-loop-problems-microsofts-kb3033929-patch-causing-422816)

---

### Post by pfeiffep on 2015-03-14
Since I don't believe that subject kb affected and user computers I ignored just that 1 update on just 1 machine.

---

### Post by Habitual on 2015-03-18
> **bashiergui said:**
> The patch put some dual boot computers in endless reboot loops.

I had similar issue with  KB3002657

---

### Post by pfeiffep on 2015-03-25
Update ... 
Recently I choose a Western Digital My Cloud and a My Book Studio to serve as a single point backup for my household's computers. The system was setup rather easily but I did have some learning / unlearning to tackle. Bottom line is that I was successful:
          * Dell Studio Laptop both Windows 7 and Linux       
          * Mac Book Pro Time Machine       
          * HP Desktop Linux       using Deja Dup (named Backups in the menu system)
          * Dell Inspiron Laptop Linux

What was missing out of this was the HP dual boot Linux and Win 7 I was unable to use WD Smartware on this computer. While trouble shooting I remembered that Win 7 was installed on the internal SSD and Linux was installed on the internal HDD and I had set the bios to boot to the HDD which had grub installed. 

When I changed the bios boot selection to SSD, repaired the MBR using testdisk, and then booted DIRECTLY to Windows I was able to install the subject, and use WD smartware successfully.

Bottom line is if you have 2 separate hard drives and want to have a dual boot system with Linux, as long as your bios can select a primary boot device other that the first listed,  it's probably a really good idea to install Grub on the Linux drive and let it select booting Windows if needed. 

In the _unusual_ situation that you need to boot DIRECTLY to Windows you have maintained that option by adjusting bios settings.

---

