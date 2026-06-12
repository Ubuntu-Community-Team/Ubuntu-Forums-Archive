---
title: "How to Upgrade from XP to windows 7 on a dual booted system?"
date: 2014-02-02
forum: Windows
---

### Post by asiancraig2 on 2014-02-02
I have a dual booted system with XP and ubuntu.  I want to upgrade only the xp partition to windows 7.   is this possible?  would this break the system? Could i still boot?  i would i need to reinstall and modify grub to work with windows 7?  Thanks.

---

### Post by Bucky Ball on 2014-02-03
Upgrade Windows, boot from the Ubuntu install disk and choose 'Try Ubuntu', open a terminal and run this command.

```
sudo grub-install /dev/sda
```

Reboot and all should be well. If not, Boot Repair is your friend:

Get Boot Repair:
[http://sourceforge.net/projects/boot-repair/?source=directory](http://sourceforge.net/projects/boot-repair/?source=directory)

Use BR:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Yannbuntu's thread:
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

---

### Post by asiancraig2 on 2014-02-03
BTW, what i meant by "upgrade" is actually reformat and re-installation

---

### Post by mips on 2014-02-03
Bucky Ball's post still applies even if you format and reinstall.

---

### Post by Bucky Ball on 2014-02-03
> **mips said:**
> Bucky Ball's post still applies even if you format and reinstall.

+1. Either way.

---

### Post by mastablasta on 2014-02-04
except you reformat only winxp part not the whole disk...

---

### Post by asiancraig2 on 2014-02-04
> **mastablasta said:**
> except you reformat only winxp part not the whole disk...

Off course lol....

---

### Post by mips on 2014-02-04
> **mastablasta said:**
> except you reformat only winxp part not the whole disk...

That's like stating the obvious :D

---

### Post by mastablasta on 2014-02-05
well windows might want to erase it all (or at least "to solve the problem of unformated disk space"). i don't know how install works in 7

---

