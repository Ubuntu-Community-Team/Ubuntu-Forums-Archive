---
title: "ubuntu server squid one nic iptables"
date: 2016-05-01
forum: Security
---

### Post by VamPikmin on 2016-05-01
Hello,

I need some assistance with setting up squid to work transparently
My setup is

Router: 192.168.1.1
Squid: 192.168.1.30
Workstation: 192.68.1.5

DHCP leases are handed out by the router and by default everything is allowed on the Internet.

on the router I have created a static route to my workstation ip
```
route add 192.168.1.5 gw 192.168.1.30
```

squid iptables so far
```
iptables -t nat -S
-P PREROUTING ACCEPT
-P INPUT ACCEPT
-P OUTPUT ACCEPT
-P POSTROUTING ACCEPT
-A PREROUTING -s 192.168.1.5/32 -p tcp -m tcp --dport 80 -j DNAT --to-destination 192.168.1.30:3128
root@squid:/var/log# iptables -S
-P INPUT DROP
-P FORWARD DROP
-P OUTPUT ACCEPT
-A INPUT -i lo -j ACCEPT
-A INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT
-A INPUT -s 192.168.1.5/32 -p tcp -m tcp --dport 3128 -j ACCEPT


```

If I set the proxy manually I can get on the Internet fine if I use port 80 or 3128, however what would be the best way to do this transparently? 
Thank you for your time, I'm still quite new to iptables

---

### Post by VamPikmin on 2016-05-05
Got it working with the help of a friend and some heavy reading

**Router Config:**
cat /etc/iproute2/rt_tables
180 was the last line in my rt_tables so i made the next rule 181

```
echo "181 SQUID" >> /etc/iproute2/rt_tables
ip route add default via 192.168.1.31 dev br0 table SQUID
ip route show table SQUID
ip rule add from all fwmark 181 lookup SQUID

iptables -t mangle -I PREROUTING -p tcp --dport 80 -j MARK --set-mark 181

```
However I only wanted one host to actually use the squid proxy so I deleted the previous line and added this:
```
 iptables -t mangle -I PREROUTING -p tcp -s 192.168.1.5/32 --dport 80 -j MARK --set-mark 181
```


**Squid Config:** (192.168.1.31)
```
squid3# iptables-A PREROUTING -p tcp -m tcp --dport 80 -j DNAT --to-destination 192.168.1.31:3128
```

squid.conf allow everything for a quick test, use transparent proxy
http_port 3128 intercept
http_access allow all
acl localnet src 192.168.1.0/24

---

