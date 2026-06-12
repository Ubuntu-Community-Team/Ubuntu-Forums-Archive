---
title: "[SOLVED] Transparent Squid proxy with IPTables cant get it to work"
date: 2008-03-02
forum: Server Platforms
---

### Post by twistedtwig on 2008-03-02
Hi all,

I am rather confused... I am trying to setup a transparent proxy with squid and iptables.

my network setup is as follows:

sky netgear router with port 80 forwarded to 192.168.0.2 (the Ubuntu server)
server does dhcp and dns for network.
internal network ip range is 192.168.10.0/24
internal network card interface is eth1 - 192.168.10.1
external IP is eth0 192.168.0.2

cat /etc/squid/squid.conf | sed '/ *#/d; /^ *$/d'
```

http_port 3128
hierarchy_stoplist cgi-bin ?
acl QUERY urlpath_regex cgi-bin \?
cache deny QUERY
acl apache rep_header Server ^Apache
broken_vary_encoding allow apache
access_log /var/log/squid/access.log squid
hosts_file /etc/hosts
refresh_pattern ^ftp:           1440    20%     10080
refresh_pattern ^gopher:        1440    0%      1440
refresh_pattern .               0       20%     4320
acl all src 0.0.0.0/0.0.0.0
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8
acl purge method PURGE
acl CONNECT method CONNECT
http_access allow manager localhost
http_access deny manager
http_access allow purge localhost
http_access deny purge
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
acl our_networks src 192.168.0.0/24 192.168.10.0/24 
http_access allow our_networks
http_access allow localhost
http_access deny all
http_reply_access allow all
icp_access allow all
cache_effective_group proxy
coredump_dir /var/spool/squid

```

and here is the same from my iptables file:
```

FWVER=0.75
echo -e "\n\nLoading simple rc.firewall version $FWVER..\n"
IPTABLES=/sbin/iptables
DEPMOD=/sbin/depmod
MODPROBE=/sbin/modprobe
EXTIF="eth0"
INTIF="eth1"
echo "   External Interface:  $EXTIF"
echo "   Internal Interface:  $INTIF"
echo -en "   loading modules: "
echo "  - Verifying that all kernel modules are ok"
$DEPMOD -a
echo "----------------------------------------------------------------------"
echo -en "ip_tables, "
$MODPROBE ip_tables
echo -en "ip_conntrack, "
$MODPROBE ip_conntrack
echo -en "ip_conntrack_ftp, "
$MODPROBE ip_conntrack_ftp
echo -en "ip_conntrack_irc, "
$MODPROBE ip_conntrack_irc
echo -en "iptable_nat, "
$MODPROBE iptable_nat
echo -en "ip_nat_ftp, "
$MODPROBE ip_nat_ftp
echo "----------------------------------------------------------------------"
echo -e "   Done loading modules.\n"
echo "   Enabling forwarding.."
echo "1" > /proc/sys/net/ipv4/ip_forward
echo "   Enabling DynamicAddr.."
echo "1" > /proc/sys/net/ipv4/ip_dynaddr
echo "   Clearing any existing rules and setting default policy.."
$IPTABLES -P INPUT DROP
$IPTABLES -F INPUT 
$IPTABLES -P OUTPUT DROP
$IPTABLES -F OUTPUT 
$IPTABLES -P FORWARD DROP
$IPTABLES -F FORWARD 
$IPTABLES -t nat -F
echo "   Opening loopback interface for socket based services."
$IPTABLES -A INPUT -i lo -j ACCEPT
$IPTABLES -A OUTPUT -o lo -j ACCEPT
echo "   Allow all connections OUT and only existing and related ones IN"
$IPTABLES -A INPUT -i $INTIF -j ACCEPT
$IPTABLES -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPTABLES -A OUTPUT -o $EXTIF -j ACCEPT
$IPTABLES -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPTABLES -A FORWARD -i $INTIF -o $EXTIF -j ACCEPT
$IPTABLES -A FORWARD -j LOG
echo "   Enabling SNAT (MASQUERADE) functionality on $EXTIF"
$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j MASQUERADE
$IPTABLES -A INPUT -i $INTIF -j ACCEPT
$IPTABLES -A OUTPUT -o $EXTIF -j ACCEPT
echo "   Allowing packets with ICMP data (i.e. ping)."
$IPTABLES -A INPUT -p icmp -j ACCEPT
$IPTABLES -A OUTPUT -p icmp -j ACCEPT
$IPTABLES -A INPUT -p udp -i $INTIF --dport 67 -m state --state NEW -j ACCEPT
echo "   Port 137 is for NetBIOS."
$IPTABLES -A INPUT -i $INTIF -p udp --dport 137 -j ACCEPT
$IPTABLES -A OUTPUT -o $INTIF -p udp --dport 137 -j ACCEPT
echo "   Opening port 53 for DNS queries."
$IPTABLES -A INPUT -p udp -i $EXTIF --sport 53 -j ACCEPT
echo "   Opening port 80 for webserver."
$IPTABLES -A INPUT -p tcp -i $EXTIF --dport 80 -m state --state NEW -j ACCEPT
echo "   Opening port 1723 for VPN initiation."
$IPTABLES -A INPUT -i $EXTIF -p TCP --dport 1723 -j ACCEPT
$IPTABLES -I INPUT -p TCP -m state --state NEW -m limit --limit 6/minute --limit-burst 5 -j ACCEPT
$IPTABLES -A INPUT -i ppp+ -j ACCEPT
$IPTABLES -A FORWARD -i ppp+ -o $INTIF -j ACCEPT
$IPTABLES -A FORWARD -i $INTIF -o ppp+ -j ACCEPT
echo -e "\nrc.firewall-2.4 v$FWVER done.\n"

```

