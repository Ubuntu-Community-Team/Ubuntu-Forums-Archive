---
title: "samba speed?"
date: 2009-10-06
forum: Server Platforms
---

### Post by artheus on 2009-10-06
Copying my files from my ubuntu-desktop to my ubuntu-server (via samba) runs with a speed of 1.1 Mb/s.. Even though I've got a 100Mbit network (both router and network cards).

Are there any way of speeding this up?

It's the same thing for the windows-machines in the network (those are the reason I'm using samba, and not NFS).

Cheers,
Artheus

---

### Post by Groover20 on 2009-10-06
I had a similar problem, and solved it by using SSH. If you go to Places - Connect to Server. You then select SSH, type in the server's name or ip adresse, the user name you want to use on the server, and then connect.  It will prompt you for a password.  Simply key it in, and you are good to go.

---

### Post by artheus on 2009-10-06
Hmm.. nope.. Still 1.1 Mbit..
:/

---

### Post by Groover20 on 2009-10-06
Can you post your iwconfig?

---

### Post by artheus on 2009-10-07
This?

```

artheus@gilbert:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

vboxnet0  no wireless extensions.

pan0      no wireless extensions.

```

Otherwise I've got no idea of where to find iwconfig.
(I'm newb)

---

### Post by Xianath on 2009-10-07
Please post ifconfig and ethtool output for the network interface in question (eth0 or eth1).

Also, is your router in between your client and server? Those things can't really cope with a lot of traffic especially if you have traffic shaping, monitoring or packet stateful inspection in place. Most of them run a measly 200MHz MIPS processor -- good enough for ADSL.

If you only have one server and one client, consider using a dedicated network (i.e. a crossover cable in this case). You should be able to get up to >90MB/sec on a gigabit connection, provided that your client and server have the disk throughput capacity.

Other than that, I would typically use Wireshark to diagnose such issues. It could be all kinds of things, from duplex mismatch to resource contention to a misconfigured service or TCP stack. Let's not get there yet unless it's not something obvious like your router or cable.

Cheers,
Peter

---

### Post by Vegan on 2009-10-07
I have an old Linksys WRT54G and I copy vast amounts of data back and forth, and everything runs fine.

---

### Post by artheus on 2009-10-07
Yes there's a router in between, because of the fact that there's several clients for the server.

ifconfig (client)
```
eth0      Link encap:Ethernet  HWaddr 00:23:54:0e:99:82  
          inet addr:192.168.1.67  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:54ff:fe0e:9982/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:950486 errors:0 dropped:12656 overruns:0 frame:0
          TX packets:840874 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:863515287 (863.5 MB)  TX bytes:333607278 (333.6 MB)
          Interrupt:17
```

ethtool (client)
```
Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: Twisted Pair
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pg
	Wake-on: d
	Current message level: 0x000000ff (255)
	Link detected: yes

```



ifconfig (server)
```
eth0      Link encap:Ethernet  HWaddr 00:50:8d:d9:77:40  
          inet addr:192.168.1.64  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:8dff:fed9:7740/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:23689599 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12526119 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3717576437 (3.7 GB)  TX bytes:2884140275 (2.8 GB)
          Interrupt:23 Base address:0x8000
```

ethtool (server)
```
Settings for eth0:
	Supported ports: [ MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 1
	Transceiver: external
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: d
	Link detected: yes

```

Thanks.

---

### Post by Xianath on 2009-10-07
Vegan: I also have a WRT54GL and could never go beyond 3-4MB/sec going through it, and then only when disabling everything it had to offer, and OC'ing it. I now have a separate gigabit network and use the router for Internet only, and it is now actually possible to open a shared folder in Windows without Explorer timing out.

artheus: it's not a link speed/duplex issue but there are a large number of dropped RX packets which shouldn't be there. Can you please also post the output of 'netstat -s'? It contains some useful statistics that *may* point to the issue.

Cheers,
Peter

---

### Post by artheus on 2009-10-07
server netstat -s

```
Ip:
    23761092 total packets received
    2 with invalid addresses
    0 forwarded
    0 incoming packets discarded
    23760479 incoming packets delivered
    12590801 requests sent out
Icmp:
    22 ICMP messages received
    0 input ICMP message failed.
    ICMP input histogram:
        destination unreachable: 13
        echo requests: 9
    821 ICMP messages sent
    0 ICMP messages failed
    ICMP output histogram:
        destination unreachable: 812
        echo replies: 9
IcmpMsg:
        InType3: 13
        InType8: 9
        OutType0: 9
        OutType3: 812
Tcp:
    2131 active connections openings
    227 passive connection openings
    1292 failed connection attempts
    41 connection resets received
    8 connections established
    23756182 segments received
    12587963 segments send out
    1625 segments retransmited
    0 bad segments received.
    1386 resets sent
Udp:
    3825 packets received
    799 packets to unknown port received.
    0 packet receive errors
    1708 packets sent
UdpLite:
TcpExt:
    25 invalid SYN cookies received
    111 TCP sockets finished time wait in fast timer
    1567 delayed acks sent
    9 delayed acks further delayed because of locked socket
    Quick ack mode was activated 317 times
    8932765 packets directly queued to recvmsg prequeue.
    3230370 bytes directly in process context from backlog
    3339846460 bytes directly received in process context from prequeue
    12318594 packet headers predicted
    7822487 packets header predicted and directly queued to user
    261645 acknowledgments not containing data payload received
    2815197 predicted acknowledgments
    449 times recovered from packet loss by selective acknowledgements
    6 congestion windows recovered without slow start by DSACK
    14 congestion windows recovered without slow start after partial ack
    1708 TCP data loss events
    TCPLostRetransmit: 120
    15 timeouts after SACK recovery
    1220 fast retransmits
    16 forward retransmits
    31 retransmits in slow start
    249 other TCP timeouts
    5 SACK retransmits failed
    24 times receiver scheduled too late for direct processing
    427 DSACKs sent for old packets
    2 DSACKs sent for out of order packets
    24 DSACKs received
    12 connections reset due to unexpected data
    27 connections reset due to early user close
    2 connections aborted due to timeout
    TCPDSACKIgnoredOld: 18
    TCPDSACKIgnoredNoUndo: 4
IpExt:
    InMcastPkts: 963
    InBcastPkts: 3250
    OutBcastPkts: 531

```


client netstat -s

```
Ip:
    154647 total packets received
    2 with invalid addresses
    0 forwarded
    0 incoming packets discarded
    150734 incoming packets delivered
    101206 requests sent out
Icmp:
    0 ICMP messages received
    0 input ICMP message failed.
    ICMP input histogram:
    0 ICMP messages sent
    0 ICMP messages failed
    ICMP output histogram:
Tcp:
    1008 active connections openings
    0 passive connection openings
    4 failed connection attempts
    70 connection resets received
    11 connections established
    149067 segments received
    100661 segments send out
    64 segments retransmited
    0 bad segments received.
    118 resets sent
Udp:
    479 packets received
    0 packets to unknown port received.
    0 packet receive errors
    478 packets sent
UdpLite:
TcpExt:
    149 TCP sockets finished time wait in fast timer
    2071 delayed acks sent
    Quick ack mode was activated 27 times
    7 packets directly queued to recvmsg prequeue.
    7 bytes directly received in process context from prequeue
    137925 packet headers predicted
    2441 acknowledgments not containing data payload received
    22125 predicted acknowledgments
    13 times recovered from packet loss by selective acknowledgements
    10 congestion windows recovered without slow start after partial ack
    12 TCP data loss events
    TCPLostRetransmit: 1
    2 timeouts after SACK recovery
    16 fast retransmits
    1 forward retransmits
    1 retransmits in slow start
    29 other TCP timeouts
    1 SACK retransmits failed
    27 DSACKs sent for old packets
    17 DSACKs received
    14 connections reset due to unexpected data
    20 connections reset due to early user close
    2 connections aborted due to timeout
    TCPDSACKIgnoredOld: 2
    TCPDSACKIgnoredNoUndo: 10
IpExt:
    InMcastPkts: 292
    OutMcastPkts: 44
    InBcastPkts: 939
```

---

### Post by Xianath on 2009-10-08
Rats, there's nothing extremely unusual there :(

Typically, such unexpected slowness is either a result of TCP stack configuration, or resource contention. In the former case, the most common reasons are insufficient windows sizes, Nagle/DACK interoperability, or the silly window syndrome (highly unlikely with any modern OS). On the resource side, your server or router may be too busy to process all requests.

Let's start by ruling the router out. How's the speed when you connect from a Windows box to another Windows box? If speed is OK, then it's not he router.

Next, let's rule out Samba itself. Can you quickly set up an FTP or WebDAV service in Ubuntu and try that from your Windows boxes? If speed is OK, then it's Samba. Post your smb.conf (the general section, shares are not important) and we can try some tuning options.

If it's not Samba, then it must be the TCP stack. This is where it gets tricky :) Start a network capture (the 96-octet packet limit guarantees that no Samba-specific information (such as usernames, password hashes, or share names) will be present in the capture):

sudo tcpdump -s 96 -w /tmp/slow-samba.pcap -i eth0 host 192.168.1.67 and not port 22 ; sudo bzip2 -9 /tmp/slow-samba.pcap

While the capture is going, transfer a large file over Samba. Pick one that will take at least a few minutes to complete. Once it's done, ctrl-c yor tcpdump session, wait for bzip2 to finish compressing and check the output file (/tmp/slow-samba.pcap.bz2). If it's within the attachment size restrictions of this forum, please post it for analysis. If not, please PM me your SSH public key and I'll give you access to a server where you can upload it for analysis.

This is an interesting problem, hopefully with just as interesting a solution :)

Cheers,
Peter

---

### Post by artheus on 2009-10-14
Hmmm. Seems that the problem is the router. As I tried to transfer a file Windows to Windows. And It was just as slow.. :(

I figure it might just be the fact that the router itself has got an NFS and FTP and stuff like that... It's a Thomson TG787 Gateway..

Any ideas?

---

### Post by CharlesA on 2009-10-14
Are you copying to an external hard drive? (stupid question I know)

---

