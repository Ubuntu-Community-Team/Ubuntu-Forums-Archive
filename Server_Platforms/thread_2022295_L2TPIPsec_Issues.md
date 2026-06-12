---
title: "L2TP/IPsec Issues"
date: 2012-07-10
forum: Server Platforms
---

### Post by JIohn on 2012-07-10
Hi,

I have done numerous installations of different VPN-solutions on my ubuntu-server, and found none of them to work. 

I recently gave it another go and have gotten quite far, I believe. This is my first attempt to actually ask for help, instead of looking on other posts and guides. 

I simply installed xl2tpd and openswan, configured it as follows:

/etc/ipsec.conf :
> 
config setup
    nat_traversal=yes
  virtual_private=%v4:10.0.0.0/8,%v4:192.168.0.0/16,%v4:172.16.0.0/12,%v4:!10.152.2.0/24
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

And, /etc/ipsec.secrets : 
> 
x.x.x.x   %any:  PSK psw1

In which both x.x.x.x stands for my global IP. After this I tried Sudo ipsec verify, successfully.

I went on to configure  /etc/xl2tpd/xl2tpd.conf : 
> 
[global]
ipsec saref = no
 
[lns default]
ip range = 10.152.2.2-10.152.2.254
local ip = 10.152.2.1
require chap = yes
refuse pap = yes
require authentication = yes
ppp debug = yes
pppoptfile = /etc/ppp/options.xl2tpd
length bit = yes

And then onto,/etc/xl2tpd/l2tp-secrets 
> * * psw2


Then onto  /etc/ppp/options.xl2tpd
> 
refuse-mschap-v2
refuse-mschap
ms-dns 8.8.8.8
ms-dns 8.8.4.4
asyncmap 0
auth
lock
hide-password
local
#debug
name l2tpd
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4


And finally;  /etc/ppp/chap-secrets: 
> user1 * psw3 *


This didn't work, and I looked in the /var/log/auth.log which said this:
> 
Jul 10 22:04:10 yggdrasil pluto[2711]: packet from xxx.xxx.xxx.xxx:55002: received Vendor ID payload [RFC 3947] method set to=109
Jul 10 22:04:10 yggdrasil pluto[2711]: packet from xxx.xxx.xxx.xxx:55002: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02] meth=107, but already using method 109
Jul 10 22:04:10 yggdrasil pluto[2711]: packet from xxx.xxx.xxx.xxx:55002: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02_n] meth=106, but already using method 109
Jul 10 22:04:10 yggdrasil pluto[2711]: packet from xxx.xxx.xxx.xxx:55002: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-00]
Jul 10 22:04:10 yggdrasil pluto[2711]: packet from xxx.xxx.xxx.xxx:55002: ignoring Vendor ID payload [FRAGMENTATION 80000000]
Jul 10 22:04:10 yggdrasil pluto[2711]: packet from xxx.xxx.xxx.xxx:55002: initial Main Mode message received on xxx.xxx.xxx.xxx:500 but no connection has been authorized with policy=PSK

And this reads from /var/log/daemon.log when I restart the two services:
> 
Jul 10 22:31:41 yggdrasil xl2tpd[2764]: death_handler: Fatal signal 15 received
Jul 10 22:31:42 yggdrasil xl2tpd[2866]: setsockopt recvref[22]: Protocol not available
Jul 10 22:31:42 yggdrasil xl2tpd[2866]: This binary does not support kernel L2TP.
Jul 10 22:31:42 yggdrasil xl2tpd[2867]: xl2tpd version xl2tpd-1.2.5 started on yggdrasil PID:2867
Jul 10 22:31:42 yggdrasil xl2tpd[2867]: Written by Mark Spencer, Copyright (C) 1998, Adtran, Inc.
Jul 10 22:31:42 yggdrasil xl2tpd[2867]: Forked by Scott Balmos and David Stipp, (C) 2001
Jul 10 22:31:42 yggdrasil xl2tpd[2867]: Inherited by Jeff McAdams, (C) 2002
Jul 10 22:31:42 yggdrasil xl2tpd[2867]: Forked again by Xelerance ([www.xelerance.com](www.xelerance.com)) (C) 2006
Jul 10 22:31:42 yggdrasil xl2tpd[2867]: Listening on IP address 0.0.0.0, port 1701
Jul 10 22:32:01 yggdrasil ipsec_setup: Stopping Openswan IPsec...
Jul 10 22:32:03 yggdrasil ipsec_setup: ...Openswan IPsec stopped
Jul 10 22:32:03 yggdrasil ipsec_setup: Starting Openswan IPsec U2.6.23/K2.6.32-40-server...
Jul 10 22:32:03 yggdrasil ipsec_setup: Using NETKEY(XFRM) stack
Jul 10 22:32:03 yggdrasil ipsec_setup: ...Openswan IPsec started
Jul 10 22:32:03 yggdrasil ipsec__plutorun: adjusting ipsec.d to /etc/ipsec.d
Jul 10 22:32:03 yggdrasil ipsec__plutorun: 002 added connection description "L2TP-PSK-NAT"
Jul 10 22:32:03 yggdrasil ipsec__plutorun: 002 added connection description "L2TP-PSK-noNAT"
Jul 10 22:32:03 yggdrasil ipsec__plutorun: 003 NAT-Traversal: Trying new style NAT-T
Jul 10 22:32:03 yggdrasil ipsec__plutorun: 003 NAT-Traversal: ESPINUDP(1) setup failed for new style NAT-T family IPv4 (errno=19)
Jul 10 22:32:03 yggdrasil ipsec__plutorun: 003 NAT-Traversal: Trying old style NAT-T


Additionally I tried all of this with ufw disabled. If there's any log, conf file or such I've missed out on pasting, do tell.  Have anyone got any idea of how to fix this, I'm on the verge of giving VPN up.

---

### Post by JIohn on 2012-07-11
Shameless self-bump

---

