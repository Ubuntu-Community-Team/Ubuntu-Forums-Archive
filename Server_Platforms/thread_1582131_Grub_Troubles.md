---
title: "Grub Troubles"
date: 2010-09-26
forum: Server Platforms
---

### Post by Jdfraser on 2010-09-26
Hi, I seem to be having an issue with grub on my Ubuntu 10 Server install and I'm hoping that someone can please help. I have run out of ideas and things to try, I would appreciate ANY input.

This is not a dual boot system. I have a single drive (SATA 1.5TB) that has been booting and running without any problems for the last 6+ months. This error has only started within the last day or so when rebooting my system.

What happens:
I boot up the PC and see the system POST, then see the flashing cursor in the top left of my screen and hear a fair bit of disk activity. After 5 - 10 seconds my monitor goes into low power mode as if it isn't receiving a signal from the PC. Disk activity stops. The system seems to stay like this indefinitely.

What I've tried:
1) I have held the shift key to get the grub menu, selected 2.6.32-21-generic-pae (recovery mode). The system starts to boot, I get text on my screen. It flys by pretty fast, but no errors that I can see. The last thing I see is something like"Running scripts \init-bottom" before the screen goes blank and disk activity stops.

2) I have used the Server CD and selected the RESCUE A BROKEN SYSTEM, mounted my /dev/sda1 and had a look around, all seems good. I've also unmounted sda1 and run fsck.ext4 -f /dev/sda1 which had no complaints. I have mounted my other ext partition on this disk as well and all look fine. I have commented out the non-essential partition from fstab.

3) I've dropped to the grub command line and done 'ls' and received the following "(hd0) (hd0,5) (hd0,2) (hd0,1) (fd0). I assume this is a-good-thing. 

4) Thinking that I might have a monitor resolution issue I've uncommented the GRUB_TERMINAL=console mode in etc/default/grub, as well uncommented GRUB_GFXMODE=640x480 and run update-grub

5) I've checked the UUID in the grub menu against the UUID listed in 'blkid' and it seems to be correct.

6) I've also tried reinstalling grub boot loader from the server CD rescue mode

I could really use some ideas, I don't know what else to check. I really don't want to have to reinstall the entire system. As far as I can tell this seems to be a grub/software issue, the hardware in this box seems to functioning fine. Please help.

Jamie

---

