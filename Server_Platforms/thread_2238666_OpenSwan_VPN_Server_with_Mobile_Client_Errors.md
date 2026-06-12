---
title: "OpenSwan VPN Server with Mobile Client Errors"
date: 2014-08-09
forum: Server Platforms
---

### Post by endy3 on 2014-08-09
Hi all

First, sorry for my bad english, but ive seen this very helpful forum and want to ask my question here and hope that somebody can bring me a solution.

To my Problem:
I set up a VPN Server with OpenSwan (2.6.37) and Configured it from [THIS]("http://ubuntuforums.org/showthread.php?t=1645473&") tutorial. When i try to connect from a Win7/Win8 Client, it works like a charm.
But: When i connect from my Mobile Device, i cant establish the connection. Here are my config Files:

ipsec.conf
```

version 2.0
config setup
  nat_traversal=yes
  virtual_private=%v4:10.0.0.0/8,%v4:192.168.1.0/32,%v4:172.16.0.0/12
  oe=off
  protostack=netkey

conn L2TP-PSK-NAT
  rightsubnet=vhost:%priv
  also=L2TP-PSK-noNAT

conn L2TP-PSK-noNAT
  authby=secret
  pfs=no
  auto=add
  keyingtries=3
  rekey=no
  type=transport
  #ikelifetime=8h
  #keylife=1h
  left=192.168.2.100
  leftnexthop=192.168.2.1
  leftprotoport=17/1701
  right=%any
  rightprotoport=17/%any
  dpddelay=15
  dpdtimeout=30
  dpdaction=clear
  #Uncomment the line below for OSX on MAC?  untested!
  #rightprotoport=17/0

```

ipsec.secrets
```

192.168.2.100 %any: PSK "mykey"

```

chap-secrets
```

testuser    l2tpd    123456    192.168.2.202

```

xl2tpd.conf
```

[global]
ipsec saref = no
[lns default]
ip range = 192.168.2.201-192.168.2.205
local ip = 192.168.2.200
refuse chap = yes
refuse pap = yes
require authentication = yes
ppp debug = yes
pppoptfile = /etc/ppp/options.xl2tpd
length bit = yes

```

options.xl2tpd
```

require-mschap-v2
ms-dns 192.168.2.1
asyncmap 0
auth
crtscts
lock
hide-password
modem
debug
name l2tpd
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4

```

