---
title: "Ubuntu with Motorola wireless modem"
date: 2012-05-12
forum: Server Platforms
---

### Post by RefinersFire on 2012-05-12
I need to DMZ my Ubuntu server/desktop, but I can't get a local 192.168.0.* IP. ifconfig shows wlan0 as my ISPs IP address. When I look in my Motorola SBG6580 wireless modem's Access Control, it shows:

```
MAC Address 	 Age(s) 	 RSSI(dBm) 	 IP Addr 	 Host Name 	 Mode 	 Speed (kbps);
00:15:E9:F6:F8:*	0	-40	63.135.15.*	Static IP	g	54000
```
MAC & IP address changed by me to protect my system.

No matter how I configure Ubuntu, I can't get a 192.168 IP address, or when I do, I can't get to an external network.

Somehow, IMAP & POP3 ports are getting blocked by either the modem, or my ISP (tech support doesn't know anything).

---

