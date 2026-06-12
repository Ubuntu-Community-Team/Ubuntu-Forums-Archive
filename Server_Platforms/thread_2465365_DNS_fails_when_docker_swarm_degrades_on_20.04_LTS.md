---
title: "DNS fails when docker swarm degrades on 20.04 LTS"
date: 2021-07-30
forum: Server Platforms
---

### Post by pivert2 on 2021-07-30
Hi, 

I can't figure out why DNS resolving breaks as soon as docker swarm set its iptables rules on Ubuntu 20.04.
The problem started after I lost one of the 3 swarm nodes, and one of the 3 DNS servers. (Degraded)
Eventually recreating and re-joining the missing swarm node and adding the missing DNS IP address on a healthy node did not fix the problem.


[LIST]
[*]/etc/resolvd.conf points to '[FONT=monospace][COLOR=#000000]nameserver 127.0.0.53' (OK)[/COLOR][/FONT] 
[*]I can resolve any hostname using the systemd-resolve command:
```
[FONT=monospace][COLOR=#000000]# systemd-resolve startpage.com [/COLOR]
startpage.com: [COLOR=#000000]**145.131.132.78**[/COLOR][COLOR=#8a8a8a]-- link: ens18[/COLOR]

[COLOR=#8a8a8a]-- Information acquired via protocol DNS in 1.0ms.[/COLOR]
[COLOR=#8a8a8a]-- Data is authenticated: no[/COLOR][/FONT]
``` 
[*]the systemd-resolve properly listens on port 53 
[*]But DNS resolution is broken:
```
[FONT=monospace][COLOR=#000000]# host startpage.com  [/COLOR]
;; connection timed out; no servers could be reached[/FONT]
```[FONT=monospace]
[/FONT] 
[*][FONT=arial]By investigating much more, I found out that there is a NAT redirection in the DOCKER-INGRESS nat table chain for DNS traffic. Removing this entry restores DNS:
[/FONT]```
[FONT=arial][FONT=monospace]# iptables -t nat -L DOCKER-INGRESS -n -v --line-numbers 
Chain DOCKER-INGRESS (2 references) 
num   pkts bytes target     prot opt in     out     source               destination          
1        4   240 DNAT       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:2222 to:172.19.0.2:2222 
2        3   180 DNAT       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:8082 to:172.19.0.2:8082 
3        0     0 DNAT       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:8080 to:172.19.0.2:8080 
4        1    59 DNAT       udp  --  *      *       0.0.0.0/0            0.0.0.0/0            udp dpt:53 to:172.19.0.2:53 
5        0     0 DNAT       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:9000 to:172.19.0.2:9000 
6        0     0 DNAT       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:8000 to:172.19.0.2:8000 
7        0     0 DNAT       tcp  --  *      *       0.0.0.0/0            0.0.0.0/0            tcp dpt:8010 to:172.19.0.2:8010 
8       32  2437 RETURN     all  --  *      *       0.0.0.0/0            0.0.0.0/0            
# iptables -t nat -D DOCKER-INGRESS 4  # Delete the 4th line in the chain     
# host startpage.com                      
startpage.com has address 145.131.132.68 
startpage.com mail is handled by 10 mx1.startmail.com. 
startpage.com mail is handled by 10 mx2.startmail.com.[/FONT][/FONT]
```[FONT=arial][FONT=monospace]
[/FONT][/FONT] 
[/LIST]
[FONT=arial][FONT=monospace]
[/FONT][/FONT][FONT=arial]From my understanding, all queries from the host are sent to the Docker Swarm to resolve container names from the host. But this Docker DNS is broken. ([COLOR=#000000]172.19.0.2 is reachable but times out on DNS queries).

How should I get DNS working ? And why does this happen after the loss of one node ?[/COLOR][/FONT][FONT=arial][FONT=monospace][FONT=monospace][COLOR=#000000]
[/COLOR]
[/FONT][/FONT][/FONT][FONT=monospace][FONT=arial]
[/FONT][/FONT]

---

### Post by pivert2 on 2021-08-02
A temporary workaround is to run this poorly crafted oneliner after docker has started on every node:
```
host startpage.com || iptables -t nat -L DOCKER-INGRESS --line-numbers | grep -E 'DNAT.*udp dpt:domain' | awk
 '{print $1};' | xargs iptables -t nat -D DOCKER-INGRESS
```

---

