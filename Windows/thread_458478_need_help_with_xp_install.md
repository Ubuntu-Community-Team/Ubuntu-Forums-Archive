---
title: "need help with xp install"
date: 2007-05-29
forum: Windows
---

### Post by racers on 2007-05-29
Im trying to dual boot xp and ubuntu (ubuntu is installed now). when i try in install xp I get a message telling me to insert the disk and press enter when the xp disk is already in so i take it out put it back in and press enter and i get the same message. how can i fix this?

---

### Post by smoker on 2007-05-29
hi, the usual way is to install windows first, and then install ubuntu, but as ubuntu is installed, did you make a free partition for windows and format it either fat32 or ntfs? if not, then i believe windows setup cd is not 'seeing' a place to start an install from.

if it is a fresh ubuntu install, you may be easiest formatting the whole drive, making three partitions, one windows, one ubuntu, and one swap, format windows partition fat32 or ntfs, and install windows. once that is done, reinstall ubuntu to the other partition, and with grub you should be able to dual boot.

best of luck

---

### Post by FuturePilot on 2007-05-29
I don't think it has anything to do with "seeing" a place to install. Maybe your CD drive went bad?

---

### Post by racers on 2007-05-29
it still doesn't see the disk and Its not the drive since i can use the live cd

---

### Post by racers on 2007-06-01
can anyone help me?

---

### Post by smoker on 2007-06-01
hi, did you create a fat or ntfs partition with enough space for xp, and make it a primary bootable partition?

also, is your xp cd ok, have you tried it on another machine to see if it will start an install, and isn't damaged?

is your bios set to boot from cd-rom as the first boot device?

---

### Post by kyphi on 2007-06-01
Hello racers,

Are you trying to install XP while in Ubuntu?  That will not work.

How did you install Ubuntu?

---

### Post by racers on 2007-06-04
i had xp then i formated the drive installed ubuntu to use the entire disk.  when I am when i looking at the partitions i am missing like 10 gb

---

