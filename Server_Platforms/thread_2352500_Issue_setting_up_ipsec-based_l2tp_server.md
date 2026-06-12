---
title: "Issue setting up ipsec-based l2tp server"
date: 2017-02-13
forum: Server Platforms
---

### Post by kyy1996 on 2017-02-13
I'm gonna set up a vpn server with xl2tpd and openswan. I've configured them as the guidance online, setting the PSK and the secret. But I failed to connect with my l2tp server with my PSK. And I check the log file on the server, I got this 
```

Feb 13 17:30:17 iZj6cfoyz3yh75pknfofjoZ pluto[13939]: packet from Client IP:500: ignoring unknown Vendor ID payload [01528bbbc00696121849ab9a1c5b2a5100000001]
Feb 13 17:30:17 iZj6cfoyz3yh75pknfofjoZ pluto[13939]: packet from Client IP:500: ignoring Vendor ID payload [MS NT5 ISAKMPOAKLEY 00000009]
Feb 13 17:30:17 iZj6cfoyz3yh75pknfofjoZ pluto[13939]: packet from Client IP:500: received Vendor ID payload [RFC 3947] method set to=115 
Feb 13 17:30:17 iZj6cfoyz3yh75pknfofjoZ pluto[13939]: packet from Client IP:500: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02_n] meth=106, but already using method 115Feb 13 17:30:17 iZj6cfoyz3yh75pknfofjoZ pluto[13939]: packet from Client IP:500: ignoring Vendor ID payload [FRAGMENTATION]
Feb 13 17:30:17 iZj6cfoyz3yh75pknfofjoZ pluto[13939]: packet from Client IP:500: ignoring Vendor ID payload [MS-Negotiation Discovery Capable]
Feb 13 17:30:17 iZj6cfoyz3yh75pknfofjoZ pluto[13939]: packet from Client IP:500: ignoring Vendor ID payload [Vid-Initial-Contact]
Feb 13 17:30:17 iZj6cfoyz3yh75pknfofjoZ pluto[13939]: packet from Client IP:500: ignoring Vendor ID payload [IKE CGA version 1]
Feb 13 17:30:17 iZj6cfoyz3yh75pknfofjoZ pluto[13939]: "L2TP-PSK-NAT"[2] Client IP #3: responding to Main Mode from unknown peer Client IP
Feb 13 17:30:17 iZj6cfoyz3yh75pknfofjoZ pluto[13939]: "L2TP-PSK-NAT"[2] Client IP #3: OAKLEY_GROUP 20 not supported.  Attribute OAKLEY_GROUP_DESCRIPTION
Feb 13 17:30:17 iZj6cfoyz3yh75pknfofjoZ pluto[13939]: "L2TP-PSK-NAT"[2] Client IP #3: OAKLEY_GROUP 19 not supported.  Attribute OAKLEY_GROUP_DESCRIPTION
Feb 13 17:30:17 iZj6cfoyz3yh75pknfofjoZ pluto[13939]: "L2TP-PSK-NAT"[2] Client IP #3: transition from state STATE_MAIN_R0 to state STATE_MAIN_R1
Feb 13 17:30:17 iZj6cfoyz3yh75pknfofjoZ pluto[13939]: "L2TP-PSK-NAT"[2] Client IP #3: STATE_MAIN_R1: sent MR1, expecting MI2
Feb 13 17:30:17 iZj6cfoyz3yh75pknfofjoZ pluto[13939]: "L2TP-PSK-NAT"[2] Client IP #3: NAT-Traversal: Result using draft-ietf-ipsec-nat-t-ike (MacOS X): peer is NATed
Feb 13 17:30:17 iZj6cfoyz3yh75pknfofjoZ pluto[13939]: "L2TP-PSK-NAT"[2] Client IP #3: transition from state STATE_MAIN_R1 to state STATE_MAIN_R2
Feb 13 17:30:17 iZj6cfoyz3yh75pknfofjoZ pluto[13939]: "L2TP-PSK-NAT"[2] Client IP #3: STATE_MAIN_R2: sent MR2, expecting MI3
Feb 13 17:30:17 iZj6cfoyz3yh75pknfofjoZ pluto[13939]: "L2TP-PSK-NAT"[2] Client IP #3: Main mode peer ID is ID_IPV4_ADDR: '192.168.99.132'
Feb 13 17:30:17 iZj6cfoyz3yh75pknfofjoZ pluto[13939]: "L2TP-PSK-NAT"[2] Client IP #3: switched from "L2TP-PSK-NAT" to "L2TP-PSK-NAT"
Feb 13 17:30:17 iZj6cfoyz3yh75pknfofjoZ pluto[13939]: "L2TP-PSK-NAT"[3] Client IP #3: transition from state STATE_MAIN_R2 to state STATE_MAIN_R3
Feb 13 17:30:17 iZj6cfoyz3yh75pknfofjoZ pluto[13939]: "L2TP-PSK-NAT"[3] Client IP #3: new NAT mapping for #3, was Client IP:500, now Client IP:4500
Feb 13 17:30:17 iZj6cfoyz3yh75pknfofjoZ pluto[13939]: "L2TP-PSK-NAT"[3] Client IP #3: STATE_MAIN_R3: sent MR3, ISAKMP SA established {auth=OAKLEY_PRESHARED_KEY cipher=aes_256 prf=oakley_sha group=modp2048}
Feb 13 17:30:17 iZj6cfoyz3yh75pknfofjoZ pluto[13939]: "L2TP-PSK-NAT"[3] Client IP #3: the peer proposed: Server IP/32:17/1701 -> 192.168.99.132/32:17/0
Feb 13 17:30:17 iZj6cfoyz3yh75pknfofjoZ pluto[13939]: "L2TP-PSK-NAT"[3] Client IP #3: NAT-Traversal: received 2 NAT-OA. using first, ignoring others
Feb 13 17:30:17 iZj6cfoyz3yh75pknfofjoZ pluto[13939]: "L2TP-PSK-NAT"[3] Client IP #4: responding to Quick Mode proposal {msgid:01000000}
Feb 13 17:30:17 iZj6cfoyz3yh75pknfofjoZ pluto[13939]: "L2TP-PSK-NAT"[3] Client IP #4:     us: Server IP<Server IP>:17/1701
Feb 13 17:30:17 iZj6cfoyz3yh75pknfofjoZ pluto[13939]: "L2TP-PSK-NAT"[3] Client IP #4:   them: Client IP[192.168.99.132]:17/1701===192.168.99.132/32
Feb 13 17:30:17 iZj6cfoyz3yh75pknfofjoZ pluto[13939]: "L2TP-PSK-NAT"[3] Client IP #4: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Feb 13 17:30:17 iZj6cfoyz3yh75pknfofjoZ pluto[13939]: "L2TP-PSK-NAT"[3] Client IP #4: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Feb 13 17:30:17 iZj6cfoyz3yh75pknfofjoZ pluto[13939]: "L2TP-PSK-NAT"[3] Client IP #4: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
Feb 13 17:30:17 iZj6cfoyz3yh75pknfofjoZ pluto[13939]: "L2TP-PSK-NAT"[3] Client IP #4: STATE_QUICK_R2: IPsec SA established transport mode {ESP=>0xaac8eb88 <0x18e62187 xfrm=AES_256-HMAC_SHA1 NATOA=192.168.99.132 NATD=Client IP:4500 DPD=none}

```
I googled this and it told me that the ipsec had succeed in establishing the connection. I checked the syslog file, and I got this related with xl2tpd 
```

xl2tpd[11926]: Listening on IP address 0.0.0.0, port 1701

```
I have no idea about what's going on with ipsec and xl2tpd.
I would appreciate it very much if you could help me with these things. Thank you!

---

