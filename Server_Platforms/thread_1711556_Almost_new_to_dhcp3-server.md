---
title: "Almost new to dhcp3-server"
date: 2011-03-21
forum: Server Platforms
---

### Post by darrenshaffer1 on 2011-03-21
I've worked with setting up dhcp servers in the past but only needed it for one subnet.  Now I need a dhcp server for multiple subnets.

What I have setup now is Ubuntu Server 10.10.  I have 3 subnets attached to the server.

10.0.8.0 netmask 255.255.255.252 eth0
192.168.5.0 netmask 255.255.255.0 eth3
192.168.6.0 netmask 255.255.255.0 eth2

What I've been searching for is how I can setup an individual range of ip addresses for a specific network or adapter.  Currently I only have one network setup for dhcp but I need 2 more without overlapping networks or the wrong client getting the wrong network address.  

dhcpd.conf
```

subnet 192.168.6.0 netmask 255.255.255.0 {
        authoritative;
        option routers 192.168.6.1;
        option subnet-mask 255.255.255.0;
        option broadcast-address 192.168.6.255;
        option domain-name "lavacorp.local";
        option domain-name-servers 192.168.6.1;
        range 192.168.6.200 192.168.6.240;
        }

```

/etc/default/dhcp3-server
```

INTERFACES="eth2"

```

Any information would be quite helpful!

---

