---
title: "Partitioning my ubuntu HDD on my other windows PC"
date: 2013-08-14
forum: System76 Support
---

### Post by anthonytaro on 2013-08-14
I recently purchased a Pangolin PanP9 from System 76, upgrading from my custom windows 7 desktop. I need windows for programs that aren't compatible with wine from school, so i have to set up a dual boot on my new laptop. Since i cannot partition the drive ubuntu is currently running off of while it is running, i figured i would hook it up to my old PC and do it there. the default windows partition editor won't let me shrink what i have because it doesn't recognize the file system. It wants me to formaat (erase) the disk, which i obviously would like to avoid :P i either need a program that recognizes ubuntu, or a way to boot up my new laptop from a separate source and partition my HDD. any suggestions?

---

### Post by anthonytaro on 2013-08-14
[COLOR=#000000]I recently purchased a Pangolin PanP9 from System 76, upgrading from my custom windows 7 desktop. I need windows for programs that aren't compatible with wine from school, so i have to set up a dual boot on my new laptop. Since i cannot partition the drive ubuntu is currently running off of while it is running, i figured i would hook it up to my old PC and do it there. the default windows partition editor won't let me shrink what i have because it doesn't recognize the file system. It wants me to format (erase) the disk, which i obviously would like to avoid [/COLOR]:razz:[COLOR=#000000] i either need a program that recognizes ubuntu, or a way to boot up my new laptop from a separate source and partition my HDD. any suggestions?

i also posted this in the system 76 help forum, but looking at other posts it seems as though i will get a slow response time from the system 76 support team.[/COLOR]

---

### Post by oldfred on 2013-08-14
Use gparted from the Ubuntu installer or download a gparted repairCD with the very newest version. 

 [http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)

      
 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

To install Windows you need a primary (sda1 thru sda4) formatted NTFS with the boot flag. A few have had to reformat with the Windows 7 tools, but then the partition is seen.

---

### Post by oldfred on 2013-08-14
Duplicate threads merged. Please do not create duplicate threads.

---

### Post by isantop on 2013-08-15
Our systems ship Ubuntu with GPT partition tables, so you'll need to reformat your hard drive, install Windows, then reinstall Ubuntu. Alternatively, you can set up a Virtual Machine, which will let you run Windows programs without needing to reboot.

---

### Post by oldfred on 2013-08-15
Windows only boots from gpt with UEFI.

 GPT Advantages (older but still valid)  srs5694 post #2:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)

You may be able to convert, but have good backups just in case.

 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
You then need to use gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)


      
 Windows convert to MBR
[http://blog.paulgu.com/2008/01/06/how-to-delete-gpt-protective-partition/](http://blog.paulgu.com/2008/01/06/how-to-delete-gpt-protective-partition/)

---

