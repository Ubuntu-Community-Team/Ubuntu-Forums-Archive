---
title: "Ubuntu 18.04.1 netplan metric priority or Priority Interface with ethernet conecction"
date: 2018-08-23
forum: Virtualisation
---

### Post by icarosnet on 2018-08-23
how can configure priority in new yaml setup network.

in old version i have this:
```

auto lo
iface lo inet loopback
auto new0
iface new0 inet static
    address xxx.xxx.xxx.xxx
    netmask xxx.xxx.xxx.xxx
    up route add default gw aaa.aaa.aaa.aaa metric 10
    down route del default gw aaa.aaa.aaa.aaa

auto new1
iface new1 inet static
    address yyy.yyy.yyy.yyy
    netmask yyy.yyy.yyy.yyy
    up route add default gw bbb.bbb.bbb.bbb
    down route del default gw bbb.bbb.bbb.bbb

```


but I need to prioritize interface with ethernet connection. because i have two, one working and one on backup connection.
yaml files:

```
01-netcfg.yaml
network:
 version: 2
 renderer: networkd
 ethernets:
   epn0s3:
     dhcp4: no
     dhcp6: no
     addresses: [192.168.1.194/24]
     gateway4: 192.168.1.1
     nameservers:
       addresses: [192.168.2.2]
```
backup
```
02-netcfg.yaml
network:
 version: 2
 renderer: networkd
 ethernets:
   epn0s8:
     dhcp4: no
     dhcp6: no
     addresses: [192.168.50.115/24]
     gateway4: 192.168.50.1
     nameservers:
       addresses: [192.168.50.1]
```

I do not get that if one connection falls, the other automatically goes into operation.
the problem is that i get error: "resolution name" when i try to ping [www.google.com]("http://www.google.com") after this -> one not automatical solution is, run some command:

```
//When this connection is not working
sudo ifconfig enp0s8 down
sudo ifconfig enp0s3 up

//or backward
sudo ifconfig enp0s8 up
sudo ifconfig enp0s3 down
```

but i think that this need to be automaticaly and not depending of user.

on fail connection or fail name resolution; linux can't walk through all network devices to try get a solution automatically???

---

