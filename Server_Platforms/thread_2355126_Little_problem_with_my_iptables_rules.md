---
title: "Little problem with my iptables rules"
date: 2017-03-09
forum: Server Platforms
---

### Post by CrewDK on 2017-03-09
I trying to set some iptables rules. Here is my bash script with some of them: 

```
#!/bin/bash

############################
# Var

IPT=/sbin/iptables
IPS=/sbin/ipset

extif=eth0
BADIPFILE=/root/ipset/badip.lst

if [ ! -e /root/ipset/badip.lst ]; then
    touch ${BADIPFILE}
fi

BADIPS=$(grep -v -E "^#|^ |^$" ${BADIPFILE} | awk '{print $1}')


#############################
## Wipe all rules

$IPT -F
$IPT -X

$IPS -F
$IPS -X

$IPT -P INPUT ACCEPT
$IPT -P OUTPUT ACCEPT
$IPT -P FORWARD ACCEPT


#############################
## 2. Set default chain policies

# Drops all by default
$IPT -P INPUT DROP -m comment --comment "DROP all INPUT traffic by default";
$IPT -P OUTPUT DROP -m comment --comment "DROP all OUTPUT traffic by default";
$IPT -P FORWARD DROP -m comment --comment "Drop all FORWARD traffic by default";
  
# lo 
$IPT -A INPUT -i lo -j ACCEPT -m comment --comment "ALLOW all LOOPBACK traffic by default";
$IPT -A OUTPUT -o lo -j ACCEPT -m comment --comment "ALLOW all LOOPBACK traffic by default";
  
# Allow ALL incoming SSH
$IPT  -A INPUT -i ${extif} -p tcp --dport 22 -m state --state NEW,ESTABLISHED -j ACCEPT
$IPT  -A OUTPUT -o ${extif} -p tcp --sport 22 -m state --state ESTABLISHED -j ACCEPT

# Allow outgoing SSH
$IPT  -A OUTPUT -o ${extif} -p tcp --dport 22 -m state --state NEW,ESTABLISHED -j ACCEPT
$IPT  -A INPUT -i ${extif} -p tcp --sport 22 -m state --state ESTABLISHED -j ACCEPT

################################
## Rules Tables

$IPT -N C_FILTER;
$IPT -N WH_LIST;
$IPT -N BAN;

$IPT -A INPUT -i ${extif} -m state --state NEW -j BAN;

#$IPT -A OUTPUT -j BAN;


#############################################
## Setting ipset rules

$IPS -N C_FILTER nethash
$IPS -N WH_LIST iphash
$IPS -N BAN iphash

for net in $(cat /root/ipset/ru.zone); do
  $IPS -A C_FILTER $net
done

for ip in $(cat /root/ipset/whitelist.lst | awk '{print $1}'); do
  $IPS -A WH_LIST $ip
done

for badip in $(cat /root/ipset/badip.lst | awk '{print $1}'); do
  $IPS -A  BAN $badip
done

$IPT -A BAN -m set --match-set BAN src -j DROP;
$IPT -A BAN -m set ! --match-set BAN src -j C_FILTER;
$IPT -A BAN -j RETURN;

$IPT -A C_FILTER -m set ! --match-set C_FILTER src -j WH_LIST;
$IPT -A C_FILTER -m set --match-set C_FILTER src -j RETURN;

$IPT -A WH_LIST -m set --match-set WH_LIST src -j RETURN;
$IPT -A WH_LIST -m set ! --match-set WH_LIST src -j DROP;


###########################################
## TCP protocol

# allow in http, https
$IPT -A INPUT -i ${extif} -p tcp -m multiport --dports 80,443 -m state --state NEW,ESTABLISHED -j ACCEPT
$IPT -A OUTPUT -o ${extif} -p tcp -m multiport --sports 80,443 -m state --state ESTABLISHED -j ACCEPT

# Allow out HTTP, HTTPS
$IPT -A OUTPUT -o ${extif} -p tcp -m multiport --sports 80,443 -m state --state NEW,ESTABLISHED -j ACCEPT
$IPT -A INPUT -i ${extif} -p tcp -m multiport --dports 80,443 -m state --state ESTABLISHED -j ACCEPT

# Prevent DoS attack
#$IPT -A INPUT -i ${extif} -p tcp -m multiport --dports 80,443 -m limit --limit 25/minute --limit-burst 100 -j ACCEPT


#############################
## ICMP protocols

# Ping from inside to outside
$IPT -A OUTPUT -p icmp --icmp-type echo-request -j ACCEPT
$IPT -A INPUT -p icmp --icmp-type echo-reply -j ACCEPT

# Ping from outside to inside
$IPT -A INPUT -p icmp --icmp-type echo-request -j ACCEPT
$IPT -A OUTPUT -p icmp --icmp-type echo-reply -j ACCEPT

#############################
## UDP protocols

# Allow outbound DNS
$IPT -A OUTPUT -p udp -o eth0 --dport 53 -j ACCEPT
$IPT -A INPUT -p udp -i eth0 --sport 53 -j ACCEPT


```

All that rules works fine, except outbound http(s) connections. When i'm trying to get some pages for test - I just got nothing: 

```
wget google.com
--2017-03-09 20:26:29--  http://google.com/
Resolving google.com (google.com)... 173.194.122.201, 173.194.122.192, 173.194.122.196, ...
Connecting to google.com (google.com)|173.194.122.201|:80...
```

....and nothing. 

So what I had forgot in my rules?

---

### Post by CrewDK on 2017-03-09
Just got it. Looks like I set wrong source and destination ports in my rules :)

---

