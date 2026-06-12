---
title: "Firewall Issue"
date: 2009-10-29
forum: Security
---

### Post by Drezard on 2009-10-29
I'm having problems with an iptables firewall.  I've got this running as part of my /etc/rc.local:

```


IPTABLES="/sbin/iptables"

# Clear all old iptables rules
$IPTABLES -F
$IPTABLES -F INPUT
$IPTABLES -F OUTPUT
$IPTABLES -F FORWARD
$IPTABLES -F -t mangle
$IPTABLES -F -t nat
$IPTABLES -X

# DropWall Chain
# Used only when something is dropped
$IPTABLES -N DROPWALL
$IPTABLES -A DROPWALL -m limit --limit 15/minute -j LOG --log-prefix
"Packet Dropped: "
$IPTABLES -A DROPWALL -j DROP

# DoS Chain
# Used only when too many connections come in
$IPTABLES -N DOS
$IPTABLES -A DOS -m limit --limit 25/minute -j LOG --log-prefix "DOS Detected: "
$IPTABLES -A DOS -j DROP

# BadFlags Chain
# Used only when packets come in with a bad tcp header
$IPTABLES -N BADFLAGS
$IPTABLES -A BADFLAGS -m limit --limit 15/minute -j LOG --log-prefix
"Bad Flags: "
$IPTABLES -A BADFLAGS -j DROP

# Silent Chain
# Silent drop chain, no logging
$IPTABLES -N SILENT
$IPTABLES -A SILENT -j DROP

# AcceptWall Chain
# Used when something is accepted
$IPTABLES -N ACCEPTWALL
$IPTABLES -A ACCEPTWALL -m limit --limit 100/minute -j LOG
--log-prefix "Accept Connection: "
$IPTABLES -A ACCEPTWALL -j ACCEPT

# Create the INPUT table
# Accept traffic from loopbacks
$IPTABLES -A INPUT -i lo -j ACCEPT
$IPTABLES -A INPUT -d 127.0.0.1 -j ACCEPT
$IPTABLES -A INPUT -d 127.0.1.1 -j ACCEPT
- Hide quoted text -
$IPTABLES -A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
# Drop the incorrect tcp packets
$IPTABLES -A INPUT -p tcp --tcp-flags ALL FIN,URG,PSH -j BADFLAGS
$IPTABLES -A INPUT -p tcp --tcp-flags ALL ALL -j BADFLAGS
$IPTABLES -A INPUT -p tcp --tcp-flags ALL SYN,RST,ACK,FIN,URG -j BADFLAGS
$IPTABLES -A INPUT -p tcp --tcp-flags ALL NONE -j BADFLAGS
$IPTABLES -A INPUT -p tcp --tcp-flags SYN,RST SYN,RST -j BADFLAGS
$IPTABLES -A INPUT -p tcp --tcp-flags SYN,FIN SYN,FIN -j BADFLAGS
# Drop most ICMP msgs, but let a few through
$IPTABLES -A INPUT -p icmp --icmp-type 0 -j ACCEPTWALL
$IPTABLES -A INPUT -p icmp --icmp-type 3 -j ACCEPTWALL
$IPTABLES -A INPUT -p icmp --icmp-type 11 -j ACCEPTWALL
$IPTABLES -A INPUT -p icmp --icmp-type 8 -m limit --limit 1/second -j ACCEPTWALL
$IPTABLES -A INPUT -p icmp -j DROPWALL
# Drop the windows netbios ****
$IPTABLES -A INPUT -p udp --sport 137 --dport 137 -j SILENT
# Accept some connections
$IPTABLES -A INPUT -p tcp --dport 21 -j ACCEPTWALL
$IPTABLES -A INPUT -p tcp --dport 22 -j ACCEPTWALL
$IPTABLES -A INPUT -p tcp --dport 80 -j ACCEPTWALL
$IPTABLES -A INPUT -p tcp --dport 443 -j ACCEPTWALL
# Drop the rest of the ****
$IPTABLES -A INPUT -j DROPWALL

# Create the OUTPUT Table
$IPTABLES -A OUTPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
$IPTABLES -A OUTPUT -p tcp --dport 20 -j ACCEPTWALL
$IPTABLES -A OUTPUT -p tcp --dport 21 -j ACCEPTWALL
$IPTABLES -A OUTPUT -p tcp --dport 25 -j ACCEPTWALL
$IPTABLES -A OUTPUT -p tcp --dport 80 -j ACCEPTWALL
$IPTABLES -A OUTPUT -p tcp --dport 443 -j ACCEPTWALL
$IPTABLES -A OUTPUT -p udp --dport 53 -j ACCEPTWALL
$IPTABLES -A OUTPUT -j DROPWALL

```

This script runs perfectly and protects the system. But when I close down the server, it hangs on this part of the shutdown:

> 
Stopping portmap daemon...


It just sits there for about 10 - 15 minutes then shuts down correctly. 

Any ideas?

---

### Post by Drezard on 2009-10-29
I know portmap is a part of nfs and I can just do a:

> 
apt-get remove nfs-common


and get rid of nfs. What do I have to unblock to be able to stop it hanging on shutdown... I don't want to have to block nfs to everyone though.

Any ideas?

---

