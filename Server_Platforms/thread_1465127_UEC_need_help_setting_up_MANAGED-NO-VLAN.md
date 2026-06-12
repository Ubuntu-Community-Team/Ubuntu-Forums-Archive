---
title: "UEC: need help setting up MANAGED-NO-VLAN"
date: 2010-04-29
forum: Server Platforms
---

### Post by deathwashd on 2010-04-29
Hi All, I'm trying to get my cloud up and running on 10.04 RC, no luck so far...

A short summary of my 2-server setup:

**CLC/Walrus/CC/SC:**
external IP on eth0
private IP on eth1 : 172.17.0.1

**NC:  **private IP 172.17.0.100

**Instances** should run on 192.168.2.x range

[SIZE=2]**The CLC server is configured as shown below:**[/SIZE]

**/etc/network/interfaces**

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
        address 77.73.98.231
        netmask 255.255.255.224
        network 77.73.98.224
        broadcast 77.73.98.255
        gateway 77.73.98.254
        dns-nameservers 8.8.8.8
        dns-search clubit.be

auto eth1
iface eth1 inet static
        address 172.17.0.1
        netmask 255.255.255.0
        network 172.17.0.0
        broadcast 172.17.0.255

#iface eth1 inet manual

#auto br0
#iface br0 inet static
#       bridge_ports eth1
#       bridge_fd 9
#       bridge_hello 2
#       bridge_maxage 12
#       bridge_stp off

**/etc/eucalyptus/eucalyptus.conf**

VNET_PUBINTERFACE="eth0"
VNET_PRIVINTERFACE="eth1"

VNET_BRIDGE="br0"

VNET_MODE="MANAGED-NOVLAN"
VNET_SUBNET="192.168.0.0"
VNET_NETMASK="255.255.0.0"
VNET_DNS="8.8.8.8"
VNET_ADDRSPERNET="64"
VNET_PUBLICIPS="77.73.98.232 77.73.98.233 77.73.98.236"

[SIZE=2]**The NC is configured as shown below:**[/SIZE]

**/etc/network/interfaces**

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet manual

auto br0
iface br0 inet static
        address 172.17.0.100
        netmask 255.255.255.0
        network 172.17.0.0
        broadcast 172.17.0.255
        gateway 172.17.0.1
        dns-nameservers 172.17.0.1
        dns-search clubit.be
        bridge_ports eth1
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

**/etc/eucalyptus/eucalyptus.conf**

VNET_PUBINTERFACE="br0"
VNET_PRIVINTERFACE="br0"

VNET_BRIDGE="br0"
VNET_MODE="MANAGED-NOVLAN"

any help would be very welcome,  I cannot get this network setup to work the way I need it to.

---

### Post by yogesh.girikumar on 2010-05-06
Hi,

You might find this useful: [http://cssoss.wordpress.com/2010/04/22/uec-installation-on-ubuntu-10-04-lucid-lynx/](http://cssoss.wordpress.com/2010/04/22/uec-installation-on-ubuntu-10-04-lucid-lynx/)

HTH,

---

### Post by wcorey on 2010-05-08
Hi, I have a quick question. You said you can't get it to work the way you need it to. Does that mean you could get it to work at all?

I have, perhaps, the same problem.


After MUCH heartburn I have the nc running and the walrus/sc/cc/clc running.

I can create volumes in the sc for the cluster. 
I can not run an EMI. It fails for "not enough resources".


In the cluster log I see the following:

[Sat May  8 20:05:38 2010][015541][EUCAINFO  ] DescribeNetworks(): called
[Sat May  8 20:05:38 2010][015541][EUCADEBUG ] DescribeNetworks(): params: userId=eucalyptus, nameserver=192.168.0.6, ccsLen=1
[Sat May  8 20:05:38 2010][015541][EUCADEBUG ] vnetSetCCS(): input CC=192.168.0.6
[Sat May  8 20:05:38 2010][015541][EUCADEBUG ] vnetSetCCS(): setting localIpId: 0
[Sat May  8 20:05:38 2010][015524][EUCAINFO  ] DescribeResources(): called
[Sat May  8 20:05:38 2010][015524][EUCADEBUG ] DescribeResources(): params: userId=eucalyptus, vmLen=5
[Sat May  8 20:05:38 2010][015524][EUCAWARN  ] vnetInitTunnels(): in MANAGED-NOVLAN mode, priv interface 'eth0' must be a bridge, tunneling disabled
[Sat May  8 20:05:38 2010][015524][EUCAINFO  ] DescribeResources(): resources 0/0 0/0 0/0 0/0 0/0
[Sat May  8 20:05:38 2010][015524][EUCADEBUG ] DescribeResources(): done


I changed MANAGED_NOVLAN to simply MANAGED and I added the bridge name under nc.

Here is my config

# /etc/eucalyptus/eucalyptus.conf
#
# These are the Ubuntu Enterprise Cloud's default Eucalyptus parameters.
> 
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
VNET_PRIVINTERFACE="eth0"
#VNET_MODE="MANAGED-NOVLAN"
VNET_NODE="MANAGED"
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


any thoughts?

I believe I followed the instructions under Packaged install to a tee.
Well, with one exception. I installed the front end on a 10.4 Desktop machine with 2.6GHz quad, 8GB RAM and 512GB disk. I do not understand why the clc, cc, sc, and walrus controllers can not be on the Desktop machine. In other words, why does this REQUIRE 3 machines, node controller(s), walrus/cloud/cluster/storage controller AND a UI machine. If you notice the sizing for the machine to run the controllers except node, it darn near can be a first generation pentium. I am not trying to open a data center here.

---

### Post by wcorey on 2010-05-09
I believe the write-up for, at least, package install of UEC is incorrect.

google Intel Cloud Builder Guilde to Cloud Design and Deployment on Intel Platforms - Ubuntu Enterprise Cloud.

That does a much more thorough job of explaining configuration. 

I also redid all the steps and put the range of public ip addresses on a different subnet (192.168.1)

---

### Post by yogesh.girikumar on 2010-05-10
Hi,
 
If you want to have CC and NC on the same machine, please refer to this:
[http://cssoss.wordpress.com/2010/03/19/uec-cc-nc-single-machine/](http://cssoss.wordpress.com/2010/03/19/uec-cc-nc-single-machine/)

Be warned though, that in this setup, managed and managed_novlan modes do not work !

HTH,

---

### Post by deathwashd on 2010-05-14
I started over with a clean install from 10.04 CD,
everything works now.

I still get the  "vnetInitTunnels(): in MANAGED-NOVLAN mode, priv interface 'eth0' must  be a bridge, tunneling disabled" warning, but my SC works, snapshots work ... all is good!

---

