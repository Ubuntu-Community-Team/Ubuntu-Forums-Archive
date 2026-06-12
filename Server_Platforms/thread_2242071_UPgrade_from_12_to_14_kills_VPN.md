---
title: "UPgrade from 12 to 14 kills VPN"
date: 2014-08-30
forum: Server Platforms
---

### Post by DigiAngel on 2014-08-30
Topic says it...here's when it works:

```
Aug 30 08:36:48 gateway pluto[1785]: packet from 166.137.180.136:33168: received Vendor ID payload [RFC 3947] method set to=109
Aug 30 08:36:48 gateway pluto[1785]: packet from 166.137.180.136:33168: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike] method set to=110
Aug 30 08:36:48 gateway pluto[1785]: packet from 166.137.180.136:33168: ignoring unknown Vendor ID payload [8f8d83826d246b6fc7a8a6a428c11de8]
Aug 30 08:36:48 gateway pluto[1785]: packet from 166.137.180.136:33168: ignoring unknown Vendor ID payload [439b59f8ba676c4c7737ae22eab8f582]
Aug 30 08:36:48 gateway pluto[1785]: packet from 166.137.180.136:33168: ignoring unknown Vendor ID payload [4d1e0e136deafa34c4f3ea9f02ec7285]
Aug 30 08:36:48 gateway pluto[1785]: packet from 166.137.180.136:33168: ignoring unknown Vendor ID payload [80d0bb3def54565ee84645d4c85ce3ee]
Aug 30 08:36:48 gateway pluto[1785]: packet from 166.137.180.136:33168: ignoring unknown Vendor ID payload [9909b64eed937c6573de52ace952fa6b]
Aug 30 08:36:48 gateway pluto[1785]: packet from 166.137.180.136:33168: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-03] meth=108, but already using method 110
Aug 30 08:36:48 gateway pluto[1785]: packet from 166.137.180.136:33168: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02] meth=107, but already using method 110
Aug 30 08:36:48 gateway pluto[1785]: packet from 166.137.180.136:33168: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02_n] meth=106, but already using method 110
Aug 30 08:36:48 gateway pluto[1785]: packet from 166.137.180.136:33168: ignoring Vendor ID payload [FRAGMENTATION 80000000]
Aug 30 08:36:48 gateway pluto[1785]: packet from 166.137.180.136:33168: received Vendor ID payload [Dead Peer Detection]
Aug 30 08:36:48 gateway pluto[1785]: "L2TP-PSK-NAT"[1] 166.137.180.136 #1: responding to Main Mode from unknown peer 166.137.180.136
Aug 30 08:36:48 gateway pluto[1785]: "L2TP-PSK-NAT"[1] 166.137.180.136 #1: transition from state STATE_MAIN_R0 to state STATE_MAIN_R1
Aug 30 08:36:48 gateway pluto[1785]: "L2TP-PSK-NAT"[1] 166.137.180.136 #1: STATE_MAIN_R1: sent MR1, expecting MI2
Aug 30 08:36:48 gateway pluto[1785]: "L2TP-PSK-NAT"[1] 166.137.180.136 #1: NAT-Traversal: Result using draft-ietf-ipsec-nat-t-ike (MacOS X): peer is NATed
Aug 30 08:36:48 gateway pluto[1785]: "L2TP-PSK-NAT"[1] 166.137.180.136 #1: transition from state STATE_MAIN_R1 to state STATE_MAIN_R2
Aug 30 08:36:48 gateway pluto[1785]: "L2TP-PSK-NAT"[1] 166.137.180.136 #1: STATE_MAIN_R2: sent MR2, expecting MI3
Aug 30 08:36:49 gateway pluto[1785]: "L2TP-PSK-NAT"[1] 166.137.180.136 #1: ignoring informational payload, type IPSEC_INITIAL_CONTACT msgid=00000000
Aug 30 08:36:49 gateway pluto[1785]: "L2TP-PSK-NAT"[1] 166.137.180.136 #1: Main mode peer ID is ID_IPV4_ADDR: '10.176.17.79'
Aug 30 08:36:49 gateway pluto[1785]: "L2TP-PSK-NAT"[1] 166.137.180.136 #1: switched from "L2TP-PSK-NAT" to "L2TP-PSK-NAT"
Aug 30 08:36:49 gateway pluto[1785]: "L2TP-PSK-NAT"[2] 166.137.180.136 #1: deleting connection "L2TP-PSK-NAT" instance with peer 166.137.180.136 {isakmp=#0/ipsec=#0}
Aug 30 08:36:49 gateway pluto[1785]: "L2TP-PSK-NAT"[2] 166.137.180.136 #1: transition from state STATE_MAIN_R2 to state STATE_MAIN_R3
Aug 30 08:36:49 gateway pluto[1785]: "L2TP-PSK-NAT"[2] 166.137.180.136 #1: new NAT mapping for #1, was 166.137.180.136:33168, now 166.137.180.136:43229
Aug 30 08:36:49 gateway pluto[1785]: "L2TP-PSK-NAT"[2] 166.137.180.136 #1: STATE_MAIN_R3: sent MR3, ISAKMP SA established {auth=OAKLEY_PRESHARED_KEY cipher=aes_256 prf=oakley_sha group=modp1024}
Aug 30 08:36:50 gateway pluto[1785]: "L2TP-PSK-NAT"[2] 166.137.180.136 #1: Applying workaround for Mac OS X NAT-OA bug, ignoring proposed subnet
Aug 30 08:36:50 gateway pluto[1785]: "L2TP-PSK-NAT"[2] 166.137.180.136 #1: the peer proposed: x.x.x.x/32:17/1701 -> 166.137.180.136/32:17/0
Aug 30 08:36:50 gateway pluto[1785]: "L2TP-PSK-NAT"[2] 166.137.180.136 #1: peer proposal was reject in a virtual connection policy because:
Aug 30 08:36:50 gateway pluto[1785]: "L2TP-PSK-NAT"[2] 166.137.180.136 #1:   a private network virtual IP was required, but the proposed IP did not match our list (virtual_private=)
Aug 30 08:36:50 gateway pluto[1785]: "L2TP-PSK-noNAT"[1] 166.137.180.136 #2: responding to Quick Mode proposal {msgid:2a3c93ba}
Aug 30 08:36:50 gateway pluto[1785]: "L2TP-PSK-noNAT"[1] 166.137.180.136 #2:     us: x.x.x.x<x.x.x.x>[+S=C]:17/1701
Aug 30 08:36:50 gateway pluto[1785]: "L2TP-PSK-noNAT"[1] 166.137.180.136 #2:   them: 166.137.180.136[10.176.17.79,+S=C]:17/51288
Aug 30 08:36:50 gateway pluto[1785]: "L2TP-PSK-noNAT"[1] 166.137.180.136 #2: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Aug 30 08:36:50 gateway pluto[1785]: "L2TP-PSK-noNAT"[1] 166.137.180.136 #2: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Aug 30 08:36:51 gateway pluto[1785]: "L2TP-PSK-noNAT"[1] 166.137.180.136 #2: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
Aug 30 08:36:51 gateway pluto[1785]: "L2TP-PSK-noNAT"[1] 166.137.180.136 #2: STATE_QUICK_R2: IPsec SA established transport mode {ESP=>0x0a5e3055 <0xdb309ef9 xfrm=AES_256-HMAC_SHA1 NATOA=none NATD=166.137.180.136:43229 DPD=none}
Aug 30 08:36:53 gateway xl2tpd[2389]: control_finish: Peer requested tunnel 1 twice, ignoring second one.
Aug 30 08:36:53 gateway xl2tpd[2389]: Connection established to 166.137.180.136, 51288.  Local: 45608, Remote: 1 (ref=0/0).  LNS session is 'default'
Aug 30 08:36:53 gateway xl2tpd[2389]: start_pppd: I'm running:
Aug 30 08:36:53 gateway xl2tpd[2389]: "/usr/sbin/pppd"
Aug 30 08:36:53 gateway xl2tpd[2389]: "passive"
Aug 30 08:36:53 gateway xl2tpd[2389]: "nodetach"
Aug 30 08:36:53 gateway xl2tpd[2389]: "192.168.1.10:192.168.1.11"
Aug 30 08:36:53 gateway xl2tpd[2389]: "refuse-pap"
Aug 30 08:36:53 gateway xl2tpd[2389]: "refuse-chap"
Aug 30 08:36:53 gateway xl2tpd[2389]: "debug"
Aug 30 08:36:53 gateway xl2tpd[2389]: "file"
Aug 30 08:36:53 gateway xl2tpd[2389]: "/etc/ppp/options.xl2tpd"
Aug 30 08:36:53 gateway xl2tpd[2389]: "ipparam"
Aug 30 08:36:53 gateway xl2tpd[2389]: "166.137.180.136"
Aug 30 08:36:53 gateway xl2tpd[2389]: "/dev/pts/8"
Aug 30 08:36:53 gateway xl2tpd[2389]: Call established with 166.137.180.136, Local: 7715, Remote: 380, Serial: 1
```

