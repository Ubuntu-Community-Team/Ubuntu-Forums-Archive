---
title: "deleted partition of dual boot containing grub, now stuck in grub rescue"
date: 2015-03-13
forum: Ubuntu/Debian BASED
---

### Post by Cirrick on 2015-03-13
Hi, yesterday I decided to install Deepin in a dual boot. I later decided I no longer needed/wanted it so I deleted the partition. Apparently I had grub on that partition as well, and now my laptop only goes to grub rescue and will not boot. 
I have an acer aspire v5 touch. Removing the hard drive is not an option. I have tried to access UEFI but my computer just beeps and goes to grub rescue. I have grub rescue disk on a flash drive, I used unetbootin to do that, but iI cannot get to any boot menu (f12), and when I use ls (hd0)/ I get a unknown file system error. Please help, and sorry for my grammar/formatting, I'm on mobile.
Tl;dr: Deleted partition containing grub and deepin, now can only get to grub rescue, and I keep getting an unknown file system error, please help.

---

### Post by ajgreeny on 2015-03-13
It is the files used to manage and configure grub that have gone; they sit in folders in /etc and /boot in your now deleted Deepin OS partition.

**Boot-repair** in my signature should be able to restore everything for you with no difficulty.

---

