---
title: "Two network interfaces forward"
date: 2017-12-18
forum: Server Platforms
---

### Post by iacoposk8 on 2017-12-18
Hello everyone! I have a server (raspberry) with two network cards: eth0 and eth1.
Before  moving on to more complicated things I would like to connect my pc on  eth0 and router to eth1 and be able to surf the internet on my pc.
I wrote this on the server:
```

sudo iptables -t nat -A POSTROUTING -o eth1 -j MASQUERADE
sudo iptables -A FORWARD -i eth1 -o eth0 -m state --state RELATED,ESTABLISHED -j ACCEPT
sudo iptables -A FORWARD -i eth0 -o eth1 -j ACCEPT

```

but when I put the server between pc and router the pc can not connect, as if the cable was disconnected.
if  on the pc I change the connection setting from automatic to manual and I  indicate as a gateway the server this error disappears but I can not  surf anyway.
thank you :)

ps: the server has just been formatted, the only changes are these 3 lines of iptables

---

### Post by darkod on 2017-12-18
You also need to enable ipv4 forward in /etc/sysctl.conf and restart the rasberry. See if that helps...

---

### Post by iacoposk8 on 2017-12-19
Thanks for the answer, i set this: net.ipv4.ip_forward=1 in /etc/sysctl.conf
and also execute this: sudo echo 1 >/proc/sys/net/ipv4/ip_forward
reboot, but same problem, the pc can't connect and if i connect in manual mode i can't ping the router

---

### Post by darkod on 2017-12-19
Are you connecting the PC directly to the server port with a standard patch cable? It can't work like that, you can't use standard network patch cable to connect PCs directly. It has to be crossover cable or it has to go through a switch.

Also, you need either static IPs or something issuing DHCP leases in the private LAN with the PCs and the server.

From the server, post the output of:
```
ifconfig
```

---

### Post by iacoposk8 on 2017-12-19
thanks for the answer
```

eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.5  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::f713:d084:6eef:2394  prefixlen 64  scopeid 0x20<link>
        ether b8:27:eb:b1:de:80  txqueuelen 1000  (Ethernet)
        RX packets 63  bytes 8878 (8.6 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 71  bytes 11698 (11.4 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

eth1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.4  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::d6b4:e542:8f2a:9dfc  prefixlen 64  scopeid 0x20<link>
        ether 00:0e:c6:a1:4d:a3  txqueuelen 1000  (Ethernet)
        RX packets 15  bytes 1485 (1.4 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 28  bytes 4378 (4.2 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```
i have many cable, maybe i have the right cable. what is the way for check it?

---

### Post by darkod on 2017-12-19
You have both eth0 and eth1 in the same subnet. Usually when you are creating a server that needs to route traffic between two subnets, it will have IPs in two different subnets.

You can search how to check crossover cables on the internet, I'm not sure I can easily explain it here.

---

### Post by iacoposk8 on 2017-12-19
thanks, i check it, if i understand normally the colored cable in the start and in the end have the same order in the crossover not.
can you send me an example for create a subnet, dhcp and other things that i need?
thanks you so much

---

### Post by darkod on 2017-12-19
You can use any subnet from the private 10.0.0.0/8 range. The important thing is to be different from the 192.168.1.0/24 subnet which will be on the NIC connected to the router.

For the other NIC use 10.1.1.1 with netmask 255.255.255.0 for example.

For DHCP you can use the server guide here [https://help.ubuntu.com/lts/serverguide/index.html](https://help.ubuntu.com/lts/serverguide/index.html) or other online tutorials.

---

### Post by iacoposk8 on 2017-12-31
thanks for the reply, sorry if I have not written for all this period. happy holidays to all: D
while I was rehearsing with the dhcp I found this: bridge-utils
I installed it, configured it and it seems to work.
now the computer is connected to eth1 and eth0 is connected to the router.
I wanted to do a test, for the definitive use with these commands:
```

sudo iptables -A INPUT -i br0 -m mac --mac-source xx:xx:xx:xx:xx:xx -j DROP
sudo iptables -A INPUT -i eth1 -m mac --mac-source xx:xx:xx:xx:xx:xx -j DROP

```
I  would like to block navigation to a certain mac address, but the result  is that it can no longer connect via ssh, it can no longer ping, but  online browsing still works

---