And here's after upgrade:
```
Aug 30 08:21:28 gateway pluto[1774]: packet from 166.137.183.221:36695: received Vendor ID payload [RFC 3947] method set to=115
Aug 30 08:21:28 gateway pluto[1774]: packet from 166.137.183.221:36695: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike] meth=114, but already using method 115
Aug 30 08:21:28 gateway pluto[1774]: packet from 166.137.183.221:36695: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-08] meth=113, but already using method 115
Aug 30 08:21:28 gateway pluto[1774]: packet from 166.137.183.221:36695: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-07] meth=112, but already using method 115
Aug 30 08:21:28 gateway pluto[1774]: packet from 166.137.183.221:36695: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-06] meth=111, but already using method 115
Aug 30 08:21:28 gateway pluto[1774]: packet from 166.137.183.221:36695: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-05] meth=110, but already using method 115
Aug 30 08:21:28 gateway pluto[1774]: packet from 166.137.183.221:36695: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-04] meth=109, but already using method 115
Aug 30 08:21:28 gateway pluto[1774]: packet from 166.137.183.221:36695: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-03] meth=108, but already using method 115
Aug 30 08:21:28 gateway pluto[1774]: packet from 166.137.183.221:36695: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02] meth=107, but already using method 115
Aug 30 08:21:28 gateway pluto[1774]: packet from 166.137.183.221:36695: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02_n] meth=106, but already using method 115
Aug 30 08:21:28 gateway pluto[1774]: packet from 166.137.183.221:36695: ignoring Vendor ID payload [FRAGMENTATION 80000000]
Aug 30 08:21:28 gateway pluto[1774]: packet from 166.137.183.221:36695: received Vendor ID payload [Dead Peer Detection]
Aug 30 08:21:28 gateway pluto[1774]: "L2TP-PSK-NAT"[7] 166.137.183.221 #7: responding to Main Mode from unknown peer 166.137.183.221
Aug 30 08:21:28 gateway pluto[1774]: "L2TP-PSK-NAT"[7] 166.137.183.221 #7: transition from state STATE_MAIN_R0 to state STATE_MAIN_R1
Aug 30 08:21:28 gateway pluto[1774]: "L2TP-PSK-NAT"[7] 166.137.183.221 #7: STATE_MAIN_R1: sent MR1, expecting MI2
Aug 30 08:21:29 gateway pluto[1774]: "L2TP-PSK-NAT"[7] 166.137.183.221 #7: NAT-Traversal: Result using draft-ietf-ipsec-nat-t-ike (MacOS X): peer is NATed
Aug 30 08:21:29 gateway pluto[1774]: "L2TP-PSK-NAT"[7] 166.137.183.221 #7: transition from state STATE_MAIN_R1 to state STATE_MAIN_R2
Aug 30 08:21:29 gateway pluto[1774]: "L2TP-PSK-NAT"[7] 166.137.183.221 #7: STATE_MAIN_R2: sent MR2, expecting MI3
Aug 30 08:21:29 gateway pluto[1774]: "L2TP-PSK-NAT"[7] 166.137.183.221 #7: ignoring informational payload, type IPSEC_INITIAL_CONTACT msgid=00000000
Aug 30 08:21:29 gateway pluto[1774]: "L2TP-PSK-NAT"[7] 166.137.183.221 #7: Main mode peer ID is ID_IPV4_ADDR: '172.20.10.2'
Aug 30 08:21:29 gateway pluto[1774]: "L2TP-PSK-NAT"[7] 166.137.183.221 #7: switched from "L2TP-PSK-NAT" to "L2TP-PSK-NAT"
Aug 30 08:21:29 gateway pluto[1774]: "L2TP-PSK-NAT"[8] 166.137.183.221 #7: deleting connection "L2TP-PSK-NAT" instance with peer 166.137.183.221 {isakmp=#0/ipsec=#0}
Aug 30 08:21:29 gateway pluto[1774]: "L2TP-PSK-NAT"[8] 166.137.183.221 #7: transition from state STATE_MAIN_R2 to state STATE_MAIN_R3
Aug 30 08:21:29 gateway pluto[1774]: "L2TP-PSK-NAT"[8] 166.137.183.221 #7: new NAT mapping for #7, was 166.137.183.221:36695, now 166.137.183.221:60281
Aug 30 08:21:29 gateway pluto[1774]: "L2TP-PSK-NAT"[8] 166.137.183.221 #7: STATE_MAIN_R3: sent MR3, ISAKMP SA established {auth=OAKLEY_PRESHARED_KEY cipher=aes_256 prf=oakley_sha group=modp1024}
Aug 30 08:21:31 gateway pluto[1774]: "L2TP-PSK-NAT"[8] 166.137.183.221 #7: the peer proposed: x.x.x.x/32:17/1701 -> 172.20.10.2/32:17/0
Aug 30 08:21:31 gateway pluto[1774]: "L2TP-PSK-NAT"[8] 166.137.183.221 #7: NAT-Traversal: received 2 NAT-OA. using first, ignoring others
Aug 30 08:21:31 gateway pluto[1774]: "L2TP-PSK-NAT"[8] 166.137.183.221 #8: responding to Quick Mode proposal {msgid:e6652dfa}
Aug 30 08:21:31 gateway pluto[1774]: "L2TP-PSK-NAT"[8] 166.137.183.221 #8:     us: x.x.x.x<x.x.x.x>:17/1701
Aug 30 08:21:31 gateway pluto[1774]: "L2TP-PSK-NAT"[8] 166.137.183.221 #8:   them: 166.137.183.221[172.20.10.2]:17/51302===172.20.10.2/32
Aug 30 08:21:31 gateway pluto[1774]: "L2TP-PSK-NAT"[8] 166.137.183.221 #8: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
Aug 30 08:21:31 gateway pluto[1774]: "L2TP-PSK-NAT"[8] 166.137.183.221 #8: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
Aug 30 08:21:31 gateway pluto[1774]: "L2TP-PSK-NAT"[8] 166.137.183.221 #8: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
Aug 30 08:21:31 gateway pluto[1774]: "L2TP-PSK-NAT"[8] 166.137.183.221 #8: STATE_QUICK_R2: IPsec SA established transport mode {ESP=>0x02a7500e <0xd525770f xfrm=AES_256-HMAC_SHA1 NATOA=172.20.10.2 NATD=166.137.183.221:60281 DPD=none}
Aug 30 08:21:51 gateway pluto[1774]: "L2TP-PSK-NAT"[8] 166.137.183.221 #7: received Delete SA(0x02a7500e) payload: deleting IPSEC State #8
Aug 30 08:21:51 gateway pluto[1774]: "L2TP-PSK-NAT"[8] 166.137.183.221 #7: ERROR: netlink XFRM_MSG_DELPOLICY response for flow eroute_connection delete included errno 2: No such file or directory
Aug 30 08:21:51 gateway pluto[1774]: "L2TP-PSK-NAT"[8] 166.137.183.221 #7: received and ignored informational message
Aug 30 08:21:51 gateway pluto[1774]: "L2TP-PSK-NAT"[8] 166.137.183.221 #7: received Delete SA payload: deleting ISAKMP State #7
Aug 30 08:21:51 gateway pluto[1774]: "L2TP-PSK-NAT"[8] 166.137.183.221: deleting connection "L2TP-PSK-NAT" instance with peer 166.137.183.221 {isakmp=#0/ipsec=#0}
Aug 30 08:21:51 gateway pluto[1774]: packet from 166.137.183.221:60281: received and ignored informational message

```

