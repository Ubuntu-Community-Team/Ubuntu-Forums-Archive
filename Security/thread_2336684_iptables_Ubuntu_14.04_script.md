---
title: "iptables Ubuntu 14.04 script"
date: 2016-09-10
forum: Security
---

### Post by cloudkos on 2016-09-10
Hey everyone fellows. Its time for me to get an iptables script ready to run . So far i was using ufw. But suddenly i feel that i would like to start thinking with iptables. I dont know if it is good for me , or better but at least i am giving it a try . 
What i need to do right now is this : 
Make a vps sealed with only ssh and a couple more ports open for developing an application. No domain - no web ports open . Since PSAD is having difficulties with ufw i would love to use iptables instead . If you want to comment something on that please be my guest. I am using ubuntu 14.04.5 LTS server for that. 

I would be gratefull if you can give a look at the script and tell me if it is ok. It is a work gathered and researched through internet and with a load of readin - not enough though- but i want to start building. 

Last time i logged to my vps and installed ufw i saw instantly like 5 blocks and a bunch more in so many ports including 22 , 23 , 80 etc. probably for brute force etc. I really don&#8217;t know if that is normal but the Host said that this is absolutely normal. Is it ?? Since i dont have Domain and port 80 and none connects beside me.  Anyways this is my script.

```

#!/bin/sh

#We flush all the previous rules we had in iptables
iptables -F

#Policies - We need to DROP everything
iptables -P OUTPUT DROP
iptables -P INPUT DROP
iptables -P FORWARD DROP

#Established Connections
iptables -A INPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
iptables -A OUTPUT -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT

#Loopback Authorization
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT

#Ping Enable
iptables -A INPUT -p icmp -j ACCEPT
iptables -A OUTPUT -p icmp -j ACCEPT

#SSH
iptables -A INPUT -p tcp --dport 22 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 22 -j ACCEPT

#DNS enable for apt-get update & upgrade
iptables -A OUTPUT -p udp --dport 53 -j ACCEPT

#NTP (time sync) enable
iptables -A OUTPUT -p udp --sport 123 --dport 123 -j ACCEPT

# Block sync
iptables -A INPUT -i eth0 -p tcp ! --syn -m state --state NEW  -m limit --limit 5/m --limit-burst 7 -j LOG --log-level 4 --log-prefix "Drop Sync"
iptables -A INPUT -i eth0 -p tcp ! --syn -m state --state NEW -j DROP

# Block Fragments
iptables -A INPUT -i eth0 -f  -m limit --limit 5/m --limit-burst 7 -j LOG --log-level 4 --log-prefix "Fragments Packets"
iptables -A INPUT -i eth0 -f -j DROP

# Block more 
iptables -A INPUT -i eth0 -p tcp --tcp-flags ALL FIN,URG,PSH -j DROP
iptables -A INPUT -i eth0 -p tcp --tcp-flags ALL ALL -j DROP
iptables -A INPUT -i eth0 -p tcp --tcp-flags ALL NONE -m limit --limit 5/m --limit-burst 7 -j LOG --log-level 4 --log-prefix "NULL Packets"
iptables -A INPUT -i eth0 -p tcp --tcp-flags ALL NONE -j DROP # NULL packets
iptables -A INPUT -i eth0 -p tcp --tcp-flags SYN,RST SYN,RST -j DROP
iptables -A INPUT -i eth0 -p tcp --tcp-flags SYN,FIN SYN,FIN -m limit --limit 5/m --limit-burst 7 -j LOG --log-level 4 --log-prefix "XMAS Packets"
iptables -A INPUT -i eth0 -p tcp --tcp-flags SYN,FIN SYN,FIN -j DROP #XMAS
iptables -A INPUT -i eth0 -p tcp --tcp-flags FIN,ACK FIN -m limit --limit 5/m --limit-burst 7 -j LOG --log-level 4 --log-prefix "Fin Packets Scan"
iptables -A INPUT -i eth0 -p tcp --tcp-flags FIN,ACK FIN -j DROP # FIN packet scans
iptables -A INPUT -i eth0 -p tcp --tcp-flags ALL SYN,RST,ACK,FIN,URG -j DROP
iptables -A INPUT -p tcp -i eth0 --dport 137:139 -j REJECT
iptables -A INPUT -p udp -i eth0 --dport 137:139 -j REJECT

#Logging and Dropping
iptables -A INPUT -j LOG
iptables -A FORWARD -j LOG
iptables -A INPUT -j DROP

```

1 : Is my script ok ? Should i add something more like limits etc per port ?
2 : Do i have to enable UFW to check blocks ?
3 : I will use ```
sudo apt-get install iptables-persistent
``` after script to make changes permanent.
4: Do you recommend any monitoring software ? 
5: Shall i change Host since i am getting port scanned since my ip is not given to anyone else besides me and they refuse to change my ip , or is it usual bot scanning ?

Really much appreciate your time ,
Regards

---

