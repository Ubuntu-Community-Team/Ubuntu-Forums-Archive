---
title: "Issues with IPv4 on alternate Interfaces"
date: 2012-12-17
forum: Server Platforms
---

### Post by mladoux on 2012-12-17
I've got a strange issue. I've got four interfaces, eth0, eth1, eth3, and eth4 ( there is no eth2 for some reason, don't know if that's important or not ). All four interfaces have got ipv6 and ipv4 ip addresses. Connecting to any ipv6 address on the server performs as expected. Here's where things get weird, when I try to connect to an ipv4 address, only the ipv4 address on eth1 works as expected. The other three interfaces don't seem to be responding to connections. I will show you what my routing table looks like. I've just set up this server, so I've not turned on the firewalls yet. In fact, I've verified that I have no iptables rules and that ufw is disabled.

OS: Ubuntu 12.10 server x64

my routing table:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         188.95.224.1    0.0.0.0         UG    0      0        0 eth1
141.255.188.0   0.0.0.0         255.255.255.0   U     0      0        0 eth3
141.255.188.0   0.0.0.0         255.255.255.0   U     0      0        0 eth4
141.255.189.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0
188.95.224.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1

```

ipconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:16:39:75:76:af  
          inet addr:141.255.189.24  Bcast:141.255.189.255  Mask:255.255.255.0
          inet6 addr: 2a00:16d8:2:300:20e5:69b2:8e10:1a9f/64 Scope:Global
          inet6 addr: 2a00:16d8:2:300:216:39ff:fe75:76af/64 Scope:Global
          inet6 addr: fe80::216:39ff:fe75:76af/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:401526 errors:0 dropped:0 overruns:0 frame:0
          TX packets:562 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:221390343 (221.3 MB)  TX bytes:129613 (129.6 KB)

eth1      Link encap:Ethernet  HWaddr 00:16:f0:e4:79:1a  
          inet addr:188.95.224.32  Bcast:188.95.224.255  Mask:255.255.255.0
          inet6 addr: 2a00:16d8:2:300:216:f0ff:fee4:791a/64 Scope:Global
          inet6 addr: fe80::216:f0ff:fee4:791a/64 Scope:Link
          inet6 addr: 2a00:16d8:2:300:31d7:1bae:e695:77ae/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:419253 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4974 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:228104507 (228.1 MB)  TX bytes:10558938 (10.5 MB)

eth3      Link encap:Ethernet  HWaddr 00:16:a7:81:ac:c8  
          inet addr:141.255.188.195  Bcast:141.255.188.255  Mask:255.255.255.0
          inet6 addr: 2a00:16d8:2:300:216:a7ff:fe81:acc8/64 Scope:Global
          inet6 addr: fe80::216:a7ff:fe81:acc8/64 Scope:Link
          inet6 addr: 2a00:16d8:2:300:181b:aad4:f4b3:af/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:406374 errors:0 dropped:0 overruns:0 frame:0
          TX packets:70 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:223523449 (223.5 MB)  TX bytes:6596 (6.5 KB)

eth4      Link encap:Ethernet  HWaddr 00:16:74:7f:12:84  
          inet addr:141.255.188.77  Bcast:141.255.188.255  Mask:255.255.255.0
          inet6 addr: 2a00:16d8:2:300:4043:ab00:d4b1:2f5c/64 Scope:Global
          inet6 addr: 2a00:16d8:2:300:216:74ff:fe7f:1284/64 Scope:Global
          inet6 addr: fe80::216:74ff:fe7f:1284/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:406540 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:224047426 (224.0 MB)  TX bytes:2124 (2.1 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2592 (2.5 KB)  TX bytes:2592 (2.5 KB)


```

output of ufw
```
ufw status
Status: inactive
```

output of iptables
```
iptables --list
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 
```

at this point there is nothing running on the server, other apache2, not sure what else is relevant at this point.

---

### Post by The Cog on 2012-12-17
Apart from the oddity of having two interfaces in the same subnet, everything looks OK there. I suspect it is a routing issue elsewhere in the network. The only route the server has for nonlocal clients is via 188.95.224.1 - will this happily pass IP traffic back to all callers?

It would be useful to run 
```
sudo tcpdump -e -i all
```
and then try your IPv4 connection to see what packets happen on the wire. Can you post the results of that?

---

### Post by The Cog on 2012-12-17
P.S. 
One possibility going through my mind is that you may have asymmetric routing - a connection coming in over one interface but returning via a different interface (eth1, with your default route). This should not be a problem unless there are other firewalls in the network, whch may not like seeing a connection in one direction only.

---

### Post by mladoux on 2012-12-17
I get an error running that command ```
tcpdump: all: No such device exists
(SIOCGIFHWADDR: No such device)
```

no effect.

---

### Post by mladoux on 2012-12-17
yeah... that would be an issue. I'd like to make sure that if data comes in on one interface, that it should respond on the same interface. How do I make that happen?

---

### Post by mladoux on 2012-12-17
turns out that the command should have been tcpdump -e -i any ( checked the man page ) here's the final readout

```
2388 packets captured
8462 packets received by filter
6043 packets dropped by kernel

```

I don't know if you need the rest of the traffic dump, there was a lot of it. that was less than 5 seconds of traffic.

---

### Post by gosteen on 2012-12-17
Your routing table shows that everything is set to route through the default gateway which is connected only to eth1.  Therefore all traffic will be sent through this interface.  You can receive traffic on other interfaces but sending checks your local routing table and that's where your problem exists.  Your solution is to explicitly set gateways for the other interfaces.

---

### Post by mladoux on 2012-12-17
thank you... let's see if we can't get this working or not now.

---

### Post by The Cog on 2012-12-17
Sorry about the any/all confusion - bad memory on my part. Glad you got it sorted in the end.

> **mladoux said:**
> yeah... that would be an issue. I'd like to make sure that if data comes in on one interface, that it should respond on the same interface. How do I make that happen?

That's not the way routing works. When you get a TCP connection to any of the IP addresses on your machine, that same IP address will issue the reply packets. But which interface the reply will physically be sent from depends on your routing table, which tells the machine which direction to send packets out of in order to reach a given destination (the caller). For the locally connected networks, it will always use an interface directly connected to that network. But for non-local addresses - callers who are further away and connecting *through* one of the local networks, it will use its default route - out via eth1 and 188.95.224.1. 

This means that if packets from a remote host are arriving on an interface other than eth1, you will have an asymmetric route to/from your client, with packets taking one path from client to server and a different path from server back to the client. This is only a problem if you have firewalls in the path firewalls don't like to see only one side of a connection.

You haven't said what IP address the problem client has, or which interface its packets are arriving on, so we can't be sure if asymmetric routing could be the cause. 

If you know the IP address of the problem client, you can narrow down the amount of traffic that tcpdump reports by specifying that we only want traffic to/from that host. I was assuming that since this is a new server there wouldnt be much traffic in the dump. Tty to filter on just your problem client wtih this command (change the final IP address to be the address of the client we're having trouble with):
```
sudo tcpdump -e -i any host 1.2.3.4
```
Yes I do want the detailed data - I want to see which interface the packets are arriving on and the replies are leaving on, and whether the client is on a local LAN or is being routed from further away.

---

### Post by mladoux on 2012-12-20
Finally got this working after some fancy routing. Gosteen got me on skype and was able to fix me up.

---

