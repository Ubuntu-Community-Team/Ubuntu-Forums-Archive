---
title: "Almost-fresh Lucid Server install starts hanging on boot after a few reboots"
date: 2010-08-29
forum: Server Platforms
---

### Post by dylanv on 2010-08-29
Hi all,

I've encountered a really frustrating problem with my Lucid Server installation. What happens is that I'll install the OS and everything will work fine for a few boot cycles, but then out of the blue the system will hang while booting. By "hang" I mean that the BIOS will perform its POST, the hard drive will churn for a second, and then the computer will stop working and sit idle. The display's LED even goes from green to amber, which usually indicates no input or a sleeping computer. When the computer is in this hung state, no key combo will rescue it and I can't log in via SSH, leaving me to force reboot. Running in recovery mode indicates that the hang occurs after the message "Running /scripts/init-bottom...Done" The only way I can get the computer to boot normally is by holding Shift to access the GRUB menu and then selecting the 2.6.32-21-generic-pae kernel, which is an old one left from before I updated the software (the current kernel it has is 2.6.32-24-generic-pae).

I tried reinstalling Ubuntu, but the same issue occurred again. This time, though, I meticulously wrote down everything I did to modify the system from its fresh install.

Installation settings: software RAID 1, continue booting if RAID array is degraded, no mail configuration, no /home encryption, install security updates automatically, "LAMP Server" and "OpenSSH Server" software collections selected, install GRUB to the MBR

Setup performed after fresh install: updated software, enabled UFW, set up wi-fi card, installed powernap package

Any help would be greatly appreciated. I just started using Ubuntu again after playing around with it in the Edgy/Feisty days, and I am impressed with how much it has matured. I would love for this issue to be overcome so I can experience the warm fuzzy feeling of having a reliable Linux server :)

---

