---
title: "removing ubuntu from dual boot"
date: 2010-08-08
forum: Ubuntu Moblin Remix
---

### Post by avix on 2010-08-08
asus EeePc 1001P. took win7 starter off and replaced with XP (some work required apps would not run under win7)

dual booted with ubuntu netbook remix. please find person who designed interface and force him to use windows ME for the rest of his life. totally unusable. installed ubuntu desktop. after 3 days of fiddling and searching finally got wifi to work (sort of, signal strenght 5 feet from wrt54G linksys is 2 bars)

screen light flickers, battery life poor. screen ratio made me put bars on autohide.  

bars now locked, can't access them at all, can't delete. can't change settings. can't use.

I never thought I would say this, but I need to remove ubuntu and just go with win XP on this box.

how do I remove ubuntu without having to reinstall XP?

---

### Post by KCormier on 2010-08-08
from a live boot, do the following in a terminal:

this should remove grub from the mbr, but leave your partition tables intact.  MAKE SURE you type 446.  A typo there could blow your entire partitions away and overwrite the data so that it is unrecoverable!
```
sudo dd if=/dev/null of=/dev/sdX bs=446 count=1
```

Turn swap off
```
sudo swapoff -a
```

Delete your linux partitions and resize XP
```
sudo gparted
```

That should do it for you!  Sorry to hear ubuntu is causing problems.  Maybe the next release in 2 months will fix the bugs if you're up for giving it another shot then.

---

### Post by avix on 2010-08-08
I assume you mean a live boot CD/Thumbdrive. can do this. I'll try again in a couple of months. the netbook remix was ok except for the damn interface. if they make it so that is changeable then I will give it another shot. I can't promote Linux with interfaces that don't work.

thanks for the fast reply KCormier

(bitchwhine mode off)

---

