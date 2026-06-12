---
title: "L2TP/IPSec VPN works when internal IP is used, but not the external IP"
date: 2013-08-09
forum: Server Platforms
---

### Post by kevin3 on 2013-08-09
[This is where I got all of my instructions from.]("http://blog.riobard.com/2010/04/30/l2tp-over-ipsec-ubuntu/")

I've been trying to set up a L2TP/IPSec VPN for personal purposes on Ubuntu. For some odd reason (and while the client and server are on the same network), when I use the internal IP address of the server (192.168.1.11), the VPN is fully functional. But when I use the external IP address (1.1.1.1), it fails to function despite being on the same network. This is despite the fact that both the client and server are on the same network. When I try to use the VPN from outside of the network, the same thing happens. I'm rather confused as to why this happens. Google produced no answers. For the obvious reasons, the IP address have been anonymized. "1.1.1.1" is my server's external IP address. "9.9.9.9" is the IP address of the device from which I tested the VPN from outside the network. The internal IP address (192.x.x.x) were unchanged. 192.168.1.4 is the internal IP address of the device I used to test the VPN. To my knowledge, I have the port forwarding settings in my router set up perfectly. Prior to using Ubuntu, I set up a L2TP/IPSec VPN server using Windows Server and it worked perfectly. So, does anyone have idea why I'm having issues?

This is the auth.log file from when I used the server's internal IP address while the client was still inside the network:
```
Aug  9 14:51:55 Ubuntu pluto[11036]: packet from 192.168.1.4:500: received Vendor ID payload [RFC 3947] method set to=115 
Aug  9 14:51:55 Ubuntu pluto[11036]: packet from 192.168.1.4:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike] meth=114, but already using method 115
Aug  9 14:51:55 Ubuntu pluto[11036]: packet from 192.168.1.4:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-08] meth=113, but already using method 115
Aug  9 14:51:55 Ubuntu pluto[11036]: packet from 192.168.1.4:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-07] meth=112, but already using method 115
Aug  9 14:51:55 Ubuntu pluto[11036]: packet from 192.168.1.4:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-06] meth=111, but already using method 115
Aug  9 14:51:55 Ubuntu pluto[11036]: packet from 192.168.1.4:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-05] meth=110, but already using method 115
Aug  9 14:51:55 Ubuntu pluto[11036]: packet from 192.168.1.4:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-04] meth=109, but already using method 115
Aug  9 14:51:55 Ubuntu pluto[11036]: packet from 192.168.1.4:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-03] meth=108, but already using method 115
Aug  9 14:51:55 Ubuntu pluto[11036]: packet from 192.168.1.4:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02] meth=107, but already using method 115
Aug  9 14:51:55 Ubuntu pluto[11036]: packet from 192.168.1.4:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02_n] meth=106, but already using method 115
Aug  9 14:51:55 Ubuntu pluto[11036]: packet from 192.168.1.4:500: ignoring Vendor ID payload [FRAGMENTATION 80000000]
Aug  9 14:51:55 Ubuntu pluto[11036]: packet from 192.168.1.4:500: received Vendor ID payload [Dead Peer Detection]
Aug  9 14:51:55 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[16] 192.168.1.4 #21: responding to Main Mode from unknown peer 192.168.1.4
Aug  9 14:51:55 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[16] 192.168.1.4 #21: transition from state STATE_MAIN_R0 to state STATE_MAIN_R1
Aug  9 14:51:55 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[16] 192.168.1.4 #21: STATE_MAIN_R1: sent MR1, expecting MI2
Aug  9 14:51:55 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[16] 192.168.1.4 #21: NAT-Traversal: Result using draft-ietf-ipsec-nat-t-ike (MacOS X): no NAT detected
Aug  9 14:51:55 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[16] 192.168.1.4 #21: transition from state STATE_MAIN_R1 to state STATE_MAIN_R2
Aug  9 14:51:55 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[16] 192.168.1.4 #21: STATE_MAIN_R2: sent MR2, expecting MI3
Aug  9 14:51:55 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[16] 192.168.1.4 #21: ignoring informational payload, type IPSEC_INITIAL_CONTACT msgid=00000000
Aug  9 14:51:55 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[16] 192.168.1.4 #21: Main mode peer ID is ID_IPV4_ADDR: '192.168.1.4'
Aug  9 14:51:55 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[16] 192.168.1.4 #21: transition from state STATE_MAIN_R2 to state STATE_MAIN_R3
Aug  9 14:51:55 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[16] 192.168.1.4 #21: STATE_MAIN_R3: sent MR3, ISAKMP SA established {auth=OAKLEY_PRESHARED_KEY cipher=aes_256 prf=oakley_sha group=modp1024}
Aug  9 14:51:56 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[16] 192.168.1.4 #21: the peer proposed: 192.168.1.11/32:17/1701 -> 192.168.1.4/32:17/0
Aug  9 14:51:56 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[16] 192.168.1.4 #22: responding to Quick Mode proposal {msgid:6a1bda80}
Aug  9 14:51:56 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[16] 192.168.1.4 #22:     us: 192.168.1.11<192.168.1.11>:17/1701
Aug  9 14:51:56 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[16] 192.168.1.4 #22:   them: 192.168.1.4:17/57481
Aug  9 14:51:56 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[16] 192.168.1.4 #22: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Aug  9 14:51:56 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[16] 192.168.1.4 #22: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Aug  9 14:51:56 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[16] 192.168.1.4 #22: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
Aug  9 14:51:56 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[16] 192.168.1.4 #22: STATE_QUICK_R2: IPsec SA established transport mode {ESP=>0x0de2fc77 <0x64108eab xfrm=AES_256-HMAC_SHA1 NATOA=none NATD=none DPD=none}
Aug  9 14:52:16 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[16] 192.168.1.4 #21: received Delete SA(0x0de2fc77) payload: deleting IPSEC State #22
Aug  9 14:52:16 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[16] 192.168.1.4 #21: received and ignored informational message
Aug  9 14:52:16 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[16] 192.168.1.4 #21: received Delete SA payload: deleting ISAKMP State #21
Aug  9 14:52:16 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[16] 192.168.1.4: deleting connection "L2TP-PSK-NAT" instance with peer 192.168.1.4 {isakmp=#0/ipsec=#0}
Aug  9 14:52:16 Ubuntu pluto[11036]: packet from 192.168.1.4:500: received and ignored informational message

```

