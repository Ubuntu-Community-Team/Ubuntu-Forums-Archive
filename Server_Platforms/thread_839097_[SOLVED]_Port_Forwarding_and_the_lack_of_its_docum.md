---
title: "[SOLVED] Port Forwarding and the lack of its documentation"
date: 2008-06-24
forum: Server Platforms
---

### Post by Doughsay on 2008-06-24
I've been tearing my hair out over this guys...  I cant seem to find much if any good documentation or tutorials or examples of simple port forwarding on an ubuntu server.

I have an Ubuntu router.  Two interfaces: eth0 is internal, eth1 is external.  I have installed the ipmasq package to enable masquerading/NAT and everything works great.  Except that I can't forward ports.

I've tried various combination of cryptic iptables commands and nothing ever works.

Latest attempt (and a lot of people seem to have it working fine with this):
```
sudo iptables -A FORWARD -i eth1 -o eth0 -p tcp --dport 8580 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
sudo iptables -A PREROUTING -t nat -p tcp -d xx.xx.xx.xx --dport 8580 -j DNAT --to 192.168.0.5:8580
```

This doesn't work.  Iptables takes the commands just fine, no errors.  But I still can't access the internal webserver from outside.  And I just don't know why.  This port is NOT being blocked by my ISP, I've tested it...  What else could be stopping this???

I'm sorry, but it's late and I've been aggravated at this all day.:(

---

### Post by windependence on 2008-06-24
Well I have to admit, I never liked IPchains or IPtables. When I build a router/firewall I use OpenBSD and pf. Much easier.

How did you test the port from the outside? What happens if you simply drop the firewall, can you access it then?

What is the output of:

```
sudo ufw status
```

-Tim

---

### Post by Doughsay on 2008-06-24
Hi thanks for the reply.  I used OpenBSD once myself, but didn't use it enough to really get familiar with packet filter anyway...

I tested the port by SSHing into a remote server and using lynx to try and get to the webserver.  Running Apache on my router box on port 8580 works fine, but trying to forward that port to my internal server doesn't work, like I said.

ufw is disabled.

Ok so I did some testing.  When running ipmasq, the commands I previously posted do not work.  BUT, they do work, if i disable ipmasq and set up iptables myself with this script I hacked together from somewhere.

```
echo "1" > '/proc/sys/net/ipv4/ip_forward'

IPTABLES=/sbin/iptables
EXTIF=eth1
INTIF=eth0
EXTIP=xx.xx.xx.xx

$IPTABLES -P INPUT ACCEPT
$IPTABLES -F INPUT 
$IPTABLES -P OUTPUT ACCEPT
$IPTABLES -F OUTPUT 
$IPTABLES -P FORWARD DROP
$IPTABLES -F FORWARD 
$IPTABLES -t nat -F

$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPTABLES -A FORWARD -i $INTIF -o $EXTIF -j ACCEPT
$IPTABLES -A FORWARD -j LOG

$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j MASQUERADE

$IPTABLES -A FORWARD -i $EXTIF -o $INTIF -p tcp --dport 8580 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPTABLES -A PREROUTING -t nat -p tcp -d $EXTIP --dport 8580 -j DNAT --to 192.168.0.5:8580
```

I just don't know iptables well enough.  Is this good enough?  can I just run this at system startup?  I wanted to trust ipmasq, I'm sure it does a lot more than just this...  But I can't get the forwarding to work together with ipmasq.

---

### Post by kevdog on 2008-06-24
Here is a skeleton script that I used in the past.  Feel free to modify for your needs.  I'm not sure its all you need however:

