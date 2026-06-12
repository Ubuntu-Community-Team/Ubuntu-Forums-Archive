---
title: "No Wireless Extension"
date: 2016-05-10
forum: Ubuntu/Debian BASED
---

### Post by Khairul_Rifqi on 2016-05-10
I have an issue with my wireless adapter . I have tried sudo apt-get update and sudo apt-get upgrade and fix missing . I also try the lspci and rfkill . But none is working . Please help me . Im currently on Elementary OS . It was working before after i remove the file and install nonfree ( I dont remember the name ) . But then i restarted my laptop and the wifi doesnt show up . And before i restart , i think i did the if wlan1 is up = sleep 1 ( I cant give detailed i didnt remember ) Please help me i have tried lots of way . It is broadcom b43 43111 thanks .

```
Lspci : khairul@Khairul:~$ lspci 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03) 
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) 
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03) 
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02) 
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02) 00:1c.2 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 3 (rev 02) 
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02) 00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02) 00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02) 
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) 00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02) 
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 02) 
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02) 01:04.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller (rev 40) 
01:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx] 
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01) 04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 20
```

---

### Post by howefield on 2016-05-10
Thread moved to the "*Ubuntu/Debian BASED*" forum.

Just a tip : wrapping your terminal output with code tags will significantly enhanced the readability for anyone who might want to offer assistance.

---

### Post by jeremy31 on 2016-05-10
Welcome to the forum.  What module is used now?  Please post ```
lsmod | egrep 'b43|wl'
```
Also post ```
lspci -nnk | grep -iA2 net
```

---

### Post by Khairul_Rifqi on 2016-05-10
khairul@Khairul:~$ lsmod | egrep 'b43|wl'
wl                   6148096  1 
cfg80211              458752  1 wl

--------------------------------------------
Im sorry im posting this through the phone so i cant do as you wish . 
--------------------------------------------


```
khairul@Khairul:~$ lspci -nnk | grep -iA2 net
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
	Subsystem: AMBIT Microsystem Corp. Device [1468:0422]
	Kernel driver in use: wl
04:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller [11ab:4362] (rev 20)
	Subsystem: Uniwill Computer Corp Device [1584:6100]
	Kernel driver in use: sky2
```

---

### Post by jeremy31 on 2016-05-10
It sounds like you just need to ```
sudo apt-get purge bcmwl-kernel-source
```
Reboot

---

### Post by Khairul_Rifqi on 2016-05-11
This is what i got : ```
khairul@Khairul:~$ sudo apt-get purge bcmwl-kernel-source
[sudo] password for khairul: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dkms fakeroot libfakeroot linux-headers-3.19.0-39
  linux-headers-3.19.0-39-generic linux-image-3.19.0-39-generic
  linux-image-extra-3.19.0-39-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 7,141 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 206555 files and directories currently installed.)
Removing bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu0.2) ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu0.2) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.103ubuntu4.3) ...
update-initramfs: Generating /boot/initrd.img-3.19.0-59-generic
```

---

### Post by jeremy31 on 2016-05-11
Reboot and post results for ```
rfkill list all; lsmod | egrep 'wl|b43'; dmesg | grep b43
```

---

### Post by Khairul_Rifqi on 2016-05-12
khairul@Khairul:~$ rfkill list all
khairul@Khairul:~$ lsmod | egrep 'wl|b43'
b43                   397312  0 
bcma                   49152  1 b43
mac80211              626688  1 b43
cfg80211              458752  2 b43,mac80211
ssb                    57344  2 b43,ssb_hcd
khairul@Khairul:~$ dmesg | grep b43
[   16.480311] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   16.516087] b43-phy0: Found PHY: Analog 4, Type 2 (G), Revision 8
[   16.516113] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2050, Revision 2, Version 0
[   16.617749] b43 ssb0:0: Direct firmware load for b43/ucode5.fw failed with error -2
[   16.617794] b43 ssb0:0: Direct firmware load for b43/ucode5.fw failed with error -2
[   16.660445] b43 ssb0:0: Direct firmware load for b43-open/ucode5.fw failed with error -2
[   16.660495] b43 ssb0:0: Direct firmware load for b43-open/ucode5.fw failed with error -2
[   16.660505] b43-phy0 ERROR: Firmware file "b43/ucode5.fw" not found
[   16.660510] b43-phy0 ERROR: Firmware file "b43-open/ucode5.fw" not found
[   16.660516] b43-phy0 ERROR: You must go to [http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware](http://wireless.kernel.org/en/users/Drivers/b43#devicefirmware) and download the correct firmware for this driver version. Please carefully read all instructions on this website.

QUOTE=jeremy31;13487442]Reboot and post results for ```
rfkill list all; lsmod | egrep 'wl|b43'; dmesg | grep b43
```[/QUOTE]

This is what i get . And sorry again for not doing the code . I cant do so . Or i dont know how to do it through smart phone .

--------------------------------------------

---

### Post by jeremy31 on 2016-05-12
With your smart phone just put [code ] before the terminal output and [/code ] without the extra space.  [http://ubuntuforums.org/misc.php?do=bbcode#code](http://ubuntuforums.org/misc.php?do=bbcode#code)

Just one last thing to do ```
sudo apt-get install firmware-b43-installer
```
Reboot

---

### Post by Khairul_Rifqi on 2016-05-12
Thanks man . Its worked . Actually i stucked
at this firmware things . I failed to find and install the manual way . Thanks man . How can i add a good reputation to you . Really thanks you . Its solved .

---

### Post by jeremy31 on 2016-05-13
Use the thread tools dropdown menu at top of the page to mark as solved

---

