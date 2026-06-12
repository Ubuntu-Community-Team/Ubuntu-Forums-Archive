---
title: "A few questions about iptables and a request to review my current rules"
date: 2008-07-11
forum: Security
---

### Post by niksun on 2008-07-11
Hi,

I've been using Ubuntu for several years now as a desktop machine running only a few services (bind, apache, sshd, vnc); actually, I only allow VNC through an SSH tunnel.  I have been using Firestarter as the frontend to iptables since the beginning, but have recently been interested in delving into the iptables world.  My default firewall policy is to allow all outgoing traffic (I trust my only user...myself), but to deny all incoming (other than established or related connections) and forwarded traffic.

I've heard about the kernel sysctl parameters (namely the net/ipv4 ones), but I'm not sure what's best for a typical desktop machine offering a few simple services for friends and family.  I've also heard about multicast traffic but don't quite understand it and if I should block or allow it, and whether ICMP traffic should be blocked or allowed (and there's a huge debate about whether to allow ping reply and such).

OK.  To my question (sorry to be so long-winded).  I am providing my current iptables rules (in the form of a simple bash script) for your perusal and review.  Please let me know what you think, if any improvements should be made, etc.  Perhaps there are glaring errors that I've missed.  I'd very much appreciate your opinion.  Also, if you like it and want to use it, please feel free to do so!

First, the main firewall, containing most rules (btw, the allow_from and disallow_from files are just lists of IP addresses to allow/disallow all traffic from):

```
#!/bin/bash
##############################
# Firewall configuration file
##############################

# executable file paths
IPT=/sbin/iptables
IFC=/sbin/ifconfig
MPB=/sbin/modprobe
LSM=/sbin/lsmod
RMM=/sbin/rmmod
SYSCTL=/sbin/sysctl

# configuration file paths
SYSCTL_SETTINGS=sysctl.conf
ALLOW_FROM=allow_from
ALLOW_SERVICES=allow_services
DISALLOW_FROM=disallow_from

# network interfaces (external and internal)
EXTIF="wlan0"
LPBIF="lo"

# other useful variables
ANY="0/0"
VNC_UID="myuserid"

# get the network info
IP=`$IFC $EXTIF | grep inet | cut -d : -f 2 | cut -d \  -f 1`
BCAST=`$IFC $EXTIF | grep Bcast | cut -d : -f 3 | cut -d \  -f 1`
MASK=`$IFC $EXTIF | grep Mask | cut -d : -f 4`
NET=$IP/$MASK

if [ "$MASK" == "" -a "$1" != "stop" ]; then
	echo "External network interface $EXTIF is not ready; aborting."
	exit 0
fi

# first, let's remove the ipchains module (if found)
$LSM | grep ipchains -q -s && $RMM ipchains

# now, let's load all the modules we'll need
$MPB ip_tables 2>/dev/null
$MPB iptable_filter 2>/dev/null
$MPB ipt_state 2>/dev/null
$MPB ip_conntrack 2>/dev/null
$MPB ip_conntrack_ftp 2>/dev/null
$MPB ip_conntrack_irc 2>/dev/null
$MPB ipt_REJECT 2>/dev/null
$MPB ipt_TOS 2>/dev/null
$MPB ipt_MASQUERADE 2>/dev/null
$MPB ipt_LOG 2>/dev/null
$MPB iptable_mangle 2>/dev/null
$MPB ipt_ipv4optsstrip 2>/dev/null

# flush, delete, and zero all chains
$IPT -F
$IPT -Z
$IPT -X
$IPT -t mangle -F 2>/dev/null
$IPT -t mangle -Z 2>/dev/null
$IPT -t mangle -X 2>/dev/null
$IPT -t nat -F 2>/dev/null
$IPT -t nat -Z 2>/dev/null
$IPT -t nat -X 2>/dev/null

# drop all input and forwarded packets; accept all output packets
$IPT -P INPUT DROP
$IPT -P FORWARD DROP
$IPT -P OUTPUT ACCEPT

# setup specified kernel net sysctl parameters
source $SYSCTL_SETTINGS

# setup firewall logging
$IPT -N LOG_ACCEPT
$IPT -N LOG_REJECT
$IPT -N LOG_DROP

# allow all traffic on the loopback interface
$IPT -A INPUT -i $LPBIF -j ACCEPT

# hosts from which connections are ALWAYS allowed
while read host
do
	echo " $host (not logged)"
	$IPT -A INPUT -s $host -j ACCEPT
done < $ALLOW_FROM

# allow related/established input packets
$IPT -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT

# drop all invalid packets
$IPT -A INPUT -m state --state INVALID -j LOG_DROP
$IPT -A OUTPUT -m state --state INVALID -j LOG_DROP

# disallow specified ips
while read host
do
	$IPT -A INPUT -s $host -j LOG_REJECT
done < $DISALLOW_FROM

# allow specified services
source $ALLOW_SERVICES

# allow limited ICMP traffic (and furthermore limit to 10/s)
$IPT -A INPUT -p icmp --icmp-type destination-unreachable -m limit --limit 10/s -j LOG_ACCEPT
$IPT -A INPUT -p icmp --icmp-type source-quench -m limit --limit 10/s -j LOG_ACCEPT

# block traffic with excessive fragmented packets and don't log
$IPT -A INPUT -f -m limit --limit 10/minute -j DROP

# block traffic with stuffed routing (local intranet traffic from getting out which could be snooped!) and don't log
$IPT -A INPUT -s 255.255.255.255 -j DROP
$IPT -A INPUT -d 0.0.0.0 -j DROP
$IPT -A OUTPUT -s 255.255.255.255 -j DROP
$IPT -A OUTPUT -d 0.0.0.0 -j DROP

# drop packets going to broadcast or multicast addresses and don't log
$IPT -A INPUT -d 255.255.255.0/24 -j DROP
$IPT -A INPUT -d 224.0.0.0/8 -j DROP
# do the same for the hamachi subnet
$IPT -A INPUT -i ham0 -d 5.255.255.255 -j DROP

# the log catchall for all other incoming and forwarded traffic
$IPT -A INPUT -j LOG_DROP
$IPT -A FORWARD -j LOG_DROP

# handle logs
$IPT -A LOG_ACCEPT -j ULOG --ulog-prefix "*ACCEPT*" --ulog-cprange 0
$IPT -A LOG_ACCEPT -j ACCEPT
$IPT -A LOG_REJECT -j ULOG --ulog-prefix "*REJECT*" --ulog-cprange 0
$IPT -A LOG_REJECT -j REJECT
$IPT -A LOG_DROP -j ULOG --ulog-prefix "*DROP*" --ulog-cprange 0
$IPT -A LOG_DROP -j DROP

echo "*Firewall started"
exit 1

```

