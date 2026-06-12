---
title: "iptables limit module not working"
date: 2011-05-14
forum: Security
---

### Post by m3xican on 2011-05-14
I'm trying to limit the number of the ICMP packets reaching my server, so I'm using the limit module of iptables, unfortunately it seems the limit I set is totally ignored as I can easily send tens of ICMP packets and get a reply in less than 0.3 second

> m3xican@m3xtop:~$ sudo ping -i0 -c20 x.x.x.x
...
20 packets transmitted, 20 received, 0% packet loss, time 230ms
rtt min/avg/max/mdev = 184.969/185.895/189.732/1.301 ms, pipe 16, ipg/ewma 12.138/186.232 msThis is the rule I'm using to accept ICMP packets (default setting is DROP)
```
iptables -A INPUT -p icmp -m limit --limit 1/s -j ACCEPT
```And these are the kernel modules related to iptables
```

Module                  Size  Used by
xt_limit                1382  0 
xt_state                1098  0 
xt_tcpudp               2011  0 
iptable_filter          2271  0 
iptable_mangle          2771  0 
iptable_nat             4414  0 
nf_nat                 15735  1 iptable_nat
nf_conntrack_ipv4      10672  3 iptable_nat,nf_nat
nf_conntrack           61615  4 xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nf_defrag_ipv4          1073  1 nf_conntrack_ipv4
ip_tables               9991  3 iptable_filter,iptable_mangle,iptable_nat
x_tables               14299  5 xt_limit,xt_state,xt_tcpudp,iptable_nat,ip_tables
```Any idea why the filter is not working as expected? Am I overlooking something?

---

### Post by The Cog on 2011-05-14
My first inclination would be to look at all the other iptables rules for some earlier rule that may be allowing all the pings. For instance, it is common to have a rule that allows all packets from interface lo which would allow the local pings.

---

### Post by m3xican on 2011-05-15
unfortunately that's not the problem.

I've already tried to move the rule to the top of the list and nothing changed. 
I'm pinging the server from lo and from some different machines, so it's not something related to the interface.

---

### Post by The Cog on 2011-05-16
Well, you're not giving much information away. It works for me - see this copy/paste. I had to specify echo-request because otherwise it also limited the replies which messed up the figures.

So your problem is in somewhere in the rules you're not posting.```
root@dingly:~# iptables -A INPUT -p icmp --icmp-type echo-request -m limit --limit 3/s -j ACCEPT
root@dingly:~# iptables -A INPUT -p icmp --icmp-type echo-request -j DROP
root@dingly:~# ping -i 0  -c 30 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_req=1 ttl=64 time=0.070 ms
64 bytes from 127.0.0.1: icmp_req=2 ttl=64 time=0.017 ms
64 bytes from 127.0.0.1: icmp_req=3 ttl=64 time=0.016 ms
64 bytes from 127.0.0.1: icmp_req=4 ttl=64 time=0.015 ms
64 bytes from 127.0.0.1: icmp_req=5 ttl=64 time=0.018 ms

--- 127.0.0.1 ping statistics ---
30 packets transmitted, 5 received, 83% packet loss, time 296ms
rtt min/avg/max/mdev = 0.015/0.027/0.070/0.021 ms, ipg/ewma 10.233/0.048 ms
root@dingly:~# iptables -nvL
Chain INPUT (policy ACCEPT 76 packets, 18387 bytes)
 pkts bytes target     prot opt in     out     source               destination         
    5   420 ACCEPT     icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 limit: avg 3/sec burst 5 
   25  2100 DROP       icmp --  *      *       0.0.0.0/0            0.0.0.0/0           icmp type 8 

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 71 packets, 9801 bytes)
 pkts bytes target     prot opt in     out     source               destination         

```

---

### Post by m3xican on 2011-05-16
Adding the DROP rule made it work
```
iptables -A INPUT -p icmp -m limit --limit 2/s -j ACCEPT
iptables -A INPUT -p icmp -j DROP
```So I realized the problem was with some other rule below that one, and indeed it was caused by this rule
```
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
```A possible solution could be changing this rule to:
```
iptables -A INPUT -m state --state ESTABLISHED,RELATED -p ! icmp -j ACCEPT
```but I decided to keep the DROP rule for ICMP packets to avoid future problems/conflicts with other rules.

Thank you The Cog!

---

### Post by The Cog on 2011-05-16
Excellent. I only added the DROP in my example because I didn't want to change the default ACCEPT and break other connectivity. But it was useful to have it in the example, so that's good.

I prefer the separate DROP rule, it "feels" more right than polluting the ESTABLISHED rule, and it's more obvious there.

---

