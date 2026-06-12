---
title: "Need some help with my iptables script"
date: 2006-03-24
forum: Server Platforms
---

### Post by frodon on 2006-03-24
Hi,

I'm trying to write my own iptables script and i have some problems.
Here is my bash script : ```
#!/bin/bash

# No spoofing !!!
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

modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe iptable_filter
modprobe iptable_nat 

# Remove all rules
iptables -F
iptables -X

# first set the default behaviour => drop all
iptables -P INPUT DROP
iptables -P OUTPUT DROP
iptables -P FORWARD DROP

# Allow loopback access.
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT

# Accept established connections
#iptables -A INPUT -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT 

# Allow dns
iptables -A INPUT -i eth0 --protocol udp --source-port 53 -j ACCEPT
iptables -A INPUT -i eth0 --protocol tcp --source-port 53 -j ACCEPT
iptables -A OUTPUT -o eth0 --protocol udp --destination-port 53 -j ACCEPT
iptables -A OUTPUT -o eth0 --protocol tcp --destination-port 53 -j ACCEPT

# Allow http
iptables -A INPUT -i eth0 --protocol tcp --source-port 80 -m state --state ESTABLISHED -j ACCEPT
iptables -A OUTPUT -o eth0 --protocol tcp --destination-port 80 -m state --state NEW,ESTABLISHED -j ACCEPT 

# Allow https
iptables -A INPUT -i eth0 --protocol udp --source-port 443 -j ACCEPT
iptables -A INPUT -i eth0 --protocol tcp --source-port 443 -j ACCEPT
iptables -A OUTPUT -o eth0 --protocol udp --destination-port 443 -j ACCEPT
iptables -A OUTPUT -o eth0 --protocol tcp --destination-port 443 -j ACCEPT

# Allow ftp
iptables -A INPUT -i eth0 -p tcp --sport 21 -m state --state ESTABLISHED -j ACCEPT
iptables -A INPUT -i eth0 -p tcp --sport 20 -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A INPUT -i eth0 -p tcp --sport 1024:65535 --dport 1024:65535 -m state --state ESTABLISHED -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp --dport 21 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp --dport 20 -m state --state ESTABLISHED -j ACCEPT
iptables -A OUTPUT -o eth0 -p tcp --sport 1024:65535 --dport 1024:65535 -m state --state ESTABLISHED,RELATED -j ACCEPT

# Allow smtp
iptables -A INPUT -i eth0 --protocol tcp --source-port 25 -j ACCEPT
iptables -A OUTPUT -o eth0 --protocol tcp --destination-port 25 -j ACCEPT

# Allow imap2
iptables -A INPUT -i eth0 --protocol udp --source-port 143 -j ACCEPT
iptables -A INPUT -i eth0 --protocol tcp --source-port 143 -j ACCEPT
iptables -A OUTPUT -o eth0 --protocol udp --destination-port 143 -j ACCEPT
iptables -A OUTPUT -o eth0 --protocol tcp --destination-port 143 -j ACCEPT

# Allow imap3
iptables -A INPUT -i eth0 --protocol udp --source-port 220 -j ACCEPT
iptables -A INPUT -i eth0 --protocol tcp --source-port 220 -j ACCEPT
iptables -A OUTPUT -o eth0 --protocol udp --destination-port 220 -j ACCEPT
iptables -A OUTPUT -o eth0 --protocol tcp --destination-port 220 -j ACCEPT

# Allow amule
iptables -A INPUT -i eth0 --protocol udp --source-port 5249 -j ACCEPT
iptables -A INPUT -i eth0 --protocol tcp --source-port 5248 -j ACCEPT
iptables -A OUTPUT -o eth0 --protocol udp --destination-port 5249 -j ACCEPT
iptables -A OUTPUT -o eth0 --protocol tcp --destination-port 5248 -j ACCEPT

# Allow IRC
iptables -A INPUT -i eth0 --protocol tcp --source-port 6667 -j ACCEPT
iptables -A OUTPUT -o eth0 --protocol tcp --destination-port 6667 -j ACCEPT
#iptables -A INPUT -i eth0 --protocol udp --source-port 133 -j ACCEPT
#iptables -A OUTPUT -o eth0 --protocol udp --destination-port 133 -j ACCEPT

# Accept eggdrop connections
iptables -A INPUT -i eth0 --protocol tcp --source-port 3333 -j ACCEPT
iptables -A OUTPUT -o eth0 --protocol tcp --destination-port 3333 -j ACCEPT

# drop all other packets
iptables -A FORWARD -j DROP
iptables -A INPUT -j DROP
iptables -A OUTPUT -j DROP 

echo " [END]"
```All seems to work well, some sites show my ports as stealth but the [sygate online steath scan]("http://scan.sygatetech.com/stealthscan.html") show my service ports as closed instead of blocked.
nmap also confirm that my ports are "closed" and not "blocked".

