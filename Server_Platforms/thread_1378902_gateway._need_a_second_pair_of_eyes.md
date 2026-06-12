---
title: "gateway. need a second pair of eyes"
date: 2010-01-12
forum: Server Platforms
---

### Post by sinclair86 on 2010-01-12
Ok so I have 


NET  <----> ROUTER <--->NETWORK 1 <--> eth1 (Ubuntu Server [DEAN]) eth0 <---> eth0 (ubuntu server [EE-Server])

router = 192.168.1.1

Dean:
eth1 = 192.168.1.3
eth0 = 10.10.0.10

EE-Server
eth0 = 10.10.0.12

```
paul@Dean:~$ sudo iptables -L
paul@Dean:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:www 
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:www 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination    

```

```

sudo iptables -t nat -L
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         
DNAT       udp  --  anywhere             anywhere            tcp dpt:www to:10.10.0.12:80 

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         
MASQUERADE  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

net.ipv4.conf.all.forwarding = 1

in my router I added a route for 10.10.0.0/24 --> 192.168.1.3

K now heres the thing is on network 2 sit EE-Server. If im on network 2 I can my ssh,http,smtp the server. On network 1 I can ping the server, when i scan it it shows all the ports opened when when i try to connect to a service it just hangs. Was just trying to knock out one problem at a time.

I did a tcpdump --vvv | grep "192.168.1.11" on both dean and EE-server. the packets were making it to dean but werent making it to EE-server and I dont know why? AM i missing something in the forwarding? And yes EE-server has internet connectivity. I am able to download files/ping stuff on EE-server.

---

### Post by wirelessmonkey on 2010-01-12
You have not defined a default route for Dean, so it's speaking out of the wrong interface.

---

### Post by sinclair86 on 2010-01-12
```
paul@Dean:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
10.10.0.0       *               255.255.255.0   U     0      0        0 eth0
default         Wireless_Broadb 0.0.0.0         UG    100    0        0 eth1

```

---

