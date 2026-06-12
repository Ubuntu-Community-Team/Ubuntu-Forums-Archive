---
title: "iptables and squid (transparent)"
date: 2007-08-01
forum: Server Platforms
---

### Post by Kyorisu on 2007-08-01
I have the following setup.

[IMG]http://img444.imageshack.us/img444/6626/examplecv0.jpg[/IMG]

The server is running squid and squid seems to be working fine, I have my browser directed through it right now and transparency is working fine (will not work unless I set firefox to use a proxy). My issue comes with iptables.

As I said I can get transparency working but when I do I haven't a clue as to how I did it. I've been trying to use the following as a guide.

[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)

Basically I want to let all traffic through (ie https, ftp, etc) and cache http on the squid box. 

My firewall as follow, this is obviously not setup to route traffic through the squid proxy. I need to know what rule to use to get that happening.

```
#!/bin/bash

# No spoofing
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 1 > $filtre
done
fi

# No icmp
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

#load some modules you may need
modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe iptable_filter
modprobe iptable_nat

# Remove all rules and chains
iptables -F
iptables -X

# first set the default behaviour => accept connections
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

# Create 2 chains, it allows to write a clean script
iptables -N FIREWALL
iptables -N TRUSTED

# Allow ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
# Allow loopback access
iptables -A FIREWALL -i lo -j ACCEPT
# Send all package to the TRUSTED chain
iptables -A FIREWALL -j TRUSTED

# Send all INPUT packets to the FIREWALL chain
iptables -A INPUT -j FIREWALL
# DROP all forward packets, we don't share internet connection in this example
iptables -A FORWARD -j DROP

# Forward only established and related connections to the lan for incoming packets iptables -A FORWARD -i eth1 -o eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT 
# Forward all OUT connections from the lan 
iptables -A FORWARD -o eth1 -i eth0 -j ACCEPT 
# hide computers behind the firewall 
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE 
echo 1 > /proc/sys/net/ipv4/ip_forward 
# then DROP all the rest 
iptables -A FORWARD -j DROP

# Allow SSH
iptables -A TRUSTED -i eth1 -p tcp -m tcp --dport 22 -j ACCEPT
iptables -A TRUSTED -i eth1 -p udp -m udp --dport 22 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 22 -j ACCEPT
iptables -A TRUSTED -i eth0 -p udp -m udp --dport 22 -j ACCEPT
# Allow FTP
iptables -A INPUT -i eth0 -p tcp -m tcp --sport 21 -m state --state ESTABLISHED -j ACCEPT
iptables -A INPUT -i eth0 -p tcp -m tcp --sport 20 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -i eth0 -p tcp -m tcp --sport 1024:65535 --dport 1024:65535 -m state --state ESTABLISHED -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp -m tcp --dport 21 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp -m tcp --dport 20 -m state --state ESTABLISHED -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp -m tcp --sport 1024:65535 --dport 1024:65535 -m state --state ESTABLISHED,RELATED -j ACCEPT

# Allow DNS
iptables -A INPUT -i eth0 -p udp -m udp --sport 53 -j ACCEPT
iptables -A OUTPUT -o eth0 -p udp -m udp --dport 53 -j ACCEPT
iptables -A INPUT -i eth0 -p tcp -m tcp --sport 53 -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp -m tcp --dport 53 -j ACCEPT

# Allow https
iptables -A TRUSTED -i eth0 -p udp -m udp --sport 443 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 443 -j ACCEPT

# Allow amule
iptables -A TRUSTED -i eth0 -p udp -m udp --dport 5349 -j ACCEPT
iptables -A TRUSTED -i eth0 -p udp -m udp --dport 5351 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 5348 -j ACCEPT

# Allow IRC IDENT & DCC
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 6667 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 113 -j ACCEPT

# Allow bittorrent
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 6881:6889 -j ACCEPT

# End message
echo " [End iptables rules setting]"

```

Any help is greatly appreciated.

---

### Post by frodon on 2007-08-01
Your FTP rules don't seem needed and you should remove all the "iptables -A FORWARD -j DROP" rules.

the following lines are also useless since you don't filter outgoing traffic :
```
iptables -A OUTPUT -o eth0 -p udp -m udp --dport 53 -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp -m tcp --dport 53 -j ACCEPT
```

