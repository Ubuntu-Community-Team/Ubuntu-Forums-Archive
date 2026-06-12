---
title: "Ping reply, but can not Remote Desktop Connect"
date: 2011-05-08
forum: Ubuntu Cloud and Juju
---

### Post by lemon1707 on 2011-05-08
[SIZE=2][FONT=&quot] Hi everybody,[/FONT][/SIZE]
  [SIZE=2][FONT=&quot]I'm in the process of setting up Cloud Coputing, It’s my thesis. I had installed CLC,CC,SC,Walrus,Nc on single machine, but that topology doesn't support for EBS ( Elastic Blocked Storage). I trying to setup Cloud on 2 machines with Ubuntu 11.04 Natty, each machine just have one Nic.[/FONT][/SIZE]
  [SIZE=2][FONT=&quot]On Dell studio 1558 ( CC,CLC,SC,Walrus)[/FONT][/SIZE]
  [SIZE=2]**[FONT=&quot]CC Interfaces : [/FONT]**[/SIZE]
  [SIZE=2][FONT=&quot]auto lo[/FONT][/SIZE]
  [SIZE=2][FONT=&quot]iface lo inet loopback[/FONT][/SIZE]
  
  [SIZE=2][FONT=&quot]auto eth0[/FONT][/SIZE]
  [SIZE=2][FONT=&quot]iface eth0 inet manual[/FONT][/SIZE]
  
  [SIZE=2][FONT=&quot]auto br0[/FONT][/SIZE][SIZE=2][FONT=&quot]iface br0 inet static[/FONT][/SIZE][SIZE=2][FONT=&quot]        address 192.168.1.35[/FONT][/SIZE][SIZE=2][FONT=&quot]        network 192.168.1.0[/FONT][/SIZE][SIZE=2][FONT=&quot]        netmask 255.255.255.0[/FONT][/SIZE][SIZE=2][FONT=&quot]        broadcast 192.168.1.255[/FONT][/SIZE][SIZE=2][FONT=&quot]        gateway 192.168.1.1[/FONT][/SIZE][SIZE=2][FONT=&quot]        bridge_ports eth0[/FONT][/SIZE][SIZE=2][FONT=&quot]        bridge_stp off[/FONT][/SIZE][SIZE=2][FONT=&quot]        bridge_fd 0[/FONT][/SIZE][SIZE=2][FONT=&quot]        bridge_maxwait 0[/FONT][/SIZE][SIZE=2]**[FONT=&quot]Eucalyptus.conf on Front end[/FONT]**[/SIZE]  [SIZE=2][FONT=&quot]# Affects: All
# See: **NOTE** below
EUCALYPTUS="/"
EUCA_USER="eucalyptus"

# Affects: CLC, Walrus, SC
DISABLE_DNS="Y"
CLOUD_OPTS="-Xmx512m"

# Affects: SC
DISABLE_EBS="N"
DISABLE_ISCSI="N"

# Affects: CC, NC
# See: **NOTE** below
ENABLE_WS_SECURITY="Y"
LOGLEVEL="DEBUG"
VNET_PUBINTERFACE="eth0"
VNET_PRIVINTERFACE="eth0"
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
DISABLE_TUNNELLING="N"
NODES="192.168.1.34"
VNET_ADDRSPERNET="32"
VNET_SUBNET="172.19.0.0"
VNET_NETMASK="255.255.255.0"
VNET_DNS="192.168.1.1"
VNET_PUBLICIPS="192.168.1.100-192.168.1.200"

# Affects: NC
NC_PORT="8775"
HYPERVISOR="kvm"
MANUAL_INSTANCES_CLEANUP=0
VNET_BRIDGE="br0"
INSTANCE_PATH="/var/lib/eucalyptus/instances/"
USE_VIRTIO_NET="0"
USE_VIRTIO_DISK="1"
USE_VIRTIO_ROOT="0"
#MAX_MEM=2048
#MAX_CORES="2"
#MAX_DISK="100"[/FONT][/SIZE]
  [SIZE=2]**[FONT=&quot]Eucalyptus.local.conf on Front end[/FONT]**[/SIZE]  [SIZE=2][FONT=&quot]# /etc/eucalyptus/eucalyptus.local.conf

# This file is read and written by euca_conf
# WARNING: You should *never* edit this file directly.

# To modify Eucalyptus parameters, either use euca_conf( 8 , or
# edit /etc/eucalyptus/eucalyptus.conf according to eucalyptus.conf(5).


