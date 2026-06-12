---
title: "Windows Black Screen"
date: 2007-08-23
forum: Windows
---

### Post by aitorcalero on 2007-08-23
I installed Ubuntu on my work laptop a month ago, with WindowsXP dual boot configured and working. At first both OS boot perfectly, but after some (most of time indeed ;) ) using Ubuntu, Windows does not start. After selecting windows in grub, it seems to load windows, but suddenly my screen gets completely black, no mouse pointer, no cursor, nothing.
The only thing I could think of that would have caused damage to Windows, was that I have installed nts3g to have write/read access to ntfs partitions.
I have also try to start it in fail safe mode and restore MBR, but after loading some sys files it (in this case) restart ](*,) 
I don't want to reinstall windows again, mainly because, it was installed by mi systems department (which do not support Linux, of course) :(
Can you give some clues, advices or whatever?
Thank you!

---

### Post by gashcrumb on 2007-08-23
If you can get your hands on a Windows XP CD boot up with it and select the "Recovery Console" option.  You'll need to know your admin password (or just hit enter when prompted if it's blank).  If you can read the C:\ drive then maybe all is not lost.  

Try hitting F8 while booting and select "Safe mode command prompt".  I think this logs each drive/system filer that's loaded, perhaps it'll provide some indication of a corrupt driver file, which you can replace using the recover console and either a floppy or a CD with the driver file burned on to it.

Still, I think you might wind up having to get the machine re-imaged by your systems department.  :-(

---

### Post by aitorcalero on 2007-08-24
> **gashcrumb said:**
> Try hitting F8 while booting and select "Safe mode command prompt".  I think this logs each drive/system filer that's loaded, perhaps it'll provide some indication of a corrupt driver file, which you can replace using the recover console and either a floppy or a CD with the driver file burned on to it.


I will try this, but I think that "Safe mode command prompt" does not work either. 
Thank you.

---

### Post by PointSource on 2007-08-25
Following on from gashcrumb, type "fixboot" into the recovery console, it might help.

---

