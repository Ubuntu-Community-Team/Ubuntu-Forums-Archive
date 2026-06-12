---
title: "VmWare, Ubuntu, xRDP and Network Issues"
date: 2014-05-10
forum: Virtualisation
---

### Post by Abhay_Nidhi_Sharma on 2014-05-10
Hi All,
 
So we are experiencing something we can't quite figure out.
 
What we have is :
 
ESXi 5.5
Ubuntu 12.04 VMs
xRDP on VMs for RDP access.
iSCSI NAS for VM storage.
vCenter Server (Physical Machine)
VXL Thin Clients running Ubuntu OS
Remmina RDP client on Ubuntu OS
 
The networking is like this:
1) ESXi, NAS are connected to one switch
2) vCenter is connected to a different switch
3) Thin Clients are connected to a third switch
4) All these switches are connected to an L3 switch
 
The issue:
1) Users experience RDP slowness, Drops and Hangs. But the VmWare Performance counters don't show anything.
2)  We were thinking it might be a network issue, so we did was to RDP to  VM and run Video on the VM. From the Labs where the Thin Clients are, we  start experience ping drops, upto 60%.
    From the vCenter PC, we do RDP to even 10 of these VMs and run Ping tests, no loss.
 
We  have tried to advice the client that is something on their network  infrastructure that's causing it, but they don't agree. They are saying  if they use a Windows Physical Machine, put into switch connected to  ESXi's switch and RDP it from the ThinClients and run the Video, no Ping  Drops again.
 
We  are sure its their network but don't if its at VmWare side or physical  network side. We need to prove either way to move forward.
 
Any suggestions will be much appreciated.
 
Also, please let us know if anyone needs any logs to check the issues.

---

