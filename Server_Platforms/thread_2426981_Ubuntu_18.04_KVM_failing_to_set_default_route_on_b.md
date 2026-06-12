---
title: "Ubuntu 18.04 KVM failing to set default route on bootup"
date: 2019-09-16
forum: Server Platforms
---

### Post by lhprojects on 2019-09-16
Recently my VPS hosted at OVH abrutly lost connectivity. Upon further inspection, `systemd-networkd` was failing to set default route:  `ens3: Could not set route: Network is unreachable`. It isn't clear to me why this is happening suddenly as configuration below worked fine in the past, no changes to the VPS since it's last maintenance were made that I'm aware of:

```
**/etc/netplan/50-cloud-init.yaml**
```
# This file is generated from information provided by
# the datasource.  Changes to it will not persist across an instance.
# To disable cloud-init's network configuration capabilities, write a file
# /etc/cloud/cloud.cfg.d/99-disable-network-config.cfg with the following:
# network: {config: disabled}
network:
    version: 2
    ethernets:
        ens3:
            dhcp4: false
            addresses:
                - 167.114.129.127/32
                - 2607:5300:201:3100:0:0:0:1225/64
            gateway4: 167.114.129.1
            gateway6: 2607:5300:0201:3100:0000:0000:0000:0001
            match:
                macaddress: fa:16:3e:65:ef:95
            set-name: ens3
```
```
```
**/run/systemd/network/10-netplan-ens3.link**
```
[Match]
MACAddress=fa:16:3e:65:ef:95

[Link]
Name=ens3
WakeOnLan=off
```

```
```
**/run/systemd/network/10-netplan-ens3.network**
```
[Match]
MACAddress=fa:16:3e:65:ef:95
Name=ens3

[Network]
LinkLocalAddressing=ipv6
Address=167.114.129.127/32
Address=2607:5300:201:3100:0:0:0:1225/64
Gateway=167.114.129.1
Gateway=2607:5300:0201:3100:0000:0000:0000:0001
```
```

```
```
ip -4 a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
2: ens3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    inet 167.114.129.127/32 scope global ens3
       valid_lft forever preferred_lft forever
```
```

Manually adding the route, `ip route add default 167.114.129.1 dev ens3`, fails with `nexthop has invalid gateway`. I manually maneuvered around this with `onlink`. Someone with a bit more experience than I could help out by shedding some light on what's going here, would be grateful?

---

### Post by SeijiSensei on 2019-09-16
The default gateway  167.114.129.1 is not pingable from outside.  Running a traceroute to the address ends at be7.bhs-s5-6k.qc.ca [178.32.135.50].  You probably need to talk to your provider.

---

