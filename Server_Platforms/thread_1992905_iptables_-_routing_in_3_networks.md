---
title: "iptables - routing in 3 networks"
date: 2012-06-01
forum: Server Platforms
---

### Post by karabiner on 2012-06-01
Hello,
I am working for hours on the following problem. The internet ist full of explainations, but I could not find something about two internal and one external networks.

I would like to configure my Router in the following way (s. picture):
[IMG]http://dl.dropbox.com/u/54130315/Proxy_Struktur.jpg[/IMG]

1. The Router should work as a proxy for Net 1
2. Net 1 should have access to net 2

_1st point_
I already solved the 1st problem with nat. The tcp port ist redirected to port 3128 where the proxy is listening. 

Here my **iptables Configuration**. 
```
*nat
# Alle tcp Anfragen über Port 80 werden zu Port 3128 maskiert und damit an den Squid übergeben.
-A PREROUTING -i eth1 -p tcp -m tcp --dport 80 -j DNAT --to-destination 192.168.0.10:3128
-A PREROUTING -i eth1 -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 3128
-A POSTROUTING -s 192.168.0.0/20 -o eth0 -j MASQUERADE
COMMIT
```Her the **/etc/interfaces**:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
  address 192.168.178.10
  netmask 255.255.255.0
  gateway 192.168.178.1

  pre-up iptables-restore < /etc/iptables.up.rules

auto eth1
iface eth1 inet static
  address 192.168.0.10
  netmask 255.255.240.0

auto eth2
iface eth2 inet static
  address 192.168.16.10
  netmask 255.255.240.0
```The internet connection from network 1 ist working well.

_2nd Point:_
How can I create an iptable chain, so that I have access from network 1 to network 2. I have created a FORWARD-chain, but it does not work.
```
*filter
:FORWARD ACCEPT [0:0]
-A FORWARD -s 192.160.0.0/20 -i eth1 -d 192.168.16.0/20 -o eth2
COMMIT
```**iptables -L** gives:
```
root@ProxyServer:/var/log/backup_16_4# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
           all  --  192.160.0.0/20       192.168.16.0/20     

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
root@ProxyServer:/var/log/backup_16_4# iptables -L -t nat
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         
DNAT       tcp  --  anywhere             anywhere            tcp dpt:www to:192.168.0.10:3128 
REDIRECT   tcp  --  anywhere             anywhere            tcp dpt:www redir ports 3128 

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         
MASQUERADE  all  --  192.168.0.0/20       anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
root@ProxyServer:/var/log/backup_16_4# 
```I would be really happy, if you could help me.

Nils

---

### Post by karabiner on 2012-06-01
Ok, I solved the problem, by adding a static route the the destination computer.

---

