---
title: "iptables"
date: 2012-08-25
forum: Security
---

### Post by Loki57701 on 2012-08-25
I'm sort of new to writing iptables manually, so please bare with me here.

I wrote a script setup all my rules:

```
#/bin/bash

#############################################
#
# This script creates a basic firewall:
#
# Deny all incoming and outgoing
#
# Allow SSH and samba from the LAN in
# Allow NTP, HTTP, HTTPS, and DNS out


#############################################
# iptables location
#

IPT=/sbin/iptables

#############################################
# Flush all current rules from iptables
#

$IPT -F

#############################################
# Allow SSH from LAN
#

$IPT -A INPUT -s 192.168.1.0/24 -d 192.168.1.15 -m state --state NEW -p tcp --dport 22 -j ACCEPT

#############################################
# Set default policies for INPUT, FORWARD and OUTPUT chains
#

$IPT -P INPUT DROP
$IPT -P OUTPUT DROP
$IPT -P FORWARD DROP

#############################################
# Set access for localhost
#

$IPT -A INPUT -i lo -j ACCEPT

#############################################
# Allow NTP, DNS, HTTP, and HTTPS out
#

$IPT -A OUTPUT -m state --state NEW -p udp --dport 123 -j ACCEPT
$IPT -A OUTPUT -m state --state NEW -p udp --dport 53 -j ACCEPT
$IPT -A OUTPUT -m state --state NEW -p tcp --dport 443 -j ACCEPT
$IPT -A OUTPUT -m state --state NEW -p tcp --dport 80 -j ACCEPT

#############################################
# Allow samba server for LAN
#

$IPT -A INPUT -s 192.168.1.0/24 -d 192.168.1.15 -m state --state NEW -p udp --dport 137 -j ACCEPT
$IPT -A INPUT -s 192.168.1.0/24 -d 192.168.1.15 -m state --state NEW -p udp --dport 138 -j ACCEPT
$IPT -A INPUT -s 192.168.1.0/24 -d 192.168.1.15 -m state --state NEW -p tcp --dport 139 -j ACCEPT
$IPT -A INPUT -s 192.168.1.0/24 -d 192.168.1.15 -m state --state NEW -p udp --dport 445 -j ACCEPT
$IPT -A INPUT -s 192.168.1.0/24 -d 192.168.1.15 -m state --state NEW -p tcp --dport 445 -j ACCEPT

#############################################
# Allow ping request/reply on LAN, Allow ping request to internet from host
#

$IPT -A INPUT -s 192.168.1.0/24 -d 192.168.1.15 -p icmp -m state --state NEW,ESTABLISHED --icmp-type echo-reply -j ACCEPT
$IPT -A INPUT -s 192.168.1.0/24 -d 192.168.1.15 -p icmp -m state --state NEW,ESTABLISHED --icmp-type echo-request -j ACCEPT
$IPT -A OUTPUT -p icmp -m state --state NEW,ESTABLISHED --icmp-type echo-request -j ACCEPT

#############################################
# Open VNC to LAN
#

$IPT -A INPUT -s 192.168.1.0/24 -d 192.168.1.15 -m state --state NEW -p tcp --dport 5800  -j ACCEPT
$IPT -A INPUT -s 192.168.1.0/24 -d 192.168.1.15 -m state --state NEW -p tcp --dport 5900  -j ACCEPT
$IPT -A INPUT -s 192.168.1.0/24 -d 192.168.1.15 -m state --state NEW -p tcp --dport 6000  -j ACCEPT

#############################################
# Log anything on eth0 claiming it's from a local or non-routable network
#

$IPT -A INPUT -i eth0 -s 10.0.0.0/8 -j LOG --log-prefix "IP DROP SPOOF A: "
$IPT -A INPUT -i eth0 -s 172.16.0.0/12 -j LOG --log-prefix "IP DROP SPOOF B: "
$IPT -A INPUT -i eth0 -s 224.0.0.0/4 -j LOG --log-prefix "IP DROP MULTICAST D: "
$IPT -A INPUT -i eth0 -s 240.0.0.0/5 -j LOG --log-prefix "IP DROP SPOOF E: "
$IPT -A INPUT -i eth0 -d 127.0.0.0/8 -j LOG --log-prefix "IP DROP LOOPBACK: "

#############################################
# Accept packets belonging to established and related connections
#

$IPT -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPT -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

#############################################
# Save the current rules
#

/sbin/service iptables save 

exit 0
```

And when I run iptables -L I see an odd rule:  **ACCEPT     all  --  anywhere             anywhere**

