---
title: "Openswan, XL2TP and PPP for Android"
date: 2013-11-04
forum: Server Platforms
---

### Post by jopare on 2013-11-04
Hi I have a problem setting a VPN connection on my Ubuntu Server 12.04 for my android 4.2.2 smartphone (Galaxy S3)

I'm not able to connect, on 4G network or on local network

I have forwarded UPD-500 and UDP-4500 to my ubuntu server on my router.

I'm getting this error in my auth.log:
"L2TP-PSK-NAT"[8] 184.151.114.97 #33: ERROR: asynchronous network error report on eth0 (sport=500) for message to 184.151.114.97 port 56486, complainant 184.151.114.97: Connection refused [errno 111, origin ICMP type 3 code 3 (not authenticated)]


Here are all the steps I took to set this up

```

sudo apt-get install openswan ppp xl2tpd[COLOR=#000000]
[/COLOR]
```


ifconfig -a
---------------------------
```

eth0      Link encap:Ethernet  HWaddr 00:22:15:d4:bf:91
          inet addr:192.168.1.99  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:15ff:fed4:bf91/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2729630 errors:274 dropped:0 overruns:274 frame:0
          TX packets:1566480 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3936087581 (3.9 GB)  TX bytes:113251319 (113.2 MB)
          Interrupt:47 Base address:0xa000


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1560 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1560 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:183496 (183.4 KB)  TX bytes:183496 (183.4 KB)

```






sudo ufw status
---------------------------
```

500/udp                    ALLOW       Anywhere
4500/udp                   ALLOW       Anywhere
1701/tcp                   ALLOW       Anywhere
500/udp                    ALLOW       Anywhere (v6)
4500/udp                   ALLOW       Anywhere (v6)
1701/tcp                   ALLOW       Anywhere (v6)

```


```

sudo iptables --table nat --append POSTROUTING --jump MASQUERADE

```




sudo nano /etc/rc.local
---------------------------
```

iptables -A FORWARD -m state --state RELATED,ESTABLISHED -j ACCEPT
iptables -A FORWARD -s 192.168.1.100-192.168.1.110 -j ACCEPT
iptables -A FORWARD -j REJECT
iptables -t nat -A POSTROUTING -s 192.168.1.100-192.169.1.110 -o eth0 -j MASQUERADE
echo 1 > /proc/sys/net/ipv4/ip_forward
for each in /proc/sys/net/ipv4/conf/*
do
    echo 0 > $each/accept_redirects
    echo 0 > $each/send_redirects
done
/etc/init.d/ipsec restart


exit 0

```


```

sudo su
for f in /proc/sys/net/ipv4/conf/*/send_redirects; do echo 0 > $f; done
for f in /proc/sys/net/ipv4/conf/*/accept_redirects; do echo 0 > $f; done

```


/etc/ipsec.conf
---------------------------
```

version 2.0


config setup
  nat_traversal=yes
  virtual_private=%v4:10.0.0.0/8,%v4:192.168.1.0/16,%v4:172.16.0.0/12
  oe=off
  protostack=netkey
  nhelpers=0
  plutodebug=all


include /etc/ipsec.d/l2tp-psk.conf

```




/etc/ipsec.d/l2tp-psk.conf
---------------------------
```

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
  left=192.168.1.99
  leftnexthop=192.168.1.1
  leftprotoport=17/1701
  right=%any
  rightprotoport=17/%any
  dpddelay=15
  dpdtimeout=30
  dpdaction=clear
  dpdtimeout=30
  dpdaction=clear
  aggrmode=yes

```




/etc/xl2tpd/xl2tpd.conf
---------------------------
```

[global]
ipsec saref = yes
[lns default]
ip range = 192.168.1.101-192.168.1.110
local ip = 192.168.1.100
refuse chap = yes
refuse pap = yes
require authentication = yes
ppp debug = yes
pppoptfile = /etc/ppp/options.xl2tpd
length bit = yes

```




/etc/ppp/options.xl2tpd
---------------------------
```

equire-mschap-v2
ms-dns 8.8.8.8
ms-dns 8.8.4.4
ms-dns 192.168.1.1
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


/etc/ppp/chap-secrets
---------------------------
```

# Secrets for authentication using CHAP
# client        server  secret                  IP addresses
vpnuser  l2tpd  password  192.168.1.100
l2tpd vpnuser   password  192.168.1.100

```


/etc/ipsec.secrets
---------------------------
```

192.168.1.99   %any:  PSK "password"

```




```

sudo /etc/init.d/pppd-dns restart
sudo /etc/init.d/xl2tpd restart
sudo /etc/init.d/ipsec restart

```




sudo ipsec verify
---------------------------
```

Checking your system to see if IPsec got installed and started correctly:
Version check and ipsec on-path                                 [OK]
Linux Openswan U2.6.37/K3.2.0-37-generic (netkey)
Checking for IPsec support in kernel                            [OK]
 SAref kernel support                                           [N/A]
 NETKEY:  Testing XFRM related proc values                      [OK]
        [OK]
        [OK]
Checking that pluto is running                                  [OK]
 Pluto listening for IKE on udp 500                             [OK]
 Pluto listening for NAT-T on udp 4500                          [OK]
Checking for 'ip' command                                       [OK]
Checking /bin/sh is not /bin/dash                               [WARNING]
Checking for 'iptables' command                                 [OK]
Opportunistic Encryption Support                                [DISABLED]

