---
title: "Additional External IP 's- Ubuntu 16.04"
date: 2017-09-05
forum: Server Platforms
---

### Post by Andrew_Murdoch on 2017-09-05
Hey Guys

I bought a batch of IP addresses from my server host, I've added them into the interface file: 
```

auto eth0
iface eth0 inet static
address xxx.xx.xxx.33
netmask 255.255.255.0
broadcast xxx.xx.xxx.255
gateway xxx.xx.xxx.254
up ip addr add yyy.yy.yyy.97/29 dev $IFACE label $IFACE:0
down ip addr del yyy.yy.yyy.97/29 dev $IFACE label $IFACE:0
up ip addr add yyy.yy.yyy.98/29 dev $IFACE label $IFACE:1
down ip addr del yyy.yy.yyy.98/29 dev $IFACE label $IFACE:1
up ip addr add yyy.yy.yyy.99/29 dev $IFACE label $IFACE:2
down ip addr del yyy.yy.yyy.99/29 dev $IFACE label $IFACE:2
up ip addr add yyy.yy.yyy.100/29 dev $IFACE label $IFACE:3
down ip addr del yyy.yy.yyy.100/29 dev $IFACE label $IFACE:3
up ip addr add yyy.yy.yyy.101/29 dev $IFACE label $IFACE:4
down ip addr del yyy.yy.yyy.101/29 dev $IFACE label $IFACE:4
up ip addr add yyy.yy.yyy.102/29 dev $IFACE label $IFACE:5
down ip addr del yyy.yy.yyy.102/29 dev $IFACE label $IFACE:5
```

When list ip addr, I get:

```
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
link/ether 0c:c4:7a:cb:00:2e brd ff:ff:ff:ff:ff:ff
inet xxx.xx.xxx.33/24 brd xxx.xx.xxx.255 scope global eth0
valid_lft forever preferred_lft forever
inet yyy.yy.yyy.97/29 scope global eth0:0
valid_lft forever preferred_lft forever
inet yyy.yy.yyy.98/29 scope global secondary eth0:1
valid_lft forever preferred_lft forever
inet yyy.yy.yyy.99/29 scope global secondary eth0:2
valid_lft forever preferred_lft forever
inet yyy.yy.yyy.100/29 scope global secondary eth0:3
valid_lft forever preferred_lft forever
inet yyy.yy.yyy.101/29 scope global secondary eth0:4
valid_lft forever preferred_lft forever
inet yyy.yy.yyy.102/29 scope global secondary eth0:5
valid_lft forever preferred_lft forever
inet6 fe80::ec4:7aff:fecb:2e/64 scope link
valid_lft forever preferred_lft forever
```


When I list ip r:

```
default via xxx.xx.xxx.254 dev eth0 onlink
10.0.3.0/24 dev lxcbr0 proto kernel scope link src 10.0.3.1 linkdown
xxx.xx.xxx.96/29 dev eth0 proto kernel scope link src xxx.xx.xxx.97
yyy.yy.yyy.0/24 dev eth0 proto kernel scope link src yyy.yy.yyy.33
192.168.0.0/24 dev br0 proto kernel scope link src 192.168.0.155
```


My questions are, how do I set this up so that I can use the external IP's to SSH to the main server? I tried putting on iptables rules in, but they don't seem to work, I can't ping the addresses in question and I can't SSH to them.

```
iptables -t nat -A PREROUTING -d yyy.yy.yyy.97 -p tcp --dport 22 -j DNAT --to 192.168.0.155
iptables -t nat -A PREROUTING -d yyy.yy.yyy.98 -p tcp --dport 22 -j DNAT --to 192.168.0.155
iptables -A FORWARD -p tcp -d 192.168.0.155 --dport 22 -j ACCEPT
```

---

### Post by deadflowr on 2017-09-05
*Thread moved to **Server Platforms***

---

### Post by darkod on 2017-09-05
First, adding additional IPs and allowing ssh in iptables are not really related.

There is much simpler way to add additional IPs to eth0. After your main eth0 ip configuration, try the following lines for each additional ip:
```
iface eth0 inet static
   address yyy.yy.yyy.97/29
```

If you use that notation you don't need to specify the netmask because the /29 does that for you. Otherwise the additional ip definition should have both 'address' and 'netmask' values. Don't add any gateway or dns on the additional ips, no need.

After you sort that out you need to make sure you allow ssh in the INPUT chain, because traffic is coming from the internet and the destination is the server itself. SSH would usually listen on all interfaces unless you have limited it to listen only to one. The important thing would be if the traffic arrives correctly to all the other IPs, and if it leaves your server routed correctly.

You might need to use static routes or similar, it all depends how the provider network is set up. They can probably give you an advise if you need to put gateway to the additional IPs (at least to one of them) so the server knows how to route the traffic for that subnet, etc...

Otherwise forwarding the traffic from one interface to another is not really a solution. I wouldn't do it.

---

### Post by SeijiSensei on 2017-09-05
Linux allows you to use virtual Ethernet interfaces which I how I handle this situation.

Let's suppose your primary address is 10.10.10.10, and you also have the use of 10.10.10.11-20.

```

/sbin/ifconfig eth0:0 10.10.10.11
/sbin/ifconfig eth0:1 10.10.10.12
[etc.]

```

I usually add these commands to /etc/rc.local.  You don't nee to prefix them with sudo since rc.local runs with root privileges.

---

