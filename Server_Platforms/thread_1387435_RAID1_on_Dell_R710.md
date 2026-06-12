---
title: "RAID1 on Dell R710"
date: 2010-01-21
forum: Server Platforms
---

### Post by engpeter on 2010-01-21
[SIZE=2]Hi guys,

We're planning to buy a new Dell R710 server, with dual disks (1TB each).
We will use it as FTP Server for storage, using RAID1-Mirroring.

My question is:
1) Is "[FONT=Arial]SAS 6i/R Internal  Controller Card RAID" considered as Hardware RAID or fake RAID?

2) Configuring RAID-1 on the Ubuntu Server 9.10, is straight forward? ANY issues reported?

3) Is the RAID chip automatically recognized by Ubuntu 9.10?


Thanks,,,,
Peter
[/FONT][/SIZE]

---

### Post by steven.jones on 2010-01-21
1) Its Real raid...I use SAS disks, tis fine, Ive used satas on the 2950s so I cant see there would be an issue.
2) You wont be configuring raid 1 IN the OS as the hardware raid presents a single 1TB disk to the OS, its a simple install.
3) The raid should be detected fine....I use RedHat or ESXi however.

The Broadcom Nics should be fine as well...you have 4, 2 twin NICs, so if you want to team a pair use ports 1 (eth0) and 3 (eth2) or 2 and 4....not 1 and 2 or 3 and 4 as they are the same chip.

Biggest thing is if Dell supports the Dell tools on ubuntu, if not get a full DRAC with the Dell then you can look at the hardware and hardware logs and reboot it remotely....


regards

---

### Post by Xianath on 2010-01-22
A bit of advice regarding Broadcom NexTreme II NICs. Their TOE ignores /proc/sys/net/ipv4/ip_no_pmtu_disc settings and will *always* perform PMTUd. If your LAN has a MTU of 1500 and your packets cross a segment with a smaller MTU (eg. a PPPeE link, L2TP, PPtP, whatever), AND some wiseguy decided to block ALL ICMP as opposed to rate-limit it and block just the dangerous types, then all your full packets to that destination will be lost. You will almost certainly need to disable TSO on them using ethtool.

Other than that, they are really awesome boxes, and DRAC is a life-saver. Its only downside is that its web console requires Windows to remotely mount media images, but that's nothing vbox can't handle.

HTH,
Peter

---

