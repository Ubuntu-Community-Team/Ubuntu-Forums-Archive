---
title: "After Ubuntu install can't boot from DVD/USB pendrive"
date: 2012-09-11
forum: System76 Support
---

### Post by robtg on 2012-09-11
I've been running Linux Mint on my PanP5 and thought I'd try Ubuntu 12.04.1 LTS.  I created a bootable USB pendrive and the Ubuntu install went OK.  After a couple of reboots (I don't remember exactly what caused it) I started getting these messages at boot time:

error: no suitable mode found
error: no video mode available

After a few moments the boot continues without any obvious problems.  I'd like to go back to Linux Mint (Unity still leaves me a bit cold) but I cannot get the laptop to boot from the DVD drive or a pen drive.  The boot order set in the BIOS is USB KEY, IDE CD, IDE HDD.  The other odd thing is that if I have a USB pen drive inserted or a bootable DVD/CD in the drive, sometimes I get a GRUB menu (after the two error messages above flash briefly).   I don't need to save anything from my Ubuntu install; I just want to reinstall Mint.  For the record, the bootable Mint DVD I'm trying to use was created on the PanP5 and does boot on another PC.  

When I have a bootable pen drive or DVD in the machine, the boot process seems to ignore them and Ubuntu boots.  

Any ideas?

Thanks.

Rob


Problem solved.  Started trolling through the BIOS settings; on the Advanced tab found "Boot legacy OS"; was set to disabled; tried setting to enabled as a WAG; seems to have solved the problem; can boot from DVD & pen drive now.  Not sure why this happened since I was able to boot from pen drive to install Ubuntu.  Oh well.

:confused:

Rob

---