```

#!/bin/sh
#
#############################################################################
#
# File: iptables.sh
#
# Purpose: To build a basic iptables policy with default log and drop rules.
#          This script was written for the book "Linux Firewalls: Attack
#          Detection and Response" published by No Starch Press.
#
# Copyright (C) 2006-2007 Michael Rash (mbr@cipherdyne.org)
#
# License (GNU Public License):
#
#   This program is distributed in the hope that it will be useful,
#   but WITHOUT ANY WARRANTY; without even the implied warranty of
#   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#   GNU General Public License for more details.
#
#   You should have received a copy of the GNU General Public License
#   along with this program; if not, write to the Free Software
#   Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA  02111-1307
#   USA
#
#
#############################################################################
#
# $Id: index.html 1706 2008-06-20 02:37:29Z mbr $
#

IPTABLES=/sbin/iptables
MODPROBE=/sbin/modprobe
INT_NET=192.168.10.0/24

### flush existing rules and set chain policy setting to DROP
echo "[+] Flushing existing iptables rules..."
$IPTABLES -F
$IPTABLES -F -t nat
$IPTABLES -X
$IPTABLES -P INPUT DROP
$IPTABLES -P OUTPUT DROP
$IPTABLES -P FORWARD DROP

### load connection-tracking modules
#
$MODPROBE ip_conntrack
$MODPROBE iptable_nat
$MODPROBE ip_conntrack_ftp
$MODPROBE ip_nat_ftp

###### INPUT chain ######
#
echo "[+] Setting up INPUT chain..."

### state tracking rules
$IPTABLES -A INPUT -m state --state INVALID -j LOG --log-prefix "DROP INVALID " \
--log-ip-options --log-tcp-options
$IPTABLES -A INPUT -m state --state INVALID -j DROP
$IPTABLES -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

### anti-spoofing rules
$IPTABLES -A INPUT -i eth1 -s ! $INT_NET -j LOG --log-prefix "SPOOFED PKT "
$IPTABLES -A INPUT -i eth1 -s ! $INT_NET -j DROP

### ACCEPT rules
$IPTABLES -A INPUT -i eth1 -p tcp -s $INT_NET --dport 22 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A INPUT -p icmp --icmp-type echo-request -j ACCEPT

### default INPUT LOG rule
$IPTABLES -A INPUT -i ! lo -j LOG --log-prefix "DROP " --log-ip-options --log-tcp-options

###### OUTPUT chain ######
#
echo "[+] Setting up OUTPUT chain..."

### state tracking rules
$IPTABLES -A OUTPUT -m state --state INVALID -j LOG --log-prefix "DROP INVALID " \
--log-ip-options --log-tcp-options
$IPTABLES -A OUTPUT -m state --state INVALID -j DROP
$IPTABLES -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

### ACCEPT rules for allowing connections out
$IPTABLES -A OUTPUT -p tcp --dport 21 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 22 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 25 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 43 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 80 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 443 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 4321 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 53 -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p udp --dport 53 -m state --state NEW -j ACCEPT
$IPTABLES -A OUTPUT -p icmp --icmp-type echo-request -j ACCEPT

### default OUTPUT LOG rule
$IPTABLES -A OUTPUT -o ! lo -j LOG --log-prefix "DROP " --log-ip-options --log-tcp-options

###### FORWARD chain ######
#
echo "[+] Setting up FORWARD chain..."

### state tracking rules
$IPTABLES -A FORWARD -m state --state INVALID -j LOG --log-prefix "DROP INVALID " \
--log-ip-options --log-tcp-options
$IPTABLES -A FORWARD -m state --state INVALID -j DROP
$IPTABLES -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT

### anti-spoofing rules
$IPTABLES -A FORWARD -i eth1 -s ! $INT_NET -j LOG --log-prefix "SPOOFED PKT "
$IPTABLES -A FORWARD -i eth1 -s ! $INT_NET -j DROP

### ACCEPT rules
$IPTABLES -A FORWARD -p tcp -i eth1 -s $INT_NET --dport 21 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A FORWARD -p tcp -i eth1 -s $INT_NET --dport 22 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A FORWARD -p tcp -i eth1 -s $INT_NET --dport 25 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A FORWARD -p tcp -i eth1 -s $INT_NET --dport 43 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A FORWARD -p tcp --dport 80 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A FORWARD -p tcp --dport 443 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A FORWARD -p tcp -i eth1 -s $INT_NET --dport 4321 --syn -m state --state NEW -j ACCEPT
$IPTABLES -A FORWARD -p tcp --dport 53 -m state --state NEW -j ACCEPT
$IPTABLES -A FORWARD -p udp --dport 53 -m state --state NEW -j ACCEPT
$IPTABLES -A FORWARD -p icmp --icmp-type echo-request -j ACCEPT

### default LOG rule
$IPTABLES -A FORWARD -i ! lo -j LOG --log-prefix "DROP " --log-ip-options --log-tcp-options

###### NAT rules ######
#
echo "[+] Setting up NAT rules..."
$IPTABLES -t nat -A PREROUTING -p tcp --dport 80 -i eth0 -j DNAT --to 192.168.10.3:80
$IPTABLES -t nat -A PREROUTING -p tcp --dport 443 -i eth0 -j DNAT --to 192.168.10.3:443
$IPTABLES -t nat -A PREROUTING -p udp --dport 53 -i eth0 -j DNAT --to 192.168.10.4:53
$IPTABLES -t nat -A POSTROUTING -s $INT_NET -o eth0 -j MASQUERADE

###### forwarding ######
#
echo "[+] Enabling IP forwarding..."
echo 1 > /proc/sys/net/ipv4/ip_forward

exit
### EOF ###

```

