---
title: "NTP over ipv6 with ip6tables"
date: 2013-03-09
forum: Server Platforms
---

### Post by Calimo on 2013-03-09
Hi there!

I am trying to run my server with NTP over IPv6. This works until I start using ip6tables.

I accept traffic on ntp port (123), both udp and tcp:
```
sudo ip6tables -A INPUT -p udp -m udp --dport 123 -j ACCEPT 
sudo ip6tables -A INPUT -p tcp -m tcp --dport 123 -j ACCEPT
```

Policy is still ACCEPT, so the server is reachable from another ipv6 machine:

```
$ ntpdate -6 -q arthur.xavasite.net
server 2001:4b98:dc0:43:216:3eff:fe1f:5b1d, stratum 2, offset 0.000884, delay 0.05556
 9 Mar 16:18:53 ntpdate[7334]: adjust time server 2001:4b98:dc0:43:216:3eff:fe1f:5b1d offset 0.000884 sec
```

Now I want to drop anything that's not allowed, so:
```
sudo ip6tables -P INPUT DROP
```

As soon as I change the policy to drop, my NTP server becomes unreachable:

```
$ ntpdate -6 -q arthur.xavasite.net
server 2001:4b98:dc0:43:216:3eff:fe1f:5b1d, stratum 0, offset 0.000000, delay 0.00000
 9 Mar 16:21:33 ntpdate[7336]: no server suitable for synchronization found
```

I don't understand because this works fine on IPv4. What's different with IPv6 ? Is NTP using another port? Is IPTables behaving differently?

Here is my ip6tables output:
```
xavier@arthur:~$ sudo ip6tables -L
[sudo] password for xavier: 
Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all      anywhere             anywhere            
ACCEPT     all      anywhere             anywhere             ctstate RELATED,ESTABLISHED
ACCEPT     tcp      anywhere             anywhere             tcp dpt:ssh
ACCEPT     tcp      anywhere             anywhere             tcp dpt:smtp
ACCEPT     tcp      anywhere             anywhere             tcp dpt:http
ACCEPT     udp      anywhere             anywhere             udp dpt:ntp
ACCEPT     tcp      anywhere             anywhere             tcp dpt:ntp
ACCEPT     tcp      anywhere             anywhere             tcp dpt:https
ACCEPT     tcp      anywhere             anywhere             tcp dpt:imaps
ACCEPT     tcp      anywhere             anywhere             tcp dpt:pop3s
ACCEPT     tcp      anywhere             anywhere             tcp dpt:ssmtp
ACCEPT     tcp      anywhere             anywhere             tcp dpt:xmpp-client
ACCEPT     tcp      anywhere             anywhere             tcp dpt:5223
ACCEPT     tcp      anywhere             anywhere             tcp dpt:xmpp-server
ACCEPT     tcp      anywhere             anywhere             tcp dpt:5280
ACCEPT     tcp      anywhere             anywhere             tcp dpt:5281
ACCEPT     ipv6-icmp    anywhere             anywhere             ipv6-icmp router-advertisement
ACCEPT     ipv6-icmp    anywhere             anywhere             ipv6-icmp router-solicitation
ACCEPT     ipv6-icmp    anywhere             anywhere             ipv6-icmp echo-request
ACCEPT     ipv6-icmp    anywhere             anywhere             ipv6-icmp echo-reply

Chain FORWARD (policy DROP)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination     
```

Any input would be appreciated.

Xavier

---

### Post by Calimo on 2013-03-14
This was solved by accepting all inbound ICMPv6 traffic (it was specifically types 135 and 136, that is neighbor advertisements and solicitations, but I decided I could as well accept everything and avoid future headaches) with only some very high speed limit (900 requests/min should never be achieve unless the server is under a DOS attack).

```
sudo ip6tables -A INPUT -p icmpv6 -m limit --limit 900/min -j ACCEPT
```

---

