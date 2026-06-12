---
title: "HP 400i RAID lesson learned"
date: 2008-05-09
forum: Server Platforms
---

### Post by whit on 2008-05-09
We got a couple of HP DL360s with their 400i RAID built in, and installed Ubuntu Server several months ago. One of them lost two partitions just recently. Long story short - although the system BIOSs were from last October, HP hadn't incorporated updated RAID firmware from the July before. This resulted in partition tables under Linux (any distro really - tried a few others in troubleshooting) that slightly overlapped at the ends, and were not written to cylinder boundaries. In order to get RAID 1 stable in the long term (it took a few months for this overlap to take one system down, and the other - which also has it - hasn't noticeably suffered yet since the overlap is small), it is necessary to update the RAID firmware (which can't be done under Ubuntu - you need to set up a USB key under Windows to do it), then remove the RAID 1 configuration (effectively deleting all data) and then recreate it. At that point Linux partitioning utilities will create clean partitions on it, and the systems will really be worthy of use as servers.

It's the 2.* RAID firmware that's not Linux-compatible. The 4.* RAID firmware works. But despite the 4.* firmware dating from last July, HP was still shipping systems with the 2.* in early 2008. Their telephone support staff has no clue about this either. Nor do their notes on the bugs the firmware upgrades fixed specify this.

Anyway, just wanted to post this in case other Ubuntu users - or other Linux users for that matter - are trying to figure out why their HPs with 400i RAID controllers have lost data. To check whether you've got the problem, the "testdisk" partition utility can be useful. It's in the repositories. If you've already lost data, the System Rescue CD (although Gentoo based) works well over RILO, and includes testdisk.

---

### Post by jgoris on 2010-03-10
I just got a few HP Proliant DL360 G5 with p400i SAS/SATA RAID controller machines second hand. Thanks heaps for the tip.

I also recommend always updating all firmware on a system prior to installing any OS. It can be risky updating RAID controller after the OS is installed. I updated RAID firmware on an Intel server motherboard upon strong advice from Intel's documentation. After the update, Windows Server 2003 wouldn't boot. I had to do a recovery installation to get the system up again. Not that I've ever had such a problem with Linux. :)

---