I think squid is working correctly as if I set a PC up to directly use 192.168.10.1 (which is $INTIF) with port 3128 they can get the net.

But what ever IP commands I have tried seem to have gone wrong.  I always get

```
ERROR

The requested URL could not be retrieved
```

I am completely stuck.  If i am right in saying that squid is working correctly then I assume it is my IPTABLES file that is not working correctly.

var/log/squid/access.log has the following entry in it

```
1204495192.571      1 192.168.10.186 TCP_DENIED/400 2455 GET error:invalid-request - NONE/- text/html
```

Any and all guidance on it at this point would be great.  I really tried to solve it by my self but failed :(

---

### Post by disnetbg on 2008-03-02
put these lines to your squid.conf and restart squid


httpd_accel_host virtual
httpd_accel_port 80
httpd_accel_with_proxy on
httpd_accel_uses_host_header on

:popcorn::popcorn:

---

### Post by twistedtwig on 2008-03-03
thanks will try that tonight

---

### Post by twistedtwig on 2008-03-03
It doesn't seem happy:

```
root@betty:/home/jon# /etc/init.d/squid force-reload
 * Reloading Squid configuration files
   ...done.
root@betty:/home/jon# /etc/init.d/squid restart
 * Restarting Squid HTTP proxy squid                                                                                                                         2008/03/03 19:33:20| parseConfigFile: line 4362 unrecognized: 'httpd_accel_host virtual'
2008/03/03 19:33:20| parseConfigFile: line 4363 unrecognized: 'httpd_accel_port 80'
2008/03/03 19:33:20| parseConfigFile: line 4364 unrecognized: 'httpd_accel_with_proxy on'
2008/03/03 19:33:20| parseConfigFile: line 4365 unrecognized: 'httpd_accel_uses_host_header on'

```

---

### Post by twistedtwig on 2008-03-03
nm.. google is my friend.. (should have gone there first with the error message).

```
http_port 3128 transparent
always_direct allow all
```

the other text (as from what I read) is old and depreciated the two lines above replace them all.

all seems to be working brilliantly now.

Thank you for the help... it guided me to the answer which I was completely stumped on. :)

---

### Post by mo1tomax on 2008-04-27
It's a shame I had to dig so far for such a simple fix...  :(

Thanks to all

My issue came from a distribution upgrade from Dapper LTS server to Hardy LTS server.

Everything else was seamless.

---

