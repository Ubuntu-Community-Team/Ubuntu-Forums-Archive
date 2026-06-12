---
title: "Openswan L2TP / IPSEC / PSK established connection, but no activity on XL2TPD"
date: 2014-03-18
forum: Server Platforms
---

### Post by robert-woodward on 2014-03-18
Hi All,

I have been pulling my hair out with this now for some time, I can connect to my server using the less secure PPTP, but would much prefer to upgrade to using L2TP / IPSEC.  My network layout is as follows:


**Internal Network**  <===>  **eth0 (DHCP Server 192.168.80.1 range 192.168.80.2 - 192.168.80.159) Ubuntu Server eth1 (DHCP Client - 94.173.XXX.XXX) ** <======> **WWW** <=====> **Android Mobile (O2 UK)**
**192.168.80.XX**

Note: I do have a Virginmedia Superhub in modem mode, which I am assured by lots of Googling should be fine!  and I have also Googled on O2 UK allowing VPN traffic, as well as Android 4.3 issues, all of which I believe are good to go.

/etc/sysctl.conf
```

net.ipv4.ip_forward=1


net.ipv4.conf.all.accept_redirects = 0
net.ipv4.conf.all.send_redirects = 0


net.ipv4.conf.default.send_redirects = 0
net.ipv4.conf.eth0.send_redirects = 0
net.ipv4.conf.eth1.send_redirects = 0
net.ipv4.conf.lo.send_redirects = 0


net.ipv4.conf.default.accept_redirects = 0
net.ipv4.conf.eth0.accept_redirects = 0
net.ipv4.conf.eth1.accept_redirects = 0
net.ipv4.conf.lo.accept_redirects = 0

```

/etc/ipsec.conf
```

version 2.0


config setup
        dumpdir=/var/run/pluto/
        nat_traversal=yes
        oe=off
        protostack=netkey
        virtual_private=%v4:10.0.0.0/8,%v4:192.168.80.0/16,%v4:172.16.0.0/12,%v4:25.0.0.0/8
        plutostderrlog=/var/log/pluto.log
        nhelpers=0


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
    left=94.173.XXX.XXX #eth1 ip address
    leftprotoport=17/1701
    right=%any
    rightprotoport=17/%any
    dpddelay=15
    dpdtimeout=30
    dpdaction=clear

```

/etc/ipsec.secrets
```

94.173.XXX.XXX  %any:   PSK "MyVeryStrongPasswordHere!"

```

/etc/xl2tpd/xl2tpd.conf
```

[global]
ipsec saref = no
listen-addr = 94.173.XXX.XXX
port = 1701
debug tunnel = yes
debug avp = yes
debug packet = yes
debug network = yes
debug state = yes


[lns default]
ip range = 192.168.80.201-192.168.80.249
local ip = 192.168.80.200
refuse chap = yes
refuse pap = yes
require authentication = yes
ppp debug = yes
pppoptfile = /etc/ppp/options.xl2tpd
length bit = yes

```


/etc/ppp/options.xl2tpd
```

require-mschap-v2
ipcp-accept-remote
ms-dns 8.8.8.8
ms-dns 8.8.4.4
asyncmap 0
auth
#crtscts
lock
hide-password
noccp
modem
dump
logfile /var/log/xl2tpd.log
logfd 2
idle 1800
mtu 1410
mru 1410
name l2tpd
proxyarp
lcp-echo-interval 30
lcp-echo-failure 4
connect-delay 5000

```

and finally...
/etc/ppp/chap-secrets
```

# Secrets for authentication using CHAP
# client        server  secret                  IP addresses




testUser  l2tpd  MyVerySafePassword  *

```


