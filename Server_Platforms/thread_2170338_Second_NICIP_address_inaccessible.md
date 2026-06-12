---
title: "Second NIC/IP address inaccessible"
date: 2013-08-25
forum: Server Platforms
---

### Post by westingham on 2013-08-25
I recently added a second NIC and IP address to one of my VPS but I am having troubles getting it to setup properly and getting it respond to inquiries.

Here is my setup for /etc/network/interfaces
```

auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
metric 2
address 209.141.43.211
netmask 255.255.255.0
gateway 209.141.43.1
# dns-* options are implemented by the resolvconf package, if installed
dns-nameservers 8.8.8.8 8.8.4.4
dns-search mt-gaming.com

auto eth1
iface eth1 inet static
metric 3
address 198.251.80.25
netmask 255.255.255.0
gateway 198.251.80.1
dns-nameservers 8.8.8.8 8.8.4.4

```

Here is what ifconfig displays
```

eth0      Link encap:Ethernet  HWaddr 00:16:3c:d1:70:e2  
          inet addr:209.141.43.211  Bcast:209.141.43.255  Mask:255.255.255.0
          inet6 addr: fe80::216:3cff:fed1:70e2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16706 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4192 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16856502 (16.8 MB)  TX bytes:555020 (555.0 KB)

eth1      Link encap:Ethernet  HWaddr 00:16:3c:df:54:6d  
          inet addr:198.251.80.25  Bcast:198.251.80.255  Mask:255.255.255.0
          inet6 addr: fe80::216:3cff:fedf:546d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2870 errors:0 dropped:0 overruns:0 frame:0
          TX packets:236 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1042288 (1.0 MB)  TX bytes:12016 (12.0 KB)

```

route -n and ip route show
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         209.141.43.1    0.0.0.0         UG    2      0        0 eth0
0.0.0.0         198.251.80.1    0.0.0.0         UG    3      0        0 eth1
198.251.80.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
209.141.43.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0

```

```

default via 209.141.43.1 dev eth0  metric 2 
default via 198.251.80.1 dev eth1  metric 3 
198.251.80.0/24 dev eth1  proto kernel  scope link  src 198.251.80.25 
209.141.43.0/24 dev eth0  proto kernel  scope link  src 209.141.43.211

```

I can ping google.com with eth0 (*ping -I eth0 google.com*) and everything works fine, but attempting to do with eth1 results in *From 198.251.80.25 icmp_seq=1 Destination Host Unreachable*.

I suspect part of the problem may be that I have two default routes, but I get the same icmp error when I remove the gateway for the second NIC in /etc/network/interfaces. Also, no matter what I do, I am unable to ping the second IP address from the rest of the internet. Could the problem be that I have not yet setup reverse DNS for the second IP address? I didn't think this would be necessary but I'm starting to grasp at straws here.

For what it's worth, the goal here is to have the second NIC/IP address be used as a GRE tunnel to another server. Any and all help would be greatly appreciated.

---

### Post by SeijiSensei on 2013-08-26
Did you enable IP packet forwarding in /etc/sysctl.conf?  By default Ubuntu systems won't forward packets across interfaces.

Can you ping other hosts on the 198.251.80.0/24 network?  Are you testing pings to Google using the "-I eth1" switch to ping?

Machines connected to eth1 will not be able to see the Internet unless you have some type of NAT masquerading enabled.  Pinging from the box itself using "-I eth1" should work, but only if packet forwarding is enabled.

---

### Post by westingham on 2013-08-26
> **SeijiSensei said:**
> Did you enable IP packet forwarding in /etc/sysctl.conf?  By default Ubuntu systems won't forward packets across interfaces.

Can you ping other hosts on the 198.251.80.0/24 network?  Are you testing pings to Google using the "-I eth1" switch to ping?

Machines connected to eth1 will not be able to see the Internet unless you have some type of NAT masquerading enabled.  Pinging from the box itself using "-I eth1" should work, but only if packet forwarding is enabled.

IP packet forwarding is enabled. I am unable to ping other hosts on the 198.251.80.0/24 networking, either from the primary or secondary IP address. Yes, that is the switch I'm using.

---

### Post by SeijiSensei on 2013-08-26
If you cannot ping hosts on the network to which eth1 is connected, you've got a bigger problem.  If you are running an iptables firewall, are you sure you allow full connectivity with the 198.251.80.0/24 network?  Are there any FORWARD rules in iptables that might be blocking traffic?

If you have any masquerading rules, make sure they include an "-o eth0" parameter so that only outbound traffic over that interface is masqueraded.  Masquerading can often block or misdirect other traffic since the source addresses are rewritten.

Is there really no other router between this box and the 198.251.80.0/24 network?  I find that a bit strange since that's a [public]("http://whois.arin.net/rest/net/NET-198-251-80-0-1") subnet.

---

### Post by westingham on 2013-08-26
Pinging any host on the 198.251.80.0/24 network results in ICMP redirect messages. iptables has no entrees in it.

---

### Post by SeijiSensei on 2013-08-26
I traced a route to your eth1 address:

```

traceroute to 198.251.80.25 (198.251.80.25), 30 hops max, 40 byte packets
 1  router1-nac.linode.com (207.99.1.13)  0.489 ms  0.543 ms  0.715 ms
 2  207.99.53.41 (207.99.53.41)  0.678 ms  0.640 ms  0.752 ms
 3  vlan801.tbr1.mmu.nac.net (209.123.10.9)  0.283 ms  0.325 ms  0.397 ms
[...]
 6  equinix.tge4-3.ar1.ewr1.us.nlayer.net (198.32.118.119)  7.715 ms  7.776 ms  7.681 ms
[...]
10  as40065.ae2-415.cr1.sea1.us.nlayer.net (63.141.219.62)  69.678 ms  69.560 ms  69.554 ms
11  198.251.80.25 (198.251.80.25)  88.053 ms  87.959 ms  87.960 ms

```

I next used nmap and found:
```

Interesting ports on 198.251.80.25:
Not shown: 1677 closed ports
PORT    STATE    SERVICE
21/tcp  open     ftp
222/tcp open     rsh-spx
445/tcp filtered microsoft-ds

```
Running nmap against the address on eth0 shows the same open ports.

I'm on a [Linode]("http://www.linode.com/") VM, and I can ping all the hosts in the same "class-C" subnet as me with "nmap -sP nnn.nnn.nnn.0/24".  My DHCP-provided upstream gateway is nnn.nnn.nnn.1.  I don't have a second public IP on this machine, but I do have a number of "tun" (tunnel) interfaces assigned to private IPs that route packets among point-to-point OpenVPN gateways. One of them is a gateway to a client's internal network, and I have a static route set up to forward traffic for that network over the VPN. I have two iptables INPUT rules and two FORWARD rules that permit traffic arriving on "-i tun+" and leaving on "-o tun+" so the machines can send traffic among themselves over the VPN.

I suggest you start by installing **nmap** and **traceroute**, if you have not done so already, and use them to explore what you can see and what you cannot.  Let us know.  

It would also help to know if you need to route packets from the network on eth1 to the network on eth0.  If so, do the machines that connect over eth1 have a route to the network on eth0 that uses your box as a default gateway?  If not, they won't send packets destined for the eth0 network to your box; they'll send them to their default gateways.

---

### Post by westingham on 2013-08-26
I found out what the problem was: apparently my host reserves eth1 for internal traffic only. Once I put my secondary IP address on eth0:1, everything started working beautifully. Thank you for all your help!

---

