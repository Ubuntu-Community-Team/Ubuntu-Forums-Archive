---
title: "Atheros AR5008"
date: 2010-01-28
forum: Server Platforms
---

### Post by whaskes on 2010-01-28
Hi all!

I bought an atheros ar5008 wificard.

I installed Ubuntu Server 9.10 Carmik but the iwconfig or ifconfig don't see the card, only the lspci. i tried the ath9k driver, but nothing did not yield a result.

how can i install the card driver? 

[COLOR=#000000][FONT=Segoe UI][SIZE=3]wifi card: 02:00.0 Ethernet controller: Atheros Communications Inc. AR5008 Wireless Network Adapter (rev 01)[/SIZE][/FONT][/COLOR]

motherboard: [COLOR=#000000][FONT=Segoe UI][SIZE=3]Intel D945gsejt

thank you for any idea!

regards!
[/SIZE][/FONT][/COLOR]

---

### Post by whaskes on 2010-01-29
hallo?

---

### Post by Erik500002 on 2011-06-28
Have you tried running in terminal sudo modprobe ath9k? That should load up the drive although seems very strange ubuntu automatically activates drivers when a device is detected.

---