```
Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  192.168.1.0/24       Odin.home           state NEW tcp dpt:ssh
**ACCEPT     all  --  anywhere             anywhere**
ACCEPT     udp  --  192.168.1.0/24       Odin.home           state NEW udp dpt:netbios-ns
ACCEPT     udp  --  192.168.1.0/24       Odin.home           state NEW udp dpt:netbios-dgm
ACCEPT     tcp  --  192.168.1.0/24       Odin.home           state NEW tcp dpt:netbios-ssn
ACCEPT     udp  --  192.168.1.0/24       Odin.home           state NEW udp dpt:microsoft-ds
ACCEPT     tcp  --  192.168.1.0/24       Odin.home           state NEW tcp dpt:microsoft-ds
ACCEPT     icmp --  192.168.1.0/24       Odin.home           state NEW,ESTABLISHED icmp echo-reply
ACCEPT     icmp --  192.168.1.0/24       Odin.home           state NEW,ESTABLISHED icmp echo-request
ACCEPT     tcp  --  192.168.1.0/24       Odin.home           state NEW tcp dpt:5800
ACCEPT     tcp  --  192.168.1.0/24       Odin.home           state NEW tcp dpt:vnc-server
ACCEPT     tcp  --  192.168.1.0/24       Odin.home           state NEW tcp dpt:x11
LOG        all  --  10.0.0.0/8           anywhere            LOG level warning prefix `IP DROP SPOOF A: '
LOG        all  --  172.16.0.0/12        anywhere            LOG level warning prefix `IP DROP SPOOF B: '
LOG        all  --  base-address.mcast.net/4  anywhere            LOG level warning prefix `IP DROP MULTICAST D: '
LOG        all  --  240.0.0.0/5          anywhere            LOG level warning prefix `IP DROP SPOOF E: '
LOG        all  --  anywhere             loopback/8          LOG level warning prefix `IP DROP LOOPBACK: '
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED

Chain FORWARD (policy DROP)
target     prot opt source               destination

Chain OUTPUT (policy DROP)
target     prot opt source               destination
ACCEPT     udp  --  anywhere             anywhere            state NEW udp dpt:ntp
ACCEPT     udp  --  anywhere             anywhere            state NEW udp dpt:domain
ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:https
ACCEPT     tcp  --  anywhere             anywhere            state NEW tcp dpt:http
ACCEPT     icmp --  anywhere             anywhere            state NEW,ESTABLISHED icmp echo-request
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED

```

To me this looks like an allow everything rule that (I don't think) I defined in my script. 

I would appreciate any advice on this.

---

### Post by Doug S on 2012-08-25
Interesting. It seems that when you use "iptables -L" it prints a misleading line. If you use "iptables -L -n -x -v" instead you will see that that is the local interface line.
I entered your exact script on one of my test machines and ran it.
 
I don't understand your last command, and I took it our for my test.
 
O.K., now to go back and restore my test machine...

---

### Post by SeijiSensei on 2012-08-25
If you don't use the "-v" (verbose) switch, you won't see the interfaces to which the rules apply.  The rule you're concerned about probably applies to the localhost interface, lo.

---

### Post by Loki57701 on 2012-08-25
Thanks guys, you were right.

---

### Post by dfreer on 2012-08-27
> ```
#############################################
# Allow ping request/reply on LAN, Allow ping request to internet from host
#

$IPT -A INPUT -s 192.168.1.0/24 -d 192.168.1.15 -p icmp -m state --state NEW,ESTABLISHED --icmp-type echo-reply -j ACCEPT
$IPT -A INPUT -s 192.168.1.0/24 -d 192.168.1.15 -p icmp -m state --state NEW,ESTABLISHED --icmp-type echo-request -j ACCEPT
$IPT -A OUTPUT -p icmp -m state --state NEW,ESTABLISHED --icmp-type echo-request -j ACCEPT

```

You should be able to simplify this rule:
```

$IPT -A INPUT -s 192.168.1.0/24 -d 192.168.1.15 -p icmp -m state --state NEW --icmp-type echo-request -j ACCEPT
$IPT -A OUTPUT -p icmp -m state --state NEW --icmp-type echo-request -j ACCEPT

```
The INPUT allows only incoming PING requests from the LAN, the OUTPUT allows outgoing PING requests from the host to anywhere. No need for specifying that ESTABLISHED packets should be allowed, as you already cover ESTABLISHED/RELATED packets at the end of the script. Also no need for the incoming LAN echo replies, as those would be either ESTABLISHED or RELATED to your previous outgoing echo request.

Also, since you are using a bash script to write this, why not use a variable for the local LAN?
```

LANRANGE="192.168.1.0/24"
LANIP="192.168.1.15"
LANONLY="-s $LANRANGE -d $LANIP"

$IPT -A INPUT $LANONLY -p icmp -m state --state NEW --icmp-type echo-request -j ACCEPT
```

EDIT: Btw, this is a great ingress/egress firewall, very similiar to the way I would write my firewalls.

NINJA EDIT: Why do you allow incoming local loopback connections, but do not allow outgoing local loopback connections?

---

