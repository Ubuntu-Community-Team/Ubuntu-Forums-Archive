---
title: "Can't get traffic to talk"
date: 2012-11-15
forum: Virtualisation
---

### Post by TheFuzz4 on 2012-11-15
So let me do my best here to explain what I have going on. 

At home I have 2 HP DL 385 G1.  One is configured with ESXi and it has 1 NIC connected to the WAN and the other the LAN.  
Running on ESXi I have several VMs including my firewall which is made by Astaro (If you don't know what it is, go check them out [www.astaro.com]("http://www.astaro.com") its free for home use)  The Astaro has 3 Virtual NICs one for LAN, WAN and DMZ.  The LAN and DMZ actually share the same physical NIC just different subnets.
So now onto the other DL 385.  This one is running Ubuntu 12.10 with KVM.  Inside of KVM I have another Astaro machine running that is identical in configuration to the first.  The reason for the second one is that its my standby so when I install updates on either the firewall or the ESXi host my internet stays up.  So when a failover happens everything on the LAN functions just like it should, but if I'm outside of my network and I'm attempting to hit a website or something that goes from the DMZ to the LAN I cannot.  I also cannot remote desktop from my DMZ machine to the LAN either.  Now I can ssh in to a DMZ ubuntu machine that is on the same host but I can't go anywhere from there except to the host.  So I'm at a loss here as to what I need to change in my configuration to get DMZ traffic to forward from my guest VMs through the DMZ back to the LAN.  Here is a copy of my interfaces file
```

auto eth0 eth0:1
iface eth0 inet static

iface eth0:1 inet static
    address 192.168.2.8
    network 192.168.2.0
    netmask 255.255.255.0
    broadcast 192.168.2.255
    gateway 192.168.2.1

#LAN
auto br0
iface br0 inet static
    address 192.168.1.139
    network 192.168.1.128
    netmask 255.255.255.128
    broadcast 192.168.1.255
    gateway 192.168.1.129
    bridge_ports eth0
    bridge_stp off
    bridge_fd 0
    bridge_maxwait 0

#WAN
auto eth1
iface eth1 inet manual

auto br1
iface br1 inet dhcp
        bridge_ports eth1
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0

```

I do appreciate everyones help with this and I am sure that its probably just something stupid that I'm missing somewhere.

---

### Post by dcstar on 2012-11-18
> **TheFuzz4 said:**
> 
..........
So I'm at a loss here as to what I need to change in my configuration to get DMZ traffic to forward from my guest VMs through the DMZ back to the LAN.
..........
I do appreciate everyones help with this and I am sure that its probably just something stupid that I'm missing somewhere.

I suggest you get basic networking functioning on your Firewall device. The whole reason of a DMZ is to restrict traffic to the LAN.

---

