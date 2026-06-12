---
title: "GRUB gone/corrupted"
date: 2012-04-03
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by Aenima99x on 2012-04-03
Just installed the latest updates on my htpc and now it's gone into a continuous reboot, it never makes it to the grub screen. Any suggestions on what steps I can take to try and recover?

---

### Post by cariboo on 2012-04-03
Boot from the Live CD/USB, chroot your / partition and reinstall grub.

---

### Post by Harry33 on 2012-04-03
The latest grub2 [SIZE=2]([/SIZE][SIZE=2]1.99-20ubuntu1[/SIZE][SIZE=2]) update is OK here on all of my three[/SIZE] setups.

---

### Post by garvinrick4 on 2012-04-03
This is in reference to post #2, I have time to give code: 

Copy and paste these one at a time with Live CD (install CD using Try ubuntu) or from another install of Ubuntu on different partion.

I am using sda5 as linux install you want to purge and reinstall grub [COLOR=Red]use your own sda#[/COLOR]
open a terminal and:
sudo mount /dev/sda5 /mnt
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /dev/pts /mnt/dev/pts
sudo mount -o bind /proc /mnt/proc
sudo mount -o bind /sys /mnt/sys
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt
apt-get purge grub-pc
apt-get install grub-pc
update-grub
exit
sudo umount /mnt/dev/pts
sudo umount /mnt/dev
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt

---

### Post by Aenima99x on 2012-04-03
Running of a Live USB now and have chrooted /mnt and tyring to reinstall. Following errors are returned -
> 
/usr/sbin/grub-setup: warn: This GPT partition table has no BIOS Boot Partition; embedding won't be possible!.
/usr/sbin/grub-setup: warn: Embedding is not possible. GRUB can only be installed in this setup by using blocklists. However, blocklists are UNRELIABLE and their use is disouraged..
/usr/sbin/grub-setup: error: cannot read `/boot/grub/core.img` correctly.


EDIT - I was able to open Gparted in the Live session and set the "bios_grub" flag on the drive and was able to reinstall grub and it says it completed successfully. However on a reboot now, it just sits at a blinking cursor. No endless reboot now, so a tiny bit of progress......

---

### Post by garvinrick4 on 2012-04-03
Seems you have a GPT disk instead of Basic disk a Microsoft thing.

I have never worked with a GPT disk in Linux.

There is a user named "oldfred" that is knowledgeable in GPT and Linux.
See if he is around.

If you did not intend to change your disk from Basic to GPT it can happen as
I understand when you try to make 5 or more Primary partitions in your scheme.
Basic only allows 4 but you can then make 1 of them extended and use all the
logical inside the extended and Linux survives fine in the logical partitions. 
When Windows likes a Primary only.

---

### Post by dino99 on 2012-04-03
Have tried to chroot by following the post above, but i cant get the dns working:
- no address associated with hostname
- root@oem-desktop:/# ping -c4 [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)

i suppose that the /run/resolvconf/ change into Precise makes some troubles. I've checked quite everything but the good solution :( Outside the chroot there is no issue with dns/nameserver.

---

### Post by NHclimber on 2012-04-03
> **Aenima99x said:**
> EDIT - I was able to open Gparted in the Live session and set the "bios_grub" flag on the drive and was able to reinstall grub and it says it completed successfully. However on a reboot now, it just sits at a blinking cursor. No endless reboot now, so a tiny bit of progress......

Nope - that's not what to do. The "bios_grub" flag is really a partition type that indicates to grub2 that it alone can use the partition for what it wants to do -- which is to write the core.img file (basically the stage 2).

What you want to do it set up a small (1MB) partition within the first 2TB of the drive and mark that as "bios_grub". Indicate this as the bootloader partition.

Read this thread for more than you ever wanted to know about GPT [http://ubuntuforums.org/showthread.php?t=1949220](http://ubuntuforums.org/showthread.php?t=1949220)

---

### Post by Aenima99x on 2012-04-03
> **NHclimber said:**
> Nope - that's not what to do. The "bios_grub" flag is really a partition type that indicates to grub2 that it alone can use the partition for what it wants to do -- which is to write the core.img file (basically the stage 2).

What you want to do it set up a small (1MB) partition within the first 2TB of the drive and mark that as "bios_grub". Indicate this as the bootloader partition.

Read this thread for more than you ever wanted to know about GPT [http://ubuntuforums.org/showthread.php?t=1949220](http://ubuntuforums.org/showthread.php?t=1949220)

Yeah that's actually what I ended up doing. I created a 2MB unformatted partition (it went at the end of the drive) and set the bios_grub flag and it booted fine.

---

### Post by NHclimber on 2012-04-03
Would you mark this thread as solved then? (see Thread tools pulldown)

---

### Post by dlwalters on 2012-04-17
After installing 12.04 on a separate new Western Digital 1TB drive, running sudo update grub in 12.04 did find,  Windows 7 64 bit,  on another Western Digital 1T byte), and also Ubuntu 11.04 on a Seagate1.TB 

But...at boot,I get an EFI missing file error for Widows 7.   12.04 still boots successfully. 

 Everything  worked fine in Ubuntu 11.04 and 11.10 until I loaded 12.04 on the new Western Digital on 14 April.  

It gets worse.  Booting into Ubuntu 11.04 and running sudo update grub in 11.04 (at 22:00 PDT 16 April, 2012).   completely hosed that disc!

I can boot each drive : Ubuntu  12.04, Windows 7 64, and Ubuntu 11.10 by  entering the EFI Bios and selecting the appropriate drive.   But 11.04 just continues to click about once each second indefinitely, as long as the +5 and +12 V connector is plugged in.  

There has got to be a serious problem with grub2 or worse yet, there is a root kit trojan in Ubuntu.

dlwalters / W9DKI

---

