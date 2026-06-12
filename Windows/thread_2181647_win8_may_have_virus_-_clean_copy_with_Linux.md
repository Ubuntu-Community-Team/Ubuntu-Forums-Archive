---
title: "win8 may have virus - clean copy with Linux?"
date: 2013-10-18
forum: Windows
---

### Post by FerryGnu on 2013-10-18
Hi All,

OK, I know this is not a win8 forum, but please read on...

My laptop has been acting weird and is frequently accessing the Internet when I launch programs. These are programs I have written and compiled myself and they have no functions or needs to access the Internet.

The firewall has asked permission to access the Internet and I have blocked them.

I am thinking of going to a full win8 factory restore and then transfer over my source code and recompile. But, my concern is that I may be transferring the virus/Trojan etc over during the copy-process.

I am thinking of using an older laptop booted with a Linux-live CD and then transfer the stuff across so hopefully the problem stuff will not get copied across.

Any thoughts, suggestions or ideas?

Thanks

---

### Post by Toz on 2013-10-18
*Moved to the **Other OS/Distro Support** forum.*

---

### Post by hhWnd8K on 2013-10-18
I am not aware of any virus's that can transfer from a Windows system to a Linux system and cause problems. However you can carry over programs/files from Windows to Linux and back to your fresh Windows and re-infect yourself. I would do the brutal windows scans and clean ups to get windows back in shape if you plan on moving files/programs back and forth.

---

### Post by Bibek on 2013-10-18
windows and linux are completely different operating systems so a windows virus or executable is not able to run on linux. i would recommend installing a good anti virus program on windows and scan before copying your files over after factory restore. this way the antivirus will hopefully catch any virus that you may have copied to your backup.

---

### Post by Habitual on 2013-10-18
take yourself out of the Administrators group and logout, then copy|compile....

---

### Post by FerryGnu on 2013-10-19
Thanks for the suggestions. I have been using Security Essentials and also did a scan with MBAM and they showed nothing untoward.

It is certainly strange requesting access to the Internet so not sure what might be going on there.

I am now running wireshark in the hopes of back-tracking to see what might be happening.

---

### Post by Bucky Ball on 2013-10-19
What makes you think they won''t get copied across? Just because Linux won't recognise them and there won't be any damage done, the moment the files are back on a Windows machine, nothing's changed. Linux hasn't miraculously cleansed anything. The file is *_exactly_* the file that left the original Win machine.

Point is, virus was written for Win, on Linux machine still there but makes no difference, transfer back to Win, same file, same virus. Not written for Linux so Linux oblivious. This does not make it not there.

---

### Post by danielr2 on 2013-10-19
> **FerryGnu said:**
> Thanks for the suggestions. I have been using  Security Essentials and also did a scan with MBAM and they showed  nothing untoward.

It is certainly strange requesting access to the Internet so not sure what might be going on there.

I am now running wireshark in the hopes of back-tracking to see what might be happening.

I recently had a similar situation on my Windows XP disk. Strange  network access and one core was always busy at 100%. Also had Security  Essentials as AV engine. To cut a long story short, I had to scrap my  Windows installation, destroy my partitions, format the drive and set it  all up from scratch. First, I tried a restoration without destroying my  partition setup. The malware was back the next day. I guess I caught  some nasty piece of software hiding in my boot sector or MBR.  Fortunately, I still had my old HDD with a virus free installation from  that laptop so I could clone that to save some work and efforts. 

In this situation, Security Essentials was plain useless. Also, none of  the online virus scanner detected anything. I used House Call and Panda.  Fortunately all user files and documents were clean. So those could be  saved and loaded back to the "new" installation. Presently, I am running  free Avira AV on my WinXP disk and the system is clean. I'm not sure if  Security Essentials is a real good AV engine, but than which one is?  None of them offer 100% protection, not even the commercial ones. 

With luck, your files might be clean. Try moving them to an external  drive and scan them on a clean system with a good AV engine and current  virus definition file(s). You should destroy infected files, if any are  found. Repairing often fails and leaves infected files on your system.

---

