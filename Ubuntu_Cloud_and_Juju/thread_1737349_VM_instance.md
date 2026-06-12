---
title: "VM instance"
date: 2011-04-23
forum: Ubuntu Cloud and Juju
---

### Post by viswacse02 on 2011-04-23
I have bundled the image on the kvm  hypervisor. While installing the cloud controller i gave three ip address for vm instances (10.1.1.106-10.1.1.108). Then i have run the instance on node controller where i have choosen the m1.xlarge vm type. The instance run on 10.1.1.106 (choosen dynamically from the 3 ip address). The main problem is the instance assigned an internal ip 172.19.1.2 I do no why it assigned an internal ip. I have to know whether the internal ip address is changeable because i have to update the instance and install netbeans ide,jdk or some server to get service from the instance. The internal ip address can ping to proxy server but i could not update the instance or ping with websites.I have in turn changed the internal ip address to 10.1.1.106 still i could not resolve.

---

### Post by lemon1707 on 2011-04-30
Hi viswacse02, 
Can you use the public ip of node ? Each instance have tow ip address : Public and Private. In your case Public Ip is : 10.1.1.106. If you want to change your priavte IP, You can open eucalyptus.conf and chang range ips. I can not remember exactly where the location of eucalyptus.conf. You can find out more infomation to do that. Good luck

---

### Post by viswacse02 on 2011-05-03
Thanks for the reply lemon 1707. 

This is the eucalyptus.conf file of node controller.The ip address id node controller is 10.1.1.221

# /etc/eucalyptus/eucalyptus.conf
#
# These are the Ubuntu Enterprise Cloud's default Eucalyptus parameters.

# Affects: All
# See: **NOTE** below
EUCALYPTUS="/"
EUCA_USER="eucalyptus"

# Affects: CLC, Walrus, SC
DISABLE_DNS="Y"
DISABLE_ISCSI="Y"
JVM_MEM="512m"

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


##########################################################################
#
# Administrative overrides and customizations may go below, in accordance
# with the manpage for eucalyptus.conf(5).
#
# However, to modify Eucalyptus parameters, you are advised to use
# euca_conf(8), which will update eucalyptus.local.conf(5) and ensure
# smooth package upgrades.
#
# **NOTE**: To activate changes of these parameters on a CC, you must:
#           sudo restart eucalyptus-cc CLEAN=1
#           HOWEVER, if you do this, all currently running virtual
#           machines in this cluster will lose network connectivity.
#
##########################################################################




This is the eucalyptus.conf of cloud controller. The ip address id cloud controller is 10.1.1.222


# /etc/eucalyptus/eucalyptus.conf
#
# These are the Ubuntu Enterprise Cloud's default Eucalyptus parameters.

# Affects: All
# See: **NOTE** below
EUCALYPTUS="/"
EUCA_USER="eucalyptus"

# Affects: CLC, Walrus, SC
DISABLE_DNS="Y"
DISABLE_ISCSI="Y"
JVM_MEM="512m"

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


##########################################################################
#
# Administrative overrides and customizations may go below, in accordance
# with the manpage for eucalyptus.conf(5).
#
# However, to modify Eucalyptus parameters, you are advised to use
# euca_conf(8), which will update eucalyptus.local.conf(5) and ensure
# smooth package upgrades.
#
# **NOTE**: To activate changes of these parameters on a CC, you must:
#           sudo restart eucalyptus-cc CLEAN=1
#           HOWEVER, if you do this, all currently running virtual
#           machines in this cluster will lose network connectivity.
#
##########################################################################




This is euca-dhcp-conf file of cloud controller where the dynamic private ip address are allotted automatically. I have infact changed the ip address but it automatically changes to the current content. Is there any other way to have both public and private ip address as same one. I don't have clear idea about the mode of configuration like managed vlan, managed no-vlan, system and static. The mamaged no-vlan in this configuration was assigned automatically.

# automatically generated config file for DHCP server
default-lease-time 1200;
max-lease-time 1200;
ddns-update-style none;

shared-network euca {
subnet 172.19.1.0 netmask 255.255.255.224 {
  option subnet-mask 255.255.255.224;
  option broadcast-address 172.19.1.31;
  option domain-name-servers 10.1.1.1, 127.0.0.1;
  option routers 172.19.1.1;
}

host node-172.19.1.2 {
  hardware ethernet d0:0d:4B:EA:08:77;
  fixed-address 172.19.1.2;
}
}

---

### Post by lemon1707 on 2011-05-05
hi viswacse02,
let take a look at [http://open.eucalyptus.com/book/export/html/4263](http://open.eucalyptus.com/book/export/html/4263), it contains everything :Eucalyptus Network Configuration, Networking Mode ...e.g ... I hope It helps you manage your cloud. []("http://ubuntuforums.org/member.php?u=1263951")

---