```


tail -f /var/log/auth.log
---------------------------
```

Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |  
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | *received 611 bytes from 184.151.114.97:56486 on eth0 (port=500)
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |   fb 77 ff 6d  92 f7 d1 2a  00 00 00 00  00 00 00 00
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |   01 10 04 00  00 00 00 00  00 00 02 63  04 00 01 24
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |   00 00 00 01  00 00 00 01  00 00 01 18  01 01 00 08
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |   03 00 00 24  01 01 00 00  80 0b 00 01  80 0c 70 80
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |   80 01 00 07  80 0e 01 00  80 03 00 01  80 02 00 02
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |   80 04 00 02  03 00 00 24  02 01 00 00  80 0b 00 01
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |   80 0c 70 80  80 01 00 07  80 0e 01 00  80 03 00 01
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |   80 02 00 01  80 04 00 02  03 00 00 24  03 01 00 00
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |   80 0b 00 01  80 0c 70 80  80 01 00 07  80 0e 00 80
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |   80 03 00 01  80 02 00 02  80 04 00 02  03 00 00 24
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |   04 01 00 00  80 0b 00 01  80 0c 70 80  80 01 00 07
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |   80 0e 00 80  80 03 00 01  80 02 00 01  80 04 00 02
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |   03 00 00 20  05 01 00 00  80 0b 00 01  80 0c 70 80
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |   80 01 00 05  80 03 00 01  80 02 00 02  80 04 00 02
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |   03 00 00 20  06 01 00 00  80 0b 00 01  80 0c 70 80
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |   80 01 00 05  80 03 00 01  80 02 00 01  80 04 00 02
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |   03 00 00 20  07 01 00 00  80 0b 00 01  80 0c 70 80
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |   80 01 00 01  80 03 00 01  80 02 00 02  80 04 00 02
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |   00 00 00 20  08 01 00 00  80 0b 00 01  80 0c 70 80
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |   80 01 00 01  80 03 00 01  80 02 00 01  80 04 00 02
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |   0a 00 00 84  d0 3e 9d e5  93 5b f6 ed  02 8d ce fa
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |   25 be a4 08  ff d4 92 ab  15 d3 11 87  62 a0 30 82
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |   14 29 0c dd  56 ea a3 44  af 8b b0 62  8a 8b 4b 66
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |   21 64 94 cf  66 63 9d c4  78 ea 2e a7  47 6f 73 80
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |   e4 4a 37 02  9a f0 bf 36  17 26 7f 03  e3 7c b9 eb
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |   f8 2f f5 8a  be da 6f 33  d3 e9 df 12  24 1b 5a 1c
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |   00 37 a1 f9  97 7f 2a e1  71 32 f6 9c  9b 2e 0e 8d
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |   38 b9 6c af  bd 62 5c ed  b7 8d 71 ca  47 c3 b8 84
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |   b4 0d ce 54  05 00 00 14  95 bd fe b5  ca e9 80 30
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |   07 ef 11 46  26 f1 54 7b  0d 00 00 0f  0b 00 00 00
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |   76 70 6e 75  73 65 72 0d  00 00 18 40  48 b7 d5 6e
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |   bc e8 85 25  e7 de 7f 00  d6 c2 d3 80  00 00 00 0d
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |   00 00 14 4a  13 1c 81 07  03 58 45 5c  57 28 f2 0e
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |   95 45 2f 0d  00 00 14 cd  60 46 43 35  df 21 f8 7c
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |   fd b2 fc 68  b6 a4 48 0d  00 00 14 90  cb 80 91 3e
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |   bb 69 6e 08  63 81 b5 ec  42 7b 1f 0d  00 00 14 44
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |   85 15 2d 18  b6 bb cd 0b  e8 a8 46 95  79 dd cc 00
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |   00 00 14 af  ca d7 13 68  a1 f1 c9 6b  86 96 fc 77
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |   57 01 00
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | **parse ISAKMP Message:
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    initiator cookie:
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |   fb 77 ff 6d  92 f7 d1 2a
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    responder cookie:
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |   00 00 00 00  00 00 00 00
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_SA
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    ISAKMP version: ISAKMP Version 1.0 (rfc2407)
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    exchange type: ISAKMP_XCHG_AGGR
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    flags: none
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    message ID:  00 00 00 00
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    length: 611
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |  processing version=1.0 packet with exchange type=ISAKMP_XCHG_AGGR (4)
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | got payload 0x2(ISAKMP_NEXT_SA) needed: 0x432 opt: 0x102000
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Security Association Payload:
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_KE
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    length: 292
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    DOI: ISAKMP_DOI_IPSEC
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | got payload 0x10(ISAKMP_NEXT_KE) needed: 0x430 opt: 0x102000
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Key Exchange Payload:
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_NONCE
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    length: 132
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | got payload 0x400(ISAKMP_NEXT_NONCE) needed: 0x420 opt: 0x102000
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Nonce Payload:
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_ID
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    length: 20
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | got payload 0x20(ISAKMP_NEXT_ID) needed: 0x20 opt: 0x102000
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Identification Payload:
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_VID
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    length: 15
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    ID type: ID_KEY_ID
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    DOI specific A: 0
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    DOI specific B: 0
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |      obj:   76 70 6e 75  73 65 72
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | got payload 0x2000(ISAKMP_NEXT_VID) needed: 0x0 opt: 0x102000
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Vendor ID Payload:
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_VID
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    length: 24
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | got payload 0x2000(ISAKMP_NEXT_VID) needed: 0x0 opt: 0x102000
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Vendor ID Payload:
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_VID
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    length: 20
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | got payload 0x2000(ISAKMP_NEXT_VID) needed: 0x0 opt: 0x102000
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Vendor ID Payload:
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_VID
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    length: 20
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | got payload 0x2000(ISAKMP_NEXT_VID) needed: 0x0 opt: 0x102000
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Vendor ID Payload:
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_VID
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    length: 20
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | got payload 0x2000(ISAKMP_NEXT_VID) needed: 0x0 opt: 0x102000
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Vendor ID Payload:
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_VID
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    length: 20
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | got payload 0x2000(ISAKMP_NEXT_VID) needed: 0x0 opt: 0x102000
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Vendor ID Payload:
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_NONE
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    length: 20
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: packet from 184.151.114.97:56486: ignoring Vendor ID payload [FRAGMENTATION 80000000]
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: packet from 184.151.114.97:56486: received Vendor ID payload [RFC 3947] method set to=109 
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: packet from 184.151.114.97:56486: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02] meth=107, but already using method 109
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: packet from 184.151.114.97:56486: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02_n] meth=106, but already using method 109
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: packet from 184.151.114.97:56486: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-00]
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: packet from 184.151.114.97:56486: received Vendor ID payload [Dead Peer Detection]
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | find_host_connection2 called from aggr_inI1_outR1_common, me=192.168.1.99:500 him=184.151.114.97:56486 policy=none
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | find_host_pair: comparing to 192.168.1.99:500 0.0.0.0:500 
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | find_host_pair_conn (find_host_connection2): 192.168.1.99:500 184.151.114.97:56486 -> hp:none 
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | find_host_connection2 returns empty
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | ****parse IPsec DOI SIT:
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    IPsec DOI SIT: SIT_IDENTITY_ONLY
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | ****parse ISAKMP Proposal Payload:
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_NONE
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    length: 280
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    proposal number: 1
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    protocol ID: PROTO_ISAKMP
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    SPI size: 0
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    number of transforms: 8
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | *****parse ISAKMP Transform Payload (ISAKMP):
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_T
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    length: 36
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    transform number: 1
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    transform ID: KEY_IKE
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_LIFE_TYPE
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    length/value: 1
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_LIFE_DURATION
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    length/value: 28800
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_ENCRYPTION_ALGORITHM
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    length/value: 7
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_KEY_LENGTH
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    length/value: 256
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_AUTHENTICATION_METHOD
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    length/value: 1
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_HASH_ALGORITHM
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    length/value: 2
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_GROUP_DESCRIPTION
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    length/value: 2
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | *****parse ISAKMP Transform Payload (ISAKMP):
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_T
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    length: 36
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    transform number: 2
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    transform ID: KEY_IKE
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_LIFE_TYPE
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    length/value: 1
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_LIFE_DURATION
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    length/value: 28800
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_ENCRYPTION_ALGORITHM
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    length/value: 7
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_KEY_LENGTH
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    length/value: 256
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_AUTHENTICATION_METHOD
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    length/value: 1
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_HASH_ALGORITHM
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    length/value: 1
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_GROUP_DESCRIPTION
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    length/value: 2
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | *****parse ISAKMP Transform Payload (ISAKMP):
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_T
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    length: 36
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    transform number: 3
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    transform ID: KEY_IKE
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_LIFE_TYPE
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    length/value: 1
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_LIFE_DURATION
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    length/value: 28800
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_ENCRYPTION_ALGORITHM
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    length/value: 7
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_KEY_LENGTH
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    length/value: 128
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_AUTHENTICATION_METHOD
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    length/value: 1
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_HASH_ALGORITHM
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    length/value: 2
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_GROUP_DESCRIPTION
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    length/value: 2
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: | *****parse ISAKMP Transform Payload (ISAKMP):
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_T
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    length: 36
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    transform number: 4
Nov  4 19:52:47 h0m3s3rv3r pluto[8344]: |    transform ID: KEY_IKE
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |  
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | next event EVENT_PENDING_DDNS in 0 seconds
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | *time to handle event
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | handling event EVENT_PENDING_DDNS
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | event after this is EVENT_RETRANSMIT in 4 seconds
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | inserting event EVENT_PENDING_DDNS, timeout in 60 seconds
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | event added after event EVENT_RETRANSMIT for #32
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | next event EVENT_RETRANSMIT in 4 seconds for #31
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |  
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | *received 611 bytes from 184.151.114.97:56486 on eth0 (port=500)
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |   fb 77 ff 6d  92 f7 d1 2a  00 00 00 00  00 00 00 00
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |   01 10 04 00  00 00 00 00  00 00 02 63  04 00 01 24
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |   00 00 00 01  00 00 00 01  00 00 01 18  01 01 00 08
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |   03 00 00 24  01 01 00 00  80 0b 00 01  80 0c 70 80
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |   80 01 00 07  80 0e 01 00  80 03 00 01  80 02 00 02
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |   80 04 00 02  03 00 00 24  02 01 00 00  80 0b 00 01
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |   80 0c 70 80  80 01 00 07  80 0e 01 00  80 03 00 01
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |   80 02 00 01  80 04 00 02  03 00 00 24  03 01 00 00
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |   80 0b 00 01  80 0c 70 80  80 01 00 07  80 0e 00 80
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |   80 03 00 01  80 02 00 02  80 04 00 02  03 00 00 24
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |   04 01 00 00  80 0b 00 01  80 0c 70 80  80 01 00 07
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |   80 0e 00 80  80 03 00 01  80 02 00 01  80 04 00 02
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |   03 00 00 20  05 01 00 00  80 0b 00 01  80 0c 70 80
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |   80 01 00 05  80 03 00 01  80 02 00 02  80 04 00 02
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |   03 00 00 20  06 01 00 00  80 0b 00 01  80 0c 70 80
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |   80 01 00 05  80 03 00 01  80 02 00 01  80 04 00 02
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |   03 00 00 20  07 01 00 00  80 0b 00 01  80 0c 70 80
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |   80 01 00 01  80 03 00 01  80 02 00 02  80 04 00 02
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |   00 00 00 20  08 01 00 00  80 0b 00 01  80 0c 70 80
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |   80 01 00 01  80 03 00 01  80 02 00 01  80 04 00 02
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |   0a 00 00 84  d0 3e 9d e5  93 5b f6 ed  02 8d ce fa
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |   25 be a4 08  ff d4 92 ab  15 d3 11 87  62 a0 30 82
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |   14 29 0c dd  56 ea a3 44  af 8b b0 62  8a 8b 4b 66
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |   21 64 94 cf  66 63 9d c4  78 ea 2e a7  47 6f 73 80
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |   e4 4a 37 02  9a f0 bf 36  17 26 7f 03  e3 7c b9 eb
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |   f8 2f f5 8a  be da 6f 33  d3 e9 df 12  24 1b 5a 1c
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |   00 37 a1 f9  97 7f 2a e1  71 32 f6 9c  9b 2e 0e 8d
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |   38 b9 6c af  bd 62 5c ed  b7 8d 71 ca  47 c3 b8 84
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |   b4 0d ce 54  05 00 00 14  95 bd fe b5  ca e9 80 30
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |   07 ef 11 46  26 f1 54 7b  0d 00 00 0f  0b 00 00 00
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |   76 70 6e 75  73 65 72 0d  00 00 18 40  48 b7 d5 6e
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |   bc e8 85 25  e7 de 7f 00  d6 c2 d3 80  00 00 00 0d
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |   00 00 14 4a  13 1c 81 07  03 58 45 5c  57 28 f2 0e
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |   95 45 2f 0d  00 00 14 cd  60 46 43 35  df 21 f8 7c
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |   fd b2 fc 68  b6 a4 48 0d  00 00 14 90  cb 80 91 3e
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |   bb 69 6e 08  63 81 b5 ec  42 7b 1f 0d  00 00 14 44
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |   85 15 2d 18  b6 bb cd 0b  e8 a8 46 95  79 dd cc 00
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |   00 00 14 af  ca d7 13 68  a1 f1 c9 6b  86 96 fc 77
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |   57 01 00
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | **parse ISAKMP Message:
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    initiator cookie:
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |   fb 77 ff 6d  92 f7 d1 2a
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    responder cookie:
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |   00 00 00 00  00 00 00 00
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_SA
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    ISAKMP version: ISAKMP Version 1.0 (rfc2407)
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    exchange type: ISAKMP_XCHG_AGGR
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    flags: none
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    message ID:  00 00 00 00
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    length: 611
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |  processing version=1.0 packet with exchange type=ISAKMP_XCHG_AGGR (4)
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | got payload 0x2(ISAKMP_NEXT_SA) needed: 0x432 opt: 0x102000
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Security Association Payload:
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_KE
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    length: 292
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    DOI: ISAKMP_DOI_IPSEC
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | got payload 0x10(ISAKMP_NEXT_KE) needed: 0x430 opt: 0x102000
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Key Exchange Payload:
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_NONCE
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    length: 132
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | got payload 0x400(ISAKMP_NEXT_NONCE) needed: 0x420 opt: 0x102000
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Nonce Payload:
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_ID
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    length: 20
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | got payload 0x20(ISAKMP_NEXT_ID) needed: 0x20 opt: 0x102000
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Identification Payload:
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_VID
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    length: 15
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    ID type: ID_KEY_ID
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    DOI specific A: 0
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    DOI specific B: 0
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |      obj:   76 70 6e 75  73 65 72
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | got payload 0x2000(ISAKMP_NEXT_VID) needed: 0x0 opt: 0x102000
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Vendor ID Payload:
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_VID
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    length: 24
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | got payload 0x2000(ISAKMP_NEXT_VID) needed: 0x0 opt: 0x102000
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Vendor ID Payload:
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_VID
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    length: 20
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | got payload 0x2000(ISAKMP_NEXT_VID) needed: 0x0 opt: 0x102000
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Vendor ID Payload:
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_VID
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    length: 20
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | got payload 0x2000(ISAKMP_NEXT_VID) needed: 0x0 opt: 0x102000
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Vendor ID Payload:
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_VID
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    length: 20
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | got payload 0x2000(ISAKMP_NEXT_VID) needed: 0x0 opt: 0x102000
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Vendor ID Payload:
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_VID
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    length: 20
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | got payload 0x2000(ISAKMP_NEXT_VID) needed: 0x0 opt: 0x102000
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Vendor ID Payload:
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_NONE
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    length: 20
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: packet from 184.151.114.97:56486: ignoring Vendor ID payload [FRAGMENTATION 80000000]
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: packet from 184.151.114.97:56486: received Vendor ID payload [RFC 3947] method set to=109 
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: packet from 184.151.114.97:56486: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02] meth=107, but already using method 109
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: packet from 184.151.114.97:56486: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02_n] meth=106, but already using method 109
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: packet from 184.151.114.97:56486: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-00]
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: packet from 184.151.114.97:56486: received Vendor ID payload [Dead Peer Detection]
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | find_host_connection2 called from aggr_inI1_outR1_common, me=192.168.1.99:500 him=184.151.114.97:56486 policy=none
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | find_host_pair: comparing to 192.168.1.99:500 184.151.114.97:500 
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | find_host_pair_conn (find_host_connection2): 192.168.1.99:500 184.151.114.97:56486 -> hp:L2TP-PSK-NAT 
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | find_host_connection2 returns L2TP-PSK-NAT
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | creating state object #33 at 0x1500dd0
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | KEY ID:  76 70 6e 75  73 65 72
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: "L2TP-PSK-NAT"[8] 184.151.114.97 #33: Aggressive mode peer ID is ID_KEY_ID: '@#0x76706e75736572'
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | refine_connection: starting with L2TP-PSK-NAT
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | started looking for secret for 192.168.1.99->@#0x76706e75736572 of kind PPK_PSK
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | actually looking for secret for 192.168.1.99->@#0x76706e75736572 of kind PPK_PSK
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | line 1: key type PPK_PSK(192.168.1.99) to type PPK_PSK 
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | 1: compared key %any to 192.168.1.99 / @#0x76706e75736572 -> 2
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | 2: compared key 192.168.1.99 to 192.168.1.99 / @#0x76706e75736572 -> 10
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | line 1: match=10 
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | best_match 0>10 best=0x14fb0c0 (line=1)
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | concluding with best_match=10 best=0x14fb0c0 (lineno=1)
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    match_id a=@#0x76706e75736572
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |             b=@#0x76706e75736572
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    results  matched
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |   trusted_ca called with a=(empty) b=(empty)
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | refine_connection: checking L2TP-PSK-NAT against L2TP-PSK-NAT, best=(none) with match=1(id=1/ca=1/reqca=1)
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | refine_connection: checked L2TP-PSK-NAT against L2TP-PSK-NAT, now for see if best
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | started looking for secret for 192.168.1.99->@#0x76706e75736572 of kind PPK_PSK
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | actually looking for secret for 192.168.1.99->@#0x76706e75736572 of kind PPK_PSK
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | line 1: key type PPK_PSK(192.168.1.99) to type PPK_PSK 
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | 1: compared key %any to 192.168.1.99 / @#0x76706e75736572 -> 2
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | 2: compared key 192.168.1.99 to 192.168.1.99 / @#0x76706e75736572 -> 10
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | line 1: match=10 
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | best_match 0>10 best=0x14fb0c0 (line=1)
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | concluding with best_match=10 best=0x14fb0c0 (lineno=1)
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | offered CA: '%none'
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | processing connection L2TP-PSK-NAT[8] 184.151.114.97
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | ICOOKIE:  fb 77 ff 6d  92 f7 d1 2a
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | RCOOKIE:  83 ec d4 28  62 8d 08 01
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | state hash entry 9
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | inserting state object #33 on chain 9
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | inserting event EVENT_SO_DISCARD, timeout in 0 seconds for #33
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | event added at head of queue
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: "L2TP-PSK-NAT"[8] 184.151.114.97 #33: responding to Aggressive Mode, state #33, connection "L2TP-PSK-NAT" from 184.151.114.97
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | sender checking NAT-t: 1 and 109
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: "L2TP-PSK-NAT"[8] 184.151.114.97 #33: enabling possible NAT-traversal with method 4
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | ****parse IPsec DOI SIT:
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    IPsec DOI SIT: SIT_IDENTITY_ONLY
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | ****parse ISAKMP Proposal Payload:
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_NONE
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    length: 280
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    proposal number: 1
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    protocol ID: PROTO_ISAKMP
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    SPI size: 0
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    number of transforms: 8
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | *****parse ISAKMP Transform Payload (ISAKMP):
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_T
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    length: 36
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    transform number: 1
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    transform ID: KEY_IKE
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_LIFE_TYPE
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    length/value: 1
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    [1 is OAKLEY_LIFE_SECONDS]
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_LIFE_DURATION
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    length/value: 28800
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_ENCRYPTION_ALGORITHM
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    length/value: 7
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    [7 is OAKLEY_AES_CBC]
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | ike_alg_enc_ok(ealg=7,key_len=0): blocksize=16, keyminlen=128, keydeflen=128, keymaxlen=256, ret=1
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_KEY_LENGTH
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    length/value: 256
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | ike_alg_enc_ok(ealg=7,key_len=256): blocksize=16, keyminlen=128, keydeflen=128, keymaxlen=256, ret=1
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_AUTHENTICATION_METHOD
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    length/value: 1
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    [1 is OAKLEY_PRESHARED_KEY]
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | started looking for secret for 192.168.1.99->@#0x76706e75736572 of kind PPK_PSK
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | actually looking for secret for 192.168.1.99->@#0x76706e75736572 of kind PPK_PSK
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | line 1: key type PPK_PSK(192.168.1.99) to type PPK_PSK 
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | 1: compared key %any to 192.168.1.99 / @#0x76706e75736572 -> 2
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | 2: compared key 192.168.1.99 to 192.168.1.99 / @#0x76706e75736572 -> 10
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | line 1: match=10 
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | best_match 0>10 best=0x14fb0c0 (line=1)
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | concluding with best_match=10 best=0x14fb0c0 (lineno=1)
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_HASH_ALGORITHM
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    length/value: 2
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: |    [2 is OAKLEY_SHA1]
Nov  4 19:52:53 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |  
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | *received 611 bytes from 184.151.114.97:56486 on eth0 (port=500)
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   fb 77 ff 6d  92 f7 d1 2a  00 00 00 00  00 00 00 00
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   01 10 04 00  00 00 00 00  00 00 02 63  04 00 01 24
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   00 00 00 01  00 00 00 01  00 00 01 18  01 01 00 08
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   03 00 00 24  01 01 00 00  80 0b 00 01  80 0c 70 80
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   80 01 00 07  80 0e 01 00  80 03 00 01  80 02 00 02
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   80 04 00 02  03 00 00 24  02 01 00 00  80 0b 00 01
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   80 0c 70 80  80 01 00 07  80 0e 01 00  80 03 00 01
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   80 02 00 01  80 04 00 02  03 00 00 24  03 01 00 00
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   80 0b 00 01  80 0c 70 80  80 01 00 07  80 0e 00 80
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   80 03 00 01  80 02 00 02  80 04 00 02  03 00 00 24
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   04 01 00 00  80 0b 00 01  80 0c 70 80  80 01 00 07
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   80 0e 00 80  80 03 00 01  80 02 00 01  80 04 00 02
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   03 00 00 20  05 01 00 00  80 0b 00 01  80 0c 70 80
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   80 01 00 05  80 03 00 01  80 02 00 02  80 04 00 02
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   03 00 00 20  06 01 00 00  80 0b 00 01  80 0c 70 80
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   80 01 00 05  80 03 00 01  80 02 00 01  80 04 00 02
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   03 00 00 20  07 01 00 00  80 0b 00 01  80 0c 70 80
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   80 01 00 01  80 03 00 01  80 02 00 02  80 04 00 02
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   00 00 00 20  08 01 00 00  80 0b 00 01  80 0c 70 80
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   80 01 00 01  80 03 00 01  80 02 00 01  80 04 00 02
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   0a 00 00 84  d0 3e 9d e5  93 5b f6 ed  02 8d ce fa
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   25 be a4 08  ff d4 92 ab  15 d3 11 87  62 a0 30 82
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   14 29 0c dd  56 ea a3 44  af 8b b0 62  8a 8b 4b 66
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   21 64 94 cf  66 63 9d c4  78 ea 2e a7  47 6f 73 80
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   e4 4a 37 02  9a f0 bf 36  17 26 7f 03  e3 7c b9 eb
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   f8 2f f5 8a  be da 6f 33  d3 e9 df 12  24 1b 5a 1c
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   00 37 a1 f9  97 7f 2a e1  71 32 f6 9c  9b 2e 0e 8d
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   38 b9 6c af  bd 62 5c ed  b7 8d 71 ca  47 c3 b8 84
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   b4 0d ce 54  05 00 00 14  95 bd fe b5  ca e9 80 30
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   07 ef 11 46  26 f1 54 7b  0d 00 00 0f  0b 00 00 00
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   76 70 6e 75  73 65 72 0d  00 00 18 40  48 b7 d5 6e
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   bc e8 85 25  e7 de 7f 00  d6 c2 d3 80  00 00 00 0d
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   00 00 14 4a  13 1c 81 07  03 58 45 5c  57 28 f2 0e
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   95 45 2f 0d  00 00 14 cd  60 46 43 35  df 21 f8 7c
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   fd b2 fc 68  b6 a4 48 0d  00 00 14 90  cb 80 91 3e
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   bb 69 6e 08  63 81 b5 ec  42 7b 1f 0d  00 00 14 44
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   85 15 2d 18  b6 bb cd 0b  e8 a8 46 95  79 dd cc 00
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   00 00 14 af  ca d7 13 68  a1 f1 c9 6b  86 96 fc 77
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   57 01 00
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | **parse ISAKMP Message:
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    initiator cookie:
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   fb 77 ff 6d  92 f7 d1 2a
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    responder cookie:
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   00 00 00 00  00 00 00 00
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_SA
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    ISAKMP version: ISAKMP Version 1.0 (rfc2407)
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    exchange type: ISAKMP_XCHG_AGGR
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    flags: none
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    message ID:  00 00 00 00
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    length: 611
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |  processing version=1.0 packet with exchange type=ISAKMP_XCHG_AGGR (4)
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | got payload 0x2(ISAKMP_NEXT_SA) needed: 0x432 opt: 0x102000
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Security Association Payload:
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_KE
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    length: 292
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    DOI: ISAKMP_DOI_IPSEC
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | got payload 0x10(ISAKMP_NEXT_KE) needed: 0x430 opt: 0x102000
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Key Exchange Payload:
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_NONCE
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    length: 132
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | got payload 0x400(ISAKMP_NEXT_NONCE) needed: 0x420 opt: 0x102000
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Nonce Payload:
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_ID
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    length: 20
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | got payload 0x20(ISAKMP_NEXT_ID) needed: 0x20 opt: 0x102000
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Identification Payload:
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_VID
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    length: 15
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    ID type: ID_KEY_ID
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    DOI specific A: 0
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    DOI specific B: 0
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |      obj:   76 70 6e 75  73 65 72
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | got payload 0x2000(ISAKMP_NEXT_VID) needed: 0x0 opt: 0x102000
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Vendor ID Payload:
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_VID
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    length: 24
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | got payload 0x2000(ISAKMP_NEXT_VID) needed: 0x0 opt: 0x102000
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Vendor ID Payload:
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_VID
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    length: 20
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | got payload 0x2000(ISAKMP_NEXT_VID) needed: 0x0 opt: 0x102000
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Vendor ID Payload:
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_VID
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    length: 20
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | got payload 0x2000(ISAKMP_NEXT_VID) needed: 0x0 opt: 0x102000
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Vendor ID Payload:
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_VID
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    length: 20
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | got payload 0x2000(ISAKMP_NEXT_VID) needed: 0x0 opt: 0x102000
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Vendor ID Payload:
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_VID
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    length: 20
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | got payload 0x2000(ISAKMP_NEXT_VID) needed: 0x0 opt: 0x102000
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Vendor ID Payload:
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_NONE
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    length: 20
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: packet from 184.151.114.97:56486: ignoring Vendor ID payload [FRAGMENTATION 80000000]
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: packet from 184.151.114.97:56486: received Vendor ID payload [RFC 3947] method set to=109 
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: packet from 184.151.114.97:56486: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02] meth=107, but already using method 109
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: packet from 184.151.114.97:56486: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02_n] meth=106, but already using method 109
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: packet from 184.151.114.97:56486: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-00]
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: packet from 184.151.114.97:56486: received Vendor ID payload [Dead Peer Detection]
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | find_host_connection2 called from aggr_inI1_outR1_common, me=192.168.1.99:500 him=184.151.114.97:56486 policy=none
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | find_host_pair: comparing to 192.168.1.99:500 184.151.114.97:500 
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | find_host_pair_conn (find_host_connection2): 192.168.1.99:500 184.151.114.97:56486 -> hp:L2TP-PSK-NAT 
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | find_host_connection2 returns L2TP-PSK-NAT
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | creating state object #35 at 0x1502d90
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | KEY ID:  76 70 6e 75  73 65 72
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: "L2TP-PSK-NAT"[8] 184.151.114.97 #35: Aggressive mode peer ID is ID_KEY_ID: '@#0x76706e75736572'
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | refine_connection: starting with L2TP-PSK-NAT
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | started looking for secret for 192.168.1.99->@#0x76706e75736572 of kind PPK_PSK
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | actually looking for secret for 192.168.1.99->@#0x76706e75736572 of kind PPK_PSK
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | line 1: key type PPK_PSK(192.168.1.99) to type PPK_PSK 
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | 1: compared key %any to 192.168.1.99 / @#0x76706e75736572 -> 2
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | 2: compared key 192.168.1.99 to 192.168.1.99 / @#0x76706e75736572 -> 10
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | line 1: match=10 
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | best_match 0>10 best=0x14fb0c0 (line=1)
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | concluding with best_match=10 best=0x14fb0c0 (lineno=1)
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    match_id a=@#0x76706e75736572
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |             b=@#0x76706e75736572
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    results  matched
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   trusted_ca called with a=(empty) b=(empty)
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | refine_connection: checking L2TP-PSK-NAT against L2TP-PSK-NAT, best=(none) with match=1(id=1/ca=1/reqca=1)
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | refine_connection: checked L2TP-PSK-NAT against L2TP-PSK-NAT, now for see if best
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | started looking for secret for 192.168.1.99->@#0x76706e75736572 of kind PPK_PSK
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | actually looking for secret for 192.168.1.99->@#0x76706e75736572 of kind PPK_PSK
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | line 1: key type PPK_PSK(192.168.1.99) to type PPK_PSK 
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | 1: compared key %any to 192.168.1.99 / @#0x76706e75736572 -> 2
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | 2: compared key 192.168.1.99 to 192.168.1.99 / @#0x76706e75736572 -> 10
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | line 1: match=10 
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | best_match 0>10 best=0x14fb0c0 (line=1)
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | concluding with best_match=10 best=0x14fb0c0 (lineno=1)
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | offered CA: '%none'
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | processing connection L2TP-PSK-NAT[8] 184.151.114.97
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | ICOOKIE:  fb 77 ff 6d  92 f7 d1 2a
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | RCOOKIE:  01 3d b5 a3  12 cf bb 32
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | state hash entry 6
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | inserting state object #35 on chain 6
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | inserting event EVENT_SO_DISCARD, timeout in 0 seconds for #35
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | event added at head of queue
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: "L2TP-PSK-NAT"[8] 184.151.114.97 #35: responding to Aggressive Mode, state #35, connection "L2TP-PSK-NAT" from 184.151.114.97
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | sender checking NAT-t: 1 and 109
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: "L2TP-PSK-NAT"[8] 184.151.114.97 #35: enabling possible NAT-traversal with method 4
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | ****parse IPsec DOI SIT:
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    IPsec DOI SIT: SIT_IDENTITY_ONLY
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | ****parse ISAKMP Proposal Payload:
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_NONE
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    length: 280
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    proposal number: 1
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    protocol ID: PROTO_ISAKMP
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    SPI size: 0
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    number of transforms: 8
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | *****parse ISAKMP Transform Payload (ISAKMP):
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_T
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    length: 36
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    transform number: 1
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    transform ID: KEY_IKE
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_LIFE_TYPE
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    length/value: 1
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    [1 is OAKLEY_LIFE_SECONDS]
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_LIFE_DURATION
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    length/value: 28800
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_ENCRYPTION_ALGORITHM
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    length/value: 7
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    [7 is OAKLEY_AES_CBC]
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | ike_alg_enc_ok(ealg=7,key_len=0): blocksize=16, keyminlen=128, keydeflen=128, keymaxlen=256, ret=1
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_KEY_LENGTH
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    length/value: 256
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | ike_alg_enc_ok(ealg=7,key_len=256): blocksize=16, keyminlen=128, keydeflen=128, keymaxlen=256, ret=1
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_AUTHENTICATION_METHOD
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    length/value: 1
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    [1 is OAKLEY_PRESHARED_KEY]
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | started looking for secret for 192.168.1.99->@#0x76706e75736572 of kind PPK_PSK
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | actually looking for secret for 192.168.1.99->@#0x76706e75736572 of kind PPK_PSK
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | line 1: key type PPK_PSK(192.168.1.99) to type PPK_PSK 
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | 1: compared key %any to 192.168.1.99 / @#0x76706e75736572 -> 2
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | 2: compared key 192.168.1.99 to 192.168.1.99 / @#0x76706e75736572 -> 10
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | line 1: match=10 
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | best_match 0>10 best=0x14fb0c0 (line=1)
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | concluding with best_match=10 best=0x14fb0c0 (lineno=1)
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_HASH_ALGORITHM
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    length/value: 2
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    [2 is OAKLEY_SHA1]
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_GROUP_DESCRIPTION
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    length/value: 2
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |    [2 is OAKLEY_GROUP_MODP1024]
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | Oakley Transform 1 accepted
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: | DH public value received:
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   d0 3e 9d e5  93 5b f6 ed  02 8d ce fa  25 be a4 08
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   ff d4 92 ab  15 d3 11 87  62 a0 30 82  14 29 0c dd
Nov  4 19:52:59 h0m3s3rv3r pluto[8344]: |   56 ea a3 44  af 8b b0 62  8a 8b 4b 66  21 64 94 cf
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |  
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | *received 611 bytes from 184.151.114.97:56486 on eth0 (port=500)
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   fb 77 ff 6d  92 f7 d1 2a  00 00 00 00  00 00 00 00
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   01 10 04 00  00 00 00 00  00 00 02 63  04 00 01 24
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   00 00 00 01  00 00 00 01  00 00 01 18  01 01 00 08
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   03 00 00 24  01 01 00 00  80 0b 00 01  80 0c 70 80
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   80 01 00 07  80 0e 01 00  80 03 00 01  80 02 00 02
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   80 04 00 02  03 00 00 24  02 01 00 00  80 0b 00 01
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   80 0c 70 80  80 01 00 07  80 0e 01 00  80 03 00 01
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   80 02 00 01  80 04 00 02  03 00 00 24  03 01 00 00
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   80 0b 00 01  80 0c 70 80  80 01 00 07  80 0e 00 80
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   80 03 00 01  80 02 00 02  80 04 00 02  03 00 00 24
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   04 01 00 00  80 0b 00 01  80 0c 70 80  80 01 00 07
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   80 0e 00 80  80 03 00 01  80 02 00 01  80 04 00 02
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   03 00 00 20  05 01 00 00  80 0b 00 01  80 0c 70 80
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   80 01 00 05  80 03 00 01  80 02 00 02  80 04 00 02
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   03 00 00 20  06 01 00 00  80 0b 00 01  80 0c 70 80
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   80 01 00 05  80 03 00 01  80 02 00 01  80 04 00 02
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   03 00 00 20  07 01 00 00  80 0b 00 01  80 0c 70 80
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   80 01 00 01  80 03 00 01  80 02 00 02  80 04 00 02
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   00 00 00 20  08 01 00 00  80 0b 00 01  80 0c 70 80
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   80 01 00 01  80 03 00 01  80 02 00 01  80 04 00 02
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   0a 00 00 84  d0 3e 9d e5  93 5b f6 ed  02 8d ce fa
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   25 be a4 08  ff d4 92 ab  15 d3 11 87  62 a0 30 82
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   14 29 0c dd  56 ea a3 44  af 8b b0 62  8a 8b 4b 66
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   21 64 94 cf  66 63 9d c4  78 ea 2e a7  47 6f 73 80
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   e4 4a 37 02  9a f0 bf 36  17 26 7f 03  e3 7c b9 eb
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   f8 2f f5 8a  be da 6f 33  d3 e9 df 12  24 1b 5a 1c
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   00 37 a1 f9  97 7f 2a e1  71 32 f6 9c  9b 2e 0e 8d
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   38 b9 6c af  bd 62 5c ed  b7 8d 71 ca  47 c3 b8 84
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   b4 0d ce 54  05 00 00 14  95 bd fe b5  ca e9 80 30
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   07 ef 11 46  26 f1 54 7b  0d 00 00 0f  0b 00 00 00
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   76 70 6e 75  73 65 72 0d  00 00 18 40  48 b7 d5 6e
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   bc e8 85 25  e7 de 7f 00  d6 c2 d3 80  00 00 00 0d
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   00 00 14 4a  13 1c 81 07  03 58 45 5c  57 28 f2 0e
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   95 45 2f 0d  00 00 14 cd  60 46 43 35  df 21 f8 7c
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   fd b2 fc 68  b6 a4 48 0d  00 00 14 90  cb 80 91 3e
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   bb 69 6e 08  63 81 b5 ec  42 7b 1f 0d  00 00 14 44
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   85 15 2d 18  b6 bb cd 0b  e8 a8 46 95  79 dd cc 00
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   00 00 14 af  ca d7 13 68  a1 f1 c9 6b  86 96 fc 77
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   57 01 00
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | **parse ISAKMP Message:
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    initiator cookie:
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   fb 77 ff 6d  92 f7 d1 2a
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    responder cookie:
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   00 00 00 00  00 00 00 00
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_SA
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    ISAKMP version: ISAKMP Version 1.0 (rfc2407)
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    exchange type: ISAKMP_XCHG_AGGR
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    flags: none
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    message ID:  00 00 00 00
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    length: 611
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |  processing version=1.0 packet with exchange type=ISAKMP_XCHG_AGGR (4)
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | got payload 0x2(ISAKMP_NEXT_SA) needed: 0x432 opt: 0x102000
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Security Association Payload:
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_KE
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    length: 292
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    DOI: ISAKMP_DOI_IPSEC
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | got payload 0x10(ISAKMP_NEXT_KE) needed: 0x430 opt: 0x102000
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Key Exchange Payload:
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_NONCE
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    length: 132
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | got payload 0x400(ISAKMP_NEXT_NONCE) needed: 0x420 opt: 0x102000
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Nonce Payload:
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_ID
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    length: 20
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | got payload 0x20(ISAKMP_NEXT_ID) needed: 0x20 opt: 0x102000
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Identification Payload:
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_VID
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    length: 15
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    ID type: ID_KEY_ID
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    DOI specific A: 0
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    DOI specific B: 0
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |      obj:   76 70 6e 75  73 65 72
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | got payload 0x2000(ISAKMP_NEXT_VID) needed: 0x0 opt: 0x102000
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Vendor ID Payload:
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_VID
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    length: 24
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | got payload 0x2000(ISAKMP_NEXT_VID) needed: 0x0 opt: 0x102000
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Vendor ID Payload:
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_VID
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    length: 20
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | got payload 0x2000(ISAKMP_NEXT_VID) needed: 0x0 opt: 0x102000
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Vendor ID Payload:
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_VID
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    length: 20
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | got payload 0x2000(ISAKMP_NEXT_VID) needed: 0x0 opt: 0x102000
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Vendor ID Payload:
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_VID
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    length: 20
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | got payload 0x2000(ISAKMP_NEXT_VID) needed: 0x0 opt: 0x102000
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Vendor ID Payload:
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_VID
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    length: 20
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | got payload 0x2000(ISAKMP_NEXT_VID) needed: 0x0 opt: 0x102000
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Vendor ID Payload:
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_NONE
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    length: 20
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: packet from 184.151.114.97:56486: ignoring Vendor ID payload [FRAGMENTATION 80000000]
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: packet from 184.151.114.97:56486: received Vendor ID payload [RFC 3947] method set to=109 
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: packet from 184.151.114.97:56486: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02] meth=107, but already using method 109
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: packet from 184.151.114.97:56486: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02_n] meth=106, but already using method 109
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: packet from 184.151.114.97:56486: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-00]
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: packet from 184.151.114.97:56486: received Vendor ID payload [Dead Peer Detection]
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | find_host_connection2 called from aggr_inI1_outR1_common, me=192.168.1.99:500 him=184.151.114.97:56486 policy=none
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | find_host_pair: comparing to 192.168.1.99:500 184.151.114.97:500 
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | find_host_pair_conn (find_host_connection2): 192.168.1.99:500 184.151.114.97:56486 -> hp:L2TP-PSK-NAT 
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | find_host_connection2 returns L2TP-PSK-NAT
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | creating state object #37 at 0x1504d50
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | KEY ID:  76 70 6e 75  73 65 72
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: "L2TP-PSK-NAT"[8] 184.151.114.97 #37: Aggressive mode peer ID is ID_KEY_ID: '@#0x76706e75736572'
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | refine_connection: starting with L2TP-PSK-NAT
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | started looking for secret for 192.168.1.99->@#0x76706e75736572 of kind PPK_PSK
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | actually looking for secret for 192.168.1.99->@#0x76706e75736572 of kind PPK_PSK
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | line 1: key type PPK_PSK(192.168.1.99) to type PPK_PSK 
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | 1: compared key %any to 192.168.1.99 / @#0x76706e75736572 -> 2
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | 2: compared key 192.168.1.99 to 192.168.1.99 / @#0x76706e75736572 -> 10
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | line 1: match=10 
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | best_match 0>10 best=0x14fb0c0 (line=1)
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | concluding with best_match=10 best=0x14fb0c0 (lineno=1)
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    match_id a=@#0x76706e75736572
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |             b=@#0x76706e75736572
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    results  matched
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   trusted_ca called with a=(empty) b=(empty)
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | refine_connection: checking L2TP-PSK-NAT against L2TP-PSK-NAT, best=(none) with match=1(id=1/ca=1/reqca=1)
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | refine_connection: checked L2TP-PSK-NAT against L2TP-PSK-NAT, now for see if best
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | started looking for secret for 192.168.1.99->@#0x76706e75736572 of kind PPK_PSK
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | actually looking for secret for 192.168.1.99->@#0x76706e75736572 of kind PPK_PSK
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | line 1: key type PPK_PSK(192.168.1.99) to type PPK_PSK 
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | 1: compared key %any to 192.168.1.99 / @#0x76706e75736572 -> 2
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | 2: compared key 192.168.1.99 to 192.168.1.99 / @#0x76706e75736572 -> 10
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | line 1: match=10 
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | best_match 0>10 best=0x14fb0c0 (line=1)
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | concluding with best_match=10 best=0x14fb0c0 (lineno=1)
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | offered CA: '%none'
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | processing connection L2TP-PSK-NAT[8] 184.151.114.97
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | ICOOKIE:  fb 77 ff 6d  92 f7 d1 2a
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | RCOOKIE:  dd 87 b3 2b  3b 0d 4c 4a
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | state hash entry 10
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | inserting state object #37 on chain 10
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | inserting event EVENT_SO_DISCARD, timeout in 0 seconds for #37
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | event added at head of queue
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: "L2TP-PSK-NAT"[8] 184.151.114.97 #37: responding to Aggressive Mode, state #37, connection "L2TP-PSK-NAT" from 184.151.114.97
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | sender checking NAT-t: 1 and 109
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: "L2TP-PSK-NAT"[8] 184.151.114.97 #37: enabling possible NAT-traversal with method 4
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | ****parse IPsec DOI SIT:
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    IPsec DOI SIT: SIT_IDENTITY_ONLY
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | ****parse ISAKMP Proposal Payload:
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_NONE
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    length: 280
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    proposal number: 1
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    protocol ID: PROTO_ISAKMP
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    SPI size: 0
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    number of transforms: 8
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | *****parse ISAKMP Transform Payload (ISAKMP):
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_T
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    length: 36
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    transform number: 1
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    transform ID: KEY_IKE
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_LIFE_TYPE
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    length/value: 1
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    [1 is OAKLEY_LIFE_SECONDS]
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_LIFE_DURATION
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    length/value: 28800
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_ENCRYPTION_ALGORITHM
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    length/value: 7
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    [7 is OAKLEY_AES_CBC]
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | ike_alg_enc_ok(ealg=7,key_len=0): blocksize=16, keyminlen=128, keydeflen=128, keymaxlen=256, ret=1
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_KEY_LENGTH
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    length/value: 256
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | ike_alg_enc_ok(ealg=7,key_len=256): blocksize=16, keyminlen=128, keydeflen=128, keymaxlen=256, ret=1
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_AUTHENTICATION_METHOD
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    length/value: 1
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    [1 is OAKLEY_PRESHARED_KEY]
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | started looking for secret for 192.168.1.99->@#0x76706e75736572 of kind PPK_PSK
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | actually looking for secret for 192.168.1.99->@#0x76706e75736572 of kind PPK_PSK
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | line 1: key type PPK_PSK(192.168.1.99) to type PPK_PSK 
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | 1: compared key %any to 192.168.1.99 / @#0x76706e75736572 -> 2
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | 2: compared key 192.168.1.99 to 192.168.1.99 / @#0x76706e75736572 -> 10
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | line 1: match=10 
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | best_match 0>10 best=0x14fb0c0 (line=1)
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | concluding with best_match=10 best=0x14fb0c0 (lineno=1)
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_HASH_ALGORITHM
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    length/value: 2
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    [2 is OAKLEY_SHA1]
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_GROUP_DESCRIPTION
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    length/value: 2
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |    [2 is OAKLEY_GROUP_MODP1024]
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | Oakley Transform 1 accepted
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: | DH public value received:
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   d0 3e 9d e5  93 5b f6 ed  02 8d ce fa  25 be a4 08
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   ff d4 92 ab  15 d3 11 87  62 a0 30 82  14 29 0c dd
Nov  4 19:53:05 h0m3s3rv3r pluto[8344]: |   56 ea a3 44  af 8b b0 62  8a 8b 4b 66  21 64 94 cf
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |  
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | *received 611 bytes from 184.151.114.97:56486 on eth0 (port=500)
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   fb 77 ff 6d  92 f7 d1 2a  00 00 00 00  00 00 00 00
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   01 10 04 00  00 00 00 00  00 00 02 63  04 00 01 24
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   00 00 00 01  00 00 00 01  00 00 01 18  01 01 00 08
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   03 00 00 24  01 01 00 00  80 0b 00 01  80 0c 70 80
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   80 01 00 07  80 0e 01 00  80 03 00 01  80 02 00 02
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   80 04 00 02  03 00 00 24  02 01 00 00  80 0b 00 01
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   80 0c 70 80  80 01 00 07  80 0e 01 00  80 03 00 01
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   80 02 00 01  80 04 00 02  03 00 00 24  03 01 00 00
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   80 0b 00 01  80 0c 70 80  80 01 00 07  80 0e 00 80
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   80 03 00 01  80 02 00 02  80 04 00 02  03 00 00 24
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   04 01 00 00  80 0b 00 01  80 0c 70 80  80 01 00 07
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   80 0e 00 80  80 03 00 01  80 02 00 01  80 04 00 02
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   03 00 00 20  05 01 00 00  80 0b 00 01  80 0c 70 80
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   80 01 00 05  80 03 00 01  80 02 00 02  80 04 00 02
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   03 00 00 20  06 01 00 00  80 0b 00 01  80 0c 70 80
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   80 01 00 05  80 03 00 01  80 02 00 01  80 04 00 02
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   03 00 00 20  07 01 00 00  80 0b 00 01  80 0c 70 80
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   80 01 00 01  80 03 00 01  80 02 00 02  80 04 00 02
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   00 00 00 20  08 01 00 00  80 0b 00 01  80 0c 70 80
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   80 01 00 01  80 03 00 01  80 02 00 01  80 04 00 02
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   0a 00 00 84  d0 3e 9d e5  93 5b f6 ed  02 8d ce fa
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   25 be a4 08  ff d4 92 ab  15 d3 11 87  62 a0 30 82
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   14 29 0c dd  56 ea a3 44  af 8b b0 62  8a 8b 4b 66
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   21 64 94 cf  66 63 9d c4  78 ea 2e a7  47 6f 73 80
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   e4 4a 37 02  9a f0 bf 36  17 26 7f 03  e3 7c b9 eb
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   f8 2f f5 8a  be da 6f 33  d3 e9 df 12  24 1b 5a 1c
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   00 37 a1 f9  97 7f 2a e1  71 32 f6 9c  9b 2e 0e 8d
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   38 b9 6c af  bd 62 5c ed  b7 8d 71 ca  47 c3 b8 84
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   b4 0d ce 54  05 00 00 14  95 bd fe b5  ca e9 80 30
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   07 ef 11 46  26 f1 54 7b  0d 00 00 0f  0b 00 00 00
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   76 70 6e 75  73 65 72 0d  00 00 18 40  48 b7 d5 6e
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   bc e8 85 25  e7 de 7f 00  d6 c2 d3 80  00 00 00 0d
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   00 00 14 4a  13 1c 81 07  03 58 45 5c  57 28 f2 0e
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   95 45 2f 0d  00 00 14 cd  60 46 43 35  df 21 f8 7c
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   fd b2 fc 68  b6 a4 48 0d  00 00 14 90  cb 80 91 3e
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   bb 69 6e 08  63 81 b5 ec  42 7b 1f 0d  00 00 14 44
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   85 15 2d 18  b6 bb cd 0b  e8 a8 46 95  79 dd cc 00
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   00 00 14 af  ca d7 13 68  a1 f1 c9 6b  86 96 fc 77
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   57 01 00
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | **parse ISAKMP Message:
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    initiator cookie:
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   fb 77 ff 6d  92 f7 d1 2a
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    responder cookie:
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   00 00 00 00  00 00 00 00
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_SA
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    ISAKMP version: ISAKMP Version 1.0 (rfc2407)
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    exchange type: ISAKMP_XCHG_AGGR
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    flags: none
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    message ID:  00 00 00 00
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    length: 611
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |  processing version=1.0 packet with exchange type=ISAKMP_XCHG_AGGR (4)
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | got payload 0x2(ISAKMP_NEXT_SA) needed: 0x432 opt: 0x102000
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Security Association Payload:
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_KE
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    length: 292
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    DOI: ISAKMP_DOI_IPSEC
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | got payload 0x10(ISAKMP_NEXT_KE) needed: 0x430 opt: 0x102000
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Key Exchange Payload:
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_NONCE
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    length: 132
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | got payload 0x400(ISAKMP_NEXT_NONCE) needed: 0x420 opt: 0x102000
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Nonce Payload:
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_ID
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    length: 20
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | got payload 0x20(ISAKMP_NEXT_ID) needed: 0x20 opt: 0x102000
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Identification Payload:
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_VID
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    length: 15
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    ID type: ID_KEY_ID
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    DOI specific A: 0
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    DOI specific B: 0
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |      obj:   76 70 6e 75  73 65 72
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | got payload 0x2000(ISAKMP_NEXT_VID) needed: 0x0 opt: 0x102000
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Vendor ID Payload:
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_VID
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    length: 24
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | got payload 0x2000(ISAKMP_NEXT_VID) needed: 0x0 opt: 0x102000
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Vendor ID Payload:
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_VID
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    length: 20
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | got payload 0x2000(ISAKMP_NEXT_VID) needed: 0x0 opt: 0x102000
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Vendor ID Payload:
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_VID
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    length: 20
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | got payload 0x2000(ISAKMP_NEXT_VID) needed: 0x0 opt: 0x102000
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Vendor ID Payload:
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_VID
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    length: 20
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | got payload 0x2000(ISAKMP_NEXT_VID) needed: 0x0 opt: 0x102000
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Vendor ID Payload:
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_VID
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    length: 20
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | got payload 0x2000(ISAKMP_NEXT_VID) needed: 0x0 opt: 0x102000
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | ***parse ISAKMP Vendor ID Payload:
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_NONE
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    length: 20
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: packet from 184.151.114.97:56486: ignoring Vendor ID payload [FRAGMENTATION 80000000]
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: packet from 184.151.114.97:56486: received Vendor ID payload [RFC 3947] method set to=109 
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: packet from 184.151.114.97:56486: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02] meth=107, but already using method 109
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: packet from 184.151.114.97:56486: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-02_n] meth=106, but already using method 109
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: packet from 184.151.114.97:56486: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-00]
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: packet from 184.151.114.97:56486: received Vendor ID payload [Dead Peer Detection]
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | find_host_connection2 called from aggr_inI1_outR1_common, me=192.168.1.99:500 him=184.151.114.97:56486 policy=none
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | find_host_pair: comparing to 192.168.1.99:500 184.151.114.97:500 
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | find_host_pair_conn (find_host_connection2): 192.168.1.99:500 184.151.114.97:56486 -> hp:L2TP-PSK-NAT 
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | find_host_connection2 returns L2TP-PSK-NAT
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | creating state object #39 at 0x1506d10
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | KEY ID:  76 70 6e 75  73 65 72
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: "L2TP-PSK-NAT"[8] 184.151.114.97 #39: Aggressive mode peer ID is ID_KEY_ID: '@#0x76706e75736572'
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | refine_connection: starting with L2TP-PSK-NAT
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | started looking for secret for 192.168.1.99->@#0x76706e75736572 of kind PPK_PSK
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | actually looking for secret for 192.168.1.99->@#0x76706e75736572 of kind PPK_PSK
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | line 1: key type PPK_PSK(192.168.1.99) to type PPK_PSK 
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | 1: compared key %any to 192.168.1.99 / @#0x76706e75736572 -> 2
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | 2: compared key 192.168.1.99 to 192.168.1.99 / @#0x76706e75736572 -> 10
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | line 1: match=10 
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | best_match 0>10 best=0x14fb0c0 (line=1)
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | concluding with best_match=10 best=0x14fb0c0 (lineno=1)
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    match_id a=@#0x76706e75736572
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |             b=@#0x76706e75736572
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    results  matched
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   trusted_ca called with a=(empty) b=(empty)
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | refine_connection: checking L2TP-PSK-NAT against L2TP-PSK-NAT, best=(none) with match=1(id=1/ca=1/reqca=1)
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | refine_connection: checked L2TP-PSK-NAT against L2TP-PSK-NAT, now for see if best
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | started looking for secret for 192.168.1.99->@#0x76706e75736572 of kind PPK_PSK
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | actually looking for secret for 192.168.1.99->@#0x76706e75736572 of kind PPK_PSK
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | line 1: key type PPK_PSK(192.168.1.99) to type PPK_PSK 
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | 1: compared key %any to 192.168.1.99 / @#0x76706e75736572 -> 2
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | 2: compared key 192.168.1.99 to 192.168.1.99 / @#0x76706e75736572 -> 10
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | line 1: match=10 
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | best_match 0>10 best=0x14fb0c0 (line=1)
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | concluding with best_match=10 best=0x14fb0c0 (lineno=1)
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | offered CA: '%none'
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | processing connection L2TP-PSK-NAT[8] 184.151.114.97
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | ICOOKIE:  fb 77 ff 6d  92 f7 d1 2a
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | RCOOKIE:  0b 9c 74 0b  26 a3 68 67
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | state hash entry 12
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | inserting state object #39 on chain 12
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | inserting event EVENT_SO_DISCARD, timeout in 0 seconds for #39
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | event added at head of queue
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: "L2TP-PSK-NAT"[8] 184.151.114.97 #39: responding to Aggressive Mode, state #39, connection "L2TP-PSK-NAT" from 184.151.114.97
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | sender checking NAT-t: 1 and 109
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: "L2TP-PSK-NAT"[8] 184.151.114.97 #39: enabling possible NAT-traversal with method 4
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | ****parse IPsec DOI SIT:
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    IPsec DOI SIT: SIT_IDENTITY_ONLY
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | ****parse ISAKMP Proposal Payload:
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_NONE
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    length: 280
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    proposal number: 1
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    protocol ID: PROTO_ISAKMP
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    SPI size: 0
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    number of transforms: 8
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | *****parse ISAKMP Transform Payload (ISAKMP):
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    next payload type: ISAKMP_NEXT_T
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    length: 36
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    transform number: 1
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    transform ID: KEY_IKE
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_LIFE_TYPE
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    length/value: 1
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    [1 is OAKLEY_LIFE_SECONDS]
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_LIFE_DURATION
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    length/value: 28800
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_ENCRYPTION_ALGORITHM
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    length/value: 7
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    [7 is OAKLEY_AES_CBC]
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | ike_alg_enc_ok(ealg=7,key_len=0): blocksize=16, keyminlen=128, keydeflen=128, keymaxlen=256, ret=1
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_KEY_LENGTH
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    length/value: 256
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | ike_alg_enc_ok(ealg=7,key_len=256): blocksize=16, keyminlen=128, keydeflen=128, keymaxlen=256, ret=1
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_AUTHENTICATION_METHOD
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    length/value: 1
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    [1 is OAKLEY_PRESHARED_KEY]
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | started looking for secret for 192.168.1.99->@#0x76706e75736572 of kind PPK_PSK
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | actually looking for secret for 192.168.1.99->@#0x76706e75736572 of kind PPK_PSK
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | line 1: key type PPK_PSK(192.168.1.99) to type PPK_PSK 
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | 1: compared key %any to 192.168.1.99 / @#0x76706e75736572 -> 2
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | 2: compared key 192.168.1.99 to 192.168.1.99 / @#0x76706e75736572 -> 10
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | line 1: match=10 
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | best_match 0>10 best=0x14fb0c0 (line=1)
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | concluding with best_match=10 best=0x14fb0c0 (lineno=1)
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_HASH_ALGORITHM
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    length/value: 2
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    [2 is OAKLEY_SHA1]
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | ******parse ISAKMP Oakley attribute:
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    af+type: OAKLEY_GROUP_DESCRIPTION
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    length/value: 2
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |    [2 is OAKLEY_GROUP_MODP1024]
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | Oakley Transform 1 accepted
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: | DH public value received:
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   d0 3e 9d e5  93 5b f6 ed  02 8d ce fa  25 be a4 08
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   ff d4 92 ab  15 d3 11 87  62 a0 30 82  14 29 0c dd
Nov  4 19:53:11 h0m3s3rv3r pluto[8344]: |   56 ea a3 44  af 8b b0 62  8a 8b 4b 66  21 64 94 cf
Nov  4 19:53:17 h0m3s3rv3r pluto[8344]: |  
Nov  4 19:53:17 h0m3s3rv3r pluto[8344]: | next event EVENT_RETRANSMIT in 0 seconds for #31
Nov  4 19:53:17 h0m3s3rv3r pluto[8344]: | *time to handle event
Nov  4 19:53:17 h0m3s3rv3r pluto[8344]: | handling event EVENT_RETRANSMIT
Nov  4 19:53:17 h0m3s3rv3r pluto[8344]: | event after this is EVENT_RETRANSMIT in 1 seconds
Nov  4 19:53:17 h0m3s3rv3r pluto[8344]: | processing connection L2TP-PSK-NAT[8] 184.151.114.97
Nov  4 19:53:17 h0m3s3rv3r pluto[8344]: | handling event EVENT_RETRANSMIT for 184.151.114.97 "L2TP-PSK-NAT" #31
Nov  4 19:53:17 h0m3s3rv3r pluto[8344]: | sending 360 bytes for EVENT_RETRANSMIT through eth0:500 to 184.151.114.97:56486 (using #31)
Nov  4 19:53:17 h0m3s3rv3r pluto[8344]: |   fb 77 ff 6d  92 f7 d1 2a  b1 d8 ad 85  63 30 24 43
Nov  4 19:53:17 h0m3s3rv3r pluto[8344]: |   01 10 04 00  00 00 00 00  00 00 01 68  04 00 00 38
Nov  4 19:53:17 h0m3s3rv3r pluto[8344]: |   00 00 00 01  00 00 00 01  00 00 00 2c  01 01 00 01
Nov  4 19:53:17 h0m3s3rv3r pluto[8344]: |   00 00 00 24  01 01 00 00  80 0b 00 01  80 0c 70 80
Nov  4 19:53:17 h0m3s3rv3r pluto[8344]: |   80 01 00 07  80 0e 01 00  80 03 00 01  80 02 00 02
Nov  4 19:53:17 h0m3s3rv3r pluto[8344]: |   80 04 00 02  0a 00 00 84  76 7a 53 eb  9f 25 3d af
Nov  4 19:53:17 h0m3s3rv3r pluto[8344]: |   42 ad ea bd  23 f0 c2 f8  22 28 02 2d  6c 62 10 b1
Nov  4 19:53:17 h0m3s3rv3r pluto[8344]: |   7b d2 cc 34  5f 8f fd 26  48 8b 39 07  2a a2 84 7e
Nov  4 19:53:17 h0m3s3rv3r pluto[8344]: |   36 0c 53 93  b5 08 9d cf  32 bd e9 32  21 db af 25
Nov  4 19:53:17 h0m3s3rv3r pluto[8344]: |   37 64 f7 52  84 1e 2b 52  2d 5b df d6  d9 65 8a 5e
Nov  4 19:53:17 h0m3s3rv3r pluto[8344]: |   6a 7f 43 b0  39 53 cb e4  c6 73 84 71  bd 72 fa 62
Nov  4 19:53:17 h0m3s3rv3r pluto[8344]: |   c6 71 6d c1  6f b3 a2 d8  59 cd b6 d9  32 cf 56 84
Nov  4 19:53:17 h0m3s3rv3r pluto[8344]: |   21 6a 68 37  5d 4a 6b 08  b7 50 50 2c  18 56 b4 42
Nov  4 19:53:17 h0m3s3rv3r pluto[8344]: |   dd 4c c6 cb  33 4a ea 92  05 00 00 14  0a d6 6e a3
Nov  4 19:53:17 h0m3s3rv3r pluto[8344]: |   00 ed 50 d0  a0 a6 f8 c5  8b 7a a6 91  08 00 00 0c
Nov  4 19:53:17 h0m3s3rv3r pluto[8344]: |   01 00 00 00  c0 a8 01 63  0d 00 00 18  fc bb d1 45
Nov  4 19:53:17 h0m3s3rv3r pluto[8344]: |   0f f7 fb 38  51 a1 49 9f  72 30 de 7a  ad 2b b5 c5
Nov  4 19:53:17 h0m3s3rv3r pluto[8344]: |   14 00 00 14  af ca d7 13  68 a1 f1 c9  6b 86 96 fc
Nov  4 19:53:17 h0m3s3rv3r pluto[8344]: |   77 57 01 00  14 00 00 18  f5 57 0f f1  c8 c8 27 06
Nov  4 19:53:17 h0m3s3rv3r pluto[8344]: |   3a ea a0 b6  4d b7 dd 66  fb 64 0c 5d  0d 00 00 18
Nov  4 19:53:17 h0m3s3rv3r pluto[8344]: |   a5 32 ed ab  99 a3 17 69  85 81 a2 42  d2 23 e5 ce
Nov  4 19:53:17 h0m3s3rv3r pluto[8344]: |   71 70 a0 1c  00 00 00 14  4a 13 1c 81  07 03 58 45
Nov  4 19:53:17 h0m3s3rv3r pluto[8344]: |   5c 57 28 f2  0e 95 45 2f
Nov  4 19:53:17 h0m3s3rv3r pluto[8344]: | inserting event EVENT_RETRANSMIT, timeout in 40 seconds for #31
Nov  4 19:53:17 h0m3s3rv3r pluto[8344]: | event added after event EVENT_PENDING_PHASE2
Nov  4 19:53:17 h0m3s3rv3r pluto[8344]: | next event EVENT_RETRANSMIT in 1 seconds for #38
Nov  4 19:53:18 h0m3s3rv3r pluto[8344]: |  
Nov  4 19:53:18 h0m3s3rv3r pluto[8344]: | next event EVENT_RETRANSMIT in 0 seconds for #38
Nov  4 19:53:18 h0m3s3rv3r pluto[8344]: | *time to handle event
Nov  4 19:53:18 h0m3s3rv3r pluto[8344]: | handling event EVENT_RETRANSMIT
Nov  4 19:53:18 h0m3s3rv3r pluto[8344]: | event after this is EVENT_RETRANSMIT in 3 seconds
Nov  4 19:53:18 h0m3s3rv3r pluto[8344]: | processing connection L2TP-PSK-NAT[8] 184.151.114.97
Nov  4 19:53:18 h0m3s3rv3r pluto[8344]: | handling event EVENT_RETRANSMIT for 184.151.114.97 "L2TP-PSK-NAT" #38
Nov  4 19:53:18 h0m3s3rv3r pluto[8344]: | sending 360 bytes for EVENT_RETRANSMIT through eth0:500 to 184.151.114.97:56486 (using #38)
Nov  4 19:53:18 h0m3s3rv3r pluto[8344]: |   fb 77 ff 6d  92 f7 d1 2a  b9 f8 c6 f2  fb 8e 21 04
Nov  4 19:53:18 h0m3s3rv3r pluto[8344]: |   01 10 04 00  00 00 00 00  00 00 01 68  04 00 00 38
Nov  4 19:53:18 h0m3s3rv3r pluto[8344]: |   00 00 00 01  00 00 00 01  00 00 00 2c  01 01 00 01
Nov  4 19:53:18 h0m3s3rv3r pluto[8344]: |   00 00 00 24  01 01 00 00  80 0b 00 01  80 0c 70 80
Nov  4 19:53:18 h0m3s3rv3r pluto[8344]: |   80 01 00 07  80 0e 01 00  80 03 00 01  80 02 00 02
Nov  4 19:53:18 h0m3s3rv3r pluto[8344]: |   80 04 00 02  0a 00 00 84  77 ba 42 f6  73 e2 7f e9
Nov  4 19:53:18 h0m3s3rv3r pluto[8344]: |   80 f6 1b 8e  19 a0 51 30  33 26 c2 49  98 04 fd 60
Nov  4 19:53:18 h0m3s3rv3r pluto[8344]: |   ab f3 64 a9  38 ae 54 a7  fb 29 d6 21  1e e0 66 76
Nov  4 19:53:18 h0m3s3rv3r pluto[8344]: |   2e 88 27 35  60 81 45 be  92 96 f7 34  50 ea b7 31
Nov  4 19:53:18 h0m3s3rv3r pluto[8344]: |   8b 2a 4c 94  44 fe 2f 95  fe ec e3 4d  59 78 d4 ad
Nov  4 19:53:18 h0m3s3rv3r pluto[8344]: |   a2 0c 53 99  25 ca e4 a5  f3 c6 d5 cd  65 a5 d1 f4
Nov  4 19:53:18 h0m3s3rv3r pluto[8344]: |   1b a1 4c 11  eb ae 15 e7  44 0e d4 de  a7 e5 e5 13
Nov  4 19:53:18 h0m3s3rv3r pluto[8344]: |   59 5d 93 6b  5c 6c 1f 61  b7 be cf 85  3d 61 5e 4e
Nov  4 19:53:18 h0m3s3rv3r pluto[8344]: |   3b b5 f9 c6  8f 3e 73 ac  05 00 00 14  04 98 22 9e
Nov  4 19:53:18 h0m3s3rv3r pluto[8344]: |   82 7c da 96  32 1c af 03  51 d3 d0 de  08 00 00 0c
Nov  4 19:53:18 h0m3s3rv3r pluto[8344]: |   01 00 00 00  c0 a8 01 63  0d 00 00 18  df 59 8f cb
Nov  4 19:53:18 h0m3s3rv3r pluto[8344]: |   de 78 b3 ad  98 ca 68 82  ae 32 52 4c  74 46 c9 bb
Nov  4 19:53:18 h0m3s3rv3r pluto[8344]: |   14 00 00 14  af ca d7 13  68 a1 f1 c9  6b 86 96 fc
Nov  4 19:53:18 h0m3s3rv3r pluto[8344]: |   77 57 01 00  14 00 00 18  20 c2 50 05  91 00 70 8e
Nov  4 19:53:18 h0m3s3rv3r pluto[8344]: |   03 fe e7 ed  0f d6 7b e5  1f 1d 30 84  0d 00 00 18
Nov  4 19:53:18 h0m3s3rv3r pluto[8344]: |   c6 57 d6 54  0c 42 01 1c  ef 6b 90 08  30 74 7e 52
Nov  4 19:53:18 h0m3s3rv3r pluto[8344]: |   b0 c9 3c e1  00 00 00 14  4a 13 1c 81  07 03 58 45
Nov  4 19:53:18 h0m3s3rv3r pluto[8344]: |   5c 57 28 f2  0e 95 45 2f
Nov  4 19:53:18 h0m3s3rv3r pluto[8344]: | inserting event EVENT_RETRANSMIT, timeout in 20 seconds for #38
Nov  4 19:53:18 h0m3s3rv3r pluto[8344]: | event added after event EVENT_RETRANSMIT for #37
Nov  4 19:53:18 h0m3s3rv3r pluto[8344]: | next event EVENT_RETRANSMIT in 3 seconds for #39
Nov  4 19:53:19 h0m3s3rv3r pluto[8344]: |  
Nov  4 19:53:19 h0m3s3rv3r pluto[8344]: | rejected packet:
Nov  4 19:53:19 h0m3s3rv3r pluto[8344]: |   fb 77 ff 6d  92 f7 d1 2a  b9 f8 c6 f2  fb 8e 21 04
Nov  4 19:53:19 h0m3s3rv3r pluto[8344]: |   01 10 04 00  00 00 00 00  00 00 01 68  04 00 00 38
Nov  4 19:53:19 h0m3s3rv3r pluto[8344]: |   00 00 00 01  00 00 00 01  00 00 00 2c  01 01 00 01
Nov  4 19:53:19 h0m3s3rv3r pluto[8344]: |   00 00 00 24  01 01 00 00  80 0b 00 01  80 0c 70 80
Nov  4 19:53:19 h0m3s3rv3r pluto[8344]: |   80 01 00 07  80 0e 01 00  80 03 00 01  80 02 00 02
Nov  4 19:53:19 h0m3s3rv3r pluto[8344]: |   80 04 00 02  0a 00 00 84  77 ba 42 f6  73 e2 7f e9
Nov  4 19:53:19 h0m3s3rv3r pluto[8344]: |   80 f6 1b 8e  19 a0 51 30  33 26 c2 49  98 04 fd 60
Nov  4 19:53:19 h0m3s3rv3r pluto[8344]: |   ab f3 64 a9  38 ae 54 a7  fb 29 d6 21  1e e0 66 76
Nov  4 19:53:19 h0m3s3rv3r pluto[8344]: |   2e 88 27 35  60 81 45 be  92 96 f7 34  50 ea b7 31
Nov  4 19:53:19 h0m3s3rv3r pluto[8344]: |   8b 2a 4c 94  44 fe 2f 95  fe ec e3 4d  59 78 d4 ad
Nov  4 19:53:19 h0m3s3rv3r pluto[8344]: |   a2 0c 53 99  25 ca e4 a5  f3 c6 d5 cd  65 a5 d1 f4
Nov  4 19:53:19 h0m3s3rv3r pluto[8344]: |   1b a1 4c 11  eb ae 15 e7  44 0e d4 de  a7 e5 e5 13
Nov  4 19:53:19 h0m3s3rv3r pluto[8344]: |   59 5d 93 6b  5c 6c 1f 61  b7 be cf 85  3d 61 5e 4e
Nov  4 19:53:19 h0m3s3rv3r pluto[8344]: |   3b b5 f9 c6  8f 3e 73 ac  05 00 00 14  04 98 22 9e
Nov  4 19:53:19 h0m3s3rv3r pluto[8344]: |   82 7c da 96  32 1c af 03  51 d3 d0 de  08 00 00 0c
Nov  4 19:53:19 h0m3s3rv3r pluto[8344]: |   01 00 00 00  c0 a8 01 63  0d 00 00 18  df 59 8f cb
Nov  4 19:53:19 h0m3s3rv3r pluto[8344]: |   de 78 b3 ad  98 ca 68 82  ae 32 52 4c  74 46 c9 bb
Nov  4 19:53:19 h0m3s3rv3r pluto[8344]: |   14 00 00 14  af ca d7 13  68 a1 f1 c9  6b 86 96 fc
Nov  4 19:53:19 h0m3s3rv3r pluto[8344]: |   77 57 01 00  14 00 00 18  20 c2 50 05  91 00 70 8e
Nov  4 19:53:19 h0m3s3rv3r pluto[8344]: |   03 fe e7 ed  0f d6 7b e5  1f 1d 30 84  0d 00 00 18
Nov  4 19:53:19 h0m3s3rv3r pluto[8344]: |   c6 57 d6 54  0c 42 01 1c  ef 6b 90 08  30 74 7e 52
Nov  4 19:53:19 h0m3s3rv3r pluto[8344]: |   b0 c9 3c e1  00 00 00 14  4a 13 1c 81  07 03 58 45
Nov  4 19:53:19 h0m3s3rv3r pluto[8344]: |   5c 57 28 f2  0e 95 45 2f
Nov  4 19:53:19 h0m3s3rv3r pluto[8344]: | control:
Nov  4 19:53:19 h0m3s3rv3r pluto[8344]: |   1c 00 00 00  00 00 00 00  00 00 00 00  08 00 00 00
Nov  4 19:53:19 h0m3s3rv3r pluto[8344]: |   02 00 00 00  c0 a8 01 63  c0 a8 01 63  ff 7f 00 00
Nov  4 19:53:19 h0m3s3rv3r pluto[8344]: |   30 00 00 00  00 00 00 00  00 00 00 00  0b 00 00 00
Nov  4 19:53:19 h0m3s3rv3r pluto[8344]: |   6f 00 00 00  02 03 03 00  00 00 00 00  00 00 00 00
Nov  4 19:53:19 h0m3s3rv3r pluto[8344]: |   02 00 00 00  b8 97 72 61  00 00 00 00  00 00 00 00
Nov  4 19:53:19 h0m3s3rv3r pluto[8344]: | name:
Nov  4 19:53:19 h0m3s3rv3r pluto[8344]: |   02 00 dc a6  b8 97 72 61  00 00 00 00  00 00 00 00
Nov  4 19:53:19 h0m3s3rv3r pluto[8344]: "L2TP-PSK-NAT"[8] 184.151.114.97 #38: ERROR: asynchronous network error report on eth0 (sport=500) for message to 184.151.114.97 port 56486, complainant 184.151.114.97: Connection refused [errno 111, origin ICMP type 3 code 3 (not authenticated)]
Nov  4 19:53:19 h0m3s3rv3r pluto[8344]: | * processed 0 messages from cryptographic helpers 
Nov  4 19:53:19 h0m3s3rv3r pluto[8344]: | next event EVENT_RETRANSMIT in 2 seconds for #39
Nov  4 19:53:19 h0m3s3rv3r pluto[8344]: | next event EVENT_RETRANSMIT in 2 seconds for #39
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |  
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: | next event EVENT_RETRANSMIT in 0 seconds for #39
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: | *time to handle event
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: | handling event EVENT_RETRANSMIT
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: | event after this is EVENT_RETRANSMIT in 0 seconds
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: | processing connection L2TP-PSK-NAT[8] 184.151.114.97
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: | handling event EVENT_RETRANSMIT for 184.151.114.97 "L2TP-PSK-NAT" #39
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: | sending 360 bytes for EVENT_RETRANSMIT through eth0:500 to 184.151.114.97:56486 (using #39)
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   fb 77 ff 6d  92 f7 d1 2a  0b 9c 74 0b  26 a3 68 67
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   01 10 04 00  00 00 00 00  00 00 01 68  04 00 00 38
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   00 00 00 01  00 00 00 01  00 00 00 2c  01 01 00 01
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   00 00 00 24  01 01 00 00  80 0b 00 01  80 0c 70 80
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   80 01 00 07  80 0e 01 00  80 03 00 01  80 02 00 02
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   80 04 00 02  0a 00 00 84  82 5f 2e 90  97 78 b9 93
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   74 69 ae 3e  03 c4 41 46  c1 3e 74 60  9f 6c 46 db
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   0b 96 81 10  5c bf 82 86  b1 2b cc 99  3f ce 1c a5
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   4f f1 47 7e  87 d0 2c 7a  2f 4f c0 20  c5 05 00 ef
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   9f dd ad 7a  47 49 5a e9  67 72 fb 96  7e 0a 77 6c
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   03 f7 ed 6f  99 46 e8 1c  97 62 ac 57  c6 d9 d6 b3
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   80 02 73 80  f1 cb 24 f4  70 07 36 43  b4 e4 d4 12
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   c9 14 83 73  74 f9 2c 61  c7 b7 2f a5  c4 44 2a 0f
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   75 3f 37 fd  19 b4 4c de  05 00 00 14  0c a7 28 a2
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   f0 46 4a ae  3f ad d1 56  a0 57 2d 0c  08 00 00 0c
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   01 00 00 00  c0 a8 01 63  0d 00 00 18  a8 9e aa 54
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   cd ef 5b d8  69 4a 47 76  2c 69 c3 d5  7d 79 ce e8
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   14 00 00 14  af ca d7 13  68 a1 f1 c9  6b 86 96 fc
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   77 57 01 00  14 00 00 18  e2 77 be 8d  6a 1f 6b 2f
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   d9 76 d9 42  bc 46 42 0b  11 e8 19 d9  0d 00 00 18
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   36 cd 37 87  bf bf ed 59  80 c3 f3 25  3a 50 2c 05
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   b2 2a 62 39  00 00 00 14  4a 13 1c 81  07 03 58 45
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   5c 57 28 f2  0e 95 45 2f
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: | inserting event EVENT_RETRANSMIT, timeout in 20 seconds for #39
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: | event added after event EVENT_RETRANSMIT for #38
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: | handling event EVENT_RETRANSMIT
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: | event after this is EVENT_RETRANSMIT in 2 seconds
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: | processing connection L2TP-PSK-NAT[8] 184.151.114.97
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: | handling event EVENT_RETRANSMIT for 184.151.114.97 "L2TP-PSK-NAT" #32
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: | sending 360 bytes for EVENT_RETRANSMIT through eth0:500 to 184.151.114.97:56486 (using #32)
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   fb 77 ff 6d  92 f7 d1 2a  42 c4 71 0e  99 59 51 bf
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   01 10 04 00  00 00 00 00  00 00 01 68  04 00 00 38
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   00 00 00 01  00 00 00 01  00 00 00 2c  01 01 00 01
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   00 00 00 24  01 01 00 00  80 0b 00 01  80 0c 70 80
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   80 01 00 07  80 0e 01 00  80 03 00 01  80 02 00 02
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   80 04 00 02  0a 00 00 84  21 d3 4d ed  6d 33 13 72
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   2a 8c 23 df  da 09 cd 5e  b6 ac c5 ca  20 2d 9c 2d
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   3d 5f 32 47  34 45 f2 45  01 15 36 1c  86 72 0c e4
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   52 62 f0 f9  df df df c0  3f 3f c6 96  e4 f1 ae 0e
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   13 89 be 58  70 a7 6a de  9c 30 88 be  0b ee d7 41
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   28 03 3f e8  59 7d 0c 75  ca da 29 33  71 a2 c3 b9
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   2c 61 82 24  3b 9c 82 8d  a4 dc b8 5f  bd af ce 87
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   a4 27 32 e0  0a 19 38 f0  fa 6f b2 60  f1 53 15 90
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   24 3f 13 fa  66 bc b3 11  05 00 00 14  81 cb 02 e5
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   f6 55 6a 05  d6 3c 36 31  cd 5d 6b a5  08 00 00 0c
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   01 00 00 00  c0 a8 01 63  0d 00 00 18  20 5b 65 4c
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   0c 26 a8 7d  f2 ad 97 37  fa 94 34 64  a1 1b 70 95
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   14 00 00 14  af ca d7 13  68 a1 f1 c9  6b 86 96 fc
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   77 57 01 00  14 00 00 18  2a ec 37 61  ba eb 6d 86
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   73 46 6d ea  43 d1 b7 96  23 a3 33 1a  0d 00 00 18
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   46 05 6f 38  39 63 b6 2b  0d eb 35 30  a1 93 53 99
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   53 85 9a dc  00 00 00 14  4a 13 1c 81  07 03 58 45
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   5c 57 28 f2  0e 95 45 2f
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: | inserting event EVENT_RETRANSMIT, timeout in 40 seconds for #32
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: | event added after event EVENT_RETRANSMIT for #31
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: | next event EVENT_RETRANSMIT in 2 seconds for #33
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |  
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: | rejected packet:
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   fb 77 ff 6d  92 f7 d1 2a  0b 9c 74 0b  26 a3 68 67
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   01 10 04 00  00 00 00 00  00 00 01 68  04 00 00 38
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   00 00 00 01  00 00 00 01  00 00 00 2c  01 01 00 01
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   00 00 00 24  01 01 00 00  80 0b 00 01  80 0c 70 80
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   80 01 00 07  80 0e 01 00  80 03 00 01  80 02 00 02
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   80 04 00 02  0a 00 00 84  82 5f 2e 90  97 78 b9 93
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   74 69 ae 3e  03 c4 41 46  c1 3e 74 60  9f 6c 46 db
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   0b 96 81 10  5c bf 82 86  b1 2b cc 99  3f ce 1c a5
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   4f f1 47 7e  87 d0 2c 7a  2f 4f c0 20  c5 05 00 ef
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   9f dd ad 7a  47 49 5a e9  67 72 fb 96  7e 0a 77 6c
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   03 f7 ed 6f  99 46 e8 1c  97 62 ac 57  c6 d9 d6 b3
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   80 02 73 80  f1 cb 24 f4  70 07 36 43  b4 e4 d4 12
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   c9 14 83 73  74 f9 2c 61  c7 b7 2f a5  c4 44 2a 0f
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   75 3f 37 fd  19 b4 4c de  05 00 00 14  0c a7 28 a2
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   f0 46 4a ae  3f ad d1 56  a0 57 2d 0c  08 00 00 0c
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   01 00 00 00  c0 a8 01 63  0d 00 00 18  a8 9e aa 54
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   cd ef 5b d8  69 4a 47 76  2c 69 c3 d5  7d 79 ce e8
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   14 00 00 14  af ca d7 13  68 a1 f1 c9  6b 86 96 fc
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   77 57 01 00  14 00 00 18  e2 77 be 8d  6a 1f 6b 2f
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   d9 76 d9 42  bc 46 42 0b  11 e8 19 d9  0d 00 00 18
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   36 cd 37 87  bf bf ed 59  80 c3 f3 25  3a 50 2c 05
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   b2 2a 62 39  00 00 00 14  4a 13 1c 81  07 03 58 45
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   5c 57 28 f2  0e 95 45 2f
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: | control:
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   1c 00 00 00  00 00 00 00  00 00 00 00  08 00 00 00
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   02 00 00 00  c0 a8 01 63  c0 a8 01 63  ff 7f 00 00
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   30 00 00 00  00 00 00 00  00 00 00 00  0b 00 00 00
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   6f 00 00 00  02 03 03 00  00 00 00 00  00 00 00 00
Nov  4 19:53:21 h0m3s3rv3r pluto[8344]: |   02 00 00 00  b8 97 72 61  00 00 00 00  00 00 00 00
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |  
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: | next event EVENT_RETRANSMIT in 0 seconds for #33
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: | *time to handle event
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: | handling event EVENT_RETRANSMIT
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: | event after this is EVENT_RETRANSMIT in 1 seconds
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: | processing connection L2TP-PSK-NAT[8] 184.151.114.97
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: | handling event EVENT_RETRANSMIT for 184.151.114.97 "L2TP-PSK-NAT" #33
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: | sending 360 bytes for EVENT_RETRANSMIT through eth0:500 to 184.151.114.97:56486 (using #33)
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   fb 77 ff 6d  92 f7 d1 2a  83 ec d4 28  62 8d 08 01
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   01 10 04 00  00 00 00 00  00 00 01 68  04 00 00 38
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   00 00 00 01  00 00 00 01  00 00 00 2c  01 01 00 01
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   00 00 00 24  01 01 00 00  80 0b 00 01  80 0c 70 80
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   80 01 00 07  80 0e 01 00  80 03 00 01  80 02 00 02
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   80 04 00 02  0a 00 00 84  ae 67 e8 4e  cf 69 22 48
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   5e 02 52 e5  99 75 7e ff  e9 5a 3e cc  7d fb 24 f9
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   29 04 60 c3  b0 d3 64 68  f5 56 7e e2  49 b0 63 54
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   49 f9 17 20  b8 4f 6e 6c  73 8a b1 19  73 c5 60 9a
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   5e c8 48 a1  f2 97 5d 43  26 aa a4 28  fa 70 e6 e9
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   d3 05 1c 39  a7 c9 ee f2  0c 45 f8 df  ef 88 3c 7c
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   ac 12 58 3f  54 f7 a8 c4  0a c7 81 c5  4b 66 92 90
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   5f eb c1 4f  e9 35 29 cc  8a a7 8d 82  ff a2 58 92
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   cc 32 65 21  a7 af 75 00  05 00 00 14  a3 04 f6 ef
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   09 e1 f7 42  50 3b f3 e8  74 88 bb 5e  08 00 00 0c
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   01 00 00 00  c0 a8 01 63  0d 00 00 18  ca 53 da e5
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   04 5d 1d 4e  27 51 99 0b  83 2e 42 cd  44 89 fe d7
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   14 00 00 14  af ca d7 13  68 a1 f1 c9  6b 86 96 fc
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   77 57 01 00  14 00 00 18  aa 46 24 da  04 cb 1a 2b
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   ef d9 c8 fe  98 ef 69 53  8b d6 07 87  0d 00 00 18
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   d0 25 b1 2c  69 fb 76 7f  b1 b8 29 02  43 2b 94 8d
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   45 f7 fa 3a  00 00 00 14  4a 13 1c 81  07 03 58 45
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   5c 57 28 f2  0e 95 45 2f
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: | inserting event EVENT_RETRANSMIT, timeout in 40 seconds for #33
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: | event added after event EVENT_RETRANSMIT for #32
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: | next event EVENT_RETRANSMIT in 1 seconds for #40
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |  
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: | rejected packet:
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   fb 77 ff 6d  92 f7 d1 2a  83 ec d4 28  62 8d 08 01
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   01 10 04 00  00 00 00 00  00 00 01 68  04 00 00 38
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   00 00 00 01  00 00 00 01  00 00 00 2c  01 01 00 01
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   00 00 00 24  01 01 00 00  80 0b 00 01  80 0c 70 80
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   80 01 00 07  80 0e 01 00  80 03 00 01  80 02 00 02
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   80 04 00 02  0a 00 00 84  ae 67 e8 4e  cf 69 22 48
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   5e 02 52 e5  99 75 7e ff  e9 5a 3e cc  7d fb 24 f9
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   29 04 60 c3  b0 d3 64 68  f5 56 7e e2  49 b0 63 54
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   49 f9 17 20  b8 4f 6e 6c  73 8a b1 19  73 c5 60 9a
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   5e c8 48 a1  f2 97 5d 43  26 aa a4 28  fa 70 e6 e9
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   d3 05 1c 39  a7 c9 ee f2  0c 45 f8 df  ef 88 3c 7c
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   ac 12 58 3f  54 f7 a8 c4  0a c7 81 c5  4b 66 92 90
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   5f eb c1 4f  e9 35 29 cc  8a a7 8d 82  ff a2 58 92
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   cc 32 65 21  a7 af 75 00  05 00 00 14  a3 04 f6 ef
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   09 e1 f7 42  50 3b f3 e8  74 88 bb 5e  08 00 00 0c
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   01 00 00 00  c0 a8 01 63  0d 00 00 18  ca 53 da e5
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   04 5d 1d 4e  27 51 99 0b  83 2e 42 cd  44 89 fe d7
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   14 00 00 14  af ca d7 13  68 a1 f1 c9  6b 86 96 fc
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   77 57 01 00  14 00 00 18  aa 46 24 da  04 cb 1a 2b
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   ef d9 c8 fe  98 ef 69 53  8b d6 07 87  0d 00 00 18
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   d0 25 b1 2c  69 fb 76 7f  b1 b8 29 02  43 2b 94 8d
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   45 f7 fa 3a  00 00 00 14  4a 13 1c 81  07 03 58 45
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   5c 57 28 f2  0e 95 45 2f
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: | control:
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   1c 00 00 00  00 00 00 00  00 00 00 00  08 00 00 00
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   02 00 00 00  c0 a8 01 63  c0 a8 01 63  ff 7f 00 00
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   30 00 00 00  00 00 00 00  00 00 00 00  0b 00 00 00
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   6f 00 00 00  02 03 03 00  00 00 00 00  00 00 00 00
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   02 00 00 00  b8 97 72 61  00 00 00 00  00 00 00 00
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: | name:
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: |   02 00 dc a6  b8 97 72 61  00 00 00 00  00 00 00 00
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: "L2TP-PSK-NAT"[8] 184.151.114.97 #33: ERROR: asynchronous network error report on eth0 (sport=500) for message to 184.151.114.97 port 56486, complainant 184.151.114.97: Connection refused [errno 111, origin ICMP type 3 code 3 (not authenticated)]
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: | * processed 0 messages from cryptographic helpers 
Nov  4 19:53:23 h0m3s3rv3r pluto[8344]: | next event EVENT_RETRANSMIT in 1 seconds for #40

```

---

### Post by rasti121 on 2013-11-20
I think you are getting this error because your IP in /etc/ppp/chap-secrets is not from the ip range in /etc/xl2tpd/xl2tpd.conf - you have used your local ip instead. Change in chap-secrets ip to fit the range, for example:

vpnuser  l2tpd  password  192.168.1.10[COLOR="#FF0000"]1[/COLOR]
l2tpd vpnuser   password  192.168.1.10[COLOR="#FF0000"]1[/COLOR]

(101 instead 100) and it should get you past this error (it did for me).

---

### Post by rasti121 on 2013-11-20
Actually I have just checked, it works with Win 7 client, but doesn't with my Nexus 5... same error as yours, which looks like the handset is dropping the connection and then the packets can't be routed, so network error :(

---

