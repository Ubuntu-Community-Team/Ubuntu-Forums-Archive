---
title: "High amount of rx dropped packets...exacerbated when using bonding"
date: 2013-03-03
forum: Server Platforms
---

### Post by joeyea3231 on 2013-03-03
I've been wrestling around with this issue for awhile now and so far have come up with nothing to solve it.  I built a new file server at my house and put 2 dual nic Intel 82571EB cards inside of it with the intention of 2 ports being used for the server side network sharing files via NFS and the other 2 ports for filer to filer communications mainly for DRBD synchronization.  The server side is configured to use balance-alb and the private side is balance-rr.  I have another machine connected to the private side using 2 single port Intel 82544GC cards.  After setting everything up (including MTU 9000 on all interfaces), I started running tests with iperf and noticed that both bonds were performing poorly.  Both sides could never get above 700Mb/s and were showing huge amounts of rx dropped packets (3+ million after just a few tests).  I've been concentrating on the private side for the time being and can get line speed when connecting from new server to old and above 900Mb/s the opposite way when setting up each NIC individually without bonding.  Despite getting line speed, I always see very large amounts of dropped rx packets on only the new servers NICs (200,000+ after a few tests).  I'm assuming that bonding is exacerbating the issue and that's why speeds ultimately get alot slower when doing tests over the bonds.
     So far I've tried everything I could find online to include upping tcp_reordering to 127, increasing the rx ring buffer to 512, 2048, and 4096, setting rx_usecs to 10, along with a host of tcp protocol tweaks.  Ethtool shows no errors on the interfaces, however tx_restart_queue is currently sitting at almost 200,000.
     I'd appreciate anyone's insight on this as I was expecting to get closer to 2 gigabit speed on the private side to improve throughput for DRBD.

---

