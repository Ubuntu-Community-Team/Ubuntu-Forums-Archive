---
title: "Can not connect internet from vm instances"
date: 2011-04-26
forum: Ubuntu Cloud and Juju
---

### Post by selvawithcommunity on 2011-04-26
hi all and specially kim0 
 
we successfully implemented the private cloud using two machines. the main problem is we cannot access internet from the VM instances.  
we are using the follwoing ip address 
10.1.1.221 for CLC/CC/SC/WS
10.1.1.222 for NC
while installing the CLC/CC/SC/WS we gave the ip series as public ip = 10.1.1.106-10.1.1.108..

***when we run the euca-describe instances give the following:

RESERVATION	r-42470853	admin	default
INSTANCE	i-417607C6	emi-210F15BA	10.1.1.106	172.19.1.2	running	mykey	0		m1.large	2011-04-26T11:42:18.567Z	cluster1eki-6E341ABC
1) the above ip's 10.1.1.106 and 172.19.1.2 both can be pingable from the CLC/CC/SC/WS  but not on the NC.
2) the ip address 172.19.1.2 we unexpected... where it came from?(actually /etc/network/interfaces shows it as automatic DHCP allocation....)
3) beacuse of this 172.19.1.2   we cant connect internet..
[FONT=monospace]
$sudo apt-get install update
[/FONT]sudo: unable to resolve host ip-172-19-1-2
0% [Connecting to archive.ubuntu.com] [Connecting to security.ubuntu.com]

**** our aim is to install the JDK in the ubuntu virtual instances. so we try to connect internet in the instances. but still it is not possible. 
so please help us to get inter net? what have we to do connect internet?
 
4)our configuration file in the CLC/CC/SC is

**********************************************************************************
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

**********************************************************************************

---

### Post by kim0 on 2011-05-03
Hi there :)
Check out the last answer in this thread
[http://open.eucalyptus.com/forum/internet-not-working-inside-instance](http://open.eucalyptus.com/forum/internet-not-working-inside-instance)

---

