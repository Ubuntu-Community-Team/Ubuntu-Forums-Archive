---
title: "Is my IPTables &quot;secure&quot; ?"
date: 2010-09-27
forum: Security
---

### Post by dlublink on 2010-09-27
Hello,

I have a server running a web server, dns server and SSH server. I tried to write a nice firewall that was as secure as possible.

My idea is to cover as many ip based attacks as possible ( DDoS is not covered by this, DoS attack on DNS and SSH should be covered as well as brute force on SSH ).

I have included below a copy of my config, can anyone give me feedback ? Is this good, bad, could I improve it? 

( advice : please don't copy anything from this script until feedback has validated it's quality ).

Thanks,

David

```

#!/bin/sh

INTERNET="eth0"
IPTABLES="iptables"
LAN="eth1"

# Flush all chains
$IPTABLES --flush

# Loopback is un firewalled
$IPTABLES -A INPUT -i lo -j ACCEPT
$IPTABLES -A OUTPUT -o lo -j ACCEPT

# Allow unlimited local traffic
$IPTABLES -A INPUT -i $LAN -j ACCEPT
$IPTABLES -A OUTPUT -o $LAN -j ACCEPT

# Allow follow up requests
$IPTABLES -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
$IPTABLES -A OUTPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

# Throttle inbound ssh connections 
$IPTABLES -I INPUT -p tcp --dport 22 -i eth0 -m state --state NEW -m recent --set
# Drop packets after second attempt ( 3rd try fails )
$IPTABLES -I INPUT -p tcp --dport 22 -i eth0 -m state --state NEW -m recent --update --seconds 60 --hitcount 2 -j DROP

# Allow incoming port 22 (ssh) connections from internet
$IPTABLES -A INPUT -i $INTERNET -p tcp --destination-port 22 -m state --state NEW -j ACCEPT

# DNS Rate limiter ( DoS protection )
$IPTABLES -I INPUT -p tcp --dport 53 -i eth0 -m state --state NEW -m recent --set
$IPTABLES -I INPUT -p udp --dport 53 -i eth0 -m state --state NEW -m recent --set
$IPTABLES -I INPUT -p udp --dport 53 -i eth0 -m state --state NEW -m recent --update --seconds 30 --hitcount 10 -j DROP
$IPTABLES -I INPUT -p udp --dport 53 -i eth0 -m state --state NEW -m recent --update --seconds 30 --hitcount 10 -j DROP


# Services :

# Allow DNS resolution and zone transfers with primary server
$IPTABLES -A INPUT -i $INTERNET -p udp --destination-port 53 -j ACCEPT
$IPTABLES -A INPUT -i $INTERNET -p udp --source-port 53 -j ACCEPT
$IPTABLES -A INPUT -i $INTERNET -p tcp --destination-port 53 -j ACCEPT
$IPTABLES -A INPUT -i $INTERNET -p tcp --source-port 53 -j ACCEPT

$IPTABLES -A OUTPUT -o $INTERNET -p udp --source-port 53 -j ACCEPT
$IPTABLES -A OUTPUT -o $INTERNET -p udp --destination-port 53 -j ACCEPT
$IPTABLES -A OUTPUT -o $INTERNET -p tcp --source-port 53 -j ACCEPT
$IPTABLES -A OUTPUT -o $INTERNET -p tcp --destination-port 53 -j ACCEPT

# Allow web ( http and https )
$IPTABLES -A INPUT -i $INTERNET -p tcp --destination-port 80 -m state --state NEW -j ACCEPT
$IPTABLES -A INPUT -i $INTERNET -p tcp --destination-port 443 -m state --state NEW -j ACCEPT

# allow outbound secure web
$IPTABLES -A OUTPUT -o $INTERNET -p tcp --destination-port 443 -m state --state NEW -j ACCEPT


iptables --policy INPUT DROP
iptables --policy FORWARD DROP
iptables --policy OUTPUT DROP



```

---

### Post by emiller12345 on 2010-09-27
I have to assume that your intent is to use this as a bridge/router seeing as you have two interfaces (INTERNET and LAN).  If you want to allow packets to travel from one interface to another, you'll need to add a rule or two using the FORWARD table.  To open the flood gates:
i.e. 
$IPTABLES -A FORWARD -i $INTERNET -o $LAN -p tcp -m tcp --sport 80 -m state --state ESTABLISHED -j ACCEPT
$IPTABLES -A FORWARD -i $LAN -o $INTERNET -p tcp -m tcp --dport 80 -m state --state NEW,ESTABLISHED -j ACCEPT
 
This is really not that secure, but would allow clients to view HTTP data to flow in through your bridge/router.  You can make a more secure by making the rules more restrictive. It also may be good to randomize your outgoing source ports if you decided to NAT the bridge/router.Try not to think of a firewall as either secure or not secure.  Its always going to be somewhere in between.

---

### Post by HermanAB on 2010-09-28
Hmm, you also need to think whether you really need any of those rules.  The modern IP stack of Linux is very robust, which is why Ubuntu has no additional IP Tables rules by default.

I have many web and mail servers online, with *NO* additional rules in IP Tables and they have been doing fine for years.

---

