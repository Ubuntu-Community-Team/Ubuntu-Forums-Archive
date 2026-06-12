---
title: "HA Virtual IP on 18.04 Not Pingable outside of VLAN"
date: 2020-01-24
forum: Server Platforms
---

### Post by johnkiddjr on 2020-01-24
I'm trying to setup high availability between 2 servers running 18.04LTS using Corosync and I'm having trouble being able to ping a virtual ip address I want to have assigned to the primary server from outside it's VLAN.

For clarity: the IP assigned to this server for it's physical server is pingable and reachable normally, the virtual ip is the one that does not seem to work outside it's vlan.

I set the virtual IP as such:

```
crm(live)configure# primitive virtual_ip ocf:heartbeat:IPaddr2 params ip="10.68.84.23"  

```

When I run the command "ip a" on the primary server, I do see the address listed on the interface:

```
4: eno3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether b0:26:28:f7:6a:86 brd ff:ff:ff:ff:ff:ff
    inet 10.68.84.239/24 brd 10.68.84.255 scope global dynamic eno3
       valid_lft 603401sec preferred_lft 603401sec
    inet 10.68.84.23/24 brd 10.68.84.255 scope global secondary eno3
       valid_lft forever preferred_lft forever
    inet6 fe80::b226:28ff:fef7:6a86/64 scope link
       valid_lft forever preferred_lft forever

```

The IP can be pinged from inside the same VLAN as the server, but for anyone outside (where the clients are that will be connecting with this IP) it cannot be pinged.

Any ideas?

---

### Post by LHammonds on 2020-01-24
You need 4 IP addresses.  Three IP addresses need to be normal LAN-only IPs and each server needs to be watching the other servers non-virtual IP to determine availability.  The other is an external IP that is accessible on the Internet and is pointed to your firewall.

The virtual IP should be setup in your firewall so that the external IP routes to your firewall and then gets translated (port forwarding) to the internal virtual IP.

LHammonds

---

### Post by johnkiddjr on 2020-01-24
I don't need anything internet facing at all, this is only about being able to communicate from 1 VLAN to another.

The clients are on VLAN 7, server on VLAN 1. Server IPs can be pinged and services are accessible by anyone internal no matter the VLAN, the virtual IP is only accessible on the same VLAN as the server.

As far as monitoring which servers are up, that's what Corosync does. My issue is with the virtual interface not being accessible outside the server VLAN.

---

### Post by LHammonds on 2020-01-24
Ah, gotcha.  Not sure why the VIP is not accessible from the other VLAN.  My servers/workstations are on different VLANs and I did not see such an issue when accessing the VIP from workstations.

The 1st place I would look is the VLAN configuration as well as any firewall rules you have setup on your servers that might be blocking communication (or just lower the shields for a bit and see if that allows connectivity from workstations)

LHammonds

---

### Post by darkod on 2020-01-24
Do you have something that is routing the traffic between the VLANs? You do know that VLAN stands for Virtual LAN, right?

Having two VLANs and expecting tham to talk to each other by default is the same like having two physical LANs and expecting them to communicate. They can never do that without a router that will have interface (IP) in each of the LANs and that will be routing the traffic between them.

---