This is the auth.log file from when I used the server's external IP address while the client was still inside the network:
```
Aug  9 15:04:40 Ubuntu pluto[11036]: packet from 1.1.1.1:500: received Vendor ID payload [RFC 3947] method set to=115 
Aug  9 15:04:40 Ubuntu pluto[11036]: packet from 1.1.1.1:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike] meth=114, but already using method 115
Aug  9 15:04:40 Ubuntu pluto[11036]: packet from 1.1.1.1:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-08] meth=113, but already using method 115
Aug  9 15:04:40 Ubuntu pluto[11036]: packet from 1.1.1.1:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-07] meth=112, but already using method 115
Aug  9 15:04:40 Ubuntu pluto[11036]: packet from 1.1.1.1:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-06] meth=111, but already using method 115
Aug  9 15:04:40 Ubuntu pluto[11036]: packet from 1.1.1.1:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-05] meth=110, but already using method 115
Aug  9 15:04:40 Ubuntu pluto[11036]: packet from 1.1.1.1:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-04] meth=109, but already using method 115
Aug  9 15:04:40 Ubuntu pluto[11036]: packet from 1.1.1.1:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-03] meth=108, but already using method 115
Aug  9 15:04:40 Ubuntu pluto[11036]: packet from 1.1.1.1:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02] meth=107, but already using method 115
Aug  9 15:04:40 Ubuntu pluto[11036]: packet from 1.1.1.1:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02_n] meth=106, but already using method 115
Aug  9 15:04:40 Ubuntu pluto[11036]: packet from 1.1.1.1:500: ignoring Vendor ID payload [FRAGMENTATION 80000000]
Aug  9 15:04:40 Ubuntu pluto[11036]: packet from 1.1.1.1:500: received Vendor ID payload [Dead Peer Detection]
Aug  9 15:04:40 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[21] 1.1.1.1 #33: responding to Main Mode from unknown peer 1.1.1.1
Aug  9 15:04:40 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[21] 1.1.1.1 #33: transition from state STATE_MAIN_R0 to state STATE_MAIN_R1
Aug  9 15:04:40 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[21] 1.1.1.1 #33: STATE_MAIN_R1: sent MR1, expecting MI2
Aug  9 15:04:40 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[21] 1.1.1.1 #33: NAT-Traversal: Result using draft-ietf-ipsec-nat-t-ike (MacOS X): i am NATed
Aug  9 15:04:40 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[21] 1.1.1.1 #33: transition from state STATE_MAIN_R1 to state STATE_MAIN_R2
Aug  9 15:04:40 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[21] 1.1.1.1 #33: STATE_MAIN_R2: sent MR2, expecting MI3
Aug  9 15:04:40 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[21] 1.1.1.1 #33: ignoring informational payload, type IPSEC_INITIAL_CONTACT msgid=00000000
Aug  9 15:04:40 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[21] 1.1.1.1 #33: Main mode peer ID is ID_IPV4_ADDR: '192.168.1.4'
Aug  9 15:04:40 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[21] 1.1.1.1 #33: switched from "L2TP-PSK-NAT" to "L2TP-PSK-NAT"
Aug  9 15:04:40 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[22] 1.1.1.1 #33: deleting connection "L2TP-PSK-NAT" instance with peer 1.1.1.1 {isakmp=#0/ipsec=#0}
Aug  9 15:04:40 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[22] 1.1.1.1 #33: transition from state STATE_MAIN_R2 to state STATE_MAIN_R3
Aug  9 15:04:40 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[22] 1.1.1.1 #33: new NAT mapping for #33, was 1.1.1.1:500, now 1.1.1.1:4500
Aug  9 15:04:40 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[22] 1.1.1.1 #33: STATE_MAIN_R3: sent MR3, ISAKMP SA established {auth=OAKLEY_PRESHARED_KEY cipher=aes_256 prf=oakley_sha group=modp1024}
Aug  9 15:04:41 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[22] 1.1.1.1 #33: the peer proposed: 1.1.1.1/32:17/1701 -> 192.168.1.4/32:17/0
Aug  9 15:04:41 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[22] 1.1.1.1 #33: NAT-Traversal: received 2 NAT-OA. ignored because peer is not NATed
Aug  9 15:04:41 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[22] 1.1.1.1 #34: responding to Quick Mode proposal {msgid:6c6c77c9}
Aug  9 15:04:41 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[22] 1.1.1.1 #34:     us: 192.168.1.11<192.168.1.11>:17/1701
Aug  9 15:04:41 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[22] 1.1.1.1 #34:   them: 1.1.1.1[192.168.1.4]:17/51720===192.168.1.4/32
Aug  9 15:04:41 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[22] 1.1.1.1 #34: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Aug  9 15:04:41 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[22] 1.1.1.1 #34: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Aug  9 15:04:41 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[22] 1.1.1.1 #34: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
Aug  9 15:04:41 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[22] 1.1.1.1 #34: STATE_QUICK_R2: IPsec SA established transport mode {ESP=>0x0a3ddc4d <0xc176dd54 xfrm=AES_256-HMAC_SHA1 NATOA=none NATD=1.1.1.1:4500 DPD=none}
Aug  9 15:05:01 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[22] 1.1.1.1 #33: received Delete SA(0x0a3ddc4d) payload: deleting IPSEC State #34
Aug  9 15:05:01 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[22] 1.1.1.1 #33: ERROR: netlink XFRM_MSG_DELPOLICY response for flow eroute_connection delete included errno 2: No such file or directory
Aug  9 15:05:01 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[22] 1.1.1.1 #33: received and ignored informational message
Aug  9 15:05:01 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[22] 1.1.1.1 #33: received Delete SA payload: deleting ISAKMP State #33
Aug  9 15:05:01 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[22] 1.1.1.1: deleting connection "L2TP-PSK-NAT" instance with peer 1.1.1.1 {isakmp=#0/ipsec=#0}
Aug  9 15:05:01 Ubuntu pluto[11036]: packet from 1.1.1.1:4500: received and ignored informational message
```

