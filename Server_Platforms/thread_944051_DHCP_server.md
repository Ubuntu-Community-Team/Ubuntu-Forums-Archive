---
title: "DHCP server"
date: 2008-10-10
forum: Server Platforms
---

### Post by mzar on 2008-10-10
Hi,

I manage to setup my own dhcp server referring to guide that available in ubuntu documentation. But the problem is ip that start with 192.168.1.0 - 192.168.3.0 cannot access internet. Ip that start 192.168.0.0 only can access internet.

```

authoritative;
default-lease-time         3600;

ddns-update-style          none;
option routers 192.168.0.1;
option domain-name-servers 202.188.0.133,202.188.1.5;
option domain-name "jasper.dungun.my";
shared-network eth1 {
    subnet 192.168.0.0 netmask 255.255.252.0 {
       range 192.168.0.10 192.168.3.254;       
    }
}

```

---

### Post by lykwydchykyn on 2008-10-10
Is the netmask on the router also set to 255.255.252.0?

---

