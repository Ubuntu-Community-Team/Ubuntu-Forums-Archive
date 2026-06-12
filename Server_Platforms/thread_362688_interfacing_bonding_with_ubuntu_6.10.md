---
title: "interfacing bonding with ubuntu 6.10"
date: 2007-02-15
forum: Server Platforms
---

### Post by dionysian_mind on 2007-02-15
I've posted this question in Networking & Wireless, but it doesn't seem to be getting much of a response. Figured I'd bring up the question, here, in hope of a bit of a response.

Following [this howto]("http://www.howtoforge.com/network_bonding_ubuntu_6.10") I've been having some problems getting interfacing bonding to work. Here's my situation:

I am currently trying to set-up interface bonding (round-robin) on ubuntu server 6.10, amd64, kernel 2.6.17, with 1 nvida gigabit card and 2 netgear gigabit cards (note: my experience does not change using only the 2 netgear interfaces). I am currently experiencing two problems:
1.) when bonding is set up, /proc/net/bonding/bond0 sees all three links as up and fine, all three NICs have the appropriate same MAC, but it will only transmit and receive on the primary interface (eth0) and only transmit (but not receive) on the secondary interfaces (eth1 and eth2) resulting in 50% packet loss.

2.) When I attempt to ifconfig bond0 down, or /etc/init.d/networking restart, or unload the bonding module the computer hard-locks (stops pinging and everything). It does not produce any errors that I can find in logs pertaining to this hard-lock.

my /etc/modprobe.d/aliases file has the following section:
```
alias bond0 bonding
alias eth0 e100
alias eth1 e100
alias eth2 e100
options bonding mode=0 miimon=100
```

my /etc/modprobe.d/arch/i386 has the following lines:
```
alias bond0 bonding 
options bonding mode=0 miimon=100 downdelay=200 updelay=200
```

my /etc/network/interfaces looks like this:
```
auto bond0 iface bond0 inet static 
address 10.0.1.253 
netmask 255.255.255.0 
hwaddress ether de:ad:be:ef:ca:fe 
network 10.0.1.0 
broadcast 10.0.1.255 
gateway 10.0.1.1 
post-up /sbin/ifenslave bond0 eth0 eth1 eth2 
down /sbin/ifenslave -d bond0 eth0 eth1 eth2
```

This all produces the following ifconfig output:
```
bond0     Link encap:Ethernet  HWaddr DE:AD:BE:EF:CA:FE
          inet addr:10.0.1.253  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::dcad:beff:feef:cafe/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:78 errors:0 dropped:0 overruns:0 frame:0
          TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:8502 (8.3 KiB)  TX bytes:5238 (5.1 KiB)

eth0      Link encap:Ethernet  HWaddr DE:AD:BE:EF:CA:FE
          inet6 addr: fe80::dcad:beff:feef:cafe/64 Scope:Link
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:42 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4534 (4.4 KiB)  TX bytes:2044 (1.9 KiB)
          Interrupt:50

eth1      Link encap:Ethernet  HWaddr DE:AD:BE:EF:CA:FE
          inet6 addr: fe80::dcad:beff:feef:cafe/64 Scope:Link
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1931 (1.8 KiB)  TX bytes:1587 (1.5 KiB)
          Interrupt:58 Base address:0x4000
eth2      Link encap:Ethernet  HWaddr DE:AD:BE:EF:CA:FE                                         
          inet6 addr: fe80::dcad:beff:feef:cafe/64 Scope:Link
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2037 (1.9 KiB)  TX bytes:1607 (1.5 KiB)
          Interrupt:66 Base address:0x6000

```

the /proc/net/bonding/bond0 looks like this:
```
Ethernet Channel Bonding Driver: v3.0.3 (March 23, 2006)

Bonding Mode: load balancing (round-robin)
MII Status: up
MII Polling Interval (ms): 100
Up Delay (ms): 200
Down Delay (ms): 200

Slave Interface: eth0
MII Status: up
Link Failure Count: 0
Permanent HW addr: 00:50:8d:81:d2:83

Slave Interface: eth1
MII Status: up
Link Failure Count: 0
Permanent HW addr: 00:14:6c:cb:d5:c7

Slave Interface: eth2
MII Status: up
Link Failure Count: 0
Permanent HW addr: 00:14:6c:82:0d:b3
```

and I get ping times that look like this:
```
PING 10.0.1.1 (10.0.1.1) 56(84) bytes of data.
64 bytes from 10.0.1.1: icmp_seq=1 ttl=64 time=0.317 ms
64 bytes from 10.0.1.1: icmp_seq=3 ttl=64 time=0.304 ms
64 bytes from 10.0.1.1: icmp_seq=5 ttl=64 time=0.303 ms
64 bytes from 10.0.1.1: icmp_seq=7 ttl=64 time=0.308 ms
64 bytes from 10.0.1.1: icmp_seq=8 ttl=64 time=0.292 ms
64 bytes from 10.0.1.1: icmp_seq=10 ttl=64 time=0.304 ms
64 bytes from 10.0.1.1: icmp_seq=12 ttl=64 time=0.339 ms
64 bytes from 10.0.1.1: icmp_seq=14 ttl=64 time=0.311 ms
64 bytes from 10.0.1.1: icmp_seq=18 ttl=64 time=0.313 ms
64 bytes from 10.0.1.1: icmp_seq=20 ttl=64 time=0.293 ms

--- 10.0.1.1 ping statistics ---
20 packets transmitted, 10 received, 50% packet loss, time 19006ms
rtt min/avg/max/mdev = 0.292/0.308/0.339/0.020 ms
```

I am incredibly frustrated by this problem. Any body have any ideas?

---

### Post by sefmars on 2007-03-23
options bonding mode=0 miimon=100

this means theat you need sw support from the other side, you have agregated the interfaces , but the sw does not recognize theat , and sends the packests to the interface theat he knows has the acording mac adress

mode=0

    This mode uses the Round-robin policy: Transmit packets in sequential order from the first available slave through the last. This mode provides load balancing and fault tolerance.


P.S. what do you want to do?? because this kind o load balancing offers few things 
1. backup 
2. agregate 2 ethernet  100full duplex in to one ethernet 200full duplex(need support on the other side)


you can try 

mode=6

    Adaptive load balancing: includes balance-transmit load balancing plus receive load balancing for IPV4 traffic, and d**oes not require any special switch support**. The receive load balancing is achieved by ARP negotiation. The bonding driver intercepts the ARP Replies sent by the local system on their way out and overwrites the source hardware address with the unique hardware address of one of the slaves in the bond such that different peers use different hardware addresses for the server.


or


mode=5

    Adaptive transmit load balancing: channel bonding that **does not require any special switch support**. The outgoing traffic is distributed according to the current load (computed relative to the speed) on each slave. Incoming traffic is received by the current slave. If the receiving slave fails, another slave takes over the MAC address of the failed receiving slave.

---

### Post by Icidic on 2007-03-24
Hmm... I saw an article recently on how to do NIC Bonding\Teaming on Debian - I think if you Googled it a bit, you might find it :).

If only Windows had support for this, even if it is software based :( ...

---

