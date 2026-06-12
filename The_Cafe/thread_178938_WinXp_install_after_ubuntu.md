---
title: "WinXp install after ubuntu?"
date: 2006-05-18
forum: The Cafe
---

### Post by dmacdonald111 on 2006-05-18
I have ubuntu system-wide, but i was wondering if I can create a partition and install winxp without losing everything. Didn't want to re-install, but work has software that is only for windows. Thanks.

---

### Post by Sef on 2006-05-18
If you do install Windows after Ubuntu, read this thread.

[http://ubuntuforums.org/showthread.php?t=158453&highlight=Reinstall+Grub]("http://ubuntuforums.org/showthread.php?t=158453&highlight=Reinstall+Grub")

---

### Post by Jose Catre-Vandis on 2006-05-18
Xp will be happy installing on a separate partition to Ubuntu, but will insist on overwriting your mbr and hence your ubuntu bootloader and boot up. To get grub back, you will need a live cd that runs grub (Preferably an ubuntu live cd). You will also need to know which partition your ubuntu is installed on for later.

Once you have Xp installed and booting up OK, do the following:

Reboot with Live CD (make sure CD is set to boot first in bios)
Once booted up, open a terminal

Type: sudo su         <- (this gives you root)

Now make a directory to load your ubuntu partiton

Type: mkdir /mnt/UBU     <- (you can choose what you call it)

Now mount your ubuntu partition

Type: sudo mount -t ext2 /dev/hda5 /mnt/UBU   <-(hda5 is the ubuntu partition in this case)

Now change the root to your mounted partition

Type: chroot /mnt/UBU

Now move onto fixing your grub:

Type: grub

Type: root and then press the <TAB> key once

This should tell you the hd that grub recognises

Type: root (hd0,4)  <-(here, grub is looking for partition hda5,  on the first hard drive. Grub starts counting with 0 instead of 1)

Type:setup (hd0)  <- this should setup grub in the right place, and overwrite the mbr, (hd0,4) will write grub to your root partition

Type: quit

and reboot, you should have your grub bootloader back, with XP as an option

If grub doesn't pick up windows, these are the lines you need to add to (to the end of) your /boot/grub/menu.lst file:

#    Windows XP installation
title		Microsoft Windows XP Professional
root		(hd0,4)
savedefault
makeactive
chainloader	+1

---

### Post by dmacdonald111 on 2006-05-18
Thanks for that guys! Wish I didn't have to do it though. lol

---