I'm not even sure where to begin...thanks for any hints you might have.

---

### Post by nerdtron on 2014-08-31
How did you upgraded from 12 to 14?
Post the content of your server.conf, and try increasing the verbosity of the logs to 5 or 6.

---

### Post by DigiAngel on 2014-09-01
Thanks for responding.  This was done with a do-release-upgrade.  Here's my xl2tpd.conf:
```
[global]
ipsec saref = yes

[lns default]
ip range = 192.168.1.11-192.168.1.12
local ip = 192.168.1.10
refuse chap = yes
refuse pap = yes
require authentication = no
ppp debug = yes
pppoptfile = /etc/ppp/options.xl2tpd
length bit = yes

```

And my ipsec.conf:
```
version 2.0
config setup
	nat_traversal=yes
	virtual_private=%v4:10.0.0.0/8,%v4:192.168.0.0/16,%v4:172.16.0.0/12
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
    ikelifetime=8h
    keylife=1h
    type=transport
    left=x.x.x.x
    leftprotoport=17/1701
    right=%any
    rightprotoport=17/%any

```

Again, this works in 12.04.5.  Further looking, here's the start in 14:
```
Aug 30 07:46:21 gateway xl2tpd[2494]: Enabling IPsec SAref processing for L2TP transport mode SAs
Aug 30 07:46:21 gateway xl2tpd[2494]: IPsec SAref does not work with L2TP kernel mode yet, enabling force userspace=yes
Aug 30 07:46:21 gateway xl2tpd[2494]: setsockopt recvref[30]: Protocol not available
Aug 30 07:46:21 gateway xl2tpd[2494]: This binary does not support kernel L2TP.
Aug 30 07:46:21 gateway xl2tpd[2495]: xl2tpd version xl2tpd-1.3.6 started on gateway PID:2495
Aug 30 07:46:21 gateway xl2tpd[2495]: Written by Mark Spencer, Copyright (C) 1998, Adtran, Inc.
Aug 30 07:46:21 gateway xl2tpd[2495]: Forked by Scott Balmos and David Stipp, (C) 2001
Aug 30 07:46:21 gateway xl2tpd[2495]: Inherited by Jeff McAdams, (C) 2002
Aug 30 07:46:21 gateway xl2tpd[2495]: Forked again by Xelerance (www.xelerance.com) (C) 2006
Aug 30 07:46:21 gateway xl2tpd[2495]: Listening on IP address 0.0.0.0, port 1701

```

