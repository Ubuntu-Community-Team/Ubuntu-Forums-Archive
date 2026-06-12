---
title: "can you guys check my dchpd.conf?"
date: 2007-04-12
forum: Server Platforms
---

### Post by 13ojo on 2007-04-12
i've got a netboot system running now, which means i've had to setup 2 dhcp servers.

now they only way ive managed to get this working, is by setting the range of the secondary server to be the same as the primary. if it hands out different IP's the etherboot stuff just hangs.

```

not authoritative;
default-lease-time 600;
max-lease-time 7200;
option subnet-mask 255.255.255.0;
option vendor-encapsulated-options 3c:09:45:74:68:65:72:62:6f:6f:74:ff;
option broadcast-address 192.168.0.255;
option routers 192.168.0.1;
option root-path "192.168.0.200:/GEEXBOX/";
next-server 192.168.0.200;
filename "/GEEXBOX/boot/pxelinux.0";
shared-network MSHOME {
subnet 192.168.0.0 netmask 255.255.255.0 {
range 192.168.0.2 192.168.0.33;}
}


```

is what the DHCP3-server is running on my box, the other router is a dlink 604g+ which hands out ips from 2 to 33.

I booted up as many Vmmachines as my pc could take, and it gave different ip's to them all, and different IP's to the physical machines, but am i going to encouter problems with this setup?.


PS. ```

not authoritative;
default-lease-time 600;
max-lease-time 7200;
option subnet-mask 255.255.255.0;
option vendor-encapsulated-options 3c:09:45:74:68:65:72:62:6f:6f:74:ff;
option broadcast-address 192.168.0.255;
option routers 192.168.0.1;
option root-path "192.168.0.200:/GEEXBOX/";
next-server 192.168.0.200;
filename "/GEEXBOX/boot/pxelinux.0";
shared-network MSHOME {
subnet 192.168.0.0 netmask 255.255.255.0 {
}
}

host Earth {
hardware ethernet 00:0C:29:84:A4:34;
fixed-address 192.168.0.203;
option vendor-encapsulated-options 3c:09:45:74:68:65:72:62:6f:6f:74:ff;
#}

```

craps out, the first router seems to offer 192.168.0.2, then the secondary says such an IP is unavailble (only wants to give out 192.168.0.203) according to syslogs.

---

