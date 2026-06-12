---
title: "vlan tagging issue on 12.04.4 LTS"
date: 2014-05-15
forum: Server Platforms
---

### Post by bickyz on 2014-05-15
Hi I have one physical NIC eth0 and I am trying to tag it to a vlan 10 where I am facing following issue: 

**#sudo vconfig add eth0 10**
Added VLAN with VID == 10 to IF -:eth0:-
**#sudo ip addr add 192.168.19.1/24 dev eth0.10**
Cannot find device "eth0.10"
**#ls /proc/net/vlan**
config vlan10

with the command "vconfig add eth0 10" I thought it will create eth0.10

Any help would be much appreciated, thank you.

---

### Post by spynappels on 2014-05-15
It is probably simpler and more robust to do this in /etc/network/interfaces, assuming you have installed the vlan package.

First you need to ensure the 802.1Q module is loaded:

```
sudo modprobe 8021q
```

then edit /etc/network/interfaces, adding the following

```
auto eth0.10
iface eth0.10 inet static
address 192.168.19.1
netmask 255.255.255.0
vlan-raw-device eth0
```

You can then bring the interface up using

```
sudo ifup eth0.10
```

If you make sure that the 802.1Q module is loaded at every boot, this should be persistent across reboots too.

---

### Post by bickyz on 2014-05-16
thank you spynappeals

---

