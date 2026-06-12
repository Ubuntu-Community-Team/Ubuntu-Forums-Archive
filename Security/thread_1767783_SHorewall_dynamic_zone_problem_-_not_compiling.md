---
title: "SHorewall dynamic zone problem - not compiling"
date: 2011-05-26
forum: Security
---

### Post by kenga on 2011-05-26
I'm trying to configure in shorewall dynamic zone on outside interface for IPSEC vpn users (Racoon + Shrew VPN Client) as most reliable and correct way to set access restrictions on vpn users network access. VPN itself working like a charm.

Have made config similar to [http://www.shorewall.net/Dynamic.html](http://www.shorewall.net/Dynamic.html) examples, but it won't compile with "ppp0 is not a defined bridge" error. 

ipset module and utilities compiled, installed,loaded as described in [http://pepoluan.posterous.com/powertip-howto-install-ipset-on-ubuntu](http://pepoluan.posterous.com/powertip-howto-install-ipset-on-ubuntu) post.

What is wrong with config or shorewall instance?

OS: Ubuntu 10.04.2 LTS.
Kernel:  2.6.32-31-server
Shorewall: 4.4.6-1
ipset: 4.5

```
$ sudo dpkg -l | grep -E '(shorewall|linux-kernel|racoon|iptables)'
ii  iptables                         1.4.4-2ubuntu2                                  administration tools for packet filtering and NAT
ii  racoon                           1:0.7.1-1.6ubuntu1                              IPsec IKE keying daemon
ii  shorewall                        4.4.6-1                                         Shoreline Firewall, netfilter configurator
```

/etc/shorewall/zones:

```
#ZONE           TYPE            OPTIONS         IN OPTIONS             
OUT OPTIONS
self            firewall
blan            ipv4
inet            ipv4
lan             ipv4
dmz             ipv4

vpn:inet        ipv4

```
/etc/shorewall/interfaces:
```
#ZONE           INTERFACE       BROADCAST       OPTIONS
### ISP metro area network
blan            eth0            detect          dhcp,routefilter
### ISP L2TP (internet)
inet            ppp0            detect          routefilter
### IPSec VPN
vpn             ppp0:dynamic
########## LAN
lan             eth1            detect          dhcp,routefilter
lan             lo0             detect          routefilter

```

/var/log/shorewall-init.log:

```
09:49:37 Compiling...
09:49:37 Processing /etc/shorewall/params ...
09:49:37 Loading Modules...
   WARNING: RFC1918_LOG_LEVEL=6 ignored. The 'norfc1918' interface/host
option is no longer supported
Shorewall has detected the following capabilities:
   Address Type Match: Available
   CLASSIFY Target: Available
   CONNMARK Target: Available
   Capability Version: 4.4.7
   Comments: Available
   Connection Tracking Match: Available
   Connlimit Match: Available
   Connmark Match: Available
   Extended CONNMARK Target: Available
   Extended Connection Tracking Match: Available
   Extended Connmark Match: Available
   Extended Mark Target: Available
   Extended Mark Target 2: Available
   Extended Multi-port Match: Available
   Extended Reject: Available
   Goto Support: Available
   Hashlimit Match: Available
   Helper Match: Available
   IP Range Match: Available
   IPMARK Target: Not Available
   IPP2P Match: Not Available
   Ipset Match: Available
   Kernel Version: 2.6.32
   LOG Target: Available
   LOGMARK Target: Not Available
   MARK Target: Available
   Mangle FORWARD Chain: Available
   Multi-port Match: Available
   NAT: Available
   NFQUEUE Target: Available
   Old Hash Limit Match: Not Available
   Old IPP2P Match Syntax: Not Available
   Old conntrack match syntax: Not Available
   Owner Match: Available
   Packet Mangling: Available
   Packet Type Match: Available
   Packet length Match: Available
   Persistent SNAT: Available
   Physdev Match: Available
   Physdev-is-bridged support: Available
   Policy Match: Available
   Raw Table: Available
   Realm Match: Available
   Recent Match: Available
   Repeat match: Available
   TCPMSS Match: Available
   Time Match: Available
09:49:38 Compiling /etc/shorewall/zones...
09:49:38 Compiling /etc/shorewall/interfaces...
09:49:38    Interface "blan eth0 detect dhcp,routefilter" Validated
09:49:38    Interface "inet ppp0 detect routefilter" Validated
   ERROR: ppp0 is not a defined bridge : /etc/shorewall/interfaces (line 9)
```

shorewall capabilities:
```
#
# Shorewall  detected the following iptables/netfilter capabilities -
&#1063;&#1090;&#1074; &#1052;&#1072;&#1081; 26 09:55:29 MSD 2011
#
NAT_ENABLED=Yes
MANGLE_ENABLED=Yes
MULTIPORT=Yes
XMULTIPORT=Yes
CONNTRACK_MATCH=Yes
NEW_CONNTRACK_MATCH=Yes
OLD_CONNTRACK_MATCH=
USEPKTTYPE=Yes
POLICY_MATCH=Yes
PHYSDEV_MATCH=Yes
PHYSDEV_BRIDGE=Yes
LENGTH_MATCH=Yes
IPRANGE_MATCH=Yes
RECENT_MATCH=Yes
OWNER_MATCH=Yes
IPSET_MATCH=Yes
CONNMARK=Yes
XCONNMARK=Yes
CONNMARK_MATCH=Yes
XCONNMARK_MATCH=Yes
RAW_TABLE=Yes
IPP2P_MATCH=
OLD_IPP2P_MATCH=
CLASSIFY_TARGET=Yes
ENHANCED_REJECT=Yes
KLUDGEFREE=Yes
MARK=Yes
XMARK=Yes
EXMARK=Yes
MANGLE_FORWARD=Yes
COMMENTS=Yes
ADDRTYPE=Yes
TCPMSS_MATCH=Yes
HASHLIMIT_MATCH=Yes
OLD_HL_MATCH=
NFQUEUE_TARGET=Yes
REALM_MATCH=Yes
HELPER_MATCH=Yes
CONNLIMIT_MATCH=Yes
TIME_MATCH=Yes
GOTO_TARGET=Yes
LOGMARK_TARGET=
IPMARK_TARGET=
LOG_TARGET=Yes
PERSISTENT_SNAT=Yes
CAPVERSION=40407
KERNELVERSION=20632
```

---