Now the kernel sysctl settings:

```
#!/bin/bash
######################################################################################
# Sysctl settings file
# Thanks to http://danieldegraaf.afraid.org/info/iptables/examples for some of these.
######################################################################################

# turn off IP forwarding
$SYSCTL -w net.ipv4.ip_forward=0 >/dev/null

# disable some potentially insecure ICMP settings
$SYSCTL -w net.ipv4.icmp_ignore_bogus_error_responses=1 >/dev/null
$SYSCTL -w net.ipv4.icmp_echo_ignore_all=1 >/dev/null
$SYSCTL -w net.ipv4.icmp_echo_ignore_broadcasts=1 >/dev/null
$SYSCTL -w net.ipv4.icmp_ratelimit=1000 >/dev/null
$SYSCTL -w net.ipv4.conf.all.accept_redirects=0 >/dev/null
$SYSCTL -w net.ipv4.conf.all.accept_source_route=0 >/dev/null
$SYSCTL -w net.ipv4.conf.all.rp_filter=1 >/dev/null
$SYSCTL -w net.ipv4.conf.all.log_martians=1 >/dev/null

# prevent SYN flood
$SYSCTL -w net.ipv4.tcp_syncookies=1 >/dev/null

# don't accept TCP connections unless we were here for their establishment
if [ -e /proc/sys/net/netfilter/ ]; then
	$SYSCTL -w net.netfilter.nf_conntrack_tcp_loose=0 >/dev/null
else
	$SYSCTL -w net.ipv4.ip_conntrack_tcp_loose=0 >/dev/null
fi
```

And finally, the separate services:

```
#!/bin/bash
##############################
# Services configuration file
##############################

# allow DNS (port 53) (bind)
$IPT -A INPUT -p tcp --dport 53 -j LOG_ACCEPT
$IPT -A INPUT -p udp --dport 53 -j LOG_ACCEPT

# allow web server (nonstandard port 4352) (apache)
$IPT -A INPUT -p tcp --dport 4352 -j LOG_ACCEPT

# allow SSH (nonstandard port 4884) from the following peers:
#  blahblah
#  hamachi subnet: 5.0.0.0/8 (we don't specify an interface so that we also include hamN)
# also limit SSH connections from the hamachi subnet to no more than three per minute to slow down scans
$IPT -N SSH
$IPT -A INPUT -p tcp --dport 4884 -j SSH
$IPT -A SSH -s blahblah -j LOG_ACCEPT
$IPT -A SSH -s 5.0.0.0/8 -m recent --update --hitcount 3 --seconds 60 --name SSHIN -j LOG_DROP
$IPT -A SSH -s 5.0.0.0/8 -m recent --set --name SSHIN -j LOG_ACCEPT
$IPT -A SSH -j LOG_DROP

# allow VNC but only by specified user already logged in via SSH (tunnel)
$IPT -A OUTPUT -o lo -p tcp --dport 5900 -m owner --uid-owner $VNC_UID -j LOG_ACCEPT
$IPT -A OUTPUT -o lo -p tcp --dport 5900 -j LOG_REJECT
```

Thanks a bunch!

---

