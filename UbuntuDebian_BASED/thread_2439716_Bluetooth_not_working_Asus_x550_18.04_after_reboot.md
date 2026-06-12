---
title: "Bluetooth not working Asus x550 18.04 after reboot"
date: 2020-03-31
forum: Ubuntu/Debian BASED
---

### Post by wtbaster on 2020-03-31
I have an Asus f550lc with ZorinOS (based on Ubuntu 18.04.2)

Bluetooth had never work with zorin

with 

#lspci -nnk 

03:00.0 Network controller [0280]: Ralink corp. RT3290 Wireless 802.11n 1T/1R PCIe [1814:3290]
	Subsystem: Foxconn International, Inc. RT3290 Wireless 802.11n 1T/1R PCIe [105b:e055]
	Kernel driver in use: rt2800pci
	Kernel modules: rt2800pci
03:00.1 Bluetooth [0d11]: Ralink corp. RT3290 Bluetooth [1814:3298]
	Subsystem: Foxconn International, Inc. RT3290 Bluetooth [105b:e056]
	Kernel driver in use: rtbt
	Kernel modules: rtbth

I did the instructions of topic [https://ubuntuforums.org/showthread.php?t=2399393&p=13795005#post13795005](https://ubuntuforums.org/showthread.php?t=2399393&p=13795005#post13795005) and bluetooth worked properly: 

sudo add-apt-repository ppa:blaze/rtbth-dkms
sudo apt-get update
sudo apt install dkms rtbth-dkms blueman
sudo modprobe -v rtbth
but after a reboot of my laptop, bluetooth appears as disconected and there is not an adapter. If I run again sudo "modprove - v rtbth" again, bluetooth get it working!

I need to fix the solution on turn on!!!!

May someone help me, please? Thank you so much

---

### Post by wtbaster on 2020-03-31
I've got to reconect bluetooth when turn on my laptop.

You must do 

*$ sudo add-apt-repository ppa:blaze/rtbth-dkms*
*$ sudo apt-get update*
*$ sudo apt install dkms rtbth-dkms blueman*
*$ sudo modprobe -v rtbth*
[COLOR=#000000]
[/COLOR]And after you must create a rc.local:

*$ sudo vi /etc/rc.local*

with this code:

*#!/bin/sh*
*modprobe rtbth*
*rfkill unblock bluetooth*
*exit 0*

After, you must activate rc.local with systemd:

[I]$ sudo vi /etc/systemd/system/rc-local.service
[/I]
with the code:

[*Unit]*
* Description=/etc/rc.local Compatibility*
* ConditionPathExists=/etc/rc.local*

*[Service]*
* Type=forking*
* ExecStart=/etc/rc.local start*
* TimeoutSec=0*
* StandardOutput=tty*
* RemainAfterExit=yes*
* SysVStartPriority=99*

*[Install]*
* WantedBy=multi-user.target*


After you must give permissions and enable rc.local:

*$ sudo chmod +x /etc/rc.local*
*$ sudo systemctl enable rc-local*
*$ sudo systemctl start rc-local.service*

And reboot

---

### Post by jeremy31 on 2020-03-31
Moved to Ubuntu/Debian based

---