Can someone help me to see where i'm wrong. 
Here is the output i get with the iptables-save command : ***

If i compare this output with *** the output of the GTX's script[/URL] it looks a little bit different (create 2 other chains) but the spirit is quite the same but the GTX script show my ports as "blocked".

I'm lost.

Thanks you for any kind of informations.

---

### Post by frodon on 2006-04-05
Well problem solved, my firewall works well now and all my ports are seen as blocked and nmap also confirm that.

I'm looking now for some experts feedback because i'm writing a guide now.
Do you think i should add/remove some lines in this script ? 

```
#!/bin/bash

# No spoofing !!!
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

modprobe ip_tables
modprobe ip_nat_ftp
modprobe ip_nat_irc
modprobe iptable_filter
modprobe iptable_nat 

# Remove all rules
iptables -F
iptables -X

# first set the default behaviour => accept connections
iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

iptables -N FIREWALL
iptables -N TRUSTED

# Allow ESTABLISHED and RELATED incoming connection
iptables -A FIREWALL -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
# Allow self communication
iptables -A FIREWALL -s 127.0.0.1 -j ACCEPT
# Send all packets to the TRUSTED chain
iptables -A FIREWALL -j TRUSTED
# DROP all other packets
iptables -A FIREWALL -j DROP

# Send all through the FIREWALL chain
iptables -A INPUT -j FIREWALL
iptables -A FORWARD -j FIREWALL
iptables -A OUTPUT -j FIREWALL

# Allow dns
iptables -A TRUSTED -o eth0 --protocol udp --destination-port 53 -j ACCEPT
iptables -A TRUSTED -o eth0 --protocol tcp --destination-port 53 -j ACCEPT

# Allow http
iptables -A TRUSTED -o eth0 --protocol tcp --destination-port 80 -m state --state NEW,ESTABLISHED -j ACCEPT

# Allow https
iptables -A TRUSTED -i eth0 --protocol udp --source-port 443 -j ACCEPT
iptables -A TRUSTED -i eth0 --protocol tcp --source-port 443 -j ACCEPT
iptables -A TRUSTED -o eth0 --protocol udp --destination-port 443 -j ACCEPT
iptables -A TRUSTED -o eth0 --protocol tcp --destination-port 443 -j ACCEPT

#Allow IRC IDENT & DCC
iptables -A TRUSTED -i eth0 --protocol tcp --source-port 6667 -j ACCEPT
iptables -A TRUSTED -i eth0 --protocol tcp --source-port 113 -j ACCEPT
iptables -A TRUSTED -o eth0 --protocol tcp --destination-port 6667 -j ACCEPT

# Allow imap2
iptables -A TRUSTED -o eth0 --protocol udp --destination-port 143 -j ACCEPT
iptables -A TRUSTED -o eth0 --protocol tcp --destination-port 143 -j ACCEPT

# Allow imap3
iptables -A TRUSTED -o eth0 --protocol udp --destination-port 220 -j ACCEPT
iptables -A TRUSTED -o eth0 --protocol tcp --destination-port 220 -j ACCEPT

# Allow smtp
iptables -A TRUSTED -o eth0 --protocol tcp --destination-port 25 -j ACCEPT

# Allow ftp
iptables -A TRUSTED -o eth0 -p tcp --dport 21 -m state --state NEW,ESTABLISHED -j ACCEPT
iptables -A TRUSTED -o eth0 -p tcp --dport 20 -m state --state ESTABLISHED -j ACCEPT
iptables -A TRUSTED -o eth0 -p tcp --sport 1024:65535 --dport 1024:65535 -m state --state ESTABLISHED,RELATED -j ACCEPT

# Allow MSN
iptables -A TRUSTED -i eth0 -p tcp --sport 1863 -j ACCEPT
iptables -A TRUSTED -o eth0 -p tcp --dport 1863 -j ACCEPT
```

Thanks.

---

