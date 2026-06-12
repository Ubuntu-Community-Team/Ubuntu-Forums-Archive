---
title: "Vlan and coova chilli"
date: 2015-05-13
forum: Server Platforms
---

### Post by j3r3my2 on 2015-05-13
Hi,
I have had on my server some vlan

```
# interface vers LAN
auto eth0
allow-hotplug eth0
iface eth0 inet static
  address 10.10.40.254
  netmask 255.255.255.0

auto eth0.4
iface eth0.4 inet static
  address 10.10.4.254
  netmask 255.255.255.0

auto eth0.801
iface eth0.801 inet static
  address 10.10.81.254
  netmask 255.255.255.0

auto eth0.802
iface eth0.802 inet static
  address 10.10.82.254
  netmask 255.255.255.0


```


So my file /proc/net/vlan/config
```
VLAN Dev name    | VLAN ID
Name-Type: VLAN_NAME_TYPE_RAW_PLUS_VID_NO_PAD
eth0.4         | 4  | eth0
eth0.801       | 801  | eth0
eth0.802       | 802  | eth0


```

I have use the script in chilli to handle the vlan stuff

But when i start chilli, he just up one vlan.

When i try to restart my networking i got this error message
```
Reconfiguring network interfaces...Removed VLAN -:eth0.802:-
Cannot find device "eth0.802"
Set name-type for VLAN subsystem. Should be visible in /proc/net/vlan/config
ERROR: trying to add VLAN #802 to IF -:eth0:-  error: File exists


```
Does anyone have an idea, why my vlans aren't working  ?

---

