---
title: "Openswan cannot install eroute"
date: 2014-08-15
forum: Security
---

### Post by Dominic--- on 2014-08-15
I am running OpenSwan on Ubuntu 14.04.
When I connect from two clients with the same public IP only one is allowd and can connect, also I receive this message in my logging.
Is this a limitation in Openswan?
```

Aug 15 20:16:55 vpn1 pluto[2911]: packet from 62.45.140.54:3: ignoring Vendor ID payload [MS NT5 ISAKMPOAKLEY 00000008]
Aug 15 20:16:55 vpn1 pluto[2911]: packet from 62.45.140.54:3: received Vendor ID payload [RFC 3947] method set to=115 
Aug 15 20:16:55 vpn1 pluto[2911]: packet from 62.45.140.54:3: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02_n] meth=106, but already using method 115
Aug 15 20:16:55 vpn1 pluto[2911]: packet from 62.45.140.54:3: ignoring Vendor ID payload [FRAGMENTATION]
Aug 15 20:16:55 vpn1 pluto[2911]: packet from 62.45.140.54:3: ignoring Vendor ID payload [MS-Negotiation Discovery Capable]
Aug 15 20:16:55 vpn1 pluto[2911]: packet from 62.45.140.54:3: ignoring Vendor ID payload [Vid-Initial-Contact]
Aug 15 20:16:55 vpn1 pluto[2911]: packet from 62.45.140.54:3: ignoring Vendor ID payload [IKE CGA version 1]
Aug 15 20:16:55 vpn1 pluto[2911]: "L2TP-PSK-noNAT"[3] 62.45.140.54 #5: responding to Main Mode from unknown peer 62.45.140.54
Aug 15 20:16:55 vpn1 pluto[2911]: "L2TP-PSK-noNAT"[3] 62.45.140.54 #5: OAKLEY_GROUP 20 not supported.  Attribute OAKLEY_GROUP_DESCRIPTION
Aug 15 20:16:55 vpn1 pluto[2911]: "L2TP-PSK-noNAT"[3] 62.45.140.54 #5: OAKLEY_GROUP 19 not supported.  Attribute OAKLEY_GROUP_DESCRIPTION
Aug 15 20:16:55 vpn1 pluto[2911]: "L2TP-PSK-noNAT"[3] 62.45.140.54 #5: transition from state STATE_MAIN_R0 to state STATE_MAIN_R1
Aug 15 20:16:55 vpn1 pluto[2911]: "L2TP-PSK-noNAT"[3] 62.45.140.54 #5: STATE_MAIN_R1: sent MR1, expecting MI2
Aug 15 20:16:55 vpn1 pluto[2911]: "L2TP-PSK-noNAT"[3] 62.45.140.54 #5: NAT-Traversal: Result using draft-ietf-ipsec-nat-t-ike (MacOS X): peer is NATed
Aug 15 20:16:55 vpn1 pluto[2911]: "L2TP-PSK-noNAT"[3] 62.45.140.54 #5: transition from state STATE_MAIN_R1 to state STATE_MAIN_R2
Aug 15 20:16:55 vpn1 pluto[2911]: "L2TP-PSK-noNAT"[3] 62.45.140.54 #5: STATE_MAIN_R2: sent MR2, expecting MI3
Aug 15 20:16:55 vpn1 pluto[2911]: "L2TP-PSK-noNAT"[3] 62.45.140.54 #5: Main mode peer ID is ID_IPV4_ADDR: '192.168.0.103'
Aug 15 20:16:55 vpn1 pluto[2911]: "L2TP-PSK-noNAT"[3] 62.45.140.54 #5: transition from state STATE_MAIN_R2 to state STATE_MAIN_R3
Aug 15 20:16:55 vpn1 pluto[2911]: "L2TP-PSK-noNAT"[3] 62.45.140.54 #5: new NAT mapping for #5, was 62.45.140.54:3, now 62.45.140.54:1026
Aug 15 20:16:55 vpn1 pluto[2911]: "L2TP-PSK-noNAT"[3] 62.45.140.54 #5: STATE_MAIN_R3: sent MR3, ISAKMP SA established {auth=OAKLEY_PRESHARED_KEY cipher=aes_256 prf=oakley_sha group=modp2048}
Aug 15 20:16:55 vpn1 pluto[2911]: "L2TP-PSK-noNAT"[3] 62.45.140.54 #5: the peer proposed: 141.138.138.37/32:17/0 -> 192.168.0.103/32:17/1701
Aug 15 20:16:55 vpn1 pluto[2911]: "L2TP-PSK-noNAT"[3] 62.45.140.54 #5: NAT-Traversal: received 2 NAT-OA. using first, ignoring others
Aug 15 20:16:55 vpn1 pluto[2911]: "L2TP-PSK-noNAT"[3] 62.45.140.54 #6: responding to Quick Mode proposal {msgid:01000000}
Aug 15 20:16:55 vpn1 pluto[2911]: "L2TP-PSK-noNAT"[3] 62.45.140.54 #6:     us: 141.138.138.37<141.138.138.37>:17/%any
Aug 15 20:16:55 vpn1 pluto[2911]: "L2TP-PSK-noNAT"[3] 62.45.140.54 #6:   them: 62.45.140.54[192.168.0.103]:17/1701
Aug 15 20:16:55 vpn1 pluto[2911]: "L2TP-PSK-noNAT"[3] 62.45.140.54 #6: cannot install eroute -- it is in use for "L2TP-PSK-noNAT"[2] 62.45.140.54 #2
Aug 15 20:16:56 vpn1 pluto[2911]: "L2TP-PSK-noNAT"[3] 62.45.140.54 #6: discarding duplicate packet; already STATE_QUICK_R0
Aug 15 20:17:01 vpn1 CRON[2983]: pam_unix(cron:session): session opened for user root by (uid=0)
```

---

