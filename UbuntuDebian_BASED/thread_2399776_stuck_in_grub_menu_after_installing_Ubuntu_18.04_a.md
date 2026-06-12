---
title: "stuck in grub menu after installing Ubuntu 18.04 and running boot-repair"
date: 2018-08-29
forum: Ubuntu/Debian BASED
---

### Post by emu-1 on 2018-08-29
Hi,
 
I am new to Ubuntu and **would need your help for dually installing Windows 10 and Ubuntu 18.04.**
 
I have a Dell laptop XPS 15 9560 2017 Core i7-7700HQ, 16 GB RAM 512GB SSD
and it has a Nvidia GeForce GTX 1050 graphic card
Windows 10 Home was pre-installed
 
I installed a custom image of Ubuntu (called custom) that I got from my teacher (I added nomodeset after quiet splash in the Grub bootloader editor before installing). Upon rebooting, I didn't get any options to choose between Windows and Ubuntu (Ubuntu is listed first in the boot setup) but** ended up at the grub menu grub>**
 
When I booted with an Ubuntu live USB drive I could launch the live Ubuntu from the USB drive (when I again added nomodeset after quiet splash in the Grub bootloader Editor):
**I ran boot-repair and was told: "Boot successfully repaired"**
The record by boot-repair is on:
 
[http://paste.ubuntu.com/p/B2RnrRHgjk/](http://paste.ubuntu.com/p/B2RnrRHgjk/)
 [B]
However, when re-booting I was again stuck in the grub menu grub>.[/B]
I checked custom (Ubuntu) in the boot setup and it points to \EFI\custom\shimx64.efi, as recommended by boot-repair.
 
I am only starting to use Ubuntu and would be very grateful for any help to fix this.
By the way, booting into Windows still works.
 
Kind regards,
emu
 
 
Things I did before installing Ubuntu - I understand it is done because of the Nvidia card:
I found several, similar installation instructions for this laptop and did the following:

[LIST=1]
[*]Run Command Prompt as an admin.
[*]Run: bcedit /set {current} safeboot minimal
[*]Reboot.
[*]Press F2 when you see the Dell logo.
[*]Select AHCI mode in the SATA option under System Configuration.
[*]Press “Apply” then “Exit”.
[*]Login as usual.
[*]Open the Command Prompt as an admin again and type: bcedit /deletevalue {current} safeboot
[*]Reboot.
[/LIST]
 
I partitioned the C drive in Windows:
249 GB for Windows (NTFS)
212 GB free, to be used for Ubuntu
then I started to install Ubuntu (see above)

---

### Post by oldfred on 2018-08-29
Moved to OtherOS since not standard Ubuntu.

Most with Dell have needed UEFI update from Dell and SSD firmware update.
Have you done those?
Note UEFI update will reset some UEFI settings, so keep track of what you have changed to redo them.

You are not showing nVidia? Did you turn it off in UEFI, that is usually a setting in UEFI.
But it should boot with internal Intel video.

Does Windows boot ok, directly from UEFI boot menu?
Did you add AHCI driver first into Windows before changing setting. You can change back, if you did not and then update Windows.

If at grub> can you do this? Not sure with newer NVMe drive, but still may be hd0 in grub.
configfile (hd0,7)/boot/grub/grub.cfg

While not exact model, issues are very common by brand for similar models.
       Dell XPS 13 9560 install without issues
[https://ubuntuforums.org/showthread.php?t=2357321](https://ubuntuforums.org/showthread.php?t=2357321)
[https://wiki.archlinux.org/index.php/Dell_XPS_15_9560](https://wiki.archlinux.org/index.php/Dell_XPS_15_9560)
Dell XPS 13 9360 16.04 worked after nvme firmware & BIOS update, 16.10 did not, new rEFInd for NVMe
[http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install](http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install)
Dell XPS 13 9360 Dualboot Windows 10 and Ubuntu 16.04 AHCI NVMe
[http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488](http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488)

---

