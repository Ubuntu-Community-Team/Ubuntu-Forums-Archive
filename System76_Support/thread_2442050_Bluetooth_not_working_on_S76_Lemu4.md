---
title: "Bluetooth not working on S76 Lemu4"
date: 2020-04-29
forum: System76 Support
---

### Post by tachum1 on 2020-04-29
I bought this laptop 7 years ago and it is still going very well indeed.

I have just installed 20.04 Ubuntu on it and all is well EXCEPT the Bluetooth connectivity. It has never been a problem in the past. 

The hardware is Intel Centrino 2230 -802.11 b/g/n Wireless LAN + Bluetooth Combo Module. 

I have installed Bluez, Bluedevil, blueman and related bluetooth support files.

When I go to Bluetooth Manager and select, it says Bluetooth is not Enabled (or no response). Sometimes the bluetooth icon appears momentarily in the bottom panel but then disappears.

This might help?

gaz@gaz-Desktop:~$ lsusb; lspci -nnk | grep -iA3 net; dmesg | egrep -i 'blue|firm'
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 04f3:0103 Elan Microelectronics Corp. ActiveJet K-2024 Multimedia Keyboard
Bus 001 Device 002: ID 12cf:0106 DEXIN Laser Gamer Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
01:00.0 Network controller [0280]: Qualcomm Atheros AR9287 Wireless Network Adapter (PCI-Express) [168c:002e] (rev 01)
	Subsystem: Qualcomm Atheros AR9287 Wireless Network Adapter (PCI-Express) [168c:30a4]
	Kernel driver in use: ath9k
	Kernel modules: ath9k
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
	Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:8677]
	Kernel driver in use: r8169
	Kernel modules: r8169


and

bluetooth.service - Bluetooth service
     Loaded: loaded (/lib/systemd/system/bluetooth.service; enabled; vendor preset: enabled)
     Active: inactive (dead)
       Docs: man:bluetoothd(8)


Apr 29 16:00:04 gaz-Desktop systemd[1]: Condition check resulted in Bluetooth service being skipped.
Apr 29 16:10:34 gaz-Desktop systemd[1]: Condition check resulted in Bluetooth service being skipped.
~
Any help appreciated


Garry

---

### Post by MoebusNet on 2020-05-13
I had a similar issue with my 2011 Serval Pro 7 runnnig Lubuntu 18.04. After much searching, I found [https://medium.com/@overcode/fixing-bluetooth-in-ubuntu-pop-os-18-04-d4b8dbf7ddd6](https://medium.com/@overcode/fixing-bluetooth-in-ubuntu-pop-os-18-04-d4b8dbf7ddd6) which added the PPA for newer versions of bluetooth drivers that fixed many bluetooth issues. It fixed my bluetooth issues with my original Intel Centrino 6230 802.11n + Bluetooth card. I have since upgraded to a newer Intel Dual Band Wireless-AC 7260 card with much faster WiFi 802.11ac speed and newer spec Bluetooth; it works superbly. This is likely what you need.

---

### Post by CelticWarrior on 2020-05-13
> **MoebusNet said:**
> I had a similar issue with my 2011 Serval Pro 7 runnnig Lubuntu 18.04. 

The System76 set of drivers should have that covered (via PPA as well). Maybe you already tried it and found out the support for your model has been removed?

---

### Post by MoebusNet on 2020-05-24
@CelticWarrior - Sorry for the late reply; real life intruded :) To be honest, I never even considered the System76 driver; I thought the concept was that the System76 drivers were incorporated into newer kernels as Ubuntu brought out newer versions, which would alleviate the need for the System76 driver on older machines like mine (2011).

---

