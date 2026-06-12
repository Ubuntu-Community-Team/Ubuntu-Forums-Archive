---
title: "Squid Proxy, EBtables and Ubuntu Kernel routing"
date: 2010-04-14
forum: Server Platforms
---

### Post by erazor999 on 2010-04-14
Hi. I have Ubuntu Server 9.10
My Proxy is Squid version 3.1.1 with TPROXY support.
I have two ethrneth cards eth0 and eth1 in bridge br0.
eth0 IP=0.0.0.0 ; eth1 IP=0.0.0.0
br0 IP=89.216.64.12
    netmask= 255.255.255.240
    gateway= 89.216.64.1
Trough this router goes more IP range different then this one.
On EBtables I have:
ebtables -t broute -A BROUTING -i eth0 -p ipv4 --ip-proto tcp --ip-sport 80 --ip-dst 89.216.64.0/24 -j redirect --redirect-target ACCEPT
ebtables -t broute -A BROUTING -i eth1 -p ipv4 --ip-proto tcp --ip-dport 80 --ip-src 89.216.64.0/24 -j redirect --redirect-target ACCEPT
ebtables -t broute -A BROUTING -i eth0 -p ipv4 --ip-proto tcp --ip-sport 80 --ip-dst 89.216.66.0/24 -j redirect --redirect-target ACCEPT
ebtables -t broute -A BROUTING -i eth1 -p ipv4 --ip-proto tcp --ip-dport 80 --ip-src 89.216.66.0/24 -j redirect --redirect-target ACCEPT

Problem is: only this range of ip address can go trough kernel routing and hit Squid port defined in IPtables:

#iptables -t mangle -N DIVERT
#iptables -t mangle -A DIVERT -j MARK --set-mark 1
#iptables -t mangle -A DIVERT -j ACCEPT
#iptables -t mangle -A PREROUTING -p tcp -m socket -j DIVERT
#iptables -t mangle -A PREROUTING -p tcp --dport 80 -j TPROXY --tproxy-mark 0x1/0x1 --on-port 3129
#cd /proc/sys/net/bridge/
#for i in *
#do
#  echo 0 > $i
#done
#unset i
#ip rule add fwmark 1 lookup 100
#ip route add local 0.0.0.0/0 dev lo table 100
#echo 0 > /proc/sys/net/ipv4/conf/lo/rp_filter
#echo 1 > /proc/sys/net/ipv4/ip_forwar

All other IP address go trough this router without hitting Squid box.

Help please... 
Sorry my English is bad...

Thanks and Best Regards...

---

