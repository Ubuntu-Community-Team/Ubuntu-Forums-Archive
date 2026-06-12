---
title: "Wireless card disapperaed at all"
date: 2012-09-24
forum: Ubuntu +1 (Quantal Quetzal) (Closed)
---

### Post by lion.guo on 2012-09-24
12.10, Thinkpad R61i, can't detect wireless at all.
Should be a Atheros card.

But run: 
  dmesg|grep -i atheros
Nothing
lspci |grep -i atheros

Nothing.

Is this mean support of this kind of card  is  not available now?

---

### Post by jerrylamos on 2012-09-24
I just did a simple lspci, no grep.  Last two lines are

01:00.0 Ethernet controller: Atheros Communications Inc. AR8152 v1.1 Fast Ethernet (rev c1)
02:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000

I'm no "grep" expert so I just look at the lspci output.  There's Atheros.  Note, "atheros" isn't there, but "Atheros" is.

Acer Aspire 1 netbook.  Now the first thing on opening the desktop Quetzal disconnects from the WPA wireless network.  I do a sudo dhclient wlan0, wait a few seconds, then Ctrl-c and it connects.  Yes, there's a launchpad bug.  Nothing promising in launchpad bug #1019083.

---

### Post by lion.guo on 2012-09-24
> **jerrylamos said:**
> I just did a simple lspci, no grep.  Last two lines are

01:00.0 Ethernet controller: Atheros Communications Inc. AR8152 v1.1 Fast Ethernet (rev c1)
02:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000

I'm no "grep" expert so I just look at the lspci output.  There's Atheros.  Note, "atheros" isn't there, but "Atheros" is.

Acer Aspire 1 netbook.  Now the first thing on opening the desktop Quetzal disconnects from the WPA wireless network.  I do a sudo dhclient wlan0, wait a few seconds, then Ctrl-c and it connects.  Yes, there's a launchpad bug.  Nothing promising in launchpad bug #1019083.

  "grep -i" means ignore CAPS, atheros Atheros ATHEROS ..., all is OK.
But in my old R61i, just nothing. 

Switch to WinXP, the wifi is OK.

---

### Post by lion.guo on 2012-09-25
Update to newest kernel, reboot
dmesg|grep -i ath :
[   20.162632] ath5k 0000:03:00.0: registered as 'phy0'
[   20.676846] ath: EEPROM regdomain: 0x67
[   20.676852] ath: EEPROM indicates we should expect a direct regpair map
[   20.676856] ath: Country alpha2 being used: 00
[   20.676858] ath: Regpair used: 0x67
[   21.283190] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
GREAT

---

