---
title: "clients in VLAN don't ask for an IP"
date: 2013-03-17
forum: Server Platforms
---

### Post by SeaKing on 2013-03-17
Hello,

I'm currently trying to set up a DHCP Server for 2 VLANs.
The setup: 
1 DHCP Server with 1 NIC connected to a LevelOne GES-1652 Switch, which has 2 VLANs configured 
VLAN50 (Port 1,2,4,6,8,10,12,14,16)
VLAN60 (Port 1, 3,5,7)

Port 1 is the "Uplink" where the DHCP-Server is connected.

/etc/network/interfaces:
```

#vlan config part:
auto vlan50
iface vlan50 inet static
address 192.168.50.1
subnet 255.255.255.0
vlan_raw_device eth1

auto vlan60
iface vlan60 inet static
address 192.168.60.1
subnet 255.255.255.0
vlan_raw_device eth1

```

dhcpd.conf
```

authoritative;
log-facility local7;



#########################Subnetconfig for seaking.lan#############

subnet 192.168.50.0 netmask 255.255.255.0 {
  range 192.168.50.20 192.168.50.150; 
  option domain-name-servers 192.168.50.1; 
  option domain-name "seaking.lan"; 
  option routers 192.168.50.1;
  option broadcast-address 192.168.50.255; 
  default-lease-time 3600; 
  max-lease-time 7200;

}

subnet 192.168.60.0 netmask 255.255.255.0 {
  range 192.168.60.2 192.168.60.150; 
  option domain-name-servers 192.168.60.1; 
  option domain-name "testing.seaking.lan"; 
  option routers 192.168.60.1;
  option broadcast-address 192.168.60.255; 
  default-lease-time 3600; 
  max-lease-time 7200;

}


```

vlan package is installed and the networking and isc-dhcp-server services starting without any problems but if I connect a device to port 6 (vlan50) on the switch the dhcp server does not get any dhcp request

Some ideas?

---

### Post by koenn on 2013-03-17
you quite sure that /etc/network/interfaces is correct ?

I'm not really familiar with this, but i remember seeing vlan configs expressed like this :
```

auto eth0.222
iface eth0.222 inet static
        address 10.10.10.1
        netmask 255.255.255.0
        vlan_raw_device eth0

```
i.e the interface name should be the raw interface name (the same as specified by vlan_raw_device), then a dot, then the VLAN ID, for example eth0.100. Also, the whitespace matters

not exactly the way you did it. 
Where did you get that from ?  Do these interfaces even come up (can you see them in the output of 'ipconfig') ?

---

### Post by darkod on 2013-03-17
I also thought eth0.50 would be the way you do it. But it seems in that case you don't need the vlan_raw_device option at all. On the other hand, the manpage says you can do it the way the OP did, but you do need the raw device option like he used it.

This thread is bit older but uses the eth0.50 way:
[http://ubuntuforums.org/showthread.php?t=703387](http://ubuntuforums.org/showthread.php?t=703387)

The manpage says both ways should work, among others:
[http://manpages.ubuntu.com/manpages/hardy/man5/vlan-interfaces.5.html](http://manpages.ubuntu.com/manpages/hardy/man5/vlan-interfaces.5.html)

In any case confirm that ifconfig is showing the interfaces as up and running. If it does, it's probably the dhcp setup playing up on you.

---

