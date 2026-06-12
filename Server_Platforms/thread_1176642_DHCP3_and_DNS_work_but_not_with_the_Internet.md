---
title: "DHCP3 and DNS work but not with the Internet"
date: 2009-06-02
forum: Server Platforms
---

### Post by matthewboh on 2009-06-02
I've been slogging through a DNS / DHCP3 install, and am stuck.  Basically, I can disable DHCP on the Linksys WRT54G router, start up the server, get a DHCP lease, get DNS functionality, but can't get out to the Internet.

Here's my network  Verizon DSL Model -> Linksys WRT54G -> My network which includes a Ubuntu 8.04 LTS server and several PC's.

If I'm running DHCP / DNS off the server, I can run nslookup and get results for hosts both inside and outside.  However, if I run curl, I can only get the headers back when I'm running DHCP off the Linksys router.

I downloaded Wireshark and did a comparison between the traffic with the Linksys router and the Ubuntu DHCP server.  Here's the traffic from the Ubuntu DHCP / DNS server.  

```
Address Resolution Protocol (reply)

No.     Time        Source                Destination           Protocol Info
      5 2.075266    192.168.1.105         192.168.1.100         DNS      Standard query A www.mit.edu

Frame 5 (71 bytes on wire, 71 bytes captured)
Ethernet II, Src: Intel_6d:d7:6a (00:04:23:6d:d7:6a), Dst: Cisco-Li_15:1c:11 (00:18:39:15:1c:11)
Internet Protocol, Src: 192.168.1.105 (192.168.1.105), Dst: 192.168.1.100 (192.168.1.100)
User Datagram Protocol, Src Port: 54427 (54427), Dst Port: domain (53)
Domain Name System (query)

No.     Time        Source                Destination           Protocol Info
      6 2.135725    192.168.1.100         192.168.1.105         DNS      Standard query response A 18.7.22.83

Frame 6 (542 bytes on wire, 542 bytes captured)
Ethernet II, Src: Cisco-Li_15:1c:11 (00:18:39:15:1c:11), Dst: Intel_6d:d7:6a (00:04:23:6d:d7:6a)
Internet Protocol, Src: 192.168.1.100 (192.168.1.100), Dst: 192.168.1.105 (192.168.1.105)
User Datagram Protocol, Src Port: domain (53), Dst Port: 54427 (54427)
Domain Name System (response)

No.     Time        Source                Destination           Protocol Info
      7 7.134129    Cisco-Li_15:1c:11     Intel_6d:d7:6a        ARP      Who has 192.168.1.105?  Tell 192.168.1.100

Frame 7 (42 bytes on wire, 42 bytes captured)
Ethernet II, Src: Cisco-Li_15:1c:11 (00:18:39:15:1c:11), Dst: Intel_6d:d7:6a (00:04:23:6d:d7:6a)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
      8 7.134178    Intel_6d:d7:6a        Cisco-Li_15:1c:11     ARP      192.168.1.105 is at 00:04:23:6d:d7:6a

Frame 8 (42 bytes on wire, 42 bytes captured)
Ethernet II, Src: Intel_6d:d7:6a (00:04:23:6d:d7:6a), Dst: Cisco-Li_15:1c:11 (00:18:39:15:1c:11)
Address Resolution Protocol (reply)
```

And here's the traffic from the Linksys router

