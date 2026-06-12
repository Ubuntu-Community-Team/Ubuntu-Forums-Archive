---
title: "Cannot start rpc.nfsd -- operation not permitted"
date: 2006-11-15
forum: Server Platforms
---

### Post by 88CV on 2006-11-15
Hello,

I have just apt-got nfs-user-server 2.2beta47-22.  It installed fine, but did not start.  I am running Kubuntu Dapper Drake 6.06.1 LTS on a Celeron 500MHz Mendocino with a 100MHz FSB.  40GiB main disk (where the main disk layout is) and a 100GiB secondary disk (where I want to export from).

I don't know why but I keep hitting a brick wall with NFS.  ](*,) 

This should provide all the information you need:

> **"Terminal"]
awilcox@NAMERICA1:/sbin$ sudo rpc.nfsd
Password:
Cannot register service: RPC: Unable to send said:**
>  (rev 02)
0000:00:01.0 VGA compatible controller: Intel Corporation 82810 DC-100 CGC [Chipset Graphics Controller] (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801AB PCI Bridge (rev 01)
0000:00:1f.0 ISA bridge: Intel Corporation 82801AB ISA Bridge (LPC) (rev 01)
0000:00:1f.1 IDE interface: Intel Corporation 82801AB IDE (rev 01)
0000:00:1f.2 USB Controller: Intel Corporation 82801AB USB (rev 01)
0000:00:1f.3 SMBus: Intel Corporation 82801AB SMBus (rev 01)
0000:01:05.0 Multimedia audio controller: ESS Technology ES1969 Solo-1 Audiodrive (rev 01)
0000:01:08.0 Serial controller: Rockwell International HCF 56k Data/Fax Modem (rev 01)
0000:01:09.0 Ethernet controller: D-Link System Inc RTL8139 Ethernet (rev 10)
0000:01:0a.0 Ethernet controller: 3Com Corporation 3c905B 100BaseTX [Cyclone] (rev 30)
root@NAMERICA1:/sbin#


I await your reply.

Andrew

---

### Post by fnjordy on 2006-11-18
Is portmap actually running?

---

