---
title: "NIC Bonding Issues possible FIX"
date: 2012-01-08
forum: Server Platforms
---

### Post by red03golf on 2012-01-08
**Disclaimer**:
I'm a noob. I've only converted to Linux in the past year - enjoying it immensely btw. I don't yet know a lot about Linux so if you have any criticisms regarding my findings please be gentle with me.  

This morning I decided to start researching NIC bonding and poured over dozens of sites / pages regaling others' problems and bugs associated with it.

Like so many others out there I could not get it to work for me. But after experimenting with the settings in the /etc/network/interfaces file I think I may have found a solution for situations like mine.

I am running Ubuntu Maverick 10.10 and set up the bonding between the integrated Via VT6120 NIC and an SMC2-1211tx PCI NIC.

In the very least this completely solved my situation and my bond is up and running - very fast I must say.

I don't know if the changes that I have made are right or wrong - perhaps someone with some experience can determine that for the community.

**Here is my /etc/network/interfaces contents:**
```
 # This file describes the network interfaces available on your system
 # and how to activate them. For more information, see interfaces(5).

 # The loopback network interface
 auto lo
 iface lo inet loopback

 # The primary network interface
 auto eth0
 iface eth0 inet dhcp

 auto bond0
 iface bond0 inet dhcp
 address 192.168.1.176
 netmask 255.255.255.0
 bond-slaves eth0 eth1
 # LACP confuration
 bond_mode 0
 bond_miimon 100
 bond_lacp_rate 1
```

I hope this will help some of you out there that have also been struggling with bond issues.

Next thing I would like to do is start researching if / how to tweak the connection and / or settings to see if / what it does to the connection speed - any suggestions / advice would be greatly appreciated.

Let me know if you need any other info about my system / settings / etc.

---

