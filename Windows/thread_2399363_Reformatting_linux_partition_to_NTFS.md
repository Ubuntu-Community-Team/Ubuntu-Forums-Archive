---
title: "Reformatting linux partition to NTFS"
date: 2018-08-24
forum: Windows
---

### Post by Rion_Zion on 2018-08-24
Hi all, i have a lenovo x220 laptop with a dual boot system. Linux ubuntu was installed first, then i have windows 7 32bit on another partition.

I now want to reformat the linux partition so i can install windows 7 64bit instead of the ubuntu installation. I want to retain my current win7 32bit installation, and then have a fresh win7 64bit installation which i keep "clean" for audio and video software only. I'm not finding much use for ubuntu these days. 

I know how to do this, in theory at least, but my concern is that i will mess up my master boot record since the original first linux installation will be gone. At the moment the first screen i get is a linux screen where i choose either ubuntu or win 7. When i choose win 7 it then shows the windows screen where i get the choice between windows and ubuntu again (althouh if i choose ubuntu at this point it doesnt work).

Any advice? 

Thanks.

---

### Post by yancek on 2018-08-24
If you are using windows 7, it is most likely a Legacy/MBR system and yes, it will overwrite your current MBR.  You won't be asked or informed that this is happening during the install.  Windows 7 usually uses a separate boot partition so your new install will likely install the windows boot files to the boot partition marked as active and will overwrite the older windows 7 boot files.  Windows should detect the currently installed OS and create an entry for it in your boot menu.  If you want to keep your current windows and put the new windows on a separate partition, you will probably need to use a manual/custom install method where you can make that selection so you do not overwrite the current install.  I've never installed 7 so I don't know what options you will see.

```
Any advice? 
```

I would suggest going to the microsoft support forum or a windows forum as your question is windows related.

---

### Post by oldfred on 2018-08-24
Moved to Windows sub-forum.

Windows only boots from primary NTFS formatted partitions with boot flag if BIOS/MBR. If installing multiple Windows best to have both in primary partitions. Windows normally uses a separate Boot partition which starts boot process and has boot flag.

         To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words, shows Vista & XP but Windows 7 similar just with added boot partition.
[URL="http://www.multibooters.co.uk/multiboot.html"]http://www.multibooters.co.uk/multiboot.html
http://www.multibooters.com/guides/visual-guide-to-the-boot-sequence.html[/URL]
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