This is the auth.log file from when I used the server's external IP address while the client was outside the network:
```
Aug  9 14:59:03 Ubuntu pluto[11036]: packet from 9.9.9.9:2082: received Vendor ID payload [RFC 3947] method set to=115 
Aug  9 14:59:03 Ubuntu pluto[11036]: packet from 9.9.9.9:2082: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike] meth=114, but already using method 115
Aug  9 14:59:03 Ubuntu pluto[11036]: packet from 9.9.9.9:2082: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-08] meth=113, but already using method 115
Aug  9 14:59:03 Ubuntu pluto[11036]: packet from 9.9.9.9:2082: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-07] meth=112, but already using method 115
Aug  9 14:59:03 Ubuntu pluto[11036]: packet from 9.9.9.9:2082: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-06] meth=111, but already using method 115
Aug  9 14:59:03 Ubuntu pluto[11036]: packet from 9.9.9.9:2082: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-05] meth=110, but already using method 115
Aug  9 14:59:03 Ubuntu pluto[11036]: packet from 9.9.9.9:2082: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-04] meth=109, but already using method 115
Aug  9 14:59:03 Ubuntu pluto[11036]: packet from 9.9.9.9:2082: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-03] meth=108, but already using method 115
Aug  9 14:59:03 Ubuntu pluto[11036]: packet from 9.9.9.9:2082: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02] meth=107, but already using method 115
Aug  9 14:59:03 Ubuntu pluto[11036]: packet from 9.9.9.9:2082: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02_n] meth=106, but already using method 115
Aug  9 14:59:03 Ubuntu pluto[11036]: packet from 9.9.9.9:2082: ignoring Vendor ID payload [FRAGMENTATION 80000000]
Aug  9 14:59:03 Ubuntu pluto[11036]: packet from 9.9.9.9:2082: received Vendor ID payload [Dead Peer Detection]
Aug  9 14:59:03 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[11] 9.9.9.9 #31: responding to Main Mode from unknown peer 9.9.9.9
Aug  9 14:59:03 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[11] 9.9.9.9 #31: transition from state STATE_MAIN_R0 to state STATE_MAIN_R1
Aug  9 14:59:03 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[11] 9.9.9.9 #31: STATE_MAIN_R1: sent MR1, expecting MI2
Aug  9 14:59:03 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[11] 9.9.9.9 #31: NAT-Traversal: Result using draft-ietf-ipsec-nat-t-ike (MacOS X): both are NATed
Aug  9 14:59:03 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[11] 9.9.9.9 #31: transition from state STATE_MAIN_R1 to state STATE_MAIN_R2
Aug  9 14:59:03 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[11] 9.9.9.9 #31: STATE_MAIN_R2: sent MR2, expecting MI3
Aug  9 14:59:03 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[11] 9.9.9.9 #31: ignoring informational payload, type IPSEC_INITIAL_CONTACT msgid=00000000
Aug  9 14:59:03 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[11] 9.9.9.9 #31: Main mode peer ID is ID_IPV4_ADDR: '192.168.43.158'
Aug  9 14:59:03 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[11] 9.9.9.9 #31: transition from state STATE_MAIN_R2 to state STATE_MAIN_R3
Aug  9 14:59:03 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[11] 9.9.9.9 #31: new NAT mapping for #31, was 9.9.9.9:2082, now 9.9.9.9:9743
Aug  9 14:59:03 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[11] 9.9.9.9 #31: STATE_MAIN_R3: sent MR3, ISAKMP SA established {auth=OAKLEY_PRESHARED_KEY cipher=aes_256 prf=oakley_sha group=modp1024}
Aug  9 14:59:04 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[11] 9.9.9.9 #31: the peer proposed: 71.194.127.170/32:17/1701 -> 192.168.43.158/32:17/59579
Aug  9 14:59:04 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[11] 9.9.9.9 #31: NAT-Traversal: received 2 NAT-OA. using first, ignoring others
Aug  9 14:59:04 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[11] 9.9.9.9 #32: responding to Quick Mode proposal {msgid:3c32fdf6}
Aug  9 14:59:04 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[11] 9.9.9.9 #32:     us: 192.168.1.11<192.168.1.11>:17/1701
Aug  9 14:59:04 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[11] 9.9.9.9 #32:   them: 9.9.9.9[192.168.43.158]:17/59579===192.168.43.158/32
Aug  9 14:59:04 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[11] 9.9.9.9 #32: keeping refhim=4294901761 during rekey
Aug  9 14:59:04 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[11] 9.9.9.9 #32: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Aug  9 14:59:04 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[11] 9.9.9.9 #32: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Aug  9 14:59:04 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[11] 9.9.9.9 #32: netlink_raw_eroute: WARNING: that_client port 59579 and that_host port 9743 don't match. Using that_client port.
Aug  9 14:59:04 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[11] 9.9.9.9 #32: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
Aug  9 14:59:04 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[11] 9.9.9.9 #32: STATE_QUICK_R2: IPsec SA established transport mode {ESP=>0x022610c7 <0xd6f2e929 xfrm=AES_256-HMAC_SHA1 NATOA=192.168.43.158 NATD=9.9.9.9:9743 DPD=none}
Aug  9 14:59:24 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[11] 9.9.9.9 #31: received Delete SA(0x022610c7) payload: deleting IPSEC State #32
Aug  9 14:59:24 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[11] 9.9.9.9 #31: ERROR: netlink XFRM_MSG_DELPOLICY response for flow eroute_connection delete included errno 2: No such file or directory
Aug  9 14:59:24 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[11] 9.9.9.9 #31: received and ignored informational message
Aug  9 14:59:24 Ubuntu pluto[11036]: "L2TP-PSK-NAT"[11] 9.9.9.9 #31: received Delete SA payload: deleting ISAKMP State #31
Aug  9 14:59:24 Ubuntu pluto[11036]: packet from 9.9.9.9:9743: received and ignored informational message

```

---

### Post by kevin3 on 2013-08-11
Nevermind, I decided to just get rid of Ubuntu and revert back to Windows Server 2008 R2.

---

