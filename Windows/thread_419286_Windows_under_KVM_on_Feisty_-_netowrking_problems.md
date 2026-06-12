---
title: "Windows under KVM on Feisty - netowrking problems"
date: 2007-04-22
forum: Windows
---

### Post by RonnieRonnieRonnie on 2007-04-22
I have installed WinXP under KVM and it works, except that I can't get networking going, which is a showstopper for me.  This is on a recent install of Feisty on an AMD X2 system.  

Some of the VMDKs (VMWare virtual disks) that I have from VMWare Server also launch OK under KVM.  I was able to get networking going fine with various Linux guests.  

Also, I have installed the same WinXP (from CDROM) on VMWare Server and VirtualBox - and it works fine on both those platforms, including networking.

The problem seems to be specific to KVM and WinXP.  In particular, KVM is setting up networking, but Windows doesn't show a LAN connection.  Windows does show a (virtual) NIC card, which I can change based on the -net model= argument I supply to KVM.  However, I can't bring up any interface for the card in Windows.  Everything I try, including getmac, says that the RPC server is not running - but it is.  Could this be a firewall issue?

Anyway, I am up and running, for the moment, on VirtualBox (VMWare is being a PITA about compiling against 2.6.20-15-generic), but I'd really much rather prefer to be using KVM.

Anyone else encountering this problem or have a solution?

Thanks.

---

