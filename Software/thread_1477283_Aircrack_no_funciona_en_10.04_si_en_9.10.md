---
title: "Aircrack no funciona en 10.04 si en 9.10"
date: 2010-05-08
forum: Software
---

### Post by Nicolas_Rocchia on 2010-05-08
Intentando usar aircrack no puedo usarlo. en ubuntu 9.10 me funcionaba de 10 pero cuando
actualize a 10.04 dejo de funcionar! esto es lo que sale

$ sudo airmon-ng start eth1
 Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!
 PID	Name
833	avahi-daemon
834	avahi-daemon
847	NetworkManager
885	wpa_supplicant
2452	dhclient
Process with PID 2452 (dhclient) is running on interface eth1
 Interface	Chipset		Driver
 eth1		Unknown 		wl (monitor mode enabled)
 $ sudo airodump-ng eth1
ioctl(SIOCSIWMODE) failed: Invalid argument
 ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start eth1 <#>'
Sysfs injection support was not found either.
 



en ubuntu 9.10 me andaba a la perfeccion aircrack

---

### Post by eddiee99 on 2010-07-03
Tengo el msimo problema en un dell studio 1558 con tarjeta inalambrica broadcom BMC4XX

---

### Post by sergiom99 on 2010-07-04
Nicolas, pone la salida de los comandos lspci y lsusb a ver que tenes.

---