Here is the Complete log from connect beginning until the connect error message shows up on my mobile:
```

Aug  9 13:47:11 vpn pluto[14763]: packet from 178.82.150.18:500: ignoring unknown Vendor ID payload [01528bbbc00696121849ab9a1c5b2a5100000001]
Aug  9 13:47:11 vpn pluto[14763]: packet from 178.82.150.18:500: ignoring Vendor ID payload [MS NT5 ISAKMPOAKLEY 00000009]
Aug  9 13:47:11 vpn pluto[14763]: packet from 178.82.150.18:500: received Vendor ID payload [RFC 3947] method set to=109 
Aug  9 13:47:11 vpn pluto[14763]: packet from 178.82.150.18:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02_n] meth=106, but already using method 109
Aug  9 13:47:11 vpn pluto[14763]: packet from 178.82.150.18:500: ignoring Vendor ID payload [FRAGMENTATION]
Aug  9 13:47:11 vpn pluto[14763]: packet from 178.82.150.18:500: ignoring Vendor ID payload [MS-Negotiation Discovery Capable]
Aug  9 13:47:11 vpn pluto[14763]: packet from 178.82.150.18:500: ignoring Vendor ID payload [Vid-Initial-Contact]
Aug  9 13:47:11 vpn pluto[14763]: packet from 178.82.150.18:500: ignoring Vendor ID payload [IKE CGA version 1]
Aug  9 13:47:11 vpn pluto[14763]: "L2TP-PSK-NAT"[3] 178.82.150.18 #8: responding to Main Mode from unknown peer 178.82.150.18
Aug  9 13:47:11 vpn pluto[14763]: "L2TP-PSK-NAT"[3] 178.82.150.18 #8: OAKLEY_GROUP 20 not supported.  Attribute OAKLEY_GROUP_DESCRIPTION
Aug  9 13:47:11 vpn pluto[14763]: "L2TP-PSK-NAT"[3] 178.82.150.18 #8: OAKLEY_GROUP 19 not supported.  Attribute OAKLEY_GROUP_DESCRIPTION
Aug  9 13:47:11 vpn pluto[14763]: "L2TP-PSK-NAT"[3] 178.82.150.18 #8: transition from state STATE_MAIN_R0 to state STATE_MAIN_R1
Aug  9 13:47:11 vpn pluto[14763]: "L2TP-PSK-NAT"[3] 178.82.150.18 #8: STATE_MAIN_R1: sent MR1, expecting MI2
Aug  9 13:47:11 vpn pluto[14763]: "L2TP-PSK-NAT"[3] 178.82.150.18 #8: NAT-Traversal: Result using RFC 3947 (NAT-Traversal): both are NATed
Aug  9 13:47:11 vpn pluto[14763]: "L2TP-PSK-NAT"[3] 178.82.150.18 #8: transition from state STATE_MAIN_R1 to state STATE_MAIN_R2
Aug  9 13:47:11 vpn pluto[14763]: "L2TP-PSK-NAT"[3] 178.82.150.18 #8: STATE_MAIN_R2: sent MR2, expecting MI3
Aug  9 13:47:11 vpn pluto[14763]: "L2TP-PSK-NAT"[3] 178.82.150.18 #8: Main mode peer ID is ID_IPV4_ADDR: '192.168.1.57'
Aug  9 13:47:11 vpn pluto[14763]: "L2TP-PSK-NAT"[3] 178.82.150.18 #8: switched from "L2TP-PSK-NAT" to "L2TP-PSK-NAT"
Aug  9 13:47:11 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #8: deleting connection "L2TP-PSK-NAT" instance with peer 178.82.150.18 {isakmp=#0/ipsec=#0}
Aug  9 13:47:11 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #8: transition from state STATE_MAIN_R2 to state STATE_MAIN_R3
Aug  9 13:47:11 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #8: new NAT mapping for #8, was 178.82.150.18:500, now 178.82.150.18:4500
Aug  9 13:47:11 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #8: STATE_MAIN_R3: sent MR3, ISAKMP SA established {auth=OAKLEY_PRESHARED_KEY cipher=aes_256 prf=oakley_sha group=modp2048}
Aug  9 13:47:11 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #8: Dead Peer Detection (RFC 3706): not enabled because peer did not advertise it
Aug  9 13:47:11 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #8: the peer proposed: 178.82.152.136/32:17/1701 -> 192.168.1.57/32:17/0
Aug  9 13:47:11 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #8: NAT-Traversal: received 2 NAT-OA. using first, ignoring others
Aug  9 13:47:11 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #9: responding to Quick Mode proposal {msgid:01000000}
Aug  9 13:47:11 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #9:     us: 192.168.2.100<192.168.2.100>[+S=C]:17/1701---192.168.2.1
Aug  9 13:47:11 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #9:   them: 178.82.150.18[192.168.1.57,+S=C]:17/1701===192.168.1.57/32
Aug  9 13:47:11 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #9: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Aug  9 13:47:11 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #9: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Aug  9 13:47:11 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #9: Dead Peer Detection (RFC 3706): not enabled because peer did not advertise it
Aug  9 13:47:11 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #9: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
Aug  9 13:47:11 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #9: STATE_QUICK_R2: IPsec SA established transport mode {ESP=>0xfc1ca0c8 <0x98e83936 xfrm=AES_128-HMAC_SHA1 NATOA=192.168.1.57 NATD=178.82.150.18:4500 DPD=none}
Aug  9 13:47:11 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #8: the peer proposed: 178.82.152.136/32:17/1701 -> 192.168.1.57/32:17/1701
Aug  9 13:47:11 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #8: NAT-Traversal: received 2 NAT-OA. using first, ignoring others
Aug  9 13:47:11 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #10: responding to Quick Mode proposal {msgid:02000000}
Aug  9 13:47:11 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #10:     us: 192.168.2.100<192.168.2.100>[+S=C]:17/1701---192.168.2.1
Aug  9 13:47:11 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #10:   them: 178.82.150.18[192.168.1.57,+S=C]:17/1701===192.168.1.57/32
Aug  9 13:47:11 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #10: keeping refhim=4294901761 during rekey
Aug  9 13:47:11 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #10: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Aug  9 13:47:11 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #10: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Aug  9 13:47:11 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #10: Dead Peer Detection (RFC 3706): not enabled because peer did not advertise it
Aug  9 13:47:11 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #10: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
Aug  9 13:47:11 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #10: STATE_QUICK_R2: IPsec SA established transport mode {ESP=>0x8bc6af60 <0x710b0240 xfrm=AES_128-HMAC_SHA1 NATOA=192.168.1.57 NATD=178.82.150.18:4500 DPD=none}
Aug  9 13:47:11 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #8: received Delete SA(0xfc1ca0c8) payload: deleting IPSEC State #9
Aug  9 13:47:11 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #8: received and ignored informational message
Aug  9 13:47:14 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #8: the peer proposed: 178.82.152.136/32:17/1701 -> 192.168.1.57/32:17/1701
Aug  9 13:47:14 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #8: NAT-Traversal: received 2 NAT-OA. using first, ignoring others
Aug  9 13:47:14 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #11: responding to Quick Mode proposal {msgid:03000000}
Aug  9 13:47:14 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #11:     us: 192.168.2.100<192.168.2.100>[+S=C]:17/1701---192.168.2.1
Aug  9 13:47:14 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #11:   them: 178.82.150.18[192.168.1.57,+S=C]:17/1701===192.168.1.57/32
Aug  9 13:47:14 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #11: keeping refhim=4294901761 during rekey
Aug  9 13:47:14 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #11: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Aug  9 13:47:14 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #11: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Aug  9 13:47:14 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #11: Dead Peer Detection (RFC 3706): not enabled because peer did not advertise it
Aug  9 13:47:14 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #11: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
Aug  9 13:47:14 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #11: STATE_QUICK_R2: IPsec SA established transport mode {ESP=>0xc8765ef8 <0x51717518 xfrm=AES_128-HMAC_SHA1 NATOA=192.168.1.57 NATD=178.82.150.18:4500 DPD=none}
Aug  9 13:47:14 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #8: received Delete SA(0x8bc6af60) payload: deleting IPSEC State #10
Aug  9 13:47:14 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #8: received and ignored informational message
Aug  9 13:47:18 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #8: the peer proposed: 178.82.152.136/32:17/1701 -> 192.168.1.57/32:17/1701
Aug  9 13:47:18 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #8: NAT-Traversal: received 2 NAT-OA. using first, ignoring others
Aug  9 13:47:18 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #12: responding to Quick Mode proposal {msgid:04000000}
Aug  9 13:47:18 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #12:     us: 192.168.2.100<192.168.2.100>[+S=C]:17/1701---192.168.2.1
Aug  9 13:47:18 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #12:   them: 178.82.150.18[192.168.1.57,+S=C]:17/1701===192.168.1.57/32
Aug  9 13:47:18 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #12: keeping refhim=4294901761 during rekey
Aug  9 13:47:18 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #12: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Aug  9 13:47:18 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #12: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Aug  9 13:47:18 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #12: Dead Peer Detection (RFC 3706): not enabled because peer did not advertise it
Aug  9 13:47:18 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #12: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
Aug  9 13:47:18 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #12: STATE_QUICK_R2: IPsec SA established transport mode {ESP=>0x2c9a24a8 <0xf55f736e xfrm=AES_128-HMAC_SHA1 NATOA=192.168.1.57 NATD=178.82.150.18:4500 DPD=none}
Aug  9 13:47:18 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #8: received Delete SA(0xc8765ef8) payload: deleting IPSEC State #11
Aug  9 13:47:18 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #8: received and ignored informational message
Aug  9 13:47:26 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #8: the peer proposed: 178.82.152.136/32:17/1701 -> 192.168.1.57/32:17/1701
Aug  9 13:47:26 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #8: NAT-Traversal: received 2 NAT-OA. using first, ignoring others
Aug  9 13:47:26 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #13: responding to Quick Mode proposal {msgid:05000000}
Aug  9 13:47:26 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #13:     us: 192.168.2.100<192.168.2.100>[+S=C]:17/1701---192.168.2.1
Aug  9 13:47:26 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #13:   them: 178.82.150.18[192.168.1.57,+S=C]:17/1701===192.168.1.57/32
Aug  9 13:47:26 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #13: keeping refhim=4294901761 during rekey
Aug  9 13:47:26 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #13: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Aug  9 13:47:26 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #13: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Aug  9 13:47:26 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #13: Dead Peer Detection (RFC 3706): not enabled because peer did not advertise it
Aug  9 13:47:26 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #13: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
Aug  9 13:47:26 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #13: STATE_QUICK_R2: IPsec SA established transport mode {ESP=>0xe9cbb414 <0x341efa84 xfrm=AES_128-HMAC_SHA1 NATOA=192.168.1.57 NATD=178.82.150.18:4500 DPD=none}
Aug  9 13:47:26 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #8: received Delete SA(0x2c9a24a8) payload: deleting IPSEC State #12
Aug  9 13:47:26 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #8: received and ignored informational message
Aug  9 13:47:40 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #8: the peer proposed: 178.82.152.136/32:17/1701 -> 192.168.1.57/32:17/1701
Aug  9 13:47:40 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #8: NAT-Traversal: received 2 NAT-OA. using first, ignoring others
Aug  9 13:47:40 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #8: received Delete SA(0xe9cbb414) payload: deleting IPSEC State #13
Aug  9 13:47:40 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #8: ERROR: netlink XFRM_MSG_DELPOLICY response for flow eroute_connection delete included errno 2: No such file or directory
Aug  9 13:47:40 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #8: received and ignored informational message
Aug  9 13:47:40 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #8: received Delete SA payload: deleting ISAKMP State #8
Aug  9 13:47:40 vpn pluto[14763]: packet from 178.82.150.18:4500: received and ignored informational message
Aug  9 13:47:40 vpn pluto[14763]: packet from 178.82.150.18:500: ignoring unknown Vendor ID payload [01528bbbc00696121849ab9a1c5b2a5100000001]
Aug  9 13:47:40 vpn pluto[14763]: packet from 178.82.150.18:500: ignoring Vendor ID payload [MS NT5 ISAKMPOAKLEY 00000009]
Aug  9 13:47:40 vpn pluto[14763]: packet from 178.82.150.18:500: received Vendor ID payload [RFC 3947] method set to=109 
Aug  9 13:47:40 vpn pluto[14763]: packet from 178.82.150.18:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02_n] meth=106, but already using method 109
Aug  9 13:47:40 vpn pluto[14763]: packet from 178.82.150.18:500: ignoring Vendor ID payload [FRAGMENTATION]
Aug  9 13:47:40 vpn pluto[14763]: packet from 178.82.150.18:500: ignoring Vendor ID payload [MS-Negotiation Discovery Capable]
Aug  9 13:47:40 vpn pluto[14763]: packet from 178.82.150.18:500: ignoring Vendor ID payload [Vid-Initial-Contact]
Aug  9 13:47:40 vpn pluto[14763]: packet from 178.82.150.18:500: ignoring Vendor ID payload [IKE CGA version 1]
Aug  9 13:47:40 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #15: responding to Main Mode from unknown peer 178.82.150.18
Aug  9 13:47:40 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #15: OAKLEY_GROUP 20 not supported.  Attribute OAKLEY_GROUP_DESCRIPTION
Aug  9 13:47:40 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #15: OAKLEY_GROUP 19 not supported.  Attribute OAKLEY_GROUP_DESCRIPTION
Aug  9 13:47:40 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #15: transition from state STATE_MAIN_R0 to state STATE_MAIN_R1
Aug  9 13:47:40 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #15: STATE_MAIN_R1: sent MR1, expecting MI2
Aug  9 13:47:40 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #14: responding to Quick Mode proposal {msgid:06000000}
Aug  9 13:47:40 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #14:     us: 192.168.2.100<192.168.2.100>[+S=C]:17/1701---192.168.2.1
Aug  9 13:47:40 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #14:   them: 178.82.150.18[192.168.1.57,+S=C]:17/1701===192.168.1.57/32
Aug  9 13:47:40 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #14: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Aug  9 13:47:40 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #14: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Aug  9 13:47:40 vpn pluto[14763]: packet from 178.82.150.18:500: ignoring unknown Vendor ID payload [01528bbbc00696121849ab9a1c5b2a5100000001]
Aug  9 13:47:40 vpn pluto[14763]: packet from 178.82.150.18:500: ignoring Vendor ID payload [MS NT5 ISAKMPOAKLEY 00000009]
Aug  9 13:47:40 vpn pluto[14763]: packet from 178.82.150.18:500: received Vendor ID payload [RFC 3947] method set to=109 
Aug  9 13:47:40 vpn pluto[14763]: packet from 178.82.150.18:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02_n] meth=106, but already using method 109
Aug  9 13:47:40 vpn pluto[14763]: packet from 178.82.150.18:500: ignoring Vendor ID payload [FRAGMENTATION]
Aug  9 13:47:40 vpn pluto[14763]: packet from 178.82.150.18:500: ignoring Vendor ID payload [MS-Negotiation Discovery Capable]
Aug  9 13:47:40 vpn pluto[14763]: packet from 178.82.150.18:500: ignoring Vendor ID payload [Vid-Initial-Contact]
Aug  9 13:47:40 vpn pluto[14763]: packet from 178.82.150.18:500: ignoring Vendor ID payload [IKE CGA version 1]
Aug  9 13:47:40 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #16: responding to Main Mode from unknown peer 178.82.150.18
Aug  9 13:47:40 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #16: OAKLEY_GROUP 20 not supported.  Attribute OAKLEY_GROUP_DESCRIPTION
Aug  9 13:47:40 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #16: OAKLEY_GROUP 19 not supported.  Attribute OAKLEY_GROUP_DESCRIPTION
Aug  9 13:47:40 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #16: transition from state STATE_MAIN_R0 to state STATE_MAIN_R1
Aug  9 13:47:40 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #16: STATE_MAIN_R1: sent MR1, expecting MI2
Aug  9 13:47:41 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #15: NAT-Traversal: Result using RFC 3947 (NAT-Traversal): both are NATed
Aug  9 13:47:41 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #15: transition from state STATE_MAIN_R1 to state STATE_MAIN_R2
Aug  9 13:47:41 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #15: STATE_MAIN_R2: sent MR2, expecting MI3
Aug  9 13:47:41 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #15: Main mode peer ID is ID_IPV4_ADDR: '192.168.1.57'
Aug  9 13:47:41 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #15: transition from state STATE_MAIN_R2 to state STATE_MAIN_R3
Aug  9 13:47:41 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #15: new NAT mapping for #15, was 178.82.150.18:500, now 178.82.150.18:4500
Aug  9 13:47:41 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #15: STATE_MAIN_R3: sent MR3, ISAKMP SA established {auth=OAKLEY_PRESHARED_KEY cipher=aes_256 prf=oakley_sha group=modp2048}
Aug  9 13:47:41 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #15: Dead Peer Detection (RFC 3706): not enabled because peer did not advertise it
Aug  9 13:47:41 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #15: the peer proposed: 178.82.152.136/32:17/1701 -> 192.168.1.57/32:17/1701
Aug  9 13:47:41 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #15: NAT-Traversal: received 2 NAT-OA. using first, ignoring others
Aug  9 13:47:41 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #17: responding to Quick Mode proposal {msgid:01000000}
Aug  9 13:47:41 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #17:     us: 192.168.2.100<192.168.2.100>[+S=C]:17/1701---192.168.2.1
Aug  9 13:47:41 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #17:   them: 178.82.150.18[192.168.1.57,+S=C]:17/1701===192.168.1.57/32
Aug  9 13:47:41 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #17: ERROR: netlink response for Add SA esp.e6c9c0cc@178.82.150.18 included errno 17: File exists
Aug  9 13:47:41 vpn pluto[14763]: | failed to install outgoing SA: 0
Aug  9 13:47:42 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #17: discarding duplicate packet; already STATE_QUICK_R0
Aug  9 13:47:43 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #17: discarding duplicate packet; already STATE_QUICK_R0
Aug  9 13:47:46 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #17: discarding duplicate packet; already STATE_QUICK_R0
Aug  9 13:47:46 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #15: received Delete SA payload: deleting ISAKMP State #15
Aug  9 13:47:46 vpn pluto[14763]: packet from 178.82.150.18:4500: received and ignored informational message
Aug  9 13:47:47 vpn pluto[14763]: packet from 178.82.150.18:500: ignoring unknown Vendor ID payload [01528bbbc00696121849ab9a1c5b2a5100000001]
Aug  9 13:47:47 vpn pluto[14763]: packet from 178.82.150.18:500: ignoring Vendor ID payload [MS NT5 ISAKMPOAKLEY 00000009]
Aug  9 13:47:47 vpn pluto[14763]: packet from 178.82.150.18:500: received Vendor ID payload [RFC 3947] method set to=109 
Aug  9 13:47:47 vpn pluto[14763]: packet from 178.82.150.18:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02_n] meth=106, but already using method 109
Aug  9 13:47:47 vpn pluto[14763]: packet from 178.82.150.18:500: ignoring Vendor ID payload [FRAGMENTATION]
Aug  9 13:47:47 vpn pluto[14763]: packet from 178.82.150.18:500: ignoring Vendor ID payload [MS-Negotiation Discovery Capable]
Aug  9 13:47:47 vpn pluto[14763]: packet from 178.82.150.18:500: ignoring Vendor ID payload [Vid-Initial-Contact]
Aug  9 13:47:47 vpn pluto[14763]: packet from 178.82.150.18:500: ignoring Vendor ID payload [IKE CGA version 1]
Aug  9 13:47:47 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #18: responding to Main Mode from unknown peer 178.82.150.18
Aug  9 13:47:47 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #18: OAKLEY_GROUP 20 not supported.  Attribute OAKLEY_GROUP_DESCRIPTION
Aug  9 13:47:47 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #18: OAKLEY_GROUP 19 not supported.  Attribute OAKLEY_GROUP_DESCRIPTION
Aug  9 13:47:47 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #18: transition from state STATE_MAIN_R0 to state STATE_MAIN_R1
Aug  9 13:47:47 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #18: STATE_MAIN_R1: sent MR1, expecting MI2
Aug  9 13:47:47 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #18: NAT-Traversal: Result using RFC 3947 (NAT-Traversal): both are NATed
Aug  9 13:47:47 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #18: transition from state STATE_MAIN_R1 to state STATE_MAIN_R2
Aug  9 13:47:47 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #18: STATE_MAIN_R2: sent MR2, expecting MI3
Aug  9 13:47:47 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #18: Main mode peer ID is ID_IPV4_ADDR: '192.168.1.57'
Aug  9 13:47:47 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #18: transition from state STATE_MAIN_R2 to state STATE_MAIN_R3
Aug  9 13:47:47 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #18: new NAT mapping for #18, was 178.82.150.18:500, now 178.82.150.18:4500
Aug  9 13:47:47 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #18: STATE_MAIN_R3: sent MR3, ISAKMP SA established {auth=OAKLEY_PRESHARED_KEY cipher=aes_256 prf=oakley_sha group=modp2048}
Aug  9 13:47:47 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #18: Dead Peer Detection (RFC 3706): not enabled because peer did not advertise it
Aug  9 13:47:47 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #18: the peer proposed: 178.82.152.136/32:17/1701 -> 192.168.1.57/32:17/1701
Aug  9 13:47:47 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #18: NAT-Traversal: received 2 NAT-OA. using first, ignoring others
Aug  9 13:47:47 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #19: responding to Quick Mode proposal {msgid:01000000}
Aug  9 13:47:47 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #19:     us: 192.168.2.100<192.168.2.100>[+S=C]:17/1701---192.168.2.1
Aug  9 13:47:47 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #19:   them: 178.82.150.18[192.168.1.57,+S=C]:17/1701===192.168.1.57/32
Aug  9 13:47:47 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #19: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Aug  9 13:47:47 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #19: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Aug  9 13:47:47 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #19: netlink_raw_eroute: WARNING: that_client port 1701 and that_host port 4500 don't match. Using that_client port.
Aug  9 13:47:47 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #19: Dead Peer Detection (RFC 3706): not enabled because peer did not advertise it
Aug  9 13:47:47 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #19: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
Aug  9 13:47:47 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #19: STATE_QUICK_R2: IPsec SA established transport mode {ESP=>0xf037d104 <0x225aa35a xfrm=AES_128-HMAC_SHA1 NATOA=192.168.1.57 NATD=178.82.150.18:4500 DPD=none}
Aug  9 13:47:47 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #18: the peer proposed: 178.82.152.136/32:17/1701 -> 192.168.1.57/32:17/1701
Aug  9 13:47:47 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #18: NAT-Traversal: received 2 NAT-OA. using first, ignoring others
Aug  9 13:47:47 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #20: responding to Quick Mode proposal {msgid:02000000}
Aug  9 13:47:47 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #20:     us: 192.168.2.100<192.168.2.100>[+S=C]:17/1701---192.168.2.1
Aug  9 13:47:47 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #20:   them: 178.82.150.18[192.168.1.57,+S=C]:17/1701===192.168.1.57/32
Aug  9 13:47:47 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #20: keeping refhim=4294901761 during rekey
Aug  9 13:47:47 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #20: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Aug  9 13:47:47 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #20: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Aug  9 13:47:47 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #20: netlink_raw_eroute: WARNING: that_client port 1701 and that_host port 4500 don't match. Using that_client port.
Aug  9 13:47:47 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #20: Dead Peer Detection (RFC 3706): not enabled because peer did not advertise it
Aug  9 13:47:47 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #20: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
Aug  9 13:47:47 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #20: STATE_QUICK_R2: IPsec SA established transport mode {ESP=>0x83b5b284 <0x674f4e23 xfrm=AES_128-HMAC_SHA1 NATOA=192.168.1.57 NATD=178.82.150.18:4500 DPD=none}
Aug  9 13:47:47 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #18: received Delete SA(0xf037d104) payload: deleting IPSEC State #19
Aug  9 13:47:47 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #18: received and ignored informational message
Aug  9 13:47:50 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #18: the peer proposed: 178.82.152.136/32:17/1701 -> 192.168.1.57/32:17/1701
Aug  9 13:47:50 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #18: NAT-Traversal: received 2 NAT-OA. using first, ignoring others
Aug  9 13:47:50 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #21: responding to Quick Mode proposal {msgid:03000000}
Aug  9 13:47:50 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #21:     us: 192.168.2.100<192.168.2.100>[+S=C]:17/1701---192.168.2.1
Aug  9 13:47:50 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #21:   them: 178.82.150.18[192.168.1.57,+S=C]:17/1701===192.168.1.57/32
Aug  9 13:47:50 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #21: keeping refhim=4294901761 during rekey
Aug  9 13:47:50 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #21: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Aug  9 13:47:50 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #21: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Aug  9 13:47:50 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #21: netlink_raw_eroute: WARNING: that_client port 1701 and that_host port 4500 don't match. Using that_client port.
Aug  9 13:47:50 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #21: Dead Peer Detection (RFC 3706): not enabled because peer did not advertise it
Aug  9 13:47:50 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #21: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
Aug  9 13:47:50 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #21: STATE_QUICK_R2: IPsec SA established transport mode {ESP=>0x45d8515c <0x022bb1fc xfrm=AES_128-HMAC_SHA1 NATOA=192.168.1.57 NATD=178.82.150.18:4500 DPD=none}
Aug  9 13:47:50 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #18: received Delete SA(0x83b5b284) payload: deleting IPSEC State #20
Aug  9 13:47:50 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #18: received and ignored informational message
Aug  9 13:47:54 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #18: the peer proposed: 178.82.152.136/32:17/1701 -> 192.168.1.57/32:17/1701
Aug  9 13:47:54 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #18: NAT-Traversal: received 2 NAT-OA. using first, ignoring others
Aug  9 13:47:54 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #22: responding to Quick Mode proposal {msgid:04000000}
Aug  9 13:47:54 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #22:     us: 192.168.2.100<192.168.2.100>[+S=C]:17/1701---192.168.2.1
Aug  9 13:47:54 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #22:   them: 178.82.150.18[192.168.1.57,+S=C]:17/1701===192.168.1.57/32
Aug  9 13:47:54 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #22: keeping refhim=4294901761 during rekey
Aug  9 13:47:54 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #22: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Aug  9 13:47:54 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #22: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Aug  9 13:47:54 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #22: netlink_raw_eroute: WARNING: that_client port 1701 and that_host port 4500 don't match. Using that_client port.
Aug  9 13:47:54 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #22: Dead Peer Detection (RFC 3706): not enabled because peer did not advertise it
Aug  9 13:47:54 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #22: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
Aug  9 13:47:54 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #22: STATE_QUICK_R2: IPsec SA established transport mode {ESP=>0xd7b55dc2 <0xa4a92c3b xfrm=AES_128-HMAC_SHA1 NATOA=192.168.1.57 NATD=178.82.150.18:4500 DPD=none}
Aug  9 13:47:54 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #18: received Delete SA(0x45d8515c) payload: deleting IPSEC State #21
Aug  9 13:47:54 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #18: received and ignored informational message
Aug  9 13:48:02 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #18: the peer proposed: 178.82.152.136/32:17/1701 -> 192.168.1.57/32:17/1701
Aug  9 13:48:02 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #18: NAT-Traversal: received 2 NAT-OA. using first, ignoring others
Aug  9 13:48:02 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #23: responding to Quick Mode proposal {msgid:05000000}
Aug  9 13:48:02 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #23:     us: 192.168.2.100<192.168.2.100>[+S=C]:17/1701---192.168.2.1
Aug  9 13:48:02 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #23:   them: 178.82.150.18[192.168.1.57,+S=C]:17/1701===192.168.1.57/32
Aug  9 13:48:02 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #23: keeping refhim=4294901761 during rekey
Aug  9 13:48:02 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #23: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Aug  9 13:48:02 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #23: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Aug  9 13:48:02 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #23: netlink_raw_eroute: WARNING: that_client port 1701 and that_host port 4500 don't match. Using that_client port.
Aug  9 13:48:02 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #23: Dead Peer Detection (RFC 3706): not enabled because peer did not advertise it
Aug  9 13:48:02 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #23: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
Aug  9 13:48:02 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #23: STATE_QUICK_R2: IPsec SA established transport mode {ESP=>0xfc606f66 <0x02175c54 xfrm=AES_128-HMAC_SHA1 NATOA=192.168.1.57 NATD=178.82.150.18:4500 DPD=none}
Aug  9 13:48:02 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #18: received Delete SA(0xd7b55dc2) payload: deleting IPSEC State #22
Aug  9 13:48:02 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #18: received and ignored informational message
Aug  9 13:48:12 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #18: the peer proposed: 178.82.152.136/32:17/1701 -> 192.168.1.57/32:17/1701
Aug  9 13:48:12 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #18: NAT-Traversal: received 2 NAT-OA. using first, ignoring others
Aug  9 13:48:12 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #24: responding to Quick Mode proposal {msgid:06000000}
Aug  9 13:48:12 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #24:     us: 192.168.2.100<192.168.2.100>[+S=C]:17/1701---192.168.2.1
Aug  9 13:48:12 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #24:   them: 178.82.150.18[192.168.1.57,+S=C]:17/1701===192.168.1.57/32
Aug  9 13:48:12 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #24: keeping refhim=4294901761 during rekey
Aug  9 13:48:12 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #24: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Aug  9 13:48:12 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #24: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Aug  9 13:48:12 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #24: netlink_raw_eroute: WARNING: that_client port 1701 and that_host port 4500 don't match. Using that_client port.
Aug  9 13:48:12 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #24: Dead Peer Detection (RFC 3706): not enabled because peer did not advertise it
Aug  9 13:48:12 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #24: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
Aug  9 13:48:12 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #24: STATE_QUICK_R2: IPsec SA established transport mode {ESP=>0x0c23dc34 <0xa7fb119c xfrm=AES_128-HMAC_SHA1 NATOA=192.168.1.57 NATD=178.82.150.18:4500 DPD=none}
Aug  9 13:48:12 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #18: received Delete SA(0xfc606f66) payload: deleting IPSEC State #23
Aug  9 13:48:12 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #18: received and ignored informational message
Aug  9 13:48:22 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #18: received Delete SA(0x0c23dc34) payload: deleting IPSEC State #24
Aug  9 13:48:22 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #18: ERROR: netlink XFRM_MSG_DELPOLICY response for flow eroute_connection delete included errno 2: No such file or directory
Aug  9 13:48:22 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #18: received and ignored informational message
Aug  9 13:48:22 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #18: received Delete SA payload: deleting ISAKMP State #18
Aug  9 13:48:22 vpn pluto[14763]: packet from 178.82.150.18:4500: received and ignored informational message
Aug  9 13:48:22 vpn pluto[14763]: packet from 178.82.150.18:500: ignoring unknown Vendor ID payload [01528bbbc00696121849ab9a1c5b2a5100000001]
Aug  9 13:48:22 vpn pluto[14763]: packet from 178.82.150.18:500: ignoring Vendor ID payload [MS NT5 ISAKMPOAKLEY 00000009]
Aug  9 13:48:22 vpn pluto[14763]: packet from 178.82.150.18:500: received Vendor ID payload [RFC 3947] method set to=109 
Aug  9 13:48:22 vpn pluto[14763]: packet from 178.82.150.18:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02_n] meth=106, but already using method 109
Aug  9 13:48:22 vpn pluto[14763]: packet from 178.82.150.18:500: ignoring Vendor ID payload [FRAGMENTATION]
Aug  9 13:48:22 vpn pluto[14763]: packet from 178.82.150.18:500: ignoring Vendor ID payload [MS-Negotiation Discovery Capable]
Aug  9 13:48:22 vpn pluto[14763]: packet from 178.82.150.18:500: ignoring Vendor ID payload [Vid-Initial-Contact]
Aug  9 13:48:22 vpn pluto[14763]: packet from 178.82.150.18:500: ignoring Vendor ID payload [IKE CGA version 1]
Aug  9 13:48:22 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #25: responding to Main Mode from unknown peer 178.82.150.18
Aug  9 13:48:22 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #25: OAKLEY_GROUP 20 not supported.  Attribute OAKLEY_GROUP_DESCRIPTION
Aug  9 13:48:22 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #25: OAKLEY_GROUP 19 not supported.  Attribute OAKLEY_GROUP_DESCRIPTION
Aug  9 13:48:22 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #25: transition from state STATE_MAIN_R0 to state STATE_MAIN_R1
Aug  9 13:48:22 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #25: STATE_MAIN_R1: sent MR1, expecting MI2
Aug  9 13:48:22 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #25: NAT-Traversal: Result using RFC 3947 (NAT-Traversal): both are NATed
Aug  9 13:48:22 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #25: transition from state STATE_MAIN_R1 to state STATE_MAIN_R2
Aug  9 13:48:22 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #25: STATE_MAIN_R2: sent MR2, expecting MI3
Aug  9 13:48:23 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #25: Main mode peer ID is ID_IPV4_ADDR: '192.168.1.57'
Aug  9 13:48:23 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #25: transition from state STATE_MAIN_R2 to state STATE_MAIN_R3
Aug  9 13:48:23 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #25: new NAT mapping for #25, was 178.82.150.18:500, now 178.82.150.18:4500
Aug  9 13:48:23 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #25: STATE_MAIN_R3: sent MR3, ISAKMP SA established {auth=OAKLEY_PRESHARED_KEY cipher=aes_256 prf=oakley_sha group=modp2048}
Aug  9 13:48:23 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #25: Dead Peer Detection (RFC 3706): not enabled because peer did not advertise it
Aug  9 13:48:23 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #25: the peer proposed: 178.82.152.136/32:17/1701 -> 192.168.1.57/32:17/1701
Aug  9 13:48:23 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #25: NAT-Traversal: received 2 NAT-OA. using first, ignoring others
Aug  9 13:48:23 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #26: responding to Quick Mode proposal {msgid:01000000}
Aug  9 13:48:23 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #26:     us: 192.168.2.100<192.168.2.100>[+S=C]:17/1701---192.168.2.1
Aug  9 13:48:23 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #26:   them: 178.82.150.18[192.168.1.57,+S=C]:17/1701===192.168.1.57/32
Aug  9 13:48:23 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #26: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Aug  9 13:48:23 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #26: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Aug  9 13:48:23 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #26: netlink_raw_eroute: WARNING: that_client port 1701 and that_host port 4500 don't match. Using that_client port.
Aug  9 13:48:23 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #26: Dead Peer Detection (RFC 3706): not enabled because peer did not advertise it
Aug  9 13:48:23 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #26: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
Aug  9 13:48:23 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #26: STATE_QUICK_R2: IPsec SA established transport mode {ESP=>0x6817bb00 <0xb5f190ef xfrm=AES_128-HMAC_SHA1 NATOA=192.168.1.57 NATD=178.82.150.18:4500 DPD=none}
Aug  9 13:48:23 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #25: the peer proposed: 178.82.152.136/32:17/1701 -> 192.168.1.57/32:17/1701
Aug  9 13:48:23 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #25: NAT-Traversal: received 2 NAT-OA. using first, ignoring others
Aug  9 13:48:23 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #27: responding to Quick Mode proposal {msgid:02000000}
Aug  9 13:48:23 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #27:     us: 192.168.2.100<192.168.2.100>[+S=C]:17/1701---192.168.2.1
Aug  9 13:48:23 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #27:   them: 178.82.150.18[192.168.1.57,+S=C]:17/1701===192.168.1.57/32
Aug  9 13:48:23 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #27: keeping refhim=4294901761 during rekey
Aug  9 13:48:23 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #27: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Aug  9 13:48:23 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #27: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Aug  9 13:48:23 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #27: netlink_raw_eroute: WARNING: that_client port 1701 and that_host port 4500 don't match. Using that_client port.
Aug  9 13:48:23 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #27: Dead Peer Detection (RFC 3706): not enabled because peer did not advertise it
Aug  9 13:48:23 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #27: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
Aug  9 13:48:23 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #27: STATE_QUICK_R2: IPsec SA established transport mode {ESP=>0xe9f2ab28 <0x1f0121e8 xfrm=AES_128-HMAC_SHA1 NATOA=192.168.1.57 NATD=178.82.150.18:4500 DPD=none}
Aug  9 13:48:23 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #25: received Delete SA(0x6817bb00) payload: deleting IPSEC State #26
Aug  9 13:48:23 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #25: received and ignored informational message
Aug  9 13:48:26 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #25: the peer proposed: 178.82.152.136/32:17/1701 -> 192.168.1.57/32:17/1701
Aug  9 13:48:26 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #25: NAT-Traversal: received 2 NAT-OA. using first, ignoring others
Aug  9 13:48:26 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #28: responding to Quick Mode proposal {msgid:03000000}
Aug  9 13:48:26 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #28:     us: 192.168.2.100<192.168.2.100>[+S=C]:17/1701---192.168.2.1
Aug  9 13:48:26 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #28:   them: 178.82.150.18[192.168.1.57,+S=C]:17/1701===192.168.1.57/32
Aug  9 13:48:26 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #28: keeping refhim=4294901761 during rekey
Aug  9 13:48:26 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #28: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Aug  9 13:48:26 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #28: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Aug  9 13:48:26 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #28: netlink_raw_eroute: WARNING: that_client port 1701 and that_host port 4500 don't match. Using that_client port.
Aug  9 13:48:26 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #28: Dead Peer Detection (RFC 3706): not enabled because peer did not advertise it
Aug  9 13:48:26 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #28: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
Aug  9 13:48:26 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #28: STATE_QUICK_R2: IPsec SA established transport mode {ESP=>0x1eb6e6bc <0x88164138 xfrm=AES_128-HMAC_SHA1 NATOA=192.168.1.57 NATD=178.82.150.18:4500 DPD=none}
Aug  9 13:48:26 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #25: received Delete SA(0xe9f2ab28) payload: deleting IPSEC State #27
Aug  9 13:48:26 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #25: received and ignored informational message
Aug  9 13:48:30 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #25: the peer proposed: 178.82.152.136/32:17/1701 -> 192.168.1.57/32:17/1701
Aug  9 13:48:30 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #25: NAT-Traversal: received 2 NAT-OA. using first, ignoring others
Aug  9 13:48:30 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #29: responding to Quick Mode proposal {msgid:04000000}
Aug  9 13:48:30 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #29:     us: 192.168.2.100<192.168.2.100>[+S=C]:17/1701---192.168.2.1
Aug  9 13:48:30 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #29:   them: 178.82.150.18[192.168.1.57,+S=C]:17/1701===192.168.1.57/32
Aug  9 13:48:30 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #29: keeping refhim=4294901761 during rekey
Aug  9 13:48:30 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #29: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Aug  9 13:48:30 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #29: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Aug  9 13:48:30 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #29: netlink_raw_eroute: WARNING: that_client port 1701 and that_host port 4500 don't match. Using that_client port.
Aug  9 13:48:30 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #29: Dead Peer Detection (RFC 3706): not enabled because peer did not advertise it
Aug  9 13:48:30 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #29: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
Aug  9 13:48:30 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #29: STATE_QUICK_R2: IPsec SA established transport mode {ESP=>0xf480ebec <0x648ce681 xfrm=AES_128-HMAC_SHA1 NATOA=192.168.1.57 NATD=178.82.150.18:4500 DPD=none}
Aug  9 13:48:30 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #25: received Delete SA(0x1eb6e6bc) payload: deleting IPSEC State #28
Aug  9 13:48:30 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #25: received and ignored informational message
Aug  9 13:48:38 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #25: the peer proposed: 178.82.152.136/32:17/1701 -> 192.168.1.57/32:17/1701
Aug  9 13:48:38 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #25: NAT-Traversal: received 2 NAT-OA. using first, ignoring others
Aug  9 13:48:38 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #30: responding to Quick Mode proposal {msgid:05000000}
Aug  9 13:48:38 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #30:     us: 192.168.2.100<192.168.2.100>[+S=C]:17/1701---192.168.2.1
Aug  9 13:48:38 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #30:   them: 178.82.150.18[192.168.1.57,+S=C]:17/1701===192.168.1.57/32
Aug  9 13:48:38 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #30: keeping refhim=4294901761 during rekey
Aug  9 13:48:38 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #30: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Aug  9 13:48:38 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #30: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Aug  9 13:48:38 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #30: netlink_raw_eroute: WARNING: that_client port 1701 and that_host port 4500 don't match. Using that_client port.
Aug  9 13:48:38 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #30: Dead Peer Detection (RFC 3706): not enabled because peer did not advertise it
Aug  9 13:48:38 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #30: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
Aug  9 13:48:38 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #30: STATE_QUICK_R2: IPsec SA established transport mode {ESP=>0xd69be804 <0x24b81740 xfrm=AES_128-HMAC_SHA1 NATOA=192.168.1.57 NATD=178.82.150.18:4500 DPD=none}
Aug  9 13:48:38 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #25: received Delete SA(0xf480ebec) payload: deleting IPSEC State #29
Aug  9 13:48:38 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #25: received and ignored informational message
Aug  9 13:48:48 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #25: the peer proposed: 178.82.152.136/32:17/1701 -> 192.168.1.57/32:17/1701
Aug  9 13:48:48 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #25: NAT-Traversal: received 2 NAT-OA. using first, ignoring others
Aug  9 13:48:48 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #31: responding to Quick Mode proposal {msgid:06000000}
Aug  9 13:48:48 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #31:     us: 192.168.2.100<192.168.2.100>[+S=C]:17/1701---192.168.2.1
Aug  9 13:48:48 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #31:   them: 178.82.150.18[192.168.1.57,+S=C]:17/1701===192.168.1.57/32
Aug  9 13:48:48 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #31: keeping refhim=4294901761 during rekey
Aug  9 13:48:48 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #31: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Aug  9 13:48:48 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #31: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Aug  9 13:48:48 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #31: netlink_raw_eroute: WARNING: that_client port 1701 and that_host port 4500 don't match. Using that_client port.
Aug  9 13:48:48 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #31: Dead Peer Detection (RFC 3706): not enabled because peer did not advertise it
Aug  9 13:48:48 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #31: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
Aug  9 13:48:48 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #31: STATE_QUICK_R2: IPsec SA established transport mode {ESP=>0x6e17b486 <0xacc1277b xfrm=AES_128-HMAC_SHA1 NATOA=192.168.1.57 NATD=178.82.150.18:4500 DPD=none}
Aug  9 13:48:48 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #25: received Delete SA(0xd69be804) payload: deleting IPSEC State #30
Aug  9 13:48:48 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #25: received and ignored informational message
Aug  9 13:48:50 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #16: max number of retransmissions (2) reached STATE_MAIN_R1
Aug  9 13:48:58 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #25: received Delete SA(0x6e17b486) payload: deleting IPSEC State #31
Aug  9 13:48:58 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #25: ERROR: netlink XFRM_MSG_DELPOLICY response for flow eroute_connection delete included errno 2: No such file or directory
Aug  9 13:48:58 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #25: received and ignored informational message
Aug  9 13:48:58 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #25: received Delete SA payload: deleting ISAKMP State #25
Aug  9 13:48:58 vpn pluto[14763]: packet from 178.82.150.18:4500: received and ignored informational message
Aug  9 13:48:58 vpn pluto[14763]: packet from 178.82.150.18:500: ignoring unknown Vendor ID payload [01528bbbc00696121849ab9a1c5b2a5100000001]
Aug  9 13:48:58 vpn pluto[14763]: packet from 178.82.150.18:500: ignoring Vendor ID payload [MS NT5 ISAKMPOAKLEY 00000009]
Aug  9 13:48:58 vpn pluto[14763]: packet from 178.82.150.18:500: received Vendor ID payload [RFC 3947] method set to=109 
Aug  9 13:48:58 vpn pluto[14763]: packet from 178.82.150.18:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02_n] meth=106, but already using method 109
Aug  9 13:48:58 vpn pluto[14763]: packet from 178.82.150.18:500: ignoring Vendor ID payload [FRAGMENTATION]
Aug  9 13:48:58 vpn pluto[14763]: packet from 178.82.150.18:500: ignoring Vendor ID payload [MS-Negotiation Discovery Capable]
Aug  9 13:48:58 vpn pluto[14763]: packet from 178.82.150.18:500: ignoring Vendor ID payload [Vid-Initial-Contact]
Aug  9 13:48:58 vpn pluto[14763]: packet from 178.82.150.18:500: ignoring Vendor ID payload [IKE CGA version 1]
Aug  9 13:48:58 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #32: responding to Main Mode from unknown peer 178.82.150.18
Aug  9 13:48:58 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #32: OAKLEY_GROUP 20 not supported.  Attribute OAKLEY_GROUP_DESCRIPTION
Aug  9 13:48:58 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #32: OAKLEY_GROUP 19 not supported.  Attribute OAKLEY_GROUP_DESCRIPTION
Aug  9 13:48:58 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #32: transition from state STATE_MAIN_R0 to state STATE_MAIN_R1
Aug  9 13:48:58 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #32: STATE_MAIN_R1: sent MR1, expecting MI2
Aug  9 13:48:58 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #32: NAT-Traversal: Result using RFC 3947 (NAT-Traversal): both are NATed
Aug  9 13:48:58 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #32: transition from state STATE_MAIN_R1 to state STATE_MAIN_R2
Aug  9 13:48:58 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #32: STATE_MAIN_R2: sent MR2, expecting MI3
Aug  9 13:48:58 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #32: Main mode peer ID is ID_IPV4_ADDR: '192.168.1.57'
Aug  9 13:48:58 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #32: transition from state STATE_MAIN_R2 to state STATE_MAIN_R3
Aug  9 13:48:58 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #32: new NAT mapping for #32, was 178.82.150.18:500, now 178.82.150.18:4500
Aug  9 13:48:58 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #32: STATE_MAIN_R3: sent MR3, ISAKMP SA established {auth=OAKLEY_PRESHARED_KEY cipher=aes_256 prf=oakley_sha group=modp2048}
Aug  9 13:48:58 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #32: Dead Peer Detection (RFC 3706): not enabled because peer did not advertise it
Aug  9 13:48:58 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #32: the peer proposed: 178.82.152.136/32:17/1701 -> 192.168.1.57/32:17/1701
Aug  9 13:48:58 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #32: NAT-Traversal: received 2 NAT-OA. using first, ignoring others
Aug  9 13:48:58 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #33: responding to Quick Mode proposal {msgid:01000000}
Aug  9 13:48:58 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #33:     us: 192.168.2.100<192.168.2.100>[+S=C]:17/1701---192.168.2.1
Aug  9 13:48:58 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #33:   them: 178.82.150.18[192.168.1.57,+S=C]:17/1701===192.168.1.57/32
Aug  9 13:48:58 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #33: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Aug  9 13:48:58 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #33: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Aug  9 13:48:58 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #33: netlink_raw_eroute: WARNING: that_client port 1701 and that_host port 4500 don't match. Using that_client port.
Aug  9 13:48:58 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #33: Dead Peer Detection (RFC 3706): not enabled because peer did not advertise it
Aug  9 13:48:58 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #33: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
Aug  9 13:48:58 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #33: STATE_QUICK_R2: IPsec SA established transport mode {ESP=>0xd1e623a6 <0xf1d79eb6 xfrm=AES_128-HMAC_SHA1 NATOA=192.168.1.57 NATD=178.82.150.18:4500 DPD=none}
Aug  9 13:48:58 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #32: the peer proposed: 178.82.152.136/32:17/1701 -> 192.168.1.57/32:17/1701
Aug  9 13:48:58 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #32: NAT-Traversal: received 2 NAT-OA. using first, ignoring others
Aug  9 13:48:58 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #34: responding to Quick Mode proposal {msgid:02000000}
Aug  9 13:48:58 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #34:     us: 192.168.2.100<192.168.2.100>[+S=C]:17/1701---192.168.2.1
Aug  9 13:48:58 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #34:   them: 178.82.150.18[192.168.1.57,+S=C]:17/1701===192.168.1.57/32
Aug  9 13:48:58 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #34: keeping refhim=4294901761 during rekey
Aug  9 13:48:58 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #34: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Aug  9 13:48:58 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #34: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Aug  9 13:48:58 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #34: netlink_raw_eroute: WARNING: that_client port 1701 and that_host port 4500 don't match. Using that_client port.
Aug  9 13:48:58 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #34: Dead Peer Detection (RFC 3706): not enabled because peer did not advertise it
Aug  9 13:48:58 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #34: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
Aug  9 13:48:58 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #34: STATE_QUICK_R2: IPsec SA established transport mode {ESP=>0x15a027fc <0x2043061d xfrm=AES_128-HMAC_SHA1 NATOA=192.168.1.57 NATD=178.82.150.18:4500 DPD=none}
Aug  9 13:48:58 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #32: received Delete SA(0xd1e623a6) payload: deleting IPSEC State #33
Aug  9 13:48:58 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #32: received and ignored informational message
Aug  9 13:49:01 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #32: the peer proposed: 178.82.152.136/32:17/1701 -> 192.168.1.57/32:17/1701
Aug  9 13:49:01 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #32: NAT-Traversal: received 2 NAT-OA. using first, ignoring others
Aug  9 13:49:01 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #35: responding to Quick Mode proposal {msgid:03000000}
Aug  9 13:49:01 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #35:     us: 192.168.2.100<192.168.2.100>[+S=C]:17/1701---192.168.2.1
Aug  9 13:49:01 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #35:   them: 178.82.150.18[192.168.1.57,+S=C]:17/1701===192.168.1.57/32
Aug  9 13:49:01 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #35: keeping refhim=4294901761 during rekey
Aug  9 13:49:01 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #35: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Aug  9 13:49:01 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #35: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Aug  9 13:49:01 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #35: netlink_raw_eroute: WARNING: that_client port 1701 and that_host port 4500 don't match. Using that_client port.
Aug  9 13:49:01 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #35: Dead Peer Detection (RFC 3706): not enabled because peer did not advertise it
Aug  9 13:49:01 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #35: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
Aug  9 13:49:01 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #35: STATE_QUICK_R2: IPsec SA established transport mode {ESP=>0x38525810 <0xc9321c84 xfrm=AES_128-HMAC_SHA1 NATOA=192.168.1.57 NATD=178.82.150.18:4500 DPD=none}
Aug  9 13:49:01 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #32: received Delete SA(0x15a027fc) payload: deleting IPSEC State #34
Aug  9 13:49:01 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #32: received and ignored informational message
Aug  9 13:49:05 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #32: the peer proposed: 178.82.152.136/32:17/1701 -> 192.168.1.57/32:17/1701
Aug  9 13:49:05 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #32: NAT-Traversal: received 2 NAT-OA. using first, ignoring others
Aug  9 13:49:05 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #36: responding to Quick Mode proposal {msgid:04000000}
Aug  9 13:49:05 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #36:     us: 192.168.2.100<192.168.2.100>[+S=C]:17/1701---192.168.2.1
Aug  9 13:49:05 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #36:   them: 178.82.150.18[192.168.1.57,+S=C]:17/1701===192.168.1.57/32
Aug  9 13:49:05 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #36: keeping refhim=4294901761 during rekey
Aug  9 13:49:05 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #36: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Aug  9 13:49:05 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #36: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Aug  9 13:49:05 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #36: netlink_raw_eroute: WARNING: that_client port 1701 and that_host port 4500 don't match. Using that_client port.
Aug  9 13:49:05 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #36: Dead Peer Detection (RFC 3706): not enabled because peer did not advertise it
Aug  9 13:49:05 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #36: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
Aug  9 13:49:05 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #36: STATE_QUICK_R2: IPsec SA established transport mode {ESP=>0xf0a535e6 <0xc3d4574e xfrm=AES_128-HMAC_SHA1 NATOA=192.168.1.57 NATD=178.82.150.18:4500 DPD=none}
Aug  9 13:49:05 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #32: received Delete SA(0x38525810) payload: deleting IPSEC State #35
Aug  9 13:49:05 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #32: received and ignored informational message
Aug  9 13:49:13 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #32: the peer proposed: 178.82.152.136/32:17/1701 -> 192.168.1.57/32:17/1701
Aug  9 13:49:13 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #32: NAT-Traversal: received 2 NAT-OA. using first, ignoring others
Aug  9 13:49:13 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #37: responding to Quick Mode proposal {msgid:05000000}
Aug  9 13:49:13 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #37:     us: 192.168.2.100<192.168.2.100>[+S=C]:17/1701---192.168.2.1
Aug  9 13:49:13 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #37:   them: 178.82.150.18[192.168.1.57,+S=C]:17/1701===192.168.1.57/32
Aug  9 13:49:13 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #37: keeping refhim=4294901761 during rekey
Aug  9 13:49:13 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #37: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Aug  9 13:49:13 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #37: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Aug  9 13:49:13 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #37: netlink_raw_eroute: WARNING: that_client port 1701 and that_host port 4500 don't match. Using that_client port.
Aug  9 13:49:13 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #37: Dead Peer Detection (RFC 3706): not enabled because peer did not advertise it
Aug  9 13:49:13 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #37: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
Aug  9 13:49:13 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #37: STATE_QUICK_R2: IPsec SA established transport mode {ESP=>0x5e28925a <0xd282a1d2 xfrm=AES_128-HMAC_SHA1 NATOA=192.168.1.57 NATD=178.82.150.18:4500 DPD=none}
Aug  9 13:49:13 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #32: received Delete SA(0xf0a535e6) payload: deleting IPSEC State #36
Aug  9 13:49:13 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #32: received and ignored informational message
Aug  9 13:49:23 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #32: the peer proposed: 178.82.152.136/32:17/1701 -> 192.168.1.57/32:17/1701
Aug  9 13:49:23 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #32: NAT-Traversal: received 2 NAT-OA. using first, ignoring others
Aug  9 13:49:23 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #38: responding to Quick Mode proposal {msgid:06000000}
Aug  9 13:49:23 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #38:     us: 192.168.2.100<192.168.2.100>[+S=C]:17/1701---192.168.2.1
Aug  9 13:49:23 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #38:   them: 178.82.150.18[192.168.1.57,+S=C]:17/1701===192.168.1.57/32
Aug  9 13:49:23 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #38: keeping refhim=4294901761 during rekey
Aug  9 13:49:23 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #38: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Aug  9 13:49:23 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #38: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Aug  9 13:49:23 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #38: netlink_raw_eroute: WARNING: that_client port 1701 and that_host port 4500 don't match. Using that_client port.
Aug  9 13:49:23 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #38: Dead Peer Detection (RFC 3706): not enabled because peer did not advertise it
Aug  9 13:49:23 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #38: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
Aug  9 13:49:23 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #38: STATE_QUICK_R2: IPsec SA established transport mode {ESP=>0x69c47e5a <0xab83b075 xfrm=AES_128-HMAC_SHA1 NATOA=192.168.1.57 NATD=178.82.150.18:4500 DPD=none}
Aug  9 13:49:23 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #32: received Delete SA(0x5e28925a) payload: deleting IPSEC State #37
Aug  9 13:49:23 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #32: received and ignored informational message
Aug  9 13:49:35 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #32: received Delete SA(0x69c47e5a) payload: deleting IPSEC State #38
Aug  9 13:49:35 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #32: ERROR: netlink XFRM_MSG_DELPOLICY response for flow eroute_connection delete included errno 2: No such file or directory
Aug  9 13:49:35 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #32: received and ignored informational message
Aug  9 13:49:35 vpn pluto[14763]: "L2TP-PSK-NAT"[4] 178.82.150.18 #32: received Delete SA payload: deleting ISAKMP State #32
Aug  9 13:49:35 vpn pluto[14763]: packet from 178.82.150.18:4500: received and ignored informational message

```

Im connecting from my home WLAN which is behind a NAT with local subnet 192.168.1.0/24.
The VPN Server is also behind a NAT with local subnet 192.168.2.0/24.

Can someone help me or give me a tip?

Thanks for help:)

---

