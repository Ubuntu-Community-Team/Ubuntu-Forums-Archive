---
title: "2 NICs donte primary?"
date: 2010-04-17
forum: Server Platforms
---

### Post by blindmist on 2010-04-17
I am having a strange problem here. I have gone through, set the nameservers correct and I have a valid /etc/network/interfaces file too. Although, only one of them should have access to the outside internet while the other stays on the home network. 

```

auto eth0
iface eth0 inet static

        address         205.209.251.20
        netmask         255.255.255.0
        network         205.209.251.0
        broadcast       205.209.251.255
        gateway         205.209.251.1

auto eth1
iface eth1 inet static

        address         192.168.1.29
        netmask         255.255.255.0
        network         192.168.1.0
        broadcast       192.168.1.255
        gateway         192.168.1.1


```

eth1 , which is what I used for the install and originally told it to use DHCP just so I could get through the install. Now should only be accessible on my home network, but while it is up, it kills eth0. Take eth1 down, eth0 goes up, put eth1 up, eth0 goes down. eth0 should also be the outside connection to the world.

---

### Post by wirelessmonkey on 2010-04-17
What's the output of
```

route

```
?

---

### Post by gombadi on 2010-04-17
You have two default gateways set. If you want the default route to be to the Internet then remove the gateway line from eth1 and restart networking.

---