And the start in 12:
```
Aug 12 05:13:15 gateway xl2tpd[2376]: Enabling IPsec SAref processing for L2TP transport mode SAs
Aug 12 05:13:15 gateway xl2tpd[2376]: IPsec SAref does not work with L2TP kernel mode yet, enabling forceuserspace=yes
Aug 12 05:13:15 gateway xl2tpd[2376]: setsockopt recvref[30]: Protocol not available
Aug 12 05:13:15 gateway xl2tpd[2376]: This binary does not support kernel L2TP.
Aug 12 05:13:15 gateway xl2tpd[2377]: xl2tpd version xl2tpd-1.3.1 started on gateway PID:2377
Aug 12 05:13:15 gateway xl2tpd[2377]: Written by Mark Spencer, Copyright (C) 1998, Adtran, Inc.
Aug 12 05:13:15 gateway xl2tpd[2377]: Forked by Scott Balmos and David Stipp, (C) 2001
Aug 12 05:13:15 gateway xl2tpd[2377]: Inherited by Jeff McAdams, (C) 2002
Aug 12 05:13:15 gateway xl2tpd[2377]: Forked again by Xelerance (www.xelerance.com) (C) 2006
Aug 12 05:13:15 gateway xl2tpd[2377]: Listening on IP address 0.0.0.0, port 1701

```

I dont' see a whole lotta differences.  Thanks agian.

---

### Post by DigiAngel on 2014-10-04
Anyone have any ideas on this?  My old server just died....so now I'm forced to try and fix this.  It looks like xl2tpd doesn't even do anything when I attempt with vpn.  Please help...dead in the water with no VPN.

---

### Post by nerdtron on 2014-10-04
No idea...why did you performed a version upgrade? It's not recommended as you won't know what will happen. Did you even test out your setup on a VM with 14.04 before you even upgrade?

Anyway, why not test now on a fresh install. OpenVPN and its configs are really easy to setup.

---

### Post by DigiAngel on 2014-10-04
I did the upgrade on a development box.  The point was not to have the dev box be put in production, but alas, the production box power supply died.  Thanks anyway.

---

