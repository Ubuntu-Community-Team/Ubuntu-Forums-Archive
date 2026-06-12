---
title: "Missing BootMGR after running Boot-Repair"
date: 2015-01-16
forum: Windows
---

### Post by andy118 on 2015-01-16
Hello, i'm new to ubuntu. I had problems with my notebook HP Mini 110, wanted to reinstall win7, but something wrent wrong and it didn't boot anymore, always displayed a systemfile error and rescue grub. so i downloaded bootrepair and mounted it on a usb stick, booted the notebook and went all the points through, now it gives me an Missing BootMGR error, pleas can anyone help me, thank you!

the link from bootrepair:
[http://paste.ubuntu.com/9761361](http://paste.ubuntu.com/9761361)

thank you!

---

### Post by oldfred on 2015-01-16
Moved to Other OS, since Windows.

Boot-Repair can only fix minor Windows issues. You generally need your Windows installer or a Windows repair flash drive.

Your system seems to have promoted the flash drive to sda, and the 160GB drive as sdb. 
But the summary report does not show any Windows boot files in sdb1, one of those boot files is bootmgr, so error report is correct.

       [http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)

---

### Post by andy118 on 2015-01-16
thanks for prompt answer! already tried sr, but it can't find a previous system and still the same problem, trying to install win xp, can't find the hard disk... now i will try to install winxp with sata drivers integrated (nlite), maybe it will work... i hope so!

---

### Post by oldfred on 2015-01-16
XP is so old, and now your cannot update it as the download sites are closed. A lot of drivers then will not be available for any newer system.
Best not to use XP.

---

### Post by andy118 on 2015-01-16
i tried, but nothing to do, still says no disk to install, with a win7 image it says missing operating system

---

### Post by oldfred on 2015-01-16
Is then your Windows 7 an upgrade, not a full install? Upgrades have to see the previous install.

---

### Post by andy118 on 2015-01-16
solved!!!! created win xp iso with nlite integrating sata drivers! installation is running now!

---