in /var/log/ I get the following:
pluto.log
```
Plutorun started on Tue Mar 18 13:02:10 GMT 2014
adjusting ipsec.d to /etc/ipsec.d
Starting Pluto (Openswan Version 2.6.38; Vendor ID OEvy\134kgzWq\134s) pid:20365
LEAK_DETECTIVE support [disabled]
OCF support for IKE [disabled]
SAref support [disabled]: Protocol not available
SAbind support [disabled]: Protocol not available
NSS support [disabled]
HAVE_STATSD notification support not compiled in
Setting NAT-Traversal port-4500 floating to on
   port floating activation criteria nat_t=1/port_float=1
   NAT-Traversal support  [enabled]
using /dev/urandom as source of random entropy
ike_alg_register_enc(): Activating OAKLEY_AES_CBC: Ok (ret=0)
ike_alg_register_hash(): Activating OAKLEY_SHA2_512: Ok (ret=0)
ike_alg_register_hash(): Activating OAKLEY_SHA2_256: Ok (ret=0)
no helpers will be started, all cryptographic operations will be done inline
Using Linux 2.6 IPsec interface code on 3.11.0-18-generic (experimental code)
ike_alg_register_enc(): Activating aes_ccm_8: Ok (ret=0)
ike_alg_add(): ERROR: algo_type '0', algo_id '0', Algorithm type already exists
ike_alg_register_enc(): Activating aes_ccm_12: FAILED (ret=-17)
ike_alg_add(): ERROR: algo_type '0', algo_id '0', Algorithm type already exists
ike_alg_register_enc(): Activating aes_ccm_16: FAILED (ret=-17)
ike_alg_add(): ERROR: algo_type '0', algo_id '0', Algorithm type already exists
ike_alg_register_enc(): Activating aes_gcm_8: FAILED (ret=-17)
ike_alg_add(): ERROR: algo_type '0', algo_id '0', Algorithm type already exists
ike_alg_register_enc(): Activating aes_gcm_12: FAILED (ret=-17)
ike_alg_add(): ERROR: algo_type '0', algo_id '0', Algorithm type already exists
ike_alg_register_enc(): Activating aes_gcm_16: FAILED (ret=-17)
added connection description "L2TP-PSK-NAT"
added connection description "L2TP-PSK-noNAT"
listening for IKE messages
adding interface eth1/eth1 94.173.XXX.XXX:500
adding interface eth1/eth1 94.173.XXX.XXX:4500
adding interface eth0/eth0 192.168.80.1:500
adding interface eth0/eth0 192.168.80.1:4500
adding interface lo/lo 127.0.0.1:500
adding interface lo/lo 127.0.0.1:4500
adding interface lo/lo ::1:500
loading secrets from "/etc/ipsec.secrets"
packet from 82.132.XXX.XXX:56526: received Vendor ID payload [RFC 3947] method set to=115
packet from 82.132.XXX.XXX:56526: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02] meth=107, but already using method 115
packet from 82.132.XXX.XXX:56526: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02_n] meth=106, but already using method 115
packet from 82.132.XXX.XXX:56526: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-00]
packet from 82.132.XXX.XXX:56526: ignoring Vendor ID payload [FRAGMENTATION 80000000]
packet from 82.132.XXX.XXX:56526: received Vendor ID payload [Dead Peer Detection]
"L2TP-PSK-NAT"[1] 82.132.XXX.XXX #1: responding to Main Mode from unknown peer 82.132.XXX.XXX
"L2TP-PSK-NAT"[1] 82.132.XXX.XXX #1: transition from state STATE_MAIN_R0 to state STATE_MAIN_R1
"L2TP-PSK-NAT"[1] 82.132.XXX.XXX #1: STATE_MAIN_R1: sent MR1, expecting MI2
"L2TP-PSK-NAT"[1] 82.132.XXX.XXX #1: NAT-Traversal: Result using draft-ietf-ipsec-nat-t-ike (MacOS X): peer is NATed
"L2TP-PSK-NAT"[1] 82.132.XXX.XXX #1: transition from state STATE_MAIN_R1 to state STATE_MAIN_R2
"L2TP-PSK-NAT"[1] 82.132.XXX.XXX #1: STATE_MAIN_R2: sent MR2, expecting MI3
"L2TP-PSK-NAT"[1] 82.132.XXX.XXX #1: Main mode peer ID is ID_IPV4_ADDR: '10.90.104.208'
"L2TP-PSK-NAT"[1] 82.132.XXX.XXX #1: switched from "L2TP-PSK-NAT" to "L2TP-PSK-NAT"
"L2TP-PSK-NAT"[2] 82.132.XXX.XXX #1: deleting connection "L2TP-PSK-NAT" instance with peer 82.132.XXX.XXX {isakmp=#0/ipsec=#0}
"L2TP-PSK-NAT"[2] 82.132.XXX.XXX #1: transition from state STATE_MAIN_R2 to state STATE_MAIN_R3
"L2TP-PSK-NAT"[2] 82.132.XXX.XXX #1: new NAT mapping for #1, was 82.132.XXX.XXX:56526, now 82.132.XXX.XXX:56527
"L2TP-PSK-NAT"[2] 82.132.XXX.XXX #1: STATE_MAIN_R3: sent MR3, ISAKMP SA established {auth=OAKLEY_PRESHARED_KEY cipher=aes_256 prf=oakley_sha group=modp1024}
"L2TP-PSK-NAT"[2] 82.132.XXX.XXX #1: Dead Peer Detection (RFC 3706): enabled
"L2TP-PSK-NAT"[2] 82.132.XXX.XXX #1: ignoring informational payload, type IPSEC_INITIAL_CONTACT msgid=00000000
"L2TP-PSK-NAT"[2] 82.132.XXX.XXX #1: received and ignored informational message
"L2TP-PSK-NAT"[2] 82.132.XXX.XXX #1: the peer proposed: 94.173.XXX.XXX/32:17/1701 -> 10.90.104.208/32:17/0
"L2TP-PSK-NAT"[2] 82.132.XXX.XXX #2: responding to Quick Mode proposal {msgid:194007dc}
"L2TP-PSK-NAT"[2] 82.132.XXX.XXX #2:     us: 94.173.XXX.XXX<94.173.XXX.XXX>:17/1701
"L2TP-PSK-NAT"[2] 82.132.XXX.XXX #2:   them: 82.132.XXX.XXX[10.90.104.208]:17/0===10.90.104.208/32
"L2TP-PSK-NAT"[2] 82.132.XXX.XXX #2: transition from state STATE_QUICK_R0 to state STATE_QUICK_R1
"L2TP-PSK-NAT"[2] 82.132.XXX.XXX #2: STATE_QUICK_R1: sent QR1, inbound IPsec SA installed, expecting QI2
"L2TP-PSK-NAT"[2] 82.132.XXX.XXX #2: Dead Peer Detection (RFC 3706): enabled
"L2TP-PSK-NAT"[2] 82.132.XXX.XXX #2: transition from state STATE_QUICK_R1 to state STATE_QUICK_R2
"L2TP-PSK-NAT"[2] 82.132.XXX.XXX #2: STATE_QUICK_R2: IPsec SA established transport mode {ESP=>0x04c60f9e <0x79137141 xfrm=AES_256-HMAC_SHA1 NATOA=none NATD=82.132.XXX.XXX:56527 DPD=enabled}
"L2TP-PSK-NAT"[2] 82.132.XXX.XXX #1: DPD: No response from peer - declaring peer dead
"L2TP-PSK-NAT"[2] 82.132.XXX.XXX #1: DPD: Clearing Connection
"L2TP-PSK-NAT" #2: deleting state (STATE_QUICK_R2)
"L2TP-PSK-NAT" #1: deleting state (STATE_MAIN_R3)
"L2TP-PSK-NAT"[2] 82.132.XXX.XXX: deleting connection "L2TP-PSK-NAT" instance with peer 82.132.XXX.XXX {isakmp=#0/ipsec=#0}
ERROR: asynchronous network error report on eth1 (sport=4500) for message to 82.132.XXX.XXX port 56527, complainant 82.132.XXX.XXX: Connection refused [errno 111, origin ICMP type 3 code 3 (not authenticated)]
ERROR: asynchronous network error report on eth1 (sport=4500) for message to 82.132.XXX.XXX port 56527, complainant 82.132.XXX.XXX: Connection refused [errno 111, origin ICMP type 3 code 3 (not authenticated)]
ERROR: asynchronous network error report on eth1 (sport=4500) for message to 82.132.XXX.XXX port 56527, complainant 82.132.XXX.XXX: Connection refused [errno 111, origin ICMP type 3 code 3 (not authenticated)]
ERROR: asynchronous network error report on eth1 (sport=4500) for message to 82.132.XXX.XXX port 56527, complainant 82.132.XXX.XXX: Connection refused [errno 111, origin ICMP type 3 code 3 (not authenticated)]

```

