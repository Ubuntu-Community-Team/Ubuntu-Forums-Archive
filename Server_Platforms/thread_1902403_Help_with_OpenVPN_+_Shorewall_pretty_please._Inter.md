---
title: "Help with OpenVPN + Shorewall pretty please. Internal routing ok, external fails :("
date: 2011-12-30
forum: Server Platforms
---

### Post by gymmarn on 2011-12-30
I'm trying to setup OpenVPN. I've got the VPN to work and the routing for the internal network 192.168.30.0/24 seems OK. But I can't seem to get it to route the VPN clients so they can access Internet through the routers external interface 77.66.55.44.

Summary:
* OpenVPN OK
* Internat routing OK
* External routing NOK (need help)

I'm really hoping someone can help me with this.

Here's my setup on the server:

**_network/interfaces_**
[PHP]# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet static
        address 77.66.55.44
        netmask 255.255.255.0
        gateway 77.66.55.1

auto eth2
iface eth2 inet static
        address 192.168.30.200
        netmask 255.255.255.0
[/PHP]

**_openvpn/server.conf_**
[PHP]local 77.66.55.44
proto tcp
port 1194
dev tun
server 192.168.31.0 255.255.255.0
push "route 192.168.30.0 255.255.255.0"
push "dhcp-option DNS 192.168.30.200"
push "redirect-gateway def1"
ifconfig-pool-persist ipp.txt
client-to-client
comp-lzo
keepalive 10 60
ping-timer-rem
persist-tun
persist-key

#Server keys
ca ca.crt
cert server.crt
key server.key
dh dh1024.pem
tls-auth ta.key 0
cipher BF-CBC
[/PHP]

***shorewall/interfaces***
[PHP]net     eth1            detect          dhcp,routefilter,tcpflags,logmartians,nosmurfs
loc     eth2            detect
vpn     ppp+            detect
vpn2    tun0            detect          tcpflags,logmartians,nosmurfs
[/PHP]

***shorewall/masq***
[PHP]#INTERFACE              SOURCE          ADDRESS         PROTO   PORT(S) IPSEC   MARK
eth1                    eth2
#LAST LINE -- ADD YOUR ENTRIES ABOVE THIS LINE -- DO NOT REMOVE
[/PHP]

***shorewall/policy***
[PHP]#SOURCE         DEST            POLICY          LOG LEVEL       LIMIT:BURST
$FW             all             ACCEPT  $LOG
vpn             all             ACCEPT  $LOG
vpn2            all             ACCEPT  $LOG
loc             all             ACCEPT  $LOG
net             all             DROP    $LOG
# The FOLLOWING POLICY MUST BE LAST
all             all             REJECT          -
#LAST LINE -- ADD YOUR ENTRIES ABOVE THIS LINE -- DO NOT REMOVE
[/PHP]

***shorewall/rules***
[PHP]#OpenVPN
ACCEPT:$LOG             net                             $FW             tcp     1194
ACCEPT:$LOG             net                             $FW             udp     1194
ACCEPT:$LOG             vpn2                            $FW
ACCEPT:$LOG             vpn2                            net
#
[/PHP]

***shorewall/tunnels***
[PHP]pptpserver              net     0.0.0.0/0
openvpnserver:1194      net     0.0.0.0/0
#LAST LINE -- ADD YOUR ENTRIES BEFORE THIS ONE -- DO NOT REMOVE
[/PHP]

***shorewall/zones***
[PHP]fw      firewall
net     ipv4
loc     ipv4
vpn     ipv4
vpn2    ipv4
#LAST LINE - ADD YOUR ENTRIES ABOVE THIS ONE - DO NOT REMOVE
[/PHP]

