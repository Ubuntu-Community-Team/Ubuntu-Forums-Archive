---
title: "I'm a beginner; need help because I can't access Windows XP now!"
date: 2008-01-30
forum: Windows
---

### Post by catiebug on 2008-01-30
I know so little about computers, and that's why I'm in trouble!  I installed Ubuntu 7.04 with the understanding that I could boot up using either Ubuntu or Windows XP, but now I seem to be unable to access any of my files!!!  I don't know what partitions are, but it seems that I didn't upload Ubuntu in the right partitions, or something.  I found the code to add "Microsoft Windows XP Professional" to the boot menu, so now it appears upon startup, but it just says "error, unable to boot" when I choose that option.  Does someone have some (English please!) simple advice for me or do I just need to hire a professional?  Arghh!!! Thanks :)

---

### Post by logos34 on 2008-01-30
open a terminal and type these two commands:

sudo fdisk -l

cat /boot/grub/menu.lst

Post them.

---

