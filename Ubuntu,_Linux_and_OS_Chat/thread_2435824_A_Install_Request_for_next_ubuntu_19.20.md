---
title: "A Install Request for next ubuntu 19.20"
date: 2020-01-27
forum: Ubuntu, Linux and OS Chat
---

### Post by at446zz on 2020-01-27
Could the Programmers Please include Boot-repair on the live desktop display. Just in-case of a grub boot problem. So I can go to terminal and access boot-repair and repair while in sudo. 
This will help greatly and I would be very grateful. Reply is not necessary. 
Thank you
Rich

---

### Post by deadflowr on 2020-01-27
[I]Moved to Chat
[/I]

---

### Post by TheFu on 2020-01-27
> **at446zz said:**
> Could the Programmers Please include Boot-repair on the live desktop display. Just in-case of a grub boot problem. So I can go to terminal and access boot-repair and repair while in sudo. 
This will help greatly and I would be very grateful. Reply is not necessary. 
Thank you
Rich

Boot-Repair is far from perfect and sometimes it does more harm than good, especially with UEFI boot issues. Most people have UEFI these days.  Also, it is a GUI, so it won't work in a non-GUI environment.  The recovery mode provided by most live-install environments allows both BIOS and UEFI repairs to be made with just a few, short, commands. If you go into recovery mode and mount the normal storage partitions, then you can reinstall grub easily with :
```
grub-install /dev/sdZ
```
where sdZ is the HDD/SSD where you want it installed and have grub search all the partitions available for other OSes and update the menu with 
```
update-grub
```
For a normal install wthout LVM or encryption, that's pretty much it to fix grub.

Alas, nobody here works for Canonical, so great ideas aren't likely to get any action. We are just people like you who happen to volunteer helping others.

BTW, Ubuntu release numbers are {YY.MM} format.  Releases happen in April (04) and October (10), hence why there are 14.04, 16.04, 18.04, 20.04 releases for the even years, in April.  The other releases (odd years and in October) are all non-LTS.  Does that make sense?

---

