---
title: "dual boot linux(sata)and winXp(pata)"
date: 2011-12-31
forum: Ubuntu Studio
---

### Post by Dennis G Irwin on 2011-12-31
I have win Xp already installed on a pata (IDE) drive as master, I removed that drive and put a sata ( as Native IDE) drive in and installed Linux Ubuntu Studio 11.04. Then replaced pata drive containing win Xp, and I need to set grub to display both os's(ubuntu studio and win Xp) as a normal dual boot system using 2 Hdd's. My setup is as follows: win Xp on pata IDE as master with dvd rom as slave. ..Linux Ubuntu Studio 11.04 on sata 0(master) and dvd writer on sata 1(slave). windows is set as 1st Hdd boot,Linux as 2nd Hdd boot as bios boot order .Because windows hdd was not present during linux install, I did not alter windows MBR, so grub was not written to windows  How do I set Grub menu to get both OS's to show for hdd boot selection without reinstalling either or both OS's ? I have done this before with both hdd's present,installing windows first on first hdd,then linux on 2nd hdd. and linux included both os's in grub menu automagically without breaking windows mbr. I know this can be done,but I can't get a clear explanation from anyone on the forums.PLEASE HELP A NOT SO NEWBIE figure this out. thanks.:confused: ](*,)](*,)](*,)

---

### Post by emmomalick on 2011-12-31
You can re-install the grub by following the steps from here. 

[http://www.tuxgarage.com/2011/01/re-installing-grub2.html](http://www.tuxgarage.com/2011/01/re-installing-grub2.html)

---

### Post by jejeman on 2011-12-31
Just issue
```
sudo update-grub
```and set in bios sata to be first boot.
No need for reinstaling grub.

---

