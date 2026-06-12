---
title: "Ubuntu 12.04 Share it's internet connection"
date: 2013-08-31
forum: Server Platforms
---

### Post by Selcuk_Demirci on 2013-08-31
Hello All,

I have two Ubuntu Servers.
Server 1 - Ubuntu: 
- eth0 = internet connection to router
- eth1 = connected directly to second ubuntu server

Server 2 - Ubuntu:
- eth0 = connected to server 1

I want to share the eth0 connection on ubuntu server 1 to ubuntu server 2. 
So if 
eth0 @ server 1: 192.168.1.3

i want eth0 @ server 2: 192.168.1.4

How can i do this?

---

### Post by ibjsb4 on 2013-08-31
I have not use ICS on a server so all I can offer you is a link.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=share+internet+ics+ubuntu+server&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=share+internet+ics+ubuntu+server&sa=Search&cof=FORID:9)

Hope it helps :)

---

### Post by houstonbofh on 2013-08-31
Are you trying to connect both systems in a peerage type araingment, or turn server 1 into a router?

If you just want a glorified switch, this might help the most. [https://help.ubuntu.com/community/KVM/Networking#Creating_a_network_bridge_on_the_host](https://help.ubuntu.com/community/KVM/Networking#Creating_a_network_bridge_on_the_host)  You will need to adapt it of course, but something like this should work...
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
# Comment out next line to make Network Manager happy
# auto eth0
iface eth0 inet manual

iface eth1 inet manual

# The bridge interface
auto br0
iface br0 inet dhcp
        bridge_ports eth0,eth1
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0

```

---

### Post by Selcuk_Demirci on 2013-10-14
I want to bridget eth0 to eth1 so eth0 is the incoming internet line.
eth1 cable is going to the second computer that needs to be on the network 
but the both computers can write/read to eachother directly then.

---

### Post by spynappels on 2013-10-15
Probably the simplest way to do this is to use the first computer is the router, routing outbound (Internet bound) packets from computer 2 (or any other computer down the line) from eth1 to eth0.

To give you more detailed instructions, you need to tell us a little bit more about your setup:

1. Will eth0 on the first computer get it's IP from the WAN by DHCP or will it have a static IP?
2. Will the LAN (internal between the 2 computers) IP addresses be static or would you like them to be assigned dynamically?
3. Do you want to be able to add other computers later to all share the same connection?

---

### Post by houstonbofh on 2013-10-16
If your ISP will allow two computers and give you two IPs, you can just bridge it.  If not you will need to set up a router and NAT.

---

### Post by Selcuk_Demirci on 2013-10-17
These are the connections
Connection1:  ISP >> Router >> Ubuntu Server Machine 1 (eth0) Static IP
Connection2:  Ubuntu Server 12.04 Machine 1 (eth1) >> Ubuntu Server 12.04 Machine 2 (eth0)

The problem is with connection 2. I want to reach Machine 2 also from other pc's & machine's that are connected to the router.
Machine 1 and Machine 2 have direct connections with eachother.

---

### Post by houstonbofh on 2013-10-17
If I understand you correctly, the config I posted about with both eth0 and eth1 in it on Machine 1 should work.

---

### Post by SeijiSensei on 2013-10-18
I never use bridging in situations like this.  Put eth1 and the machine(s) behind it in a different IP subnet from eth0.  Enable packet forwarding by uncommenting "net.ipv4.ip_forward=1" in /etc/sysctl.conf.  Run "sudo sysctl -p" to reread that file. Then add a "masquerading" rule using iptables like this:

```
/sbin/iptables -t nat -A POSTROUTING -o eth0 -j SNAT --to-source 192.168.1.3
```

So, we might have
eth0 = 192.168.1.3
eth1 = 192.168.2.1 
machines behind eth1 = 192.168.2.2-254

More details here: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

