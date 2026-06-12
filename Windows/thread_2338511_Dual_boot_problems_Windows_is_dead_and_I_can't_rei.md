---
title: "Dual boot problems: Windows is dead and I can't reinstall it"
date: 2016-09-28
forum: Windows
---

### Post by howwyhoward on 2016-09-28
So a while back I set up a dual boot on my laptop with Windows 7 and Ubuntu (I think 14.04). Started out with Windows on the primary drive and installed Ubuntu on a flash drive. Everything worked fine for quite a while but I began to run into problems with booting. At some point I needed to hold f11 while booting and boot from the flash drive to get into grub and boot windows from there. Eventually one time when I tried to boot windows nothing appeared but a purple grub-ish screen appeared and I could no longer access windows. I am currently attempting to reinstall. I booted from the Win7 disc to reinstall it on the primary hard drive. I reformatted the drive and started the install. Everything went fine through the unpacking, expanding, and installing of windows. However when it rebooted to finish the installation I couldn't complete it. I found I could still not boot directly to the hard drive so I booted to the flashdrive and went through grub to boot to the primary drive. After a few minutes of the "finishing installation" screen, an error message came up saying something like "windows setup could not install windows on this hardware." Hardware specs are below. Please help :( Thanks
32GB RAM
graphics: GTX 780M
processor: I think intel i7 4700HQ
primary HD is 120GB solid state
flash drive is a 32GB patriot supersonic pulse
there's also a 1TB storage drive inside but that shouldn't matter

---

### Post by oldfred on 2016-09-28
You have an UEFI system, which normally uses gpt partitioning. 
Windows 7 default install is BIOS/MBR. And Windows only boots from MBR with BIOS and UEFI with gpt.

Was Windows 7 installed in BIOS or UEFI boot mode? 
To install Windows 7 in UEFI mode, you have to copy to flash drive and move a boot file or two into /EFI/Boot.

Windows will complain if partitioning does not match boot mode and how you boot install media UEFI or BIOS is how it installs.

Post this from Ubuntu live installer:
sudo parted -l

---

### Post by howwyhoward on 2016-09-29
Thanks for the quick response! I'm not sure which boot mode Windows 7 was installed in. Should I upgrade Ubuntu to 16.04 to change the boot mode? Can't do it through Ubuntu because of some software bugs I've run into, so I would have to do it from a CD. (not a problem for me). And would I just choose an upgrade option or reinstall it completely? (either is fine since it wouldn't be much trouble reinstalling the software on here.) Sorry for the noob-ish questions, don't know too much about all this.

---

### Post by howwyhoward on 2016-09-29
UPDATE: SOMEHOW I managed to install Windows from the CD and then boot into Windows using a CD I burned Ubuntu onto. Figured this out because I was about to reinstall Ubuntu but it sent me to Windows. It finished the installation and it works now. Thanks for the help/advice.

---

