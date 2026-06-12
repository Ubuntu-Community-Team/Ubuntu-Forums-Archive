---
title: "install server on Dell Laptop"
date: 2020-11-10
forum: Server Platforms
---

### Post by MemoryDump on 2020-11-10
Hi,

I have a Dell Laptop which had Windows 10 installed on it. I wanted to replace it entirely with Ubuntu Server since I only use this laptop as my Plex server.
I made myself a USB boot using the Ubuntu Server 20.04.1 ISO with Rufus.
I plugged in the USB stick in my laptop and rebooted.. the install started and I went through all the steps. I picked use entire disk.
Once the install was completed, I removed the USB stick and rebooted.
Now all I get is "NO OPERATING SYSTEM FOUND". I checked my BIOS and I am setup to boot off the HARD DISKS first. My drive is being detected.

Any ideas?

Thanks

---

### Post by TheFu on 2020-11-10
Fishing for "ubuntu install dell {insert-model-of-laptop}"

At first guess, I have an older Dell laptop, I have only 2 guesses.
[LIST]
[*]You installed with BIOS mode, but the system is setup to boot in UEFI mode    or the opposite.
[*]Might there be 2 GPUs in the system?  Disable all but 1.
[/LIST]

But I really don't know.  My Dell is from 2011.

---

### Post by MemoryDump on 2020-11-10
> **TheFu said:**
> Fishing for "ubuntu install dell {insert-model-of-laptop}"

At first guess, I have an older Dell laptop, I have only 2 guesses.
[LIST]
[*]You installed with BIOS mode, but the system is setup to boot in UEFI mode    or the opposite.
[*]Might there be 2 GPUs in the system?  Disable all but 1.
[/LIST]

But I really don't know.  My Dell is from 2011.

Thanks for the quick reply!

This is a rather old laptop too. It's a Dell Inspiron N7110

I checked through my bios settings and I don't see any options for UEFI mode.

I've attached some screenshots of my bios settings.

---

### Post by mastablasta on 2020-11-11
boot from live USB and check what is actually on the disk.
GRUB has to be there at the start. you can fix that easily (using boot repair).  "[COLOR=#000000]NO OPERATING SYSTEM FOUND" means GRUB is not where is is supposed to be [/COLOR]

---

### Post by SeijiSensei on 2020-11-11
During the install, you'll get the opportunity to identify where the boot loader and grub should be installed.  On a single-drive machine, choose /dev/sda.

---

### Post by MemoryDump on 2020-11-11
> **mastablasta said:**
> boot from live USB and check what is actually on the disk.
GRUB has to be there at the start. you can fix that easily (using boot repair).  "[COLOR=#000000]NO OPERATING SYSTEM FOUND" means GRUB is not where is is supposed to be [/COLOR]

After trying for several hours I decided to put my Windows 10 USB stick back in and see if that install would work. When I went through that setup I saw that all the ext4 partitions I created were there (I tried to manually create them during one of my attempts.. normally I’d pick “use the entire disk”). I had to delete them manually so Windows would install. 
After Windows setup was done, I rebooted and it booted up no problem. So again, I’m not sure why the Ubuntu server setup is failing to setup the mbr properly. I even watched the install logs as best as I could and couldn’t see anything that would indicate a boot error. 

Should I be trying to install this some other way? Windows 10 Pro (October 2020 version) is currently installed. 

Thanks

Ps: boot-repair doesn’t work on the Ubuntu server setup. It requires a graphic interface. (Found out the hard way)

---

### Post by TheFu on 2020-11-11
Boot-repair has been 'iffy' since UEFI came along. There are just too many possible options to handle them all, I suppose.
It should work fine on Legacy BIOS setups with no EUFI involvement.

