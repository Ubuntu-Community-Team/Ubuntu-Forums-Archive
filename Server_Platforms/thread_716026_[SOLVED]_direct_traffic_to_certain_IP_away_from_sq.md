---
title: "[SOLVED] direct traffic to certain IP away from squid, IPTABLES, SQUID, APACHE"
date: 2008-03-05
forum: Server Platforms
---

### Post by twistedtwig on 2008-03-05
OK,

so that title is not great!!!

A little about my setup.  I have a linux box as my main server, does dhcp, dns, IPtables firewall, apache etc.

I have a windows 2003 server inside the network.  the linux box uses proxypassreverse inside apache to forward part of my site to this box which works fine.

the problem is that I just installed squid as a transparent proxy server on the linux box.  Now now one can see the windows box.  I presume this is because all port 80 traffic for the internal interface on the linux box is getting routed to 3128 rather than going back to apache.

I am not great with IPTables and have no idea where to start with this.  I presume I need a rule to say all port 80 traffic coming in and out should stay on port 80.  all else can carry on as normal.

Is this even possible?

my iptables file is as follows:

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
$IPTABLES -t nat -A PREROUTING -i $INTIF -p tcp --dport 80 -j REDIRECT --to-port 3128
echo "   Opening port 1723 for VPN initiation."
$IPTABLES -A INPUT -i $EXTIF -p TCP --dport 1723 -j ACCEPT
$IPTABLES -I INPUT -p TCP -m state --state NEW -m limit --limit 6/minute --limit-burst 5 -j ACCEPT
$IPTABLES -A INPUT -i ppp+ -j ACCEPT
$IPTABLES -A FORWARD -i ppp+ -o $INTIF -j ACCEPT
$IPTABLES -A FORWARD -i $INTIF -o ppp+ -j ACCEPT

```

the windows box IP is 192.168.10.101 (static IP).

Thank you for any and all advice and help

---

### Post by twistedtwig on 2008-03-05
it would seem that it might not be squid.  Well it might be that as well.

But something has gone rather wrong in my IPtables firewall.

I can no longer route from the server to internal IP's.  I.e. if I vnc onto the server and go to firefox it can not open web pages on either of my webservers inside the network.  it can get to google just fine though.

I do not know whats wrong with it to be honest.  I am going to have to have a good look at it now, but I am not great with this.  any and all help would be amazing!!!

Thanks

---

### Post by twistedtwig on 2008-03-08
figured it out.. was my firewall.  I had corrected, what I thought was a typo (well it was), but I put the wrong interface in it.

---

