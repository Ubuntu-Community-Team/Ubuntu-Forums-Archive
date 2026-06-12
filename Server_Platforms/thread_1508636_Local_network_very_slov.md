---
title: "Local network very slov"
date: 2010-06-13
forum: Server Platforms
---

### Post by imjakes on 2010-06-13
Setup.

Machine 1:
Windows vista, using vireless, 1Gb netcard.

Machine 2:
Ubuntu commandline server directly connected to router, 1Gb netcard.

Router is only a 1Gb router.

/etc/network/interfaces look like this:
> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
pre-up /usr/sbin/ethtool -s eth0 speed 1000 duplex full


ifconfig looks like this:
> 
jakes@jakes-server:/etc/init$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:63:f9:31:b1
          inet addr:192.168.111.5  Bcast:192.168.111.255  Mask:255.255.255.0
          inet6 addr: fe80::240:63ff:fef9:31b1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:110936260 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63650313 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:559802662 (559.8 MB)  TX bytes:210906450 (210.9 MB)
          Interrupt:28 Base address:0xe800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2514 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2514 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:297596 (297.5 KB)  TX bytes:297596 (297.5 KB)

virbr0    Link encap:Ethernet  HWaddr be:d1:3a:f9:77:2b
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::bcd1:3aff:fef9:772b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:215 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:47899 (47.8 KB)



I have tryed using samba and ftp and both have the same transfer rate at around 1,5Mb

Any suggestions to whats wrong?

/Jakes

---

### Post by cariboo on 2010-06-13
I would suggest installing iperf on both systems, it is in the repositories for your server, and available [here]("http:///www.noc.ucf.edu/Tools/Iperf/"). It is a command line app for both Windows and Linux.

On the server start iperf by issueing this command:

```
iperf -s
```


Then on the Windows system open a cmd window and type:

```
iperf -c <server>
```

WHere <server> is either your server name or ip address. You should get and output similar to this:

```
iperf -c willy
------------------------------------------------------------
Client connecting to willy, TCP port 5001
TCP window size: 43.4 KByte (default)
------------------------------------------------------------
[  3] local 192.168.1.225 port 49085 connected with 192.168.1.250 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec    112 MBytes  94.2 Mbits/sec
```

I have a 100Mbps network, so the above result is acceptable. Using the above utility will tell you if the problem is with your network, or the programs you are using.

For more options check man iperf.

---

### Post by imjakes on 2010-06-14
Tryed to use iperf and this is the result:


On windows vista machine
> 
C:\vmware>iperf -c jakes-server
------------------------------------------------------------
Client connecting to jakes-server, TCP port 5001
TCP window size: 8.00 KByte (default)
------------------------------------------------------------
[336] local 192.168.111.6 port 62795 connected with 192.168.111.5 port 5001
[ ID] Interval       Transfer     Bandwidth
[336]  0.0-10.0 sec  14.6 MBytes  12.2 Mbits/sec


On ubuntu server
> 
oCAL$ sudo iperf -s
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.111.5 port 5001 connected with 192.168.111.6 port 62795
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.0 sec  14.6 MBytes  12.2 Mbits/sec



So it looks like the problem is the network?

Any ideas to what i can do?

---

### Post by imjakes on 2010-06-18
Any ideas?

---

### Post by clrg on 2010-06-18
You are getting 12.6Mbit/s. That is average for a 802.11g wireless network. If you need faster data transfer, use a Cat5 LAN cable.

---

