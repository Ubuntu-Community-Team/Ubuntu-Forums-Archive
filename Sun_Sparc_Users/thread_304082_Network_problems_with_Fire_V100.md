---
title: "Network problems with Fire V100"
date: 2006-11-21
forum: Sun Sparc Users
---

### Post by can2002 on 2006-11-21
After a few problems last week I managed to get Edgy installed on a Fire V100 last week; however I've been experiencing problems with the inbuilt network cards.

The Tulip driver is loading, but I'm noticing big latency problems.  A basic ping to a box on the same (unloaded) subnet is consistently taking 1000ms, with pretty much everything on the network demonstrating similar latency.

I've done an 'apt-get update' followed by and 'apt-get upgrade', but this has made no difference.

I've check the port settings on the switch (a FastEthernet blade on a Cisco 4506), which were set to auto speed/duplex.  No input output errors are being reported.

I've seen some posts suggesting the dmfe driver is unreliable, but then I've also seen other postings suggesting that people have had problems with the tulip driver, so I'm not really sure which way to go now.

Has anyone else experienced anything similar?

Cheers,
Chris

---

### Post by ler0y on 2006-12-01
I am having the same exact issue with a Netra X1. I am using a known good cable and known good port on the switch. 
I find it odd that the TX packets are at 0 with the TX errors are  in line with the carrier count. I have no clue.. ANYONE have an idea? ](*,) 

# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:03:BA:0F:A5:3E
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:baff:fe0f:a53e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2261 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:233 dropped:0 overruns:0 carrier:233
          collisions:0 txqueuelen:1000
          RX bytes:160938 (157.1 KiB)  TX bytes:0 (0.0 b)
          Interrupt:192 Base address:0x100

---

### Post by cwinslett on 2006-12-04
The funny thing is:

eth1 != eth0

What I mean is, the hardware network interfaces listed on the back of the box do not match the software eth0, eth1, eth2, and eth3 interfaces.

Try different interfaces associations between the hardware and software interfaces.

---

### Post by ler0y on 2006-12-05
> **cwinslett said:**
> The funny thing is:

eth1 != eth0

What I mean is, the hardware network interfaces listed on the back of the box do not match the software eth0, eth1, eth2, and eth3 interfaces.

Try different interfaces associations between the hardware and software interfaces.

Yup... caught that right after the install.. that screwed with my head. I will switch around the cabling when I get back in town to the box so I can rule out the port being hosed. 
This part I do not get.. there are no TX packets being logged. 
> 
RX packets:7602 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:1015 dropped:0 overruns:0 carrier:1015

I can shell into the box, so obviously there are packets going out...

---