I don't know anything about this Windows10 thing. People seem to be using it a few places, but I doubt it will ever catch on. I've heard that Windows only used MS-DOS partitions with Legacy booting, so any boot HDD over 2TB will be limited to 2TB.  To access more than 2TB, GPT is required and only 64-bit Windows in UEFI mode supports that.  Linux doesn't care - legacy or uefi, gpt or msdos partitions - doesn't matter.

Don't know if any of this is helpful or not.

---

### Post by MemoryDump on 2020-11-11
yeah I don't know.. i've tried to install Ubuntu server like 5 times now and every time the install is complete it reboots and NO OPERATING SYSTEM IS FOUND. :sad:

---

### Post by MemoryDump on 2020-11-11
Just tried booting a live-DVD of Ubuntu Desktop 20.10. I was able to run boot-repair. I followed the instructions it gave and it appeared to have re-installed Grub. Once that was all done I rebooted and got.. NO OPERATING SYSTEM FOUND. This makes absolutely no sense to me. I’m obviously missing something.

[https://paste.ubuntu.com/p/HffjVH2Zfw/](https://paste.ubuntu.com/p/HffjVH2Zfw/)

---

### Post by TheFu on 2020-11-11
BIOS seems to have motherboard RAID. Don't do that. There is usually a toggle to change from RAID to AHCI or something like that.
Try the install without LVM selected.

Have you considered NOT installing Ubuntu Server and using a like Ubuntu Desktop - perhaps Xubuntu - instead?

---

### Post by MemoryDump on 2020-11-11
> **TheFu said:**
> BIOS seems to have motherboard RAID. Don't do that. There is usually a toggle to change from RAID to AHCI or something like that.
Try the install without LVM selected.

Have you considered NOT installing Ubuntu Server and using a like Ubuntu Desktop - perhaps Xubuntu - instead?

I don't see any options in my bios for RAID. SATA Operation is set to AHCI.
Pretty sure I had attempted an install with LVM de-selected. I'll try that again.

My next step was to try Ubuntu desktop. I did put the ISO on a USB stick and it wouldn't boot up.. would fail and go to a grub shell/prompt of some sorts..
I burned the ISO on a DVD and that appears to work.. just VERY slow to load.

We shall see what happens. Thanks for the help! ;)

---

### Post by TheFu on 2020-11-11
The normal Ubuntu Desktop is fairly bloated - almost as bad as Win10.  It really is sad for all the people using older hardware that the default, pushed, Ubuntu, doesn't run great on any generation Core i5 hardware.

If you use LVM, I think the Ubuntu Installer is going to wipe the entire hard disk. BTW, I didn't see any Windows left in that boot-repair report. LVM probably wiped it. I have a dream of someday being able to setup LVM in the way I want without having to use an entire HDD.  With 20.04, the disk partitioning is 100x better than the prior installer - it was so much better that I cried tears of joy, but still has more to improve.
 Tears of joy, I say!

I love LVM and use it almost everywhere, so don't take my statements to be anti-LVM.

---

### Post by MemoryDump on 2020-11-11
> **TheFu said:**
> The normal Ubuntu Desktop is fairly bloated - almost as bad as Win10.  It really is sad for all the people using older hardware that the default, pushed, Ubuntu, doesn't run great on any generation Core i5 hardware.

If you use LVM, I think the Ubuntu Installer is going to wipe the entire hard disk. BTW, I didn't see any Windows left in that boot-repair report. LVM probably wiped it. I have a dream of someday being able to setup LVM in the way I want without having to use an entire HDD.  With 20.04, the disk partitioning is 100x better than the prior installer - it was so much better that I cried tears of joy, but still has more to improve.
 Tears of joy, I say!

I love LVM and use it almost everywhere, so don't take my statements to be anti-LVM.

I gave up trying to get Ubuntu running on this laptop. I've tried every possible way I could think of.

I ended up downloading the latest Debian ISO and it installed it no problem and it boots properly after the installer rebooted! So there's something's up with Ubuntu's installer when it comes to this particular laptop.

Thanks guys/gals for the help anyways!

---

