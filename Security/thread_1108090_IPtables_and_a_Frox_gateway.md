---
title: "IPtables and a Frox gateway"
date: 2009-03-27
forum: Security
---

### Post by Scormen on 2009-03-27
Hi all,

Since a few days I'm trying to setup a "cache gateway server". Everything is okay, except one little thing: FTP. This is my setup:

Squid is caching the HTTP traffic, everything oke.
On the server, there is installed a own webserver, everything oke.

On the server, there is also installed a own FTP server (vsftpd), that works fine.
Frox should cache the FTP traffic, but I can't connect to a external FTP server. The strange thing is: via the terminal I can connect to a external FTP server and get a listing. But... via Firefox or Filezilla I can connect, but the listing fails.

I think that the problem is with my IPtables and has something to do with active or passive FTP:
```
#!/bin/bash

################################################################################
# Basic

# IPtables binary
IPT="/sbin/iptables"

# External interface (WAN)
EXTIF="eth0"

# Internal interface (LAN)
INTIF="eth1"

# Everyone
UNIVERSE="0/0"

# Own LAN
LAN="192.168.0.0/0"


LOOPBACK="127.0.0.1"

CLASS_A="10.0.0.0/8"

CLASS_B="172.16.0.0/12"

CLASS_C="192.168.0.0/24"


################################################################################
# Flush

$IPT -F
$IPT -X
$IPT -Z
$IPT -t nat -F
$IPT -t nat -X
$IPT -t nat -Z

# Flush our own chain INFWD
if [ "`$IPT -L | grep INFWD`" ]; then
   $IPT -F INFWD
fi

# Load modules
/sbin/modprobe ip_conntrack
/sbin/modprobe ip_conntrack_ftp ports=21,2121
/sbin/modprobe ip_nat_ftp ports=21,2121

echo 1 > /proc/sys/net/ipv4/ip_forward



################################################################################
#

for f in /proc/sys/net/ipv4/conf/*/rp_filter ; do
echo 1 > $f
done

for f in /proc/sys/net/ipv4/conf/*/accept_redirects ; do
echo 0 > $f
done

for f in /proc/sys/net/ipv4/conf/*/send_redirects ; do
echo 0 > $f
done

for f in /proc/sys/net/ipv4/conf/*/accept_source_route ; do
echo 0 > $f
done

for f in /proc/sys/net/ipv4/conf/*/log_martians ; do
echo 1 > $f
done

echo 1 > /proc/sys/net/ipv4/tcp_syncookies

echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

echo 1 > /proc/sys/net/ipv4/icmp_ignore_bogus_error_responses

echo 1 > /proc/sys/net/ipv4/ip_dynaddr


################################################################################
# DROP some packets by default

$IPT -A INPUT -i $EXTIF -f -j LOG --log-prefix "FRAGMENT! "
$IPT -A INPUT -i $EXTIF -f -j DROP

$IPT -A INPUT -i $EXTIF -s $LOOPBACK -j LOG --log-prefix "SPOOFING! "
$IPT -A INPUT -i $EXTIF -s $CLASS_A -j LOG --log-prefix "CLASS A ADDRESS! "
$IPT -A INPUT -i $EXTIF -s $CLASS_B -j LOG --log-prefix "CLASS B ADDRESS! "
$IPT -A INPUT -i $EXTIF -s $CLASS_C -j LOG --log-prefix "CLASS C ADDRESS! "
$IPT -A INPUT -i $EXTIF -s $LOOPBACK -j DROP
$IPT -A INPUT -i $EXTIF -s $CLASS_A -j DROP
$IPT -A INPUT -i $EXTIF -s $CLASS_B -j DROP
$IPT -A INPUT -i $EXTIF -s $CLASS_C -j DROP



################################################################################
# The rules

# DROP policy
$IPT -P INPUT DROP
$IPT -P FORWARD DROP

# ACCEPT loopback
$IPT -A INPUT -i lo -j ACCEPT
$IPT -A OUTPUT -o lo -j ACCEPT
$IPT -N INFWD

$IPT -A INFWD -m state --state ESTABLISHED,RELATED -j ACCEPT

# Ping
$IPT -A INFWD -m state --state NEW -p icmp -s $LAN -j ACCEPT

# SSH en Telnet
$IPT -A INFWD -m state --state NEW -p tcp --dport 22 -j ACCEPT

# DNS
$IPT -A INFWD -m state --state NEW -p tcp -s $LAN --dport 53 -j ACCEPT
$IPT -A INFWD -m state --state NEW -p udp -s $LAN --dport 53 -j ACCEPT

# HTTP + HTTPS + Squid
$IPT -A INFWD -m state --state NEW -p tcp -s $LAN --dport 80 -j ACCEPT
$IPT -A INFWD -m state --state NEW -p tcp -s $LAN --dport 443 -j ACCEPT
$IPT -A INFWD -m state --state NEW -p tcp -s $LAN --dport 81 -j ACCEPT # Own apache
$IPT -A INFWD -m state --state NEW -p tcp -s $LAN --dport 3128 -j ACCEPT

# FTP
$IPT -A INFWD -m state --state NEW -p tcp -s $LAN --dport 20 -j ACCEPT
$IPT -A INFWD -m state --state NEW -p tcp -s $LAN --dport 21 -j ACCEPT
$IPT -A INFWD -m state --state NEW -p tcp -s $LAN --dport 23 -j ACCEPT # Own vsfptd
$IPT -A INFWD -m state --state NEW -p tcp -s $LAN --dport 2121 -j ACCEPT
$IPT -A INFWD -m state --state NEW -p tcp -s $LAN --dport 40000:50000 -j ACCEPT
$IPT -A INFWD -m state --state NEW -p tcp -s $LAN --dport 989 -j ACCEPT
$IPT -A INFWD -m state --state NEW -p tcp -s $LAN --dport 990 -j ACCEP

# ----------

# DROP the rest
$IPT -A INFWD -j DROP

# Send all INPUT and FORWARD packages to our own chain INFWD
$IPT -A INPUT -j INFWD
$IPT -A FORWARD -j INFWD


################################################################################
# PREROUTING

# 1. Squid HTTP cache-proxy
# Local website
$IPT -t nat -A PREROUTING -s $LAN -d 192.168.2.1 -p tcp --dport 80 -j REDIRECT --to-port 81

# Other HTTP traffic to Squid
$IPT -t nat -A PREROUTING -s $LAN -m state --state NEW -p tcp --dport 80 -j REDIRECT --to-port 3128


# 2. Frox FTP cache-proxy
# Local FTP server
$IPT -t nat -A PREROUTING -s $LAN -d 192.168.2.1 -p tcp --dport 21 -j REDIRECT --to-port 23

# Other FTP traffic to Frox
$IPT -t nat -A PREROUTING -s $LAN -m state --state NEW -p tcp --dport 21 -j REDIRECT --to-port 2121


################################################################################
# POSTROUTING

$IPT -t nat -A POSTROUTING -o $EXTIF -j MASQUERADE
```

Note that this is not all, there are also rules for DNS, etc...


And here is my frox.conf:
```
Listen 192.168.2.1
Port 2121
BindToDevice eth1
ResolvLoadHack blackhole.somewhere.abc
PASVAddress 192.168.2.1
User frox
Group frox
WorkingDir /cache/frox
LogLevel 25
LogFile /var/log/frox
PidFile /var/run/frox.pid
APConv yes
BounceDefend yes
CacheModule local
CacheSize 10000 MB # Working dir max
MaxForks 10
MaxForksPerHost 10
ACL Allow * - *

```


My question: what is wrong :confused:

Many thanks,
Kris

---

