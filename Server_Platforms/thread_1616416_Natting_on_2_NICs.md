---
title: "Natting on 2 NICs"
date: 2010-11-08
forum: Server Platforms
---

### Post by dbehterev on 2010-11-08
Hello guys, I have broken my head trying solve this problem:
I have Ubuntu 10.10 server gateway:
```

                                 _______________________________
| ISP1 |<---->|ADSL modem, internal IP 192.168.1.1 |<------->|eth0 IP 192.168.1.10        |
                                 |        ubuntu server        |
| ISP2 |<--------------------------------------------------->|wimax0, DHCP                  |
                                 |                   |
                                      |          int. ip 192.168.0.250 |<----->LAN
            -------------------------------         |                    |
            |Server VOiP, 172.16.0.10     |<---->|eth1 (for DMZ), IP 172.16.0.1 |
            -------------------------------         --------------------------------

```My goal is LAN must use ISP 2 to go to Internet and VOiP server must use ISP1. So, I write some iptables rules:
```

#!/bin/sh
#
IPT="/sbin/iptables"

# Internet Interface
INET_IFACE="wimax0"

# ADSL Internet interface
INET_ADSL_IFACE="eth0"

# DMZ Iface
LOCAL_DMZ_IFACE="eth1"
LOCAL_DMZ_IP="172.16.0.1/32"
DMZ_IP="172.16.0.10/32"
DMZ_NET="172.16.0.0/24"
# Local Interface Information
LOCAL_IFACE="eth2"
LOCAL_IP="192.168.0.250"
LOCAL_NET="192.168.0.0/24"
LOCAL_BCAST="192.168.0.255"

# Localhost Interface
LO_IFACE="lo"
LO_IP="127.0.0.1"

echo "Flushing Tables ..."

# Reset Default Policies
$IPT -P INPUT ACCEPT
$IPT -P FORWARD ACCEPT
$IPT -P OUTPUT ACCEPT
$IPT -t nat -P PREROUTING ACCEPT
$IPT -t nat -P POSTROUTING ACCEPT
$IPT -t nat -P OUTPUT ACCEPT
$IPT -t mangle -P PREROUTING ACCEPT
$IPT -t mangle -P OUTPUT ACCEPT

# Flush all rules
$IPT -F
$IPT -t nat -F
$IPT -t mangle -F

# Erase all non-default chains
$IPT -X
$IPT -t nat -X
$IPT -t mangle -X

$IPT -P INPUT ACCEPT
$IPT -P OUTPUT ACCEPT
$IPT -P FORWARD ACCEPT


$IPT -A FORWARD -p ALL -i $LOCAL_IFACE -j ACCEPT
$IPT -A FORWARD -p ALL -i $LOCAL_DMZ_IFACE -j ACCEPT

# Deal with responses from the internet
$IPT -A FORWARD -i $INET_IFACE -m state --state ESTABLISHED,RELATED \
     -j ACCEPT

$IPT -A FORWARD -i $INET_ADSL_IFACE -m state --state ESTABLISHED,RELATED -j ACCEPT

echo "Load rules for nat table ..."

$IPT -t nat -A POSTROUTING -s $LOCAL_NET -o $INET_IFACE -j MASQUERADE
$IPT -t nat -A POSTROUTING -s $DMZ_NET -o $INET_ADSL_IFACE -j MASQUERADE

```As you see there are double NATting: one for local NET and one for DMZ NET.
But there is problem: packets from DMZ network are not natting or may be something else wrong.
Also my routing table:
```

# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     199    0        0 eth0
172.16.0.0      0.0.0.0         255.255.255.0   U     0      0        0 eth1
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth2
10.117.56.0     0.0.0.0         255.255.248.0   U     0      0        0 wimax0
0.0.0.0         10.117.56.1     0.0.0.0         UG    0      0        0 wimax0
0.0.0.0         10.117.56.1     0.0.0.0         UG    100    0        0 wimax0
0.0.0.0         192.168.1.1     0.0.0.0         UG    200    0        0 eth0

```If anyone have any idea please let me know. Thanks.

---

### Post by koenn on 2010-11-10
nice one.

your drawing is not very clear, so I'm going by what I can make out of your iptables rules and your explanation.

your problem is that on your router (your "server gateway"), the default route is through the wimax : 
```
0.0.0.0         10.117.56.1     0.0.0.0         UG    0      0        0 wimax0
```
so  your ```

IPT -t nat -A POSTROUTING -s $DMZ_NET -o $INET_ADSL_IFACE -j MASQUERADE

``` is never executed
contrary to what you might think, that rule says : IF trafic comes from  -s $DMZ_NET  AND is routed out through -o $INET_ADSL_IFACE, THEN masquerade it. It does not say : IF trafic comes from  -s $DMZ_NET THEN route it out through -o $INET_ADSL_IFACE and masquerade it. 
So because nothing is routed out through -o $INET_ADSL_IFACE, that masquerading is never done. 


Source NAT and MASQuerading happens after routing decisions are taken, so it's not going to be easy to fix this, unless you know the IP address of your ADSL connection (which would preferably be static or not changing too often) - in that case i think there's a reasonable change you can set up routing on your DMZ hosts so that they route out through the ADSL. 


otoh, i have a feeling I'm overlooking something, but it's late, and I'm off to bed. So maybe someone with a clear had could have an other look.

---

