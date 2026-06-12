---
title: "Server KVM bridging"
date: 2009-07-08
forum: Virtualisation
---

### Post by patryk77 on 2009-07-08
```
vnet0     Link encap:Ethernet  HWaddr 02:21:4c:17:7f:a3  
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21:4cff:fe17:7fa3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:102 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2455 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:4500 (4.5 KB)  TX bytes:169613 (169.6 KB)

vnet1     Link encap:Ethernet  HWaddr 52:60:0b:75:22:e8  
          inet6 addr: fe80::5060:bff:fe75:22e8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:328 (328.0 B)

```

These are the vnet devices I have on my server, running Ubuntu Jaunty.

I built my VPS using vmbuilder as per the instructions in the server guide.

I set an IP address, and all the other information.

vnet0, I added to /etc/network/interfaces with all the settings.

If I assign 192.168.1.2 to vmbuilder, I can't connect it. If I assign the same IP to vmbuilder and to vnet0, I can SSH into it, but I am just connecting to the host system and not the guests.

vnet1 appears automatically when I start my VPS, but it has no IP address assigned on the host.

Pinging the guest system returns Destination Unreachable

Should my virtual connections show an IP on my Host system?

How can I make the bridge work on it?

The MAC address of the virtual eth0 shows up when I run 'brctl showmacs br0', with br0 being the bridge between physical eth0 and my virtual machines.

---