Which I'm pretty sure the "***STATE_QUICK_R2: IPsec SA established transport mode***" part means I have successfully established the connection, just need to authenticate!  It is some time before the "***DPD: No response from peer - declaring peer dead***" line appears.


But...... syslog / auth.log are both dormant, nothing at all from XL2TPD after it's initial start-up in syslog
```

Mar 18 16:33:01 Ubuntu-Server xl2tpd[25772]: IPsec SAref does not work with L2TP kernel mode yet, enabling forceuserspace=yes
Mar 18 16:33:01 Ubuntu-Server xl2tpd[25772]: setsockopt recvref[30]: Protocol not available
Mar 18 16:33:01 Ubuntu-Server xl2tpd[25772]: This binary does not support kernel L2TP.
Mar 18 16:33:01 Ubuntu-Server xl2tpd[25773]: xl2tpd version xl2tpd-1.3.1 started on Ubuntu-Server PID:25773
Mar 18 16:33:01 Ubuntu-Server xl2tpd[25773]: Written by Mark Spencer, Copyright (C) 1998, Adtran, Inc.
Mar 18 16:33:01 Ubuntu-Server xl2tpd[25773]: Forked by Scott Balmos and David Stipp, (C) 2001
Mar 18 16:33:01 Ubuntu-Server xl2tpd[25773]: Inherited by Jeff McAdams, (C) 2002
Mar 18 16:33:01 Ubuntu-Server xl2tpd[25773]: Forked again by Xelerance (www.xelerance.com) (C) 2006
Mar 18 16:33:01 Ubuntu-Server xl2tpd[25773]: Listening on IP address 94.173.XXX.XXX, port 1701

```