---

### Post by Doughsay on 2008-06-24
What does this script assume eth0 and eth1 are?

edit:
I really just wanted to know how to get port forwarding working together with ubuntu's ipmasq package.  I like the way the rules are organized, it seems secure:

```

$ ls /etc/ipmasq/rules/
A00path.def             A03flush.def      I10lo.def        I90external.def  O32intmcast.def       Z99ipmasqrules.def
A00sanitycheck.def      A04functions.def  I15lospoof.def   M00chain.rul     O70masq.def           ZZYdenyigmp.def
A01interfaces.def       C00chain.rul      I30intbcast.def  M70masq.def      O90extbcast.def       ZZZdenyandlog.def
A01mungeexternal.def    F00chain.rul      I30internal.def  O00chain.rul     O90external.def
A01precompute.def       F10portfw.rul     I32intmcast.def  O10lo.def        S00chain.rul
A02masqmethod.def       F30internal.def   I70masq.def      O30intbcast.def  Z90kernelforward.def
A02unkernelforward.def  I00chain.rul      I90extbcast.def  O30internal.def  Z92timeouts.def

```

I added just that one file "F10portfw.rul" and I want it to contain all my port forwarding rules.  I see a couple of people on the internet doing it this way, but I just can't get it to work...

I want that file to look something like this:
```

port=8580
box=192.168.0.5

$IPTABLES -A FORWARD -p tcp -d $EXTIP --dport $port -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
$IPTABLES -A PREROUTING -t nat -p tcp -d $EXTIP --dport $port -j DNAT --to-destination $box:$port

```

But some other rule somewhere or something is letting this not work the way it should.

---

### Post by Doughsay on 2008-06-28
After many hours of searching and messing around with stuff, I finally got port forwarding to work together with ipmasq.

To me this seems like such a common practice, that I don't understand why there isn't more documentation and help for this sort of thing.  So I will include here how I did it hoping that it will help others.  Maybe I should also post this on the wiki or somewhere...

So my router has a pretty standard setup:
Ubuntu 8.04
two NICs: eth0 is internal, eth1 is external
running ipmasq for general router iptables setup

I added a .rul file: /etc/ipmasq/rules/F10portfw.rul
```

# Forwards ports from external internet to internal network
# Assumes $EXTERNAL and $INTERNAL are each just one interface
# Assumes you're using iptables
ipnm_cache $EXTERNAL

forward()
{
        port=$2
        box=$3
        for proto in $1
        do
                $IPTABLES -A FORWARD -i $EXTERNAL -o $INTERNAL -p $proto --dport $port -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
                $IPTABLES -A PREROUTING -t nat -p $proto -d $IPOFIF --dport $port -m state --state NEW,ESTABLISHED,RELATED -j DNAT --to $box:$port
        done
}

# usage:
# forward proto port destination
# proto can be "tcp", "udp", or "'tcp udp'" for both
forward tcp 8580 192.168.0.5
forward 'tcp udp' 56896 192.168.0.198

```

---

### Post by needtosearchforum on 2009-05-11
oh yes! this was exactly what i was looking for. such a shame "port forwarding" is so hidden in ipmasq.

works perfectly! thanks!

---

