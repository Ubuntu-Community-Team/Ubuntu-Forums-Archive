---
title: "Revert bootloader back to Windows 7 or 8"
date: 2015-02-04
forum: Tutorials
---

### Post by sai7 on 2015-02-04
So I just recently ran into a problem. I went into panic mode and using   my mobile phone. I was able to fix my problem. I'll take you step by   step on how I solved it. I know there might be solutions of the same   kind, but seeing that I am still new to this forum, I want to give a   little something back.

[SIZE=5]**How to revert back to Windows 7 or 8 bootloader**[/SIZE]

So  you just recently installed Ubuntu and you removed Ubuntu the wrong   way? If you installed Ubuntu on a 2nd partition on your hard-drive and   you deleted Ubuntu via Window 7's Computer Management and then extended   the partition back to Windows 7. Rebooted your computer and saw the   messages
[HTML]error: no such partition
grub rescue >[/HTML] If you installed Ubuntu with a CD,  boot-able  USB, .etc and you still have the original hard copy that you  used to  install it on your Windows OS. You can use the following steps.

1. Insert your hard copy of Ubuntu whether it'd be CD, boot-able USB, .etc.

2. Upon the Installation Screen, look for the page that has two options:
[LIST]
[*]Try Ubuntu 
[*]Install Ubuntu 
[/LIST]
   (This should be on the first page or the second page of the Installation Screen)

3. Click on "Try Ubuntu". From there you should be able to get into a demo version of Ubuntu.

4. You should be in Ubuntu now. Search for the Terminal if it isn't present.

**If you don't have internet access do Step A. If you DO have internet access. Do Step B.**

Step A. In the terminal, type the following command.
[LIST]
[*]sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda 
[*]Then reboot your computer 
[/LIST]

Step B. In the terminal, type the following commands.
[LIST]
[*]sudo apt-get install lilo 
[*]sudo lilo -M /dev/sda mbr 
[*]Then reboot your computer 
[/LIST]

After that, Windows bootloarder should be working.

SOURCE: [https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

