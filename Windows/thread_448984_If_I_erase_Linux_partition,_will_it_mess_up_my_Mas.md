---
title: "If I erase Linux partition, will it mess up my Master boot record?"
date: 2007-05-19
forum: Windows
---

### Post by Zaosyn on 2007-05-19
If I erase my Linux partition will it mess up my master boot record with Windows?

---

### Post by taurus on 2007-05-19
Yip since GRUB can't find /boot/grub/menu.lst.  Therefore, you need to boot your machine with Windows CD and fix MBR so you can boot from Windows again.

---

### Post by xpod on 2007-05-19
Just use the recovery console of your XP cd to do a"fixmbr"
Or if you dont have an XP cd get a 98 bootdisk or similar with the fdisk utility on it and do a 
"fdisk /mbr".

That should do the job:)

EDIT:Taurus is always so much quicker than me.:-)

---

### Post by Malibu Illusion on 2007-05-19
If you're running a bootloader such as GRUB, obviously it will not run because you'd be deleting it.

You can restore the Windows MBR by loading up a Windows XP disk, opening up a recovery console and typing: fixmbr.

If you can't do that, you may want to check MbrFix application:

[http://www.sysint.no/en/Download.aspx](http://www.sysint.no/en/Download.aspx)

Documentation:

[http://www.sysint.no/nedlasting/mbrfix.htm](http://www.sysint.no/nedlasting/mbrfix.htm)

Take care.

---

