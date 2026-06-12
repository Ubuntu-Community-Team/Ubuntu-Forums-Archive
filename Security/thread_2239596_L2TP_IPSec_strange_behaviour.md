---
title: "L2TP IPSec strange behaviour"
date: 2014-08-14
forum: Security
---

### Post by Dominic--- on 2014-08-14
Hello guys,

I have been struggling with IPSec (openswan) configuration and I cannot seem to find the issue.
I am running Ubuntu 14.04LTS with Linux Openswan U2.6.38/K3.13.0-33-generic (netkey).

When I boot the server I can connect to my VPN server without any problems.
Note that iptables are NOT configured at boot.

Now when I reboot again and then load the iptable rules in the CLI and my iptables are configured I cannot connect anymore to the VPN server.
Then,  when I remove the iptable configuration (iptables -F) I can connect again, and guess what, when I configure the SAME rules again, I can login and all works well.

Below is the auth-log of the situation when I apply iptables first thing at boot (when I CANNOT connect):
The syslog shows nothing.
Now again, when I flush iptables, connect the client again to the server, and after apply the iptable rules again, then I can connect.
I can replicate this time after time.

What can explain such an issue?
```

Aug 14 22:22:42 vpn1 pluto[928]: packet from x.x.x.x:8: ignoring Vendor ID payload [MS NT5 ISAKMPOAKLEY 00000008]
Aug 14 22:22:42 vpn1 pluto[928]: packet from x.x.x.x:8: received Vendor ID payload [RFC 3947] method set to=115 
Aug 14 22:22:42 vpn1 pluto[928]: packet from x.x.x.x:8: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02_n] meth=106, but already using method 115
Aug 14 22:22:42 vpn1 pluto[928]: packet from x.x.x.x:8: ignoring Vendor ID payload [FRAGMENTATION]
Aug 14 22:22:42 vpn1 pluto[928]: packet from x.x.x.x:8: ignoring Vendor ID payload [MS-Negotiation Discovery Capable]
Aug 14 22:22:42 vpn1 pluto[928]: packet from x.x.x.x:8: ignoring Vendor ID payload [Vid-Initial-Contact]
Aug 14 22:22:42 vpn1 pluto[928]: packet from x.x.x.x:8: ignoring Vendor ID payload [IKE CGA version 1]
Aug 14 22:22:42 vpn1 pluto[928]: "L2TP-PSK-noNAT"[1] x.x.x.x #1: responding to Main Mode from unknown peer x.x.x.x
Aug 14 22:22:42 vpn1 pluto[928]: "L2TP-PSK-noNAT"[1] x.x.x.x #1: OAKLEY_GROUP 20 not supported.  Attribute OAKLEY_GROUP_DESCRIPTION
Aug 14 22:22:42 vpn1 pluto[928]: "L2TP-PSK-noNAT"[1] x.x.x.x #1: OAKLEY_GROUP 19 not supported.  Attribute OAKLEY_GROUP_DESCRIPTION
Aug 14 22:22:42 vpn1 pluto[928]: "L2TP-PSK-noNAT"[1] x.x.x.x #1: transition from state STATE_MAIN_R0 to state STATE_MAIN_R1
Aug 14 22:22:42 vpn1 pluto[928]: "L2TP-PSK-noNAT"[1] x.x.x.x #1: STATE_MAIN_R1: sent MR1, expecting MI2
Aug 14 22:22:43 vpn1 pluto[928]: "L2TP-PSK-noNAT"[1] x.x.x.x #1: NAT-Traversal: Result using draft-ietf-ipsec-nat-t-ike (MacOS X): peer is NATed
Aug 14 22:22:43 vpn1 pluto[928]: "L2TP-PSK-noNAT"[1] x.x.x.x #1: transition from state STATE_MAIN_R1 to state STATE_MAIN_R2
Aug 14 22:22:43 vpn1 pluto[928]: "L2TP-PSK-noNAT"[1] x.x.x.x #1: STATE_MAIN_R2: sent MR2, expecting MI3
Aug 14 22:22:43 vpn1 pluto[928]: "L2TP-PSK-noNAT"[1] x.x.x.x #1: Main mode peer ID is ID_IPV4_ADDR: '192.168.0.106'
Aug 14 22:22:43 vpn1 pluto[928]: "L2TP-PSK-noNAT"[1] x.x.x.x #1: switched from "L2TP-PSK-noNAT" to "L2TP-PSK-noNAT"
Aug 14 22:22:43 vpn1 pluto[928]: "L2TP-PSK-noNAT"[2] x.x.x.x #1: deleting connection "L2TP-PSK-noNAT" instance with peer x.x.x.x {isakmp=#0/ipsec=#0}
Aug 14 22:22:43 vpn1 pluto[928]: "L2TP-PSK-noNAT"[2] x.x.x.x #1: transition from state STATE_MAIN_R2 to state STATE_MAIN_R3
Aug 14 22:22:43 vpn1 pluto[928]: "L2TP-PSK-noNAT"[2] x.x.x.x #1: new NAT mapping for #1, was x.x.x.x:8, now x.x.x.x:1307
Aug 14 22:22:43 vpn1 pluto[928]: "L2TP-PSK-noNAT"[2] x.x.x.x #1: STATE_MAIN_R3: sent MR3, ISAKMP SA established {auth=OAKLEY_PRESHARED_KEY cipher=aes_256 prf=oakley_sha group=modp2048}
Aug 14 22:22:43 vpn1 pluto[928]: "L2TP-PSK-noNAT"[2] x.x.x.x #1: the peer proposed: 141.138.138.37/32:17/0 -> 192.168.0.106/32:17/0
Aug 14 22:22:43 vpn1 pluto[928]: "L2TP-PSK-noNAT"[2] x.x.x.x #1: NAT-Traversal: received 2 NAT-OA. using first, ignoring others
Aug 14 22:22:43 vpn1 pluto[928]: "L2TP-PSK-noNAT"[2] x.x.x.x #2: responding to Quick Mode proposal {msgid:01000000}
Aug 14 22:22:43 vpn1 pluto[928]: "L2TP-PSK-noNAT"[2] x.x.x.x #2:     us: 141.138.138.37<141.138.138.37>:17/%any
Aug 14 22:22:43 vpn1 pluto[928]: "L2TP-PSK-noNAT"[2] x.x.x.x #2:   them: x.x.x.x[192.168.0.106]:17/1701
Aug 14 22:22:43 vpn1 pluto[928]: "L2TP-PSK-noNAT"[2] x.x.x.x #2: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Aug 14 22:22:43 vpn1 pluto[928]: "L2TP-PSK-noNAT"[2] x.x.x.x #2: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Aug 14 22:22:43 vpn1 pluto[928]: "L2TP-PSK-noNAT"[2] x.x.x.x #2: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
Aug 14 22:22:43 vpn1 pluto[928]: "L2TP-PSK-noNAT"[2] x.x.x.x #2: STATE_QUICK_R2: IPsec SA established transport mode {ESP=>0x0615eac0 <0x3e2835c1 xfrm=AES_128-HMAC_SHA1 NATOA=192.168.0.106 NATD=x.x.x.x:1307 DPD=none}
Aug 14 22:22:56 vpn1 pluto[928]: "L2TP-PSK-noNAT"[2] x.x.x.x #1: received Delete SA(0x0615eac0) payload: deleting IPSEC State #2
Aug 14 22:22:56 vpn1 pluto[928]: "L2TP-PSK-noNAT"[2] x.x.x.x #1: received and ignored informational message
Aug 14 22:22:56 vpn1 pluto[928]: "L2TP-PSK-noNAT"[2] x.x.x.x #1: received Delete SA payload: deleting ISAKMP State #1
Aug 14 22:22:56 vpn1 pluto[928]: "L2TP-PSK-noNAT"[2] x.x.x.x: deleting connection "L2TP-PSK-noNAT" instance with peer x.x.x.x {isakmp=#0/ipsec=#0}
Aug 14 22:22:56 vpn1 pluto[928]: packet from x.x.x.x:1307: received and ignored informational message
```

---

