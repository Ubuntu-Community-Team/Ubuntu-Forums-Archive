---
title: "ubuntu router. wtf dhcp?"
date: 2010-09-30
forum: Server Platforms
---

### Post by sinclair86 on 2010-09-30
the dhcp doesnt work unless i put a switch or router between the ubuntu gateway and the connecting computer.

setup
```
internet < > [eth0] ubuntu server [eth2] < > switch < > computers 
```

iptables

```
iptables -t nat -A POSTROUTING -o eth0 -j ACCEPT
```

/etc/default/dhcp-server
```
INTERFACES="eth2"
```

/etc/network/interfaces
```
auto eth0
iface eth0 inet static
        address 192.168.1.25
        netmask 255.255.255.0
        gateway 192.168.1.1

auto eth2
iface eth2 inet static
        address 172.24.3.1
        netmask 255.255.255.0
        broadcast 172.24.3.255
        network 172.24.3.0

```

/etc/dhcp/dhcpd.conf
```

subnet 172.24.3.0 netmask 255.255.255.0 {
  range 172.24.3.2 172.24.3.255;
  option domain-name-servers 192.168.1.1;
  option domain-name "venture";
  option routers 172.24.3.1;
  option broadcast-address 172.24.3.255;
  default-lease-time 600;
  max-lease-time 7200;
}

```

and yes i enabled ip forwarding. 
echo "1" > /proc/sys/net/ipv4/ip_forward
and in /etc/sysctl.conf
net.ipv4.ip_forward=1



Im on ubuntu 10.04. is this normal? or should i be able to connect without having a router or switch between the ubuntu server and the internal network....

---

### Post by spynappels on 2010-09-30
So if you run a Cat5 cable from the server's eth2 to the clients ethernet port it does not work, but if there is a switch in there it does?

Are you perhaps using a straight-through cable to connect the two computers? That is never going to work, if you want to do that you need a crossover cable.

---

### Post by sinclair86 on 2010-09-30
yes im using a cat5 cable.... and i shouldnt say all computers dont work cause all ive tried is the xbox which does work (tried after i made this post) and a windows 7 laptop which doesnt. im going to try my fedora desktop, ubuntu server #2 and win7 desktop tomorrow. i might just be an idiot... lol

---

### Post by P4man on 2010-09-30
Some LAN adapters (most gigabit NICs) do auto sensing and dont require a cross cable. Others do not support it and will not work unless you put a switch inbetween or you use a cross cable:
[http://en.wikipedia.org/wiki/Auto-MDIX#Auto-MDIX](http://en.wikipedia.org/wiki/Auto-MDIX#Auto-MDIX)

---