# network configuration from the input configuration file
VNET_MODE="MANAGED-NOVLAN"
VNET_SUBNET="172.19.0.0"
VNET_NETMASK="255.255.255.0"
VNET_DNS="192.168.1.1"
VNET_ADDRSPERNET="32"
VNET_PUBLICIPS="192.168.1.100-192.168.1.200"[/FONT][/SIZE]
  
  [SIZE=2]**[FONT=&quot]On Dell studio 1555( Node Controller)[/FONT]**[/SIZE]
  [SIZE=2]**[FONT=&quot]Interfaces file[/FONT]**[/SIZE]
  [SIZE=2][FONT=&quot]Vim /etc/network/interfaces[/FONT][/SIZE]
  [SIZE=2][FONT=&quot]auto lo[/FONT][/SIZE]
  [SIZE=2][FONT=&quot]iface lo inet loopback[/FONT][/SIZE]
  
  [SIZE=2][FONT=&quot]auto eth0[/FONT][/SIZE]
  [SIZE=2][FONT=&quot]iface eth0 inet manual[/FONT][/SIZE]
  
  [SIZE=2][FONT=&quot]auto br0[/FONT][/SIZE][SIZE=2][FONT=&quot]iface br0 inet static[/FONT][/SIZE][SIZE=2][FONT=&quot]        address 192.168.1.34[/FONT][/SIZE][SIZE=2][FONT=&quot]        network 192.168.1.0[/FONT][/SIZE][SIZE=2][FONT=&quot]        netmask 255.255.255.0[/FONT][/SIZE][SIZE=2][FONT=&quot]        broadcast 192.168.1.255[/FONT][/SIZE][SIZE=2][FONT=&quot]        gateway 192.168.1.1[/FONT][/SIZE][SIZE=2][FONT=&quot]        bridge_ports eth0[/FONT][/SIZE][SIZE=2][FONT=&quot]        bridge_stp off[/FONT][/SIZE][SIZE=2][FONT=&quot]        bridge_fd 0[/FONT][/SIZE][SIZE=2][FONT=&quot]        bridge_maxwait 0[/FONT][/SIZE]  [SIZE=2]**[FONT=&quot]Eucalyptus.conf[/FONT]**[/SIZE]
  [SIZE=2][FONT=&quot]# /etc/eucalyptus/eucalyptus.conf
#
# These are the Ubuntu Enterprise Cloud's default Eucalyptus parameters.

# Affects: All
# See: **NOTE** below
EUCALYPTUS="/"
EUCA_USER="eucalyptus"

# Affects: CLC, Walrus, SC
DISABLE_DNS="Y"
CLOUD_OPTS="-Xmx512m"

# Affects: SC
DISABLE_EBS="N"
DISABLE_ISCSI="N"

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
DISABLE_TUNNELLING="N"
NODES="192.168.1.34"
VNET_ADDRSPERNET="32"
#VNET_SUBNET=""
#VNET_NETMASK=""
#VNET_DNS=""
#VNET_PUBLICIPS="”[/FONT][/SIZE]
  [SIZE=2][FONT=&quot]
# Affects: NC
NC_PORT="8775"
HYPERVISOR="kvm"
MANUAL_INSTANCES_CLEANUP=0
VNET_BRIDGE="br0"
INSTANCE_PATH="/var/lib/eucalyptus/instances/"
USE_VIRTIO_NET="0"
USE_VIRTIO_DISK="1"
USE_VIRTIO_ROOT="0"
#MAX_MEM=2048
#MAX_CORES="2"
#MAX_DISK="100"[/FONT][/SIZE]
  
  [SIZE=2]**[FONT=&quot]cat eucalyptus.local.conf[/FONT]**[/SIZE]
  [SIZE=2][FONT=&quot]cloud@uec02:/etc/eucalyptus$ **cat eucalyptus.local.conf **
# /etc/eucalyptus/eucalyptus.local.conf

# This file is read and written by euca_conf( 8 )
# WARNING: You should *never* edit this file directly.

# To modify Eucalyptus parameters, either use euca_conf( 8 ) , or
# edit /etc/eucalyptus/eucalyptus.conf according to eucalyptus.conf(5).[/FONT][/SIZE]
  
  [SIZE=2][FONT=&quot]When I run image with Hybridfox, the instance have 2 IPs : public 192.168.1.100, private 172.19.1.2, but when I view the nc.log on Node, something appear like the instane can’t get public IP. The instance is always running state and I can Ping 192.168.1.100 from  the other computer, but I can not Remote Desktop Connection to the instance. ( I enabled the remote desktop for image when I bundle It and open port to RDP)[/FONT][/SIZE]
  [SIZE=2][FONT=&quot]Any ideas for this solution ? [/FONT][/SIZE]
  [SIZE=2][FONT=&quot]The view of nc.log[/FONT][/SIZE]
  [SIZE=2]**[FONT=&quot][Sun May 8  10:45:02 2011][EUCADEBUG] dodescribeInstances(): instanceId=i-2C0706DA publicIP=0.0.0.0 privateIp=172.19.1.2 mac=D0 : 0D : 2C : 07 : 06 : DA vlan=10 networkIndex=2[/FONT]**[/SIZE]

---

### Post by kim0 on 2011-05-10
All ports are by default closed for security reasons. So, you probably want to use euca-authorize to open RDP ports?

---

### Post by lemon1707 on 2011-05-10
thank for replying kim0,
I had already opened RDP port ( also http,ssl, icmp ports ). I think I didn't install kvm-pxe package, It allows VMs connect to Internet and the machine outsite can connect into VMs. But when I reinstall, the VMs always pending state and then terminated. I didn't create br0 as above configuration. Is that problem ?

Please clarify it !!!

---

### Post by kim0 on 2011-05-12
Hi,
I don't think the kvm-pxe package is related to the problems you're seeing. Also I'm not clear what's the status .. Does the instance boot, does it get an IP, is it reachable from CC/CLC, is it reachable from outside .. etc

---

### Post by lemon1707 on 2011-05-12
Sorry kim0,
I had reinstalled system, and then maked another problem in [http://ubuntuforums.org/showthread.php?t=1756331](http://ubuntuforums.org/showthread.php?t=1756331). Can you give me some infomation to solve that ?

---

