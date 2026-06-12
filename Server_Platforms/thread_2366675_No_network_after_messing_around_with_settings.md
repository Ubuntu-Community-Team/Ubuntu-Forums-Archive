---
title: "No network after messing around with settings"
date: 2017-07-20
forum: Server Platforms
---

### Post by nnielsen on 2017-07-20
So I tried to configure a bridge network in KVM, which failed miserably. I lost all connections to my server and I haven't been able to get it up and running since. 
It's a Ubuntu 16.04 Server and it have been running for a few months by now. 

When I boot the machine, the network interface does not establish a connection to my switch (no blinking light on the switch or on the port). I assume this is because the lacking entry in /etc/network/interfaces - but more on that later. 

This is my output from ifconfig: 

> 
ifconfig

enp37s0 Link encap: Ethernet HWaddr: [Removed]
UP BROADCAST MULTICAST MTU:1500 Metric:1 
RX packets: 0 errors:0 dropped:0 overruns:0 frame:0
TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0B) TX Bytes:924 (924.0 B)

lo Link encap: Local Loopback
inet addr:127.0.0.1 Mask: 255.0.0.0
RX packets:9567 errors:0 dropped:0 overruns:0 frame:0
TX packets: 9567 errors:0 dropped:0 overruns:0 carrier:0 
collisions:0 txqueuelen:1000 
RX bytes:2085469 (2.0 MB) TX bytes:2085469 (2.0 MB)


If I cat my /etc/network/interfaces, it looks like this: 

> 
source /etc/network/interfaces.d/*

auto lo
iface lo inet loopback

Maybe I should mention that /etc/network/interfaces.d/ is an empty folder, I am not sure how it's used.

When I initially started debugging the problem, virbr0 was mentioned in /etc/network/interfaces, however I removed it in the hopes of fixing the issue. 
I tried to insert: 
auto enp37s0 
iface enp37s0 inet dhcp
into the interfaces file, but no luck with that either. 

I am kinda lost by now, so any help would be appreciated.

---

### Post by Michael_McKenney on 2017-07-20
Try getting a cheap network adapter and installing it in a slot.   I picked one up for $20 at Microcenter.

---

### Post by nnielsen on 2017-07-20
> **Michael_McKenney said:**
> Try getting a cheap network adapter and installing it in a slot.   I picked one up for $20 at Microcenter.
Hmm, you mean for debugging? 
I have a USB one laying around, worst case. 

However, I would obviously love to get my built-in network card working again, as it worked perfect for months.


Edit: 
I tinkered a bit more and it seems like I am able to run tcpdump and capture packages from the network. So it seems like the network card work as intended, but I still don't get an IP or access to the network.

---

### Post by nnielsen on 2017-07-20
Okay... No idea, but it suddenly worked. I have no idea what I did different, but it works..

---

### Post by Michael_McKenney on 2017-07-20
I had the onboard nic stop working after an upgrade.   I installed a PCIe NIC to get it up and running till I could figure out why.   Good news, its working.

---

### Post by ajgreeny on 2017-07-20
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

