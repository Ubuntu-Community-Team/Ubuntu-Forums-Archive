---
title: "UEC NC Connectivity Issue"
date: 2010-06-16
forum: Server Platforms
---

### Post by yoshokun on 2010-06-16
Hi all,

Setting up a MANAGED-NOVLAN UEC Cloud running on 10.04. Very new to the cloud thing, so sorry about any stupidity in advance. We have two systems installed using the Ubuntu 10.4 CD. Details are included at the bottom.

**The problem:**

The CC can access the private cloud net and the private internet-accessible net fine. But the NC (which doesn't even have instances on it yet) cannot get out to the internet to patch via apt-get. It is able to ping 192.168.1.97, but cannot ping or touch any other 192.168.1.* IPs beyond that (including the external gateway for the internet net, which is 192.168.1.1, which also acts as the internal DNS).

Thanks for any help you guys can throw our way, 

**The CC/CLC/WS3/SC's info is:**

_Summarized:_

eth0 - 192.168.1.97. This is static and internet accessible.
eth1 - 192.168.20.1. This is static and the internal net for the cloud.

_The iptables settings are default:_

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

_The ifconfig output is:_

```
eth0      Link encap:Ethernet  HWaddr 00:13:72:3c:bc:75  
          inet addr:192.168.1.97  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:72ff:fe3c:bc75/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11433 errors:163 dropped:0 overruns:0 frame:1
          TX packets:7040 errors:0 dropped:0 overruns:0 carrier:0
          collisions:9 txqueuelen:1000 
          RX bytes:8924456 (8.9 MB)  TX bytes:502889 (502.8 KB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:13:72:3c:bc:76  
          inet addr:192.168.20.1  Bcast:192.168.20.255  Mask:255.255.255.0
          inet6 addr: fe80::213:72ff:fe3c:bc76/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:667 errors:0 dropped:0 overruns:0 frame:0
          TX packets:462 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:83121 (83.1 KB)  TX bytes:56581 (56.5 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:78930 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78930 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:11773385 (11.7 MB)  TX bytes:11773385 (11.7 MB)

```

_The route output is:_

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.20.0    *               255.255.255.0   U     0      0        0 eth1
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         dslrouter       0.0.0.0         UG    100    0        0 eth0

```

_The /etc/network/interfaces file looks like:_

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface (Public)
auto eth0
iface eth0 inet static
address 192.168.1.97
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1

# The cloud interface (Private)
auto eth1
iface eth1 inet static
address 192.168.20.1
netmask 255.255.255.0
broadcast 192.168.20.255

```

_The eucalyptus.conf looks like:_

```

# Affects: All
# See: **NOTE** below
EUCALYPTUS="/"
EUCA_USER="eucalyptus"

# Affects: CLC, Walrus, SC
DISABLE_DNS="Y"
DISABLE_ISCSI="Y"

# Affects: CC, NC
# See: **NOTE** below
ENABLE_WS_SECURITY="Y"
LOGLEVEL="DEBUG"
VNET_PUBINTERFACE="eth0"
VNET_PRIVINTERFACE="eth1"
VNET_MODE="MANAGED-NOVLAN"

# Affects: CC
# See: **NOTE** below
CC_PORT="8774"
SCHEDPOLICY="ROUNDROBIN"
POWER_IDLETHRESH="300"
POWER_WAKETHRESH="300"
NC_SERVICE="axis2/services/EucalyptusNC"
VNET_DHCPDAEMON="/usr/sbin/dhcpd3"
VNET_DHCPUSER="dhcpd"
NODES=""
VNET_ADDRSPERNET="32"
VNET_SUBNET="192.168.2.0"
VNET_NETMASK="255.255.255.0"
VNET_DNS="192.168.1.1"
VNET_PUBLICIPS="192.168.1.99 192.168.1.98"

# Affects: NC
NC_PORT="8775"
HYPERVISOR="kvm"
MANUAL_INSTANCES_CLEANUP=0
VNET_BRIDGE="br0"
INSTANCE_PATH="/var/lib/eucalyptus/instances/"

```

**The NC's info is:**

_Summarized:_

br0 - 192.168.20.2. This is static and the internal net for the cloud and is bridging to eth1, which is set to manual. The default gateway is set to 192.168.20.1 (the CC) and the DNS server is set to 192.168.1.1 (the internet gateway).

_The ifconfig output is:_

```
br0       Link encap:Ethernet  HWaddr 00:1d:09:82:3e:f8  
          inet addr:192.168.20.2  Bcast:192.168.20.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:fe82:3ef8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:115 errors:0 dropped:0 overruns:0 frame:0
          TX packets:175 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10049 (10.0 KB)  TX bytes:21423 (21.4 KB)

eth1      Link encap:Ethernet  HWaddr 00:1d:09:82:3e:f8  
          inet6 addr: fe80::21d:9ff:fe82:3ef8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:182 errors:0 dropped:0 overruns:0 frame:0
          TX packets:409 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:21932 (21.9 KB)  TX bytes:42687 (42.6 KB)
          Memory:fdfc0000-fdfe0000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:105 errors:0 dropped:0 overruns:0 frame:0
          TX packets:105 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4754 (4.7 KB)  TX bytes:4754 (4.7 KB)

virbr0    Link encap:Ethernet  HWaddr 86:fa:ab:6c:8d:ad  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          inet6 addr: fe80::84fa:abff:fe6c:8dad/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:98 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:8055 (8.0 KB)

```

_The route output is:_

```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
localnet        *               255.255.255.0   U     0      0        0 br0
192.168.122.0   *               255.255.255.0   U     0      0        0 virbr0
default         cloudcc.local   0.0.0.0         UG    100    0        0 br0

```

_The /etc/network/interfaces file looks like this:_

```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet manual

auto br0
iface br0 inet static
	address 192.168.20.2
	netmask 255.255.255.0
	network 192.168.20.0
	broadcast 192.168.20.255
	gateway 192.168.20.1
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 192.168.1.1
	dns-search pal.lab
	bridge_ports eth1
	bridge_fd 9
	bridge_hello 2
	bridge_maxage 12
	bridge_stp off
```

_The eucalyptus.conf looks like:_

```


# Affects: All
# See: **NOTE** below
EUCALYPTUS="/"
EUCA_USER="eucalyptus"

# Affects: CLC, Walrus, SC
DISABLE_DNS="Y"
DISABLE_ISCSI="Y"

# Affects: CC, NC
# See: **NOTE** below
ENABLE_WS_SECURITY="Y"
LOGLEVEL="DEBUG"
VNET_PUBINTERFACE="br0"
VNET_PRIVINTERFACE="br0"
VNET_MODE="MANAGED-NOVLAN"

# Affects: CC
# See: **NOTE** below
CC_PORT="8774"
SCHEDPOLICY="ROUNDROBIN"
POWER_IDLETHRESH="300"
POWER_WAKETHRESH="300"
NC_SERVICE="axis2/services/EucalyptusNC"
VNET_DHCPDAEMON="/usr/sbin/dhcpd3"
VNET_DHCPUSER="dhcpd"
NODES=""
VNET_ADDRSPERNET="32"
#VNET_SUBNET=""
#VNET_NETMASK=""
#VNET_DNS=""
#VNET_PUBLICIPS=""

# Affects: NC
NC_PORT="8775"
HYPERVISOR="kvm"
MANUAL_INSTANCES_CLEANUP=0
VNET_BRIDGE="br0"
INSTANCE_PATH="/var/lib/eucalyptus/instances/"

```

---