Here is what i the modified file i suggest :
```
#!/bin/bash

# No spoofing
if [ -e /proc/sys/net/ipv4/conf/all/rp_filter ]
then
for filtre in /proc/sys/net/ipv4/conf/*/rp_filter
do
echo 1 > $filtre
done
fi

# No icmp
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_all
echo 1 > /proc/sys/net/ipv4/icmp_echo_ignore_broadcasts

# enable ip forward
echo 1 > /proc/sys/net/ipv4/ip_forward 

#load some modules you may need
modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe iptable_filter
modprobe iptable_nat

# Remove all rules and chains
iptables -F
iptables -X

# first set the default behaviour => accept connections
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

# Create 2 chains, it allows to write a clean script
iptables -N FIREWALL
iptables -N TRUSTED

# Allow ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
# Allow loopback access
iptables -A FIREWALL -i lo -j ACCEPT
# Send all package to the TRUSTED chain
iptables -A FIREWALL -j TRUSTED
# DROP all other packets
iptables -A FIREWALL -j DROP

# Send all INPUT packets to the FIREWALL chain
iptables -A INPUT -j FIREWALL

# Forward only established and related connections to the lan for incoming packets 
iptables -A FORWARD -i eth1 -o eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT 
# Forward all OUT connections from the lan 
iptables -A FORWARD -o eth1 -i eth0 -j ACCEPT 
# hide computers behind the firewall 
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE 
# then DROP all the rest 
iptables -A FORWARD -j DROP

# Allow SSH
iptables -A TRUSTED -i eth1 -p tcp -m tcp --dport 22 -j ACCEPT
iptables -A TRUSTED -i eth1 -p udp -m udp --dport 22 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 22 -j ACCEPT
iptables -A TRUSTED -i eth0 -p udp -m udp --dport 22 -j ACCEPT

# Allow DNS
iptables -A TRUSTED -i eth0 -p udp -m udp --sport 53 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 53 -j ACCEPT

# Allow https
iptables -A TRUSTED -i eth0 -p udp -m udp --sport 443 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 443 -j ACCEPT

# Allow amule
iptables -A TRUSTED -i eth0 -p udp -m udp --dport 5349 -j ACCEPT
iptables -A TRUSTED -i eth0 -p udp -m udp --dport 5351 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 5348 -j ACCEPT

# Allow IRC IDENT & DCC
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 6667 -j ACCEPT
iptables -A TRUSTED -i eth0 -p tcp -m tcp --sport 113 -j ACCEPT

# Allow bittorrent
iptables -A TRUSTED -i eth0 -p tcp -m tcp --dport 6881:6889 -j ACCEPT

# End message
echo " [End iptables rules setting]"
```

---

### Post by Kyorisu on 2007-08-01
Thanks for that, I have a lot of experience in a windows environment but when it comes to anything else I know squat. Googling doesn't help much either you'll find too much conflicting information, it hurts my head.

Still need to know how to filter http traffic through to squid on top of this configuration. If I can get that done without setting each machines browser to use the proxy I'd be set. If I try doing it myself I usually break the whole damn thing and cannot access anything.

Squid is listening on the default 3128 and http traffic is obviously 80.

Main reason to get this done is to cache updates for a bunch of programs without having to get each one by itself and rather let the programs grab them from said cache. Only 3 machines yet but I do bring in machines from customers and get them fully updated. Country area so not many people have an ADSL1 (yes 1, 2 would be awesome but no) and cannot update on their dialup connections. That or they have DSL with strict quotas.

Again help is highly appreciated I'd love to get this thing working properly.

---

### Post by frodon on 2007-08-01
Here are 2 useful link for web content filtering :
[https://help.ubuntu.com/community/SquidGuard](https://help.ubuntu.com/community/SquidGuard)
[http://software.newsforge.com/software/04/06/23/1521209.shtml](http://software.newsforge.com/software/04/06/23/1521209.shtml)

Then if squid is listening the port 3128 then maybe don't forward the packets on port 80 therefore LAN users will have to use the squid proxy on port 3128 to get web access.
Would it fit your needs ?

Otherwise a rule like that would allow to re-route traffic from port 80 to 3128 but here i'm not an expert:
```
iptables -t nat -A PREROUTING -i eth1 -p tcp --dport 80 -j DNAT --to-destination 192.168.1.10:3128 
```

---

### Post by Kyorisu on 2007-08-01
I'll try it all out in the morning. Well it is the morning (2am), but I'd rather do this when I have a clearer head.

I know for a fact I can simply redirect programs to the proxy and that will work, the amount of ads that disappear in IE thanks to adzapper agrees with me. That and checking the squid access.log.

The second link you posted looks interesting and the blacklisting tool used may have its uses as well. Certain person on my network accessing things they shouldn't be.

Thanks as always.

---