```
No.     Time        Source                Destination           Protocol Info
      3 21.471934   192.168.1.105         192.168.1.100         DNS      Standard query A www.mit.edu

Frame 3 (71 bytes on wire, 71 bytes captured)
Ethernet II, Src: Intel_6d:d7:6a (00:04:23:6d:d7:6a), Dst: Cisco-Li_15:1c:11 (00:18:39:15:1c:11)
Internet Protocol, Src: 192.168.1.105 (192.168.1.105), Dst: 192.168.1.100 (192.168.1.100)
User Datagram Protocol, Src Port: 54154 (54154), Dst Port: domain (53)
Domain Name System (query)

No.     Time        Source                Destination           Protocol Info
      4 21.530578   192.168.1.100         192.168.1.105         DNS      Standard query response A 18.7.22.83

Frame 4 (542 bytes on wire, 542 bytes captured)
Ethernet II, Src: Cisco-Li_15:1c:11 (00:18:39:15:1c:11), Dst: Intel_6d:d7:6a (00:04:23:6d:d7:6a)
Internet Protocol, Src: 192.168.1.100 (192.168.1.100), Dst: 192.168.1.105 (192.168.1.105)
User Datagram Protocol, Src Port: domain (53), Dst Port: 54154 (54154)
Domain Name System (response)

No.     Time        Source                Destination           Protocol Info
      5 21.531126   192.168.1.105         18.7.22.83            TCP      42296 > http [SYN] Seq=0 Win=5840 Len=0 MSS=1460 TSV=910140 TSER=0 WS=6

Frame 5 (74 bytes on wire, 74 bytes captured)
Ethernet II, Src: Intel_6d:d7:6a (00:04:23:6d:d7:6a), Dst: Cisco-Li_d0:46:9e (00:0c:41:d0:46:9e)
Internet Protocol, Src: 192.168.1.105 (192.168.1.105), Dst: 18.7.22.83 (18.7.22.83)
Transmission Control Protocol, Src Port: 42296 (42296), Dst Port: http (80), Seq: 0, Len: 0

No.     Time        Source                Destination           Protocol Info
      6 21.597195   18.7.22.83            192.168.1.105         TCP      http > 42296 [SYN, ACK] Seq=0 Ack=1 Win=8192 Len=0 MSS=1452

Frame 6 (58 bytes on wire, 58 bytes captured)
Ethernet II, Src: Cisco-Li_d0:46:9e (00:0c:41:d0:46:9e), Dst: Intel_6d:d7:6a (00:04:23:6d:d7:6a)
Internet Protocol, Src: 18.7.22.83 (18.7.22.83), Dst: 192.168.1.105 (192.168.1.105)
Transmission Control Protocol, Src Port: http (80), Dst Port: 42296 (42296), Seq: 0, Ack: 1, Len: 0

No.     Time        Source                Destination           Protocol Info
      7 21.597270   192.168.1.105         18.7.22.83            TCP      42296 > http [ACK] Seq=1 Ack=1 Win=5840 Len=0

Frame 7 (54 bytes on wire, 54 bytes captured)
Ethernet II, Src: Intel_6d:d7:6a (00:04:23:6d:d7:6a), Dst: Cisco-Li_d0:46:9e (00:0c:41:d0:46:9e)
Internet Protocol, Src: 192.168.1.105 (192.168.1.105), Dst: 18.7.22.83 (18.7.22.83)
Transmission Control Protocol, Src Port: 42296 (42296), Dst Port: http (80), Seq: 1, Ack: 1, Len: 0

No.     Time        Source                Destination           Protocol Info
      8 21.597573   192.168.1.105         18.7.22.83            HTTP     HEAD / HTTP/1.1 

Frame 8 (205 bytes on wire, 205 bytes captured)
Ethernet II, Src: Intel_6d:d7:6a (00:04:23:6d:d7:6a), Dst: Cisco-Li_d0:46:9e (00:0c:41:d0:46:9e)
Internet Protocol, Src: 192.168.1.105 (192.168.1.105), Dst: 18.7.22.83 (18.7.22.83)
Transmission Control Protocol, Src Port: 42296 (42296), Dst Port: http (80), Seq: 1, Ack: 1, Len: 151
Hypertext Transfer Protocol

No.     Time        Source                Destination           Protocol Info
      9 21.642094   18.7.22.83            192.168.1.105         TCP      http > 42296 [ACK] Seq=1 Ack=152 Win=8192 Len=0

Frame 9 (54 bytes on wire, 54 bytes captured)
Ethernet II, Src: Cisco-Li_d0:46:9e (00:0c:41:d0:46:9e), Dst: Intel_6d:d7:6a (00:04:23:6d:d7:6a)
Internet Protocol, Src: 18.7.22.83 (18.7.22.83), Dst: 192.168.1.105 (192.168.1.105)
Transmission Control Protocol, Src Port: http (80), Dst Port: 42296 (42296), Seq: 1, Ack: 152, Len: 0

No.     Time        Source                Destination           Protocol Info
     10 21.642947   18.7.22.83            192.168.1.105         TCP      [TCP Window Update] http > 42296 [ACK] Seq=1 Ack=152 Win=5840 Len=0

Frame 10 (54 bytes on wire, 54 bytes captured)
Ethernet II, Src: Cisco-Li_d0:46:9e (00:0c:41:d0:46:9e), Dst: Intel_6d:d7:6a (00:04:23:6d:d7:6a)
Internet Protocol, Src: 18.7.22.83 (18.7.22.83), Dst: 192.168.1.105 (192.168.1.105)
Transmission Control Protocol, Src Port: http (80), Dst Port: 42296 (42296), Seq: 1, Ack: 152, Len: 0

No.     Time        Source                Destination           Protocol Info
     11 21.644136   18.7.22.83            192.168.1.105         TCP      [TCP Previous segment lost] http > 42296 [FIN, ACK] Seq=306 Ack=152 Win=5840 Len=0

Frame 11 (54 bytes on wire, 54 bytes captured)
Ethernet II, Src: Cisco-Li_d0:46:9e (00:0c:41:d0:46:9e), Dst: Intel_6d:d7:6a (00:04:23:6d:d7:6a)
Internet Protocol, Src: 18.7.22.83 (18.7.22.83), Dst: 192.168.1.105 (192.168.1.105)
Transmission Control Protocol, Src Port: http (80), Dst Port: 42296 (42296), Seq: 306, Ack: 152, Len: 0

No.     Time        Source                Destination           Protocol Info
     12 21.644167   192.168.1.105         18.7.22.83            TCP      [TCP Dup ACK 8#1] 42296 > http [ACK] Seq=152 Ack=1 Win=5840 Len=0

Frame 12 (54 bytes on wire, 54 bytes captured)
Ethernet II, Src: Intel_6d:d7:6a (00:04:23:6d:d7:6a), Dst: Cisco-Li_d0:46:9e (00:0c:41:d0:46:9e)
Internet Protocol, Src: 192.168.1.105 (192.168.1.105), Dst: 18.7.22.83 (18.7.22.83)
Transmission Control Protocol, Src Port: 42296 (42296), Dst Port: http (80), Seq: 152, Ack: 1, Len: 0

No.     Time        Source                Destination           Protocol Info
     13 21.645785   18.7.22.83            192.168.1.105         TCP      [TCP Out-Of-Order] [TCP segment of a reassembled PDU]

Frame 13 (359 bytes on wire, 359 bytes captured)
Ethernet II, Src: Cisco-Li_d0:46:9e (00:0c:41:d0:46:9e), Dst: Intel_6d:d7:6a (00:04:23:6d:d7:6a)
Internet Protocol, Src: 18.7.22.83 (18.7.22.83), Dst: 192.168.1.105 (192.168.1.105)
Transmission Control Protocol, Src Port: http (80), Dst Port: 42296 (42296), Seq: 1, Ack: 152, Len: 305

No.     Time        Source                Destination           Protocol Info
     14 21.645821   192.168.1.105         18.7.22.83            TCP      42296 > http [ACK] Seq=152 Ack=307 Win=6432 Len=0

Frame 14 (54 bytes on wire, 54 bytes captured)
Ethernet II, Src: Intel_6d:d7:6a (00:04:23:6d:d7:6a), Dst: Cisco-Li_d0:46:9e (00:0c:41:d0:46:9e)
Internet Protocol, Src: 192.168.1.105 (192.168.1.105), Dst: 18.7.22.83 (18.7.22.83)
Transmission Control Protocol, Src Port: 42296 (42296), Dst Port: http (80), Seq: 152, Ack: 307, Len: 0

No.     Time        Source                Destination           Protocol Info
     15 21.646500   192.168.1.105         18.7.22.83            TCP      42296 > http [FIN, ACK] Seq=152 Ack=307 Win=6432 Len=0

Frame 15 (54 bytes on wire, 54 bytes captured)
Ethernet II, Src: Intel_6d:d7:6a (00:04:23:6d:d7:6a), Dst: Cisco-Li_d0:46:9e (00:0c:41:d0:46:9e)
Internet Protocol, Src: 192.168.1.105 (192.168.1.105), Dst: 18.7.22.83 (18.7.22.83)
Transmission Control Protocol, Src Port: 42296 (42296), Dst Port: http (80), Seq: 152, Ack: 307, Len: 0

No.     Time        Source                Destination           Protocol Info
     16 21.689551   18.7.22.83            192.168.1.105         TCP      http > 42296 [ACK] Seq=307 Ack=153 Win=5840 Len=0

Frame 16 (54 bytes on wire, 54 bytes captured)
Ethernet II, Src: Cisco-Li_d0:46:9e (00:0c:41:d0:46:9e), Dst: Intel_6d:d7:6a (00:04:23:6d:d7:6a)
Internet Protocol, Src: 18.7.22.83 (18.7.22.83), Dst: 192.168.1.105 (192.168.1.105)
Transmission Control Protocol, Src Port: http (80), Dst Port: 42296 (42296), Seq: 307, Ack: 153, Len: 0

No.     Time        Source                Destination           Protocol Info
     17 26.468082   Intel_6d:d7:6a        Cisco-Li_15:1c:11     ARP      Who has 192.168.1.100?  Tell 192.168.1.105

Frame 17 (42 bytes on wire, 42 bytes captured)
Ethernet II, Src: Intel_6d:d7:6a (00:04:23:6d:d7:6a), Dst: Cisco-Li_15:1c:11 (00:18:39:15:1c:11)
Address Resolution Protocol (request)

No.     Time        Source                Destination           Protocol Info
     18 26.473013   Cisco-Li_15:1c:11     Intel_6d:d7:6a        ARP      192.168.1.100 is at 00:18:39:15:1c:11

Frame 18 (42 bytes on wire, 42 bytes captured)
Ethernet II, Src: Cisco-Li_15:1c:11 (00:18:39:15:1c:11), Dst: Intel_6d:d7:6a (00:04:23:6d:d7:6a)
Address Resolution Protocol (reply)
```

As you can see, both are resolving the name, but the Ubuntu server doesn't transfer the TCP and HTTP protocol traffic.

I'm kind of new at networking, being an application / programming guy, so am at a loss as what to look at next.  Any help greatly appreciated!

Thanks,

---

### Post by Alekz_ on 2009-06-02
Did you set the dhcpd.conf file?

You supposed to have something like this into your /etc/dhcp3/dhcpd.conf

```
option domain-name "yourdomain.something";
option domain-name-servers DNS_SERVER_IP;
option routers YOUR_DEFAULT_GATEWAY_IP;
```

If it doesn't work, post the output of nslookup of a external address!

Important: If you change your dhcpd.conf file, you have to restart the daemon:
```
/etc/init.d/dhcp3-server restart
```

[]'s

---

### Post by Iowan on 2009-06-02
Still on my to-do list is replacing DHCP3 with [DNSMasq]("https://help.ubuntu.com/community/Dnsmasq").

---

### Post by matthewboh on 2009-06-03
I was missing the option router statement and as soon as I put that in, everything works!  Thanks!

---

