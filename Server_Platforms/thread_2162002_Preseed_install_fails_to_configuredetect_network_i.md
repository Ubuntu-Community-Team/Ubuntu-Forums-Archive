---
title: "Preseed install fails to configure/detect network interfaces properly"
date: 2013-07-12
forum: Server Platforms
---

### Post by eclay on 2013-07-12
Hello,

I've been struggling with getting a preseed install of ubuntu 13.04 to function properly on some Intel i3 E312x0 servers.  What appears to be happening for these systems is that we specify the netcfg/choose_interface=ethx to the appropriate interface as we have since ubuntu 10.  But when we pxe boot the server up it downloads the PXE kernel/initrd and loads them into memory and starts the install but then fails on configuring the network.  When I go to tty2 and start checking around I've found that there is no device called ethx, only a p1px and emx devices ( substitute x with 1 or 2).  Once I attempt to manually configure the network interface, never lets me select which interface to use, I can go back to tty2 and execute dhclient p1px for the appropriate interface.  The ip addr list command shows that an IP address was received via the dhcp server and I can continue the install without issue.  The 2 models of E312x0 servers I've been working use either the igb or e1000e drivers and there NIC's are either 82580 (igb) or 82574L and 82574LM (e1000e).


igb see p1p1 and p1p2 interfaces
e1000e sees em1 and p4p1

Device names seem to stay the same upon reboot.  p1px and em1 etc.

We have been installing Ubuntu on these types of servers since 10.10 and have not run into this problem before.  Ubuntu 12.04/12.10 i386/amd64 install without issue on these same servers.  

Anyone come across this issue or know how to resolve?

---

