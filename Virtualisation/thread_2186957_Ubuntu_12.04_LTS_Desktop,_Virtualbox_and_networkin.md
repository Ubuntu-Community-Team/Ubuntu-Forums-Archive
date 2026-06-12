---
title: "Ubuntu 12.04 LTS Desktop, Virtualbox and networking"
date: 2013-11-10
forum: Virtualisation
---

### Post by mr.coolerer on 2013-11-10
I'm trying to install pfSense to act as a firewall to my network and my ubuntu box.

I've installed the version of virtualbox in the ubuntu repositories, have a VM Setup with the following settings 
1024 MB ram
Enable IO APIC
No Audio
PAE/NX Enabled, Accelleration Enabled
No USB
3 Network Devices
1 Bridged to eth0 WAN interface, ip assigned by DHCP
2 Bridged to eth1 LAN interface, static IP
3 Host Only.

My issue is this; after pfsense is installed and configured the DHCP server on my SOHO router assigns the virtualbox an ip address, but i cant ping it from the host howerver i can ping the host from the VM. Its the same story with the LAN and host only interfaces too.

I feel like I'm overlooking something basic, could you help a brother out?

---

### Post by houstonbofh on 2013-11-10
Two points...

By default, pfSense blocks private IP traffic on WAN.  Unblock that.

You are trying to learn, and trouble shoot several products at once.  Find an old computer that can run anything of value anymore and learn pfSense on that.  After it is working, you can start trying to virtualize it.  It will make more sense that way.

---

