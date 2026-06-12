---
title: "damaged grub in Ubuntu 9.10"
date: 2010-02-02
forum: The Cafe
---

### Post by Mat11 on 2010-02-02
Hi i've tried to repair my boot up problem whereby i had to press the power on switch 3 times to get the O/S to work, so i took a chance with a suggestion on the forum.
Deleted pc grub and grub common using sudo then tried to reinstall them with only the pc grub installing properly.
My laptop is a i386 how do i start to fix the problem ?
All i see at the moment is a question mark after Grub recovery.Think i'm in the **** !
Ran the 9.10 boot CD and it indicated i had 3 missing files. 
How can i use my CD to recover ?
 
Need help 
 
Matt

---

### Post by k@e on 2010-02-02
Coincidentally, I reinstated grub just yesterday.

Boot the 9.10 live CD and open a terminal. First, mount the boot partition of your hard drive. Partition number and drive may vary for you, find it out with fdisk -l:
```
sudo mount /dev/sda1 /mnt
```

Then reinstall grub using this command
```
sudo grub-install --root-directory=/mnt /dev/sda
```

Reboot and check if you can boot into your OS.

---

### Post by Mat11 on 2010-11-10
Hi think i've found the answer its my Xpress 200m graphics card fails to start properly on boot in Ubuntu 9.10. Have to start the comp twice to get to the Log-on screen
Thanks for your suggestion.

---