***shorewall/shorewall.conf***
[PHP]STARTUP_ENABLED=Yes
VERBOSITY=1
SHOREWALL_COMPILER=
LOGFILE=/var/log/shorewall.log
STARTUP_LOG=
LOG_VERBOSITY=
LOGFORMAT="Shorewall:%s:%s:"
LOGTAGONLY=No
LOGRATE=
LOGBURST=
LOGALLNEW=
BLACKLIST_LOGLEVEL=$LOG
MACLIST_LOG_LEVEL=$LOG
TCP_FLAGS_LOG_LEVEL=$LOG
SMURF_LOG_LEVEL=$LOG
LOG_MARTIANS=Yes
IPTABLES=
PATH=/sbin:/bin:/usr/sbin:/usr/bin:/usr/local/bin:/usr/local/sbin
SHOREWALL_SHELL=/bin/sh
SUBSYSLOCK=""
MODULESDIR=
CONFIG_PATH=/etc/shorewall:/usr/share/shorewall
RESTOREFILE=
IPSECFILE=zones
LOCKFILE=
DROP_DEFAULT="Drop"
REJECT_DEFAULT="Reject"
ACCEPT_DEFAULT="none"
QUEUE_DEFAULT="none"
NFQUEUE_DEFAULT="none"
RSH_COMMAND='ssh ${root}@${system} ${command}'
RCP_COMMAND='scp ${files} ${root}@${system}:${destination}'
IP_FORWARDING=On
ADD_IP_ALIASES=Yes
ADD_SNAT_ALIASES=No
RETAIN_ALIASES=No
TC_ENABLED=Internal
TC_EXPERT=No
CLEAR_TC=Yes
MARK_IN_FORWARD_CHAIN=No
CLAMPMSS=No
ROUTE_FILTER=Yes
DETECT_DNAT_IPADDRS=No
MUTEX_TIMEOUT=60
ADMINISABSENTMINDED=Yes
BLACKLISTNEWONLY=Yes
DELAYBLACKLISTLOAD=No
MODULE_SUFFIX=
DISABLE_IPV6=Yes
BRIDGING=No
DYNAMIC_ZONES=No
PKTTYPE=Yes
RFC1918_STRICT=No
MACLIST_TABLE=filter
MACLIST_TTL=
SAVE_IPSETS=No
MAPOLDACTIONS=No
FASTACCEPT=No
IMPLICIT_CONTINUE=No
HIGH_ROUTE_MARKS=No
USE_ACTIONS=Yes
OPTIMIZE=0
EXPORTPARAMS=Yes
EXPAND_POLICIES=Yes
KEEP_RT_TABLES=No
DELETE_THEN_ADD=Yes
MULTICAST=No
DONT_LOAD=
AUTO_COMMENT=Yes
MANGLE_ENABLED=Yes
USE_DEFAULT_RT=No
RESTORE_DEFAULT_ROUTE=Yes
FAST_STOP=No
BLACKLIST_DISPOSITION=DROP
MACLIST_DISPOSITION=REJECT
TCP_FLAGS_DISPOSITION=DROP
[/PHP]

And now to my **client config** (Windows computers running OpenVPN 2.2.3)

[PHP]client
dev tun
remote 77.66.55.44 1194
resolv-retry infinite
proto tcp
nobind
persist-key
persist-tun
ca ca.crt
cert client.crt
key client.key
tls-auth ta.key 1
cipher BF-CBC
comp-lzo
verb 3[/PHP]

As you can see from my shorewall config I'm using PPTPd server aswell. But I want to switch to OpenVPN because it's safer and much faster.

---

### Post by gymmarn on 2011-12-31
Solved it by throwing out shorewall and adding

iptables -t nat -I POSTROUTING -o eth1 -j MASQUERADE
iptables -A INPUT -i tun+ -j ACCEPT
iptables -A FORWARD -i tun+ -o eth1 -j ACCEPT
iptables -A FORWARD -i eth1 -o tun+ -j ACCEPT
iptables -A INPUT -p tcp --dport 1194 -j ACCEPT
iptables -A INPUT -p udp --dport 1194 -j ACCEPT
iptables -A FORWARD -i tun+ -o eth2 -j ACCEPT
iptables -A FORWARD -i eth2 -o tun+ -j ACCEPT

---

