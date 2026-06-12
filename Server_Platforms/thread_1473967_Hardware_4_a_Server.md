---
title: "Hardware 4 a Server"
date: 2010-05-05
forum: Server Platforms
---

### Post by si907 on 2010-05-05
Hi Again now different question. 

Need some advice about  what kind of hardware(for "server") to buy or which configuration i will need for:

Office LAN of max 10 users (windows xp - windows 7):

Users work on server direct  (word excel documents)
server is connected to 100 mbit  switch like other lan users
server use tapes or another hd for backup or something else ;p???
server does another remote backup for remote dedicated server - rsync
i thinkin to setup a group policy for shared resources -files???
of course use UBUNTU for that :)

which version of Ubuntu server to use ???

Regards 

Simon

don't have to be real server but maybe just some specks for RAM PROCESSOR HD MAINBOARD  so i will build it from parts :)

---

### Post by dudumomo on 2010-05-05
You don't need a big machine for that.
According to your need, you can go for 2x 500GB 7200 tr/m HD in RAID (RAID1 may be ?)
For the RAM, 2GB is far enough (1gb should be too, as you plan to use few software)
For the proc, a sigle core P4 seems enough too...

But If I were you, I would go for a dualcore (ATOM for low consumption, or E5200/E5300 for good value) + 2GB of ram to be large.

I bought my server 2 months ago (For my website + Mail + FTP + Torrent + ...), I have an ITX MB with an E5300 + 2GB of ram + 250gb 5200tr/m 2.5.
I don't use half of my memory and my proc is far underused (But I'm using BOINC to help the science with the remaining)

---

### Post by tgalati4 on 2010-05-05
Lots of older Dell poweredge and HP proliant servers floating around.  I picked up a Dell Poweredge 1750 for $300 US.  3 disk drives, Dual Xenon (4 cores), real RAID, decent powersupply with provision for 2nd power supply.  Dual gigabit NIC's.

Runs hardy server just fine.

---

### Post by intel on 2010-05-05
A few quick pointers

a) Setup  RAID1(atleast 2 HDDs), investigate LVM as it will allow you to seamlessly grow storage over time without disturbing your current setup.
b) Use Ext4 (with journaling, ordered etc be safe not sorry)
c) Its a file-server which does not require big CPU power, so save money here
d) network I/O will he high, get atleast 2 NICs (gigabit) and bond them to increase network throughput.
e) Setup user quotas for file-server space management in samba, assuming you are authenticating users against an existing AD, else get likewise and setup a LDAP solution.
f) Make sure file-server has its own UPS, and that it triggers shutdown when battery is low.

---

