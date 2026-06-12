---
title: "RTL8101E SLOW transfer speeds"
date: 2009-08-06
forum: Server Platforms
---

### Post by dniesen on 2009-08-06
Freshly installed Ubuntu Server x86 8.04.3 and currently performing the first dist-upgrade since install and only getting 2792B/s over a 3MB DSL connection (yes, BYTES).  These speeds aren't limited to any specific internte servers.


It is running the following kernel:

2.6.24-24-server #1 SMP Tue Jul 7 20:21:17 UTC 2009 i686 GNU/Linux

This is the Ethernet controller:

Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 02)

ethtool reports:

driver: r8169
version: 2.2LK
firmware-version:
bus-info: 0000:01:00.0


Other machines on the network are pulling expected speeds.  I tried different switch ports and network cables just to be sure.

Nothing in dmesg/syslog looks suspicious.  Just getting the link up/down messages when I try plugging into different ports.  

Pings to various internet sites are between 30/40ms.

What else can I do to troubleshoot this issue?  I have more than a few hours before the dist-upgrade packages download and am kind of crossing my fingers that a kernel update will somehow resolve this.

---

