---
title: "Network slowdown on high torrent uploads..."
date: 2011-06-24
forum: Server Platforms
---

### Post by ross104 on 2011-06-24
Hi!

I have a home server based on Ubuntu Linux 10.04.2.

Hardware:
Motherboard - Asus AT4NM10-I (Intel NM10, PCI)
CPU - Integrated Intel Atom D410
RAM - 2 Gb
Lan - D-Link DGE-528T Gigabit Adapter

Provider gives 8/2 Mbit ADSL connection.

So tried Deluge and Transmission, and integrated or external network card and no luck.

When torrent file is being seeded on top speed network starts freezing, server almost unreachable, video freezing when watching it by LAN from server... etc...

When I pause upload - everything starts working ok!

What can be the problem??

P.S. Network based on gigabit switch and cooper UTP cables...

---

### Post by spynappels on 2011-06-24
You could try limiting the number of upload threads allowed or setting a bandwidth cap on uploads as it sounds like the link is starting to get saturated. Are you using a desktop or server edition, the "based on" in your post is making me wonder....

---

### Post by Grenage on 2011-06-24
Most home routers cannot handle large numbers of connection, which are commonly used with torrents.  You could replace the device, or simply lower the maximum connections per-torrent.  Does the home router also encompass your switch, or is it separate?  While the router would be affected, a separate switch or PC is less likely to be affected.

---

### Post by ross104 on 2011-06-24
Its a headless server based on Ubuntu Server Edition...

Well router is tested by Years of torrenting on a PC :) No network lags or something else where found... And after adding a server and moving torrent activity to it got those issues ...

Ill try to replace router on other and give it a try...

---

### Post by Moneysworth on 2011-06-24
Unless you have routers laying around to try, suggest you cap the number of connections first and see if that helps. Worked wonders in my home environment where dns lookups would get flaky. Throttling bandwidth did not help but capping connections did.

---

### Post by Gyokuro on 2011-06-24
Could be also a hardware problem (NIC  ) as I have a similar system but with an Intel NIC which fully saturate an internal 1GB connection. Could you post a top output and vmstat 5 30 when this behaviour occurs?

---

### Post by ross104 on 2011-07-11
Was digging more on this problem...

So during network slowdown top shows only 10-13% CPU load - so the problem isn't there.

iotop - shows some strange stats
> Total DISK READ: [COLOR="Red"]123.12 K/s[/COLOR] | Total DISK WRITE: 34.63 K/s
marked with red drops to zero during lag... 

I think the problem is in LVM (2 HDD 1+2 Tb) and torrent upload queue but don't know how to find it...

---

### Post by ross104 on 2011-07-12
Bump

---

