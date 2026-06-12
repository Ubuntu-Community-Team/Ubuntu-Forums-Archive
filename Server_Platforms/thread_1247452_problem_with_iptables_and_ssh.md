---
title: "problem with iptables and ssh"
date: 2009-08-22
forum: Server Platforms
---

### Post by crazyone on 2009-08-22
hi i have been setting up a router for the last few days and have been having problems getting ssh to forward to another system on my network. when i try to login from a remote host i keep getting connection refused but i can ssh into the router then go into the computer. both sshd configs are running on differnt ports. the router on port 22 and my computer on port 2222. here is my config file not sure what i am doing worng with it for it not to forward right. the router is running ubuntu 8.04 and my computer is running ubuntu 9.04 64bit if that helps at all.

```
LAN_INT=eth1
WAN_INT=ppp0
echo flushing

iptables -t nat -F 
iptables -t filter -F

echo startign script
#enable IP forwarding.
echo 1 >/proc/sys/net/ipv4/ip_forward
echo 1
#enable IP masquerading
iptables -t nat -A POSTROUTING -j MASQUERADE

#port forwarding - each of these for each port forwarded
#iptables -t nat -A PREROUTING -p tcp -i eth0 --dport $external_port -j DNAT --to $internal_ip:$internal_port
#iptables -A FORWARD -p tcp -i $WAN_INT -o $LAN_INT -d $internal_ip --dport $internal_port -j ACCEPT
iptables -t nat -A PREROUTING -p tcp -i $WAN_INT --dport 22 -j DNAT --to 192.168.58.60:22
iptables -A FORWARD -p tcp -i $WAN_INT --dport 22 -j ACCEPT



echo 2
#accepting packets to the server
iptables -t filter -A INPUT -i $WAN_INT -p tcp --dport 3306 -j DROP
iptables -t filter -A INPUT -j ACCEPT

#accept outgoing packets
iptables -t filter -A FORWARD -i $LAN_INT -j ACCEPT
#iptables -t filter -A FORWARD -i $LAN_INT -o $WAN_INT -j ACCEPT #if lots of NICs

echo 3
#accept related incoming packets
# note: --state ESTABLISHED,RELATED -- HAS NO SPACES!
iptables -t filter -A FORWARD -i $WAN_INT -o $LAN_INT -m state --state ESTABLISHED,RELATED -j ACCEPT


#drop illegal packets
iptables -t filter -A FORWARD -i $WAN_INT -j DROP

```

here is route -n information too

```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
xx.xx.xx.xx     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
192.168.58.0    0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0

```

and here is iptables -L -vnx

```
Chain INPUT (policy ACCEPT 206 packets, 53948 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 DROP       tcp  --  eth0   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:3306 
      15     1068 ACCEPT     all  --  *      *       0.0.0.0/0            0.0.0.0/0           

Chain FORWARD (policy ACCEPT 17506 packets, 13050693 bytes)
    pkts      bytes target     prot opt in     out     source               destination         
       0        0 ACCEPT     tcp  --  eth0   *       0.0.0.0/0            0.0.0.0/0           tcp dpt:2222 
       3      157 ACCEPT     all  --  eth1   *       0.0.0.0/0            0.0.0.0/0           
       0        0 ACCEPT     all  --  eth0   eth1    0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
       0        0 DROP       all  --  eth0   *       0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT 4970 packets, 654751 bytes)
    pkts      bytes target     prot opt in     out     source               destination
```

any help on this would be helpful it is jsut and odd problem becuase its not supose to be blocking anything just forwarding it to the system.


ok after looking over my computer and looking at ssh i foudn out i changed the port but never restarted ssh like i thought i did

---

### Post by HermanAB on 2009-08-23
Howdy,

You also don't seem to have a default route.  Something like:
route add default gw 192.168.0.1 eth0

BTW, the best way to debug SSH connectivity issues is with the verbosity flags, for example:
ssh -vvv user@server -p 2222

---

### Post by crazyone on 2009-08-23
ok thanks you. will add that beuase it decied to stop workign agian :(

---

