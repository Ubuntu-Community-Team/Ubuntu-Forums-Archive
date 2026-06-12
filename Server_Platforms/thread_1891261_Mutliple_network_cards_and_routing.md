---
title: "Mutliple network cards and routing"
date: 2011-12-05
forum: Server Platforms
---

### Post by michellez on 2011-12-05
Hi All

This is my set up, running Ubuntu 10.04.

/etc/network/interfaces
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
```

route
```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.50.0    *               255.255.255.0   U     0      0        0 eth0
192.168.2.0     *               255.255.255.0   U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
default         192.168.50.1    0.0.0.0         UG    100    0        0 eth0
default         192.168.2.254   0.0.0.0         UG    100    0        0 eth1
```

eth0 is on to a LAN of just phone equipment. The gateway only routes to a data centre and not the public internet.

eth1 is a general LAN full computers and has internet access.

eth0 I just want to use for monitoring some equipment on that LAN.
eth1 to be used for everything else.

As you can see though the routing is set up as above and now this box can no longer access the internet. I can manually go and delete the default route for 192.168.50.1 now I am sure to fix it but how do I get this set up so that after a reboot it continues to route as required?

Thank you
Michelle

---

### Post by ephmanjmm on 2011-12-05
If it were me, I would set the IP address of eth0 staticly and not configure a default gateway on that interface.  It should still be able to connect to that LAN and also use the eth1 interface for other usage.

---

### Post by spynappels on 2011-12-05
What he said ^^^ but maybe with both interfaces with a static IP as its a server? Only set a gateway for eth1 though.

---

### Post by michellez on 2011-12-06
I had thought of doing it statically but I've always gone for the DHCP with a reservation on the server myself. Then if something does go screwy (like a remote site, someone not knowing what they are doing and just swapping a router that is configured with a different subnet etc) at least it's still accessible then. There are benefits to be being static too. Just me being stung once or twice ;)

Is there no way to program something to remove the default route for this NIC after it comes up?

Thanks
Shell

---

### Post by hawkmage on 2011-12-06
The issue is likely that you have two default routes with the same metric.  SInce the eth0 comes up first its entry in the rout table is likely first so that is what is used.  

I have not tested it but you should be able to change the eth1 config to remove the eth0 default route when it comes up like this:
```
auto eth1
iface eth1 inet dhcp
    up ip route del default 192.168.50.1
```

---

