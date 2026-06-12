---
title: "Unable to access UEC instance from public ip"
date: 2010-04-14
forum: Server Platforms
---

### Post by Richaa on 2010-04-14
Hi All
I have setrup Ubuntu Enterprise Cloud on a single machine. Please help me 
 
 
1) I am able to run the instances from store (karmic)
On running the instance two ips are assigned (public and private) as 10.B.C.X
and 172.19.1.2
 
2) I am able to connect to the instance (10.B.C.X) through ssh (using key)
 
3) However I am unable to access the instance outside the UEC (using public ip). When I try pinging, I get an error Request timed out or sometimes Destination host unreachable.
 
4) I have provided the following access using euca-authorize
icmp 0 
tcp 22
 
Details below:
1) Hardware : Blade (64 bit)
2) Version : Ubuntu 9.10; Eucalyptus the one using apt-get install eucalyptus
3) Topology : Single physical system
4) Mode : Managed no-vlan
 
interfaces
[HTML] 
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet manual
auto br0
iface br0 inet static
    address 10.B.C.D2
    netmask  255.255.255.x
    network 10.B.C.D3
    broadcast 10.B.C.D4
    gateway 10.B.C.D5
    dns-nameserver 10.B.C.D6 10.B.C.D7
    dns-search ubuntucloud.com
bridge_ports eth0
bridge_fd 9
bridge_hello 2
bridge_maxage 12
bridge_stp off
[/HTML]
 
 
Eucalyptus.conf
VNET_privinterface="br0"
VNET_pubinterface="br0"
VNET_bridge="br0"
VNET_DHCPDAEMON="/usr/sbin/dhcpd3"
 
VNET_MODE="MANAGED-NOVLAN"
VNET_SUBNET="172.19.0.0" -- Default
VNET_NETMASK="255.255.0.0" -- Default
VNET_DNS="10.B.C.D" -- DNS server ip
VNET_ADDRSPERNET="32"
VNET_PUBLICIPS="10.B.C.X" -- Free unallocated static public ip to be assigned
for instances (available in the network)
 
/etc/default/dhcp3-server
Interfaces parameter is empty -- I think it is ok as I am using static public ip
 
$ brctl show
shows 2 bridges br0 (with stp yes and interfaces eth0) and virbr0
 
ifconfig shows
br0
br0:metadata
etho
eth1
virbr0
 
 
 
Thanks and Regards
Richa

---

### Post by kiranmurari on 2010-04-22
Hi,

You should run your instances from the machine from where you want to access the instance, then only ping/ssh from that machine succeeds.

To achieve this, you can use ec2ools (command line tools) or Hybridfox.

If you want to run the instance from another linux machine, follow the steps of
downloading the credentials and setting up the EC2 environment (exporting
EC2_URL etc...) and execute the euca commands to start the instance. Once the
instance is running, you should be able to ping and ssh to the instance.

Similarly, bundling custom images can also be done on a separate machine (not on
the single CC/NC), just by exporting the environment variables from eucarc and
using regular euca bundling commands.
[UEC: Bundling Linux Image]("http://kiranmurari.wordpress.com/2010/03/23/bundling-linux-image-for-uec/")
[UEC: Bundling Windows Image]("http://kiranmurari.wordpress.com/2010/03/29/uec-bundling-windows-image/")

Hope that helps.

---

