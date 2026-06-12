---
title: "How to configure LVM to autodecrypt partition?"
date: 2011-09-03
forum: Security
---

### Post by isoman on 2011-09-03
I have recently installed ubuntu server 11.04 with the full lvm encryption(installed from the setup) . I wish now to use a key file to do automatic unlock. I have tried to follow this guide [http://ubuntuforums.org/showthread.php?t=837416](http://ubuntuforums.org/showthread.php?t=837416)

I generated a key with this command: sudo dd if=/dev/urandom of=/boot/grub/keyfile bs=1024 count=4

i putted it in /boot/grub beacause i think that it's not encrypted . When i try to add the key with this commad sudo cryptsetup luksAddKey /dev/sdX /boot/grub/keyfile

it asks me for the passphrase and when i put it nothing happen , nothing is printed to the screen ! I ignore it and continue the others steps and reboot but nothing happened and it ask for the passphrase .

Thanks for the help .

---

