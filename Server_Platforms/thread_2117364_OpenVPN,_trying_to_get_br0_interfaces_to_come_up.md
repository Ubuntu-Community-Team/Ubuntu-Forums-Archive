---
title: "OpenVPN, trying to get br0 interfaces to come up"
date: 2013-02-18
forum: Server Platforms
---

### Post by duplex1000 on 2013-02-18
Hello,

I'm trying to get OpenVPN working but when I try to bring my br0 interface up it gives me an error.

The below messages is from when I run

```
/etc/init.d/networking restart
``````

 * Reconfiguring network interfaces...
RTNETLINK answers: No such process
ssh stop/waiting
ssh start/running, process 23617
ssh stop/waiting
ssh start/running, process 23680
add bridge failed: Package not installed
run-parts: /etc/network/if-pre-up.d/bridge exited with return code 1
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

SIOCSIFADDR: No such device
br0: ERROR while getting interface flags: No such device
br0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up br0.

```     ```
/etc/network/interfaces 
``` looks like the following atm:

     ```
auto lo
iface lo inet loopback
        address 127.0.0.1
        netmask 255.0.0.0
        broadcast 127.255.255.255
        up ip route replace 127.0.0.0/8 dev lo


# Auto generated venet0 interfaces
auto venet0
iface venet0 inet static
        address 127.0.0.1
        netmask 255.255.255.255
        broadcast 0.0.0.0
        up route add -net 191.255.255.1 netmask 255.255.255.255 dev venet0
        up route add default gw 191.255.255.1

auto venet0:0
iface venet0:0 inet static
        address 91.250.96.253
        netmask 255.255.255.255

auto br0
iface br0 inet dhcp
        bridge_ports venet0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off
```Any ideas?

---

### Post by koenn on 2013-02-18
> Any ideas?

this ?
```
add bridge failed: Package not installed
```

---