extra iptables commands issued:
```

iptables -I INPUT -p UDP --dport 4500 -j ACCEPT
iptables -I INPUT -p UDP --dport 500 -j ACCEPT
iptables -I INPUT --protocol ESP --in-interface eth1 --jump ACCEPT

```

Can any of you see if there's anything wrong / missing with the set up please?!  I'd really like to get this up and running!!  Even be happy to change to Certificates if it's know to be more reliable, and anyone can tell me how to set it up!!!!

Thanks in advance.

---

### Post by robert-woodward on 2014-03-21
Anybody at all?  Any VPN Guru's (Or at least someone with a similar network layout which is working?!) on this forum that could help?!


Thanks.


[UPDATE]
Also maybe worth mentioning I tried this before with LinuxMCE 10.04, therefore, a different OS, Linux kernel, version of Openswan, and a different phone, so I'm assuming it must be something fundamental I'm missing here.

[FURTHER UPDATE]

Also tried the following guide:
[https://help.ubuntu.com/community/L2TPServer](https://help.ubuntu.com/community/L2TPServer)

No success, and despite my setting ```
net.ipv4.ip_forward=1
```, and ```
iptables -A POSTROUTING -o eth1 -j MASQUERADE
```. I still get the following from ipsec verify:

```

Checking your system to see if IPsec got installed and started correctly:
Version check and ipsec on-path                                           [OK]
Linux Openswan U2.6.38/K3.11.0-18-generic (netkey)
Checking for IPsec support in kernel                                      [OK]
 SAref kernel support                                                           [N/A]
 NETKEY:  Testing XFRM related proc values                          [OK]
                                                                                         [OK]
                                                                                         [OK]
Checking that pluto is running                                               [OK]
 Pluto listening for IKE on udp 500                                         [OK]
 Pluto listening for NAT-T on udp 4500                                   [OK]
Two or more interfaces found, checking IP forwarding            [COLOR=#ff0000]**[FAILED]**[/COLOR]
Checking NAT and MASQUERADEing                                      [OK]
Checking for 'ip' command                                                    [OK]
Checking /bin/sh is not /bin/dash                                           [WARNING]
Checking for 'iptables' command                                            [OK]
Opportunistic Encryption Support                                           [DISABLED]

```

my /network/interfaces is as follows:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The External network interface
auto eth1
iface eth1 inet dhcp


# The Internal network interface
auto eth0
iface eth0 inet static
        address 192.168.80.1
        netmask 255.255.255.0
        post-up iptables-restore < /etc/iptables.up.rules
        gateway 192.168.80.1

```

---

### Post by robert-woodward on 2014-03-25
Can anyone help with this please?!  Or should I have put it in a different forum?  i.e. Networking & Wireless etc, happy to move it (if that's possible, re-post there if not) if it will attract some help / insight into what I'm doing wrong here!

---

### Post by robert-woodward on 2014-04-01
Bump.......?!  Anyone?

---

### Post by robert-woodward on 2014-04-07
Feeling a little lonely on this post, normally, people who talk to themselves are sectioned, so I'm getting a little worried now?!

Can someone move this to Networking please?  See if I can attract more assistance there?

---

### Post by Konstantin_Yakovle on 2014-04-23
@robert-woodward

Hello, I have the same problems
Which started right after i performed do-release-upgrade
Same ipsec behavior, same xl2tpd silence after all.
This message is not very helpful, just to warn you not lonely with this problem )

---

### Post by robert-woodward on 2014-04-23
Thanks for the reply @Konstantin_Yakovle, I thought I was going to have to call the men in white coats myself for a bit!

Since my last update however, things have got slightly worse, in that I upgraded from 13:10 to 14:04 yesterday (thinking I might get further with the VPN, and get the latest ssl updates for security purposes).......and instead, my external networking has stopped working?!  eth1 has an ip Address from my ISP, but I cannot ping anything at all?!  I've tried various permutations of web addresses and ip addresses including the favourites of [www.google.co.uk](www.google.co.uk), and 8.8.4.4 all of which come back with "Destination host unreachable" 100% packet loss.

Oddly, all internal networking seems to be fine?!  So, after a discussion with an IT techy mate of mine I'm going to follow that good old IT approach of "Switch it off and back on", but this time on the ISP's modem, not the server, which I rebooted several times yesterday post upgrade in frustration, as well as restarting the networking countless times (Once I'd figured out that "service networking <start/stop/restart>" has been depreciated, and we now have to use ifup / ifdown of course!!).  Unfortunately, as the server is my gateway, so, searching for answers to sort this out has been difficult to say the least!!  Will also be trying a greatly cut down iptables rule set to make sure nothing's gone wrong with them either!

Hopefully, and of course assuming I will not be subject to a miracle of some sorts, I'll be back to square 1 with the VPN soon, beating my head off the desk trying to figure out why nothing responds!!

---

### Post by Konstantin_Yakovle on 2014-04-26
Good day @robert-woodward
I solved my problem a few minutes ago,
thanks to this post [https://lists.openswan.org/pipermail/users/2013-July/022546.html](https://lists.openswan.org/pipermail/users/2013-July/022546.html)
Especially to this part of message:
**"I also make it my habit to make leftprotoport 17/%any instead of 17/1701"**

After i changed leftprotoport from 17/1701 to 17/%any in ipsec.conf and restarted ipsec service - everything got back to normal and vpn started working properly.
I hope this would solve your issue too.

---

### Post by robert-woodward on 2014-05-02
Thanks for all your help @Konstantin_Yakovle, worked a treat, VPN now connecting!!  I'll mark this thread as Solved.

---

### Post by Ewald_Jurgens on 2014-09-23
Amazing, works like a charm. I could connect my android device without any problems with 17/1701 but not with my iphone, works great now. Anyone able to explain why this would fix it specificly for an iphone?

---

### Post by alexvancasper on 2015-04-18
Hello everyone,
Thanks for this solve, very helpful for me. 
I have one question, what does it mean value 17/1701 and 17/%any?

> **Konstantin_Yakovle said:**
> 
After i changed leftprotoport from 17/1701 to 17/%any in ipsec.conf and restarted ipsec service - everything got back to normal and vpn started working properly.


Thanks!

---

