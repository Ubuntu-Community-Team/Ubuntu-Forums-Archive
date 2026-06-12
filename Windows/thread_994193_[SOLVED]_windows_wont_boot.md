---
title: "[SOLVED] windows wont boot"
date: 2008-11-26
forum: Windows
---

### Post by inxygnuu on 2008-11-26
Hello, yesterday, I was trying to clean up my system, and using NeoGrub bootloader, I removed some invalid entries, and when i went to reboot, an error message came up displaying: "operating system not found" I have to say, i have never seen an error message of such. I also know there is some "boot.ini" or something like that. I have windows 7 and windows vista that i can't access. I am also currently using Ubuntu. Does anyone know how to get my system working without reinstalling everything?

thanks in advance,

3v4n

---

### Post by RoyalShrubber on 2008-11-28
[this might help you :)]("http://linuxhelp.blogspot.com/2005/11/how-to-repair-corrupt-mbr-and-boot.html")

---

### Post by inxygnuu on 2008-11-30
> **RoyalShrubber said:**
> [this might help you :)]("http://linuxhelp.blogspot.com/2005/11/how-to-repair-corrupt-mbr-and-boot.html")

Thanks, but i need to edit the menu.lst and GRUB in order to get it so GRUB recognizes my vista, or more importantly, my windows 7. I know there is a way to add in options, i just need to know how to do it. My GRUB was not overwritten, and therefore, your article is irrelevant to my problem.

thanks,
3v4n

---

### Post by inxygnuu on 2008-12-06
(Bumpity bump) Ok, i found a solution, in the gpartition live cd, if you add boot as a flag, it will boot into that bootlaoder. Should i switch the bootloader to the windows one, or try to fix GRUB? I really want to get to beta testing windows. 

Thanks,
3v4n

---

