---
title: "[Ubuntu 9.10/Server] VIA C7 PX 5000EG with USB Stick"
date: 2010-01-11
forum: Server Platforms
---

### Post by dolphs on 2010-01-11
Hi, I installed Ubuntu Server 9.10 x32 on a 2Gb USB Stick with 512Mb Memory (hardware VIA EPIO PICO PX 5000EG). 

Yet I like to recompile my kernel on a faster system in an effort to tweak the kernel as it has default settings that need to be adjusted (eg. remove support for wireless, bluetooth, change x86 generic to VIA C7 CPU support, etc etc).

Anyway after installing first thing I did was updating /etc/fstab adding: " tmpfs  /tmp  tmpfs nosuid,nodev 0 0 " to limit writes to USB stick and create /tmp in to RAM.

Yet I followed [http://www.howtoforge.com/kernel_compilation_ubuntu]("http://www.howtoforge.com/kernel_compilation_ubuntu_p2") to start recompiling on an other system except I changed step 5 " cp /boot/config-`uname -r` ./.config " to " scp from remote machine to local ( eg scp user@hostname:/boot/config-2.6.31-14-generic ./.config-viac7 ). 

Before I dig further in to the kernel params I hope I can get some hints which I certainly should include and what not if you take in account I like to have a quick booting system and small kernel just tuned accoring following specs:


Processor 500 MHz VIA C7 Eden ULV
Chipset VIA VX700 
512Mb System Memory DDR2 533 SO-DIMM
VGA Integrated VIA UniChrome Pro II Graphics 
Onboard IDE ATA 133 (2.0 mm 44-pin pin header) 
Onboard Serial ATA 1 SATA connector  
Onboard LAN VIA VT6106S 10/100 
Onboard Audio VIA VT1708A 8 channel HD codec 
1 RS-232 COM pin header


As it is meant to be a server I will require just COM, USB ( including FTDI 232 USB-Serial support ). I don't need audio to be enabled for example, but to start with I like to enable all components also if these are not used. Please let me know if one built a specific kernel for this VIA C7 motherboard

---

