---
title: "SAMBA/DHCP/NMBD issue"
date: 2006-06-03
forum: Server Platforms
---

### Post by global_dev on 2006-06-03
I am trying to setup a dhcp server behind a router (192.168.0.1) to create a 2nd local network ... i intend to move it out to the front once it works.
modem--->router (192.168.0.1) to

ubuntu server-    eth0   192.168.0.177      eth1  10.5.5.31

PC2 has one of 2 addresses depending on if its connected to the router  (192.168.0.136)  or to eth1 to switch to PC2(10.5.5.29)

the switch is a router witth no dhcp server enabled (address of 10.5.5.30)
and all cord is plugged into the lan ports (wan port is empty)

when its at 192.168.0.136 file shares on PC2 can be seen
when its at 10.5.5.29  file shares aren't able to be seen

the dhcp client lease file shows that an address is given as above
                                                                            
dhcpd.conf
```
# A slightly different configuration for an internal subnet
subnet 10.5.5.0 netmask 255.255.255.0 {
        #authoritative;
        range 10.5.5.0 10.5.5.30;
        # option routers 10.5.5.1;
        option routers 192.168.0.1;
        option subnet-mask 255.255.255.224;
        option broadcast-address 10.5.5.31;
        default-lease-time 64800;
        max-lease-time 64800;
        }
```

when smbtree is run when PC2 is behind router i get everything ok
when the same is run behind eth1, i get cli_fail error PC2(20) <0.0.0.0>

I think this should be relatively simple since it is a basic dhcp server

there is no firewall all tcp/udp are accepted in both eth1 and eth0.

any help...

---

