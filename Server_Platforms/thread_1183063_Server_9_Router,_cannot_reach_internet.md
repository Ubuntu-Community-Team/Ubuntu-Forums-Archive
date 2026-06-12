---
title: "Server 9 Router, cannot reach internet"
date: 2009-06-09
forum: Server Platforms
---

### Post by tookey on 2009-06-09
I have installed server 9 with dchp3 and shorewall.  After configuration I have attached a laptop to eth1 (my local adapter) and am successfull pulling an address from the dchp server.  I am able to ping the server but I cannot get out to the internet.  I have checked to make sure that I have the correct DNS addresses.  Anyone have any thoughts.  I am new to ubuntu so please go easy on me :)

---

### Post by windependence on 2009-06-09
Is your gateway set correctly? Can you post your config file here?

-Tim

---

### Post by tookey on 2009-06-10
Not sure which config you want so I'll post a few.

**/etc/network/interfaces**

auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 209.198.84.26
        netmask 255.255.255.252
        gateway 209.198.84.25

auto eth1
iface eth1 inet static
        address 192.168.99.10
        network 192.168.99.0
        netmask 255.255.255.0
        broadcast 192.168.99.255
[B]
/etc/dchp3/dhcpd.conf[/B]


ddns-update-style none;

option domain-name "*our domain per isp*";
option domain-name-servers *Our NS Addresses per ISP*;

default-lease-time 600;
max-lease-time 7200;

authoritative;

log-facility local7;

subnet 192.168.99.0 netmask 255.255.255.0 {
        option routers 192.168.99.10;
        authoritative;
        option domain-name-servers *per ISP*;
        option broadcast-address 192.168.99.255;
        max-lease-time 7200;
        default-lease-time 600;
        range 192.168.99.100 192.168.99.200;
        }


I am using shorewall, made sure IP forwarding was turned on and that it had a very basic setup.  I've tried it will the firewall on and off.

Essentially I can ping the router (192.168.99.10) but that's it.... I can't get out anywhere.

Thanks for any help!!!

Tookey

---

### Post by tookey on 2009-06-11
bump...can anyone offer any thoughts?

---

### Post by gombadi on 2009-06-11
Can ping local machines but not remote machines tend to be a problem with routing and gateways.

Can you ping the gateway 209.198.84.25

Traceroute to a remote machine from another computer and find the next hop after the gateway - can you ping that ip address etc.

Can you show us the output of the route command
```

route -n

```

---

### Post by windependence on 2009-06-14
You have no gateway specified for eth1, and the gateway for eth0 will not work. Most likely the gateway should be 192.168.99.1, but you know better than I do, I'm just guessing.

-Tim

---

### Post by gombadi on 2009-06-14
> 
# The primary network interface
auto eth0
iface eth0 inet static
address 209.198.84.26
netmask 255.255.255.252
gateway 209.198.84.25


> 
You have no gateway specified for eth1, and the gateway for eth0 will not work


```

human@zagbot:~/down$ ipcalc 209.198.84.26/255.255.255.252
Address:   209.198.84.26        11010001.11000110.01010100.000110 10
Netmask:   255.255.255.252 = 30 11111111.11111111.11111111.111111 00
Wildcard:  0.0.0.3              00000000.00000000.00000000.000000 11
=>
Network:   209.198.84.24/30     11010001.11000110.01010100.000110 00
HostMin:   209.198.84.25        11010001.11000110.01010100.000110 01
HostMax:   209.198.84.26        11010001.11000110.01010100.000110 10
Broadcast: 209.198.84.27        11010001.11000110.01010100.000110 11
Hosts/Net: 2                     Class C


```

209.198.84.25 is a valid host in the network for eth0 so it should work as the default gateway therefore the OP does not need a gateway on eth1.

---

### Post by drave on 2009-06-16
do you have ip forwarding turned on ?

echo -n "Checking IP Forwarding"
if [ -e /proc/sys/net/ipv4/ip_forward ] ; then
	echo 1 >/proc/sys/net/ipv4/ip_forward
	echo ": enabled"
fi

---

### Post by Iowan on 2009-06-16
I was wondering if the forwarding was controlled by iptables, or something else...

---

### Post by windependence on 2009-06-17
> **gombadi said:**
> ```

human@zagbot:~/down$ ipcalc 209.198.84.26/255.255.255.252
Address:   209.198.84.26        11010001.11000110.01010100.000110 10
Netmask:   255.255.255.252 = 30 11111111.11111111.11111111.111111 00
Wildcard:  0.0.0.3              00000000.00000000.00000000.000000 11
=>
Network:   209.198.84.24/30     11010001.11000110.01010100.000110 00
HostMin:   209.198.84.25        11010001.11000110.01010100.000110 01
HostMax:   209.198.84.26        11010001.11000110.01010100.000110 10
Broadcast: 209.198.84.27        11010001.11000110.01010100.000110 11
Hosts/Net: 2                     Class C


```209.198.84.25 is a valid host in the network for eth0 so it should work as the default gateway therefore the OP does not need a gateway on eth1.

I'm quite aware that the gateway he specified for eth0 is valid and I am not disputing that point. Since I don't have more information about his network configuration, I am assuming his eth0 interface is an internet facing connection with no routing, and that possibly the eth1 interface has another route to the internet. It's a guess at best but if that were the case, he cannot use the external IP gateway for that route to the outside.

-Tim

---

### Post by mbaas on 2009-06-17
Hi,

Could you post the content of the relevant /etc/shorewall config files (interfaces, zones, policy and masq)?

Mikey

---

