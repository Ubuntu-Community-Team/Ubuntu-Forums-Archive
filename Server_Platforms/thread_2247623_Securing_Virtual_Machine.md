---
title: "Securing Virtual Machine"
date: 2014-10-09
forum: Server Platforms
---

### Post by daniel201 on 2014-10-09
Hi,

I'm sorting out my infrastructure at home. 

I currently have a mail server running on Syno NAS box and an Apache server running on a netbook, both using Port Forwarding.
I am planning to migrate these to a KVM virtual machine running Ubuntu. This is hosted on the Ubuntu Server.

I'm a bit concerned that if the virtual machine is compromised than the host machine and other machines on the network could be compromised*. To help counter this threat, I was thinking about running an internal VPN with virtual interfaces on the virtual machine and the pfSense firewall. Is this feasible?

What other considerations should I have in terms of hardening Ubuntu Server on the VM itself?

*In an ideal world I would have a separate email/web server attached to a separate interface on the firewall, but this isn't possible without adding a NIC to the firewall and investing in a larger case for it. The extra box would also add to the electric bill!

---

### Post by TheFu on 2014-10-09
This is a HUGE, HUGE, HUGE question that cannot be fully answered in a free forum response. 
Starting with network security is smart and hard to fix later.

Add a NIC. 2 are necessary (if you care about security) - one for the public facing LAN and another for the management LAN (which all systems connect).

If you don't want a guestOS being able to enter promiscuous mode and see all traffic for other VMs, setup separate bridges for each VM.

Lots of other things - general server security stuff - 

Oh - and I'd put the pfsense onto a dedicated hw solution, not into a VM. Too many reasons to list them all for this. A $100 Atom-based box is fine.

---

### Post by daniel201 on 2014-10-09
Thank you TheFu for the response.I'm only planning on a single VM to host web/email - I figure if the VM is allowed to run it's network interface in promiscuous mode then it could be used to monitor all the traffic on that interface? I need to do a bit more research here, I figure. The host does incidentally have two NICs. Once could be the bridged interface and the other could be used for everything else?The PFSense box is real hardware. I picked up an atom board with dual NICs and that sits in an mini ITX case. The interfaces at the minute will be WAN and LAN. I could add an additional NIC to the pfSense box but that means investing in a larger case too.I clearly have some more reading to do - any recommended links?Thanks again.

---

