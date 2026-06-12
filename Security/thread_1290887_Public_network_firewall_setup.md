---
title: "Public network firewall setup"
date: 2009-10-14
forum: Security
---

### Post by dvlchd3 on 2009-10-14
Hello all.  My favorite coffee shop recently caught some heat because of malicious activity originating from their network.  That coffee shop then asked for my advice (I am there pretty much everyday...).  I figured their best option would be to setup a server that forces users to fill-out a registration page before then can browse anything outside of the network.  Then, utilize snort to monitor any malicious looking activity.  This way, we would have a name to go with an ip/mac address.

Anyway, I'm pretty sure I have the majority covered, however, I need some advice on how to setup the firewall on this machine.  I have to have two-sided protection.  I don't want this person or persons to be able to gain access to the router and bypass all the security measures.

I'm generally familiar with iptables, however, I have always used Robert Ziegler's firewall script, and modified it to my liking.  Looking through this script, it seems to focus most of its attention around outside attacks.  Are there any things I can do to strengthen the security inside as well?

Just some points in the right direction would be extremely helpful.

[http://audiophile.tam.cornell.edu/~dm68/Computer/Security/TAMFirewall/rc.firewall](http://audiophile.tam.cornell.edu/~dm68/Computer/Security/TAMFirewall/rc.firewall)

---

### Post by __p1n__ on 2009-10-14
Can you define "malicious activity" a bit?  If you're referring to network traffic involving torrents then you might want to forego the whole registration thing and just packet-shape egress traffic.

I'm not certain however if the registration approach would be effective.  AP-based mac filtering and passphrases are trivially defeatable in a starbucks type setting as long as there is one legitimate user around.

---

### Post by dvlchd3 on 2009-10-14
Malicious activity meaning 3 or 4 different attacks to several external places.  This includes port scans, brute force, and DoS attacks.  (At least this is how it appears from snort logs)  It seems that these hosts blocked the entire block of ip addresses, and the coffee shop's ISP called them and said they needed to take preventive measures, or they would be dropped.

I don't really care about bit torrents and other p2p stuff.  Potential for viruses doesn't really bother me.  However, having the ISP stop service, or customers of the coffee shop not being able to access certain services, is a problem.

My only real challenge is learning how to filter ports inside and outside of the network on the router.  I'm not really sure the current script protects from internal attacks, of course, I could be completely wrong...

---

### Post by __p1n__ on 2009-10-14
Try protocol filtering, rate limiting, fragment blocking (all supported by the iptables interface to netfiler.)  You should be able to deal with the outgoing DoS and portscans that way.

---

### Post by update_manager on 2009-10-16
> **dvlchd3 said:**
> Hello all.  My favorite coffee shop recently caught some heat because of malicious activity originating from their network.  That coffee shop then asked for my advice (I am there pretty much everyday...).  I figured their best option would be to setup a server that forces users to fill-out a registration page before then can browse anything outside of the network.  Then, utilize snort to monitor any malicious looking activity.  This way, we would have a name to go with an ip/mac address.

Anyway, I'm pretty sure I have the majority covered, however, I need some advice on how to setup the firewall on this machine.  I have to have two-sided protection.  I don't want this person or persons to be able to gain access to the router and bypass all the security measures.

I'm generally familiar with iptables, however, I have always used Robert Ziegler's firewall script, and modified it to my liking.  Looking through this script, it seems to focus most of its attention around outside attacks.  Are there any things I can do to strengthen the security inside as well?

Just some points in the right direction would be extremely helpful.

[http://audiophile.tam.cornell.edu/~dm68/Computer/Security/TAMFirewall/rc.firewall](http://audiophile.tam.cornell.edu/~dm68/Computer/Security/TAMFirewall/rc.firewall)

This script seems really old (ipchains?) and adds blackhole routes for some reason.

This might get you started. You can add custom rules to the "# protect the network" part, like:
iptables -A FORWARD -p tcp --dport 5900:5910 -j DROP
iptables -A FORWARD -s 10.0.0.0/8 -j DROP
etc

You might want to look at fwsnort for clues on whats going on - [http://www.cipherdyne.org/fwsnort/](http://www.cipherdyne.org/fwsnort/)

#!/bin/bash

LAN="eth0"
WAN="eth1"

iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP

# allow localhost
iptables -I INPUT -s 127.0.0.1 -d 127.0.0.1 -j ACCEPT

# allow SSH
iptables -A INPUT -p tcp -m multiport --dport 22 -j ACCEPT

# create a new chain that will log and reject 
iptables -N rlog
iptables -A rlog -j LOG
iptables -A rlog -j REJECT

# using the new chain
# protect the server 
iptables -A INPUT -p tcp -m multiport --dport 445 -j rlog
iptables -A INPUT -p udp -m multiport --dport 137:139,445,631,5353 -j rlog
iptables -A OUTPUT -p udp -m multiport --dport 137:139,445,631,5353 \
-j rlog

# protect the network
iptables -A FORWARD -p udp -m multiport --dport 137:139,445,5353 -j rlog
iptables -A FORWARD -p tcp -m multiport --dport 3389,5900 -j rlog

# drop obviously bad traffic
iptables -A INPUT -p TCP --tcp-flags ALL FIN,URG,PSH -j DROP
iptables -A INPUT -p TCP --tcp-flags ALL SYN,RST,ACK,FIN,URG -j DROP
iptables -A INPUT -p TCP --tcp-flags SYN,RST SYN,RST -j DROP
iptables -A INPUT -p TCP --tcp-flags SYN,FIN SYN,FIN -j DROP
iptables -A INPUT -p TCP --tcp-flags SYN,ACK NONE -j DROP
iptables -A INPUT -p TCP --tcp-flags RST,FIN RST,FIN -j DROP
iptables -A INPUT -p TCP --tcp-flags SYN,URG SYN,URG -j DROP
iptables -A INPUT -p TCP --tcp-flags ALL SYN,PSH -j DROP
iptables -A INPUT -p TCP --tcp-flags ALL SYN,ACK,PSH -j DROP

# allow some ICMP, drop the rest
iptables -A INPUT -i $LAN -p udp -m multiport --dport 67,68 -j ACCEPT
iptables -A INPUT -p icmp --icmp-type destination-unreachable -j ACCEPT
iptables -A INPUT -p icmp --icmp-type source-quench -j ACCEPT
iptables -A INPUT -p icmp --icmp-type time-exceeded -j ACCEPT
iptables -A INPUT -p icmp --icmp-type parameter-problem -j ACCEPT
iptables -A INPUT -p icmp --icmp-type echo-request -j ACCEPT
iptables -A INPUT -p icmp --icmp-type echo-reply -j ACCEPT

iptables -A FORWARD -p icmp --icmp-type destination-unreachable -j ACCEPT
iptables -A FORWARD -p icmp --icmp-type source-quench -j ACCEPT
iptables -A FORWARD -p icmp --icmp-type time-exceeded -j ACCEPT
iptables -A FORWARD -p icmp --icmp-type parameter-problem -j ACCEPT
iptables -A FORWARD -p icmp --icmp-type echo-request -j ACCEPT
iptables -A FORWARD -p icmp --icmp-type echo-reply -j ACCEPT

iptables -A INPUT -p icmp -j DROP
iptables -A FORWARD -p icmp -j DROP

# allow forwarding and NAT
iptables -A FORWARD -p all -i $LAN -j ACCEPT
iptables -t nat -A POSTROUTING -o $WAN -j MASQUERADE

# stateful stuff
iptables -A INPUT -p all -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -p all -m state --state ESTABLISHED,RELATED -j ACCEPT

# allow all output
iptables -A OUTPUT -p all -j ACCEPT

---

### Post by dvlchd3 on 2009-10-17
My apologies.  That link doesn't not accurately represent the script I'm using.  I attempted to upload my current script, however, it was too big.  That was just my attempt at finding a link to a script that was close to mine.  I have compressed and uploaded my current script.  It does not use ipchains, and seems similar to the one posted above.  I obtained it from my father a year or so ago.  There are items in there he has added, commented out, edited, etc.  I have also done the same.

---

