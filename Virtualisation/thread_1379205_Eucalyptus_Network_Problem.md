---
title: "Eucalyptus Network Problem"
date: 2010-01-12
forum: Virtualisation
---

### Post by jws7 on 2010-01-12
Hello all,

Newbie poster, so please bear with me.

I am trying to install Eucalyptus 1.6.1 on Ubuntu (9.10) Karmic Kola. I have been following this guide to do the installation: [https://help.ubuntu.com/community/UEC/PackageInstall](https://help.ubuntu.com/community/UEC/PackageInstall)

Everything works fine until I try to spin up some instances, at which point I get some problems. The instances begin to run, but never get past pending. The setup is very simple, I have one front end at IP 138.251.198.1 and one node at 138.251.198.11. I am trying to allocate publicly accessible IPs in the range 138.251.198.100-138.251.198.254 to new VMs.

I have installed the standard Ubuntu amd64 image from the store using the web UI. I try to run this image in the standard way.

```
euca-run-instances -k <your key pair> emi-DF74107E
```

The instances begin to run, but never get past pending. This is a sample of euca-describe-instances:
```
RESERVATION     r-38DA06F6      admin   default
INSTANCE        i-452707AB      emi-DF74107E    138.251.198.100 172.19.1.2      pending         mykey   0       m1.small        2010-01-11T22:43:12.262Z        cluster1        eki-F58E10EF    eri-09FF11
5A
RESERVATION     r-486D07EB      admin   default
INSTANCE        i-46090783      emi-DF74107E    138.251.198.101 172.19.1.3      pending         mykey   0       m1.small        2010-01-11T22:43:44.538Z        cluster1        eki-F58E10EF    eri-09FF11
5A


```

The cc.log reports the following:
```
[Mon Jan 11 22:55:55 2010][004454][EUCADEBUG ] DescribeInstances(): called
[Mon Jan 11 22:55:55 2010][004421][EUCAWARN  ] in MANAGED-NOVLAN mode, priv interface 'eth0' must be a bridge, tunneling disabled
[Mon Jan 11 22:55:55 2010][004458][EUCADEBUG ] 	time left for next op: 60
[Mon Jan 11 22:55:55 2010][004458][EUCAINFO  ] 	node=138.251.198.11 mem=16209/15953 disk=422125/421097 cores=8/6
[Mon Jan 11 22:55:55 2010][004458][EUCADEBUG ] refresh_resources(): done
[Mon Jan 11 22:55:55 2010][004454][EUCADEBUG ] 	timeout(10/10)
[Mon Jan 11 22:55:55 2010][004454][EUCAINFO  ] DescribeInstances(): describing instance i-452707AB, Pending, 0
[Mon Jan 11 22:55:55 2010][004454][EUCADEBUG ] 	i-452707AB in cache
[Mon Jan 11 22:55:55 2010][004454][EUCADEBUG ] refreshing instance 'i-452707AB'
[Mon Jan 11 22:55:55 2010][004454][EUCADEBUG ] returning instance state: i-452707AB/Pending
[Mon Jan 11 22:55:55 2010][004454][EUCAINFO  ] DescribeInstances(): describing instance i-46090783, Pending, 1
[Mon Jan 11 22:55:55 2010][004454][EUCADEBUG ] 	i-46090783 in cache
[Mon Jan 11 22:55:55 2010][004454][EUCADEBUG ] refreshing instance 'i-46090783'
[Mon Jan 11 22:55:55 2010][004454][EUCADEBUG ] returning instance state: i-46090783/Pending
[Mon Jan 11 22:55:55 2010][004454][EUCADEBUG ] DescribeInstances(): done
[Mon Jan 11 22:55:55 2010][004458][EUCADEBUG ] DescribeResources(): done
[Mon Jan 11 22:55:55 2010][004454][EUCAERROR ] bad input params to vnetAttachTunnels()
[Mon Jan 11 22:55:55 2010][004454][EUCADEBUG ] failed to attach tunnels for vlan 10 during maintainNetworkState()
[Mon Jan 11 22:55:55 2010][004454][EUCAERROR ] network state maintainance failed
[Mon Jan 11 22:55:55 2010][004458][EUCAERROR ] bad input params to vnetAttachTunnels()
[Mon Jan 11 22:55:55 2010][004458][EUCADEBUG ] failed to attach tunnels for vlan 10 during maintainNetworkState()
[Mon Jan 11 22:55:55 2010][004458][EUCAERROR ] network state maintainance failed
[Mon Jan 11 22:56:01 2010][004403][EUCAWARN  ] in MANAGED-NOVLAN mode, priv interface 'eth0' must be a bridge, tunneling disabled
[Mon Jan 11 22:56:01 2010][004403][EUCADEBUG ] DescribeNetworks(): called
[Mon Jan 11 22:56:01 2010][004403][EUCADEBUG ] setting localIpId: 0
[Mon Jan 11 22:56:01 2010][004403][EUCADEBUG ] DescribeNetworks(): done
[Mon Jan 11 22:56:01 2010][004403][EUCAERROR ] bad input params to vnetAttachTunnels()
[Mon Jan 11 22:56:01 2010][004403][EUCADEBUG ] failed to attach tunnels for vlan 10 during maintainNetworkState()
[Mon Jan 11 22:56:01 2010][004403][EUCAERROR ] network state maintainance failed
[Mon Jan 11 22:56:01 2010][004405][EUCAWARN  ] in MANAGED-NOVLAN mode, priv interface 'eth0' must be a bridge, tunneling disabled
[Mon Jan 11 22:56:01 2010][004405][EUCADEBUG ] printing instance cache in describeInstances()
[Mon Jan 11 22:56:01 2010][004405][EUCADEBUG ] 	cache: i-452707AB 138.251.198.100 172.19.1.2
[Mon Jan 11 22:56:01 2010][004405][EUCADEBUG ] 	cache: i-46090783 138.251.198.101 172.19.1.3

```

The eucalyptus.conf on the controller (138.251.198.1) is as follows:
```
#
# Eucalyptus configuration. 

####
# These are to instruct the init.d script on what to start.
####

# This variable points to where eucalyptus has been installed.
EUCALYPTUS="/"

# This is the username that you would like eucalyptus to run as
EUCA_USER="eucalyptus"

# Uncomment this field if you do not plan on using the dynamic block
# store functionality of Eucalyptus
# DISABLE_EBS="Y"

# Uncomment this field if you do not plan on using the dynamic DNS
# functionality of Eucalyptus
DISABLE_DNS="Y"

# This variable controls whether ws-security is enabled between
# eucalyptus components.  The default settings provide secure
# connections between the Cloud, Cluster, and Node Controllers and we
# recommend that this feature remains enabled.  If you wish to disable security,
# you must change this variable to "N" and manually configure the
# services.xml for both Cluster and Node Controllers (see documentation
# for more details).
ENABLE_WS_SECURITY="Y"

# This variable controls the level of logging output that appears in
# various eucalyptus log files.  The options are, in descending order
# of verbosity, 'DEBUG, INFO, WARN, ERROR, and
# FATAL'. The default is DEBUG (everything).
LOGLEVEL="DEBUG"

####
# These following are Cluster Controller configuration options.
####

# This is the port the Cluster Controller will be listening on.
CC_PORT="8774"

# This option configures the Cluster Controller's scheduling policy.
# Currently, this option can be set to GREEDY (first node that is
# found that can run the VM will be chosen), ROUNDROBIN (nodes are
# selected one after another until one is found that can run the VM),
# or POWERSAVE (nodes are put to sleep when they are not running VMs,
# and reawakened when new resources are required.  VMs will be placed
# on the first awake machine, followed by machines that are asleep).
SCHEDPOLICY="ROUNDROBIN"

# Powersave options.  POWER_IDLETHRESH is the number of seconds that a
# node can remain idle (i.e. no running VMs) before a powerdown is
# attempted.  POWER_WAKETHRESH is the number of seconds that
# Eucalyptus should wait after attempting a node wake-up before it
# will consider the node actually down (and not waking up).
POWER_IDLETHRESH="300"
POWER_WAKETHRESH="300"

# The list of Node Controllers the Cluster Controller will communicate with. 
#
# If you are running Rocks, you can run "rocks list host" to
# find out the list of machines available to you (in our case we are
# interested in the VM Container kind).
NODES=" 138.251.198.11"

# The name of the Node Controller service. Change this if you want
# to plug in your own Node Controller service.
NC_SERVICE="axis2/services/EucalyptusNC"

####
# The following are Node Controller configuration options.
####

# This is the port the Node Controller will be listening on. 
NC_PORT="8775"

# The hypervisor that the Node Controller will interact with in order
# to manage virtual machines.  Currently, supported values are 'kvm'
# and 'xen'.
HYPERVISOR="not_configured"

# The maximum amount of memory Eucalyptus is allowed to use on the node:
# if you leave this commented out, Eucalyptus will use all available
# memory, otherwise it will use at most this value for ALL running instances.
# MAX_MEM=2048

# The maximum number of CPU/cores Eucalyptus is allowed to use on the
# node (at the moment we don't differentiate between cores and CPU). If
# you leave this commented out, Eucalyptus will use all available
# CPU/cores it can find. 
# MAX_CORES="2"

# The size of the swap partition, in MB, for each instance started on the 
# node (default is 512MB).  If the maximum disk allowed for the instance 
# is not big enough to accommodate the swap together with the root partition, 
# then no swap is allocated.  If there is extra room left, then an "ephemeral" 
# partition will be created, available as /dev/sda3 inside the VM.
# SWAP_SIZE=512

# Setting this to 1 disables the cleanup of instance files (root, kernel,
# ramdisk) for failed and terminated instances.  This is not 
# recommended for normal use, but it can be useful in debugging VM startup.
# MANUAL_INSTANCES_CLEANUP=0

####
# The following are options for image storage on the Node Controller
####

# This variable points to a directory which is used by the Node Controller
# to store images of running instances as well as local cached copies of
# images.  The running images will be deleted after the instance is
# terminated, but the cached copies will persist, subject to LRU cache
# replacement and the NC_CACHE_SIZE size limit, below.  So, this
# partition should be at least as big as the cache size (or the maximum
# space needed by all images, whichever is bigger) plus the maximum space
# needed by the maximum number of instances allowed on the node.
# This directory should be local to the Node Controller (as
# opposed to a NFS share) for performance reasons.
INSTANCE_PATH="not_configured"

# The maximum amount of disk space, in Megabytes, that Eucalyptus is 
# allowed to use in the cache directory (INSTANCES_PATH/eucalyptus/cache).
# A generous size is recommended.  Setting this to zero disables caching.
# NC_CACHE_SIZE=99999

####
# The following are networking options
####

# VNET_PRIVINTERFACE and VNET_PUBINTERFACE specify the local physical
# ethernet interfaces that eucalyptus should use to manage the VM
# network.  On the front-end, VNET_PRIVINTERFACE should be set to the
# device that is attached to the same ethernet network as your nodes.
# VNET_PUBINTERFACE should be set to the device which is connected to
# the 'public' network.  If you have only one interface, these should
# be set to the same value.  On the nodes, both should be set to
# either the name of the bridge that has been set up by Xen (xenbr0,
# eth0, etc), or the physical ethernet device that is attached to the
# xen bridge (peth0, peth1, etc), depending on your xen configuration.
VNET_PUBINTERFACE="eth1"
VNET_PRIVINTERFACE="eth2"

# (node setting only) VNET_BRIDGE should be set to the name of the
# bridge that xen has configured.  This is typically named 'xenbr0,
# xenbr1, etc' on older Xen versions, and 'eth0, eth1, etc' on newer
# Xen versions.  The command 'brctl show' will give you more
# information on your local bridge setup.
VNET_BRIDGE="br0"

# This indicates where we have a dhcp server binary. We use it to provide
# the images with IPs: Eucalyptus provides its own configuration per
# instance. 
VNET_DHCPDAEMON="/usr/sbin/dhcpd3"

# Some systems have their DHCP daemon configured to run as a non-root
# user.  If this is the case, set the name of that user here (by
# default, Eucalyptus will set up DHCPD configuration files and
# directories as owned by root).
VNET_DHCPUSER="dhcpd"

# Following are example eucalyptus VM networking configurations.
# There are four modes to choose from (MANAGED, MANAGED-NOVLAN,
# SYSTEM, or STATIC) and each has its own sub-options.  The first
# modes (MANAGED, MANAGED-NOVLAN) configure eucalyptus to fully manage
# the VM networks, and enables the ability to use security groups and
# dynamic public IP assignment (with and without vlan tagging of
# security group networks, respectively).  VNET_SUBNET should be set
# to an IP subnet that is free for eucalyptus to use (i.e. no other
# system connected to your network directly is configured with
# addresses from this subnet).  VNET_NETMASK defines the size of the
# subnet.  VNET_DNS should be set to a DNS server that your systems
# use (usually safe to use the same DNS that is configured on the
# front-end).  VNET_ADDRSPERNET can be used to limit the number of
# instances that can be attached to each named security group
# simultaneously.  Finally, VNET_PUBLICIPS should be set to any public
# IPs, that are currently unused, that can be dynamically assigned to
# VMs.  Of these options, only VNET_PUBLICIPS can be left blank or
# undefined.  If you are running in multi-cluster mode (more than one
# CC), you should uncomment VNET_LOCALIP and set it to the local IP of
# the CC that is accessible by all other CCs in the system.  If
# VNET_LOCALIP is unset, the CC will try to determine the list of all
# IPs currently assigned to the machine at CC run time.  If your CC
# and CLC are on different machines, uncomment VNET_CLOUDIP and set it
# to your cloud-contoller's IP address (must be an address that can be
# reached by the CC).

#VNET_MODE="MANAGED-NOVLAN"
#VNET_SUBNET="192.168.0.0"
#VNET_NETMASK="255.255.0.0"
#VNET_DNS="your-dns-server-ip"
#VNET_ADDRSPERNET="32"
#VNET_PUBLICIPS="your-free-public-ip-1 your-free-public-ip-2 ..."
#VNET_LOCALIP="your-public-interface's-ip"
#VNET_CLOUDIP="your-cloud-controller's-ip"

# If you would like eucalyptus to not manage the VM network at all,
# you can set VNET_MODE to SYSTEM.  In this mode, VM interfaces are
# attached directly to your physical ethernet, at which point they
# will typically invoke a DHCP client to aquire an IP address.  Use
# this mode if you wish to manage VM IPs yourself, or allow the VMs to
# pick up an IP from a non-eucalyptus managed DHCP server.
#VNET_MODE="SYSTEM"

# If VNET_MODE is set to STATIC, you can manually configure a set of
# IP addresses that will be allocated to VMs at boot time in a first
# come, first served manner.  VNET_SUBNET, VNET_NETMASK, and
# VNET_BROADCAST define your subnet (front-end must have an interface
# configured on this subnet).  VNET_ROUTER defines the subnet's
# gateway.  VNET_DNS is a nameserver address.  It is usually safe to
# get these settings by examining your front-end network settings and
# duplicating them here.  VNET_MACMAP is a list of mac address/IP
# address mappings that you would like to be allocated to VMs at run
# time (see example below for the format of this list).
#VNET_MODE="STATIC"
#VNET_SUBNET="192.168.1.0"
#VNET_NETMASK="255.255.255.0"
#VNET_BROADCAST="192.168.1.255"
#VNET_ROUTER="192.168.1.1"
#VNET_DNS="192.168.1.1"
#VNET_MACMAP="AA:DD:11:CE:FF:ED=192.168.1.2 AA:DD:11:CE:FF:EE=192.168.1.3"

# network configuration from the input configuration file
VNET_MODE="MANAGED-NOVLAN"
VNET_SUBNET="138.251.198.0"
VNET_NETMASK="255.255.255.0"
VNET_DNS="138.251.206.2"
VNET_ADDRSPERNET="32"
VNET_PUBLICIPS="138.251.198.100-138.251.198.254"

```

The /etc/network/interfaces file on 138.251.198.1 is as follows:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet static
	address 138.251.214.32
	netmask 255.255.255.0
	network 138.251.214.0
	broadcast 138.251.214.255
	gateway 138.251.214.1
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 138.251.206.2
	dns-search cs.st-andrews.ac.uk

auto eth2
iface eth2 inet static
	address 138.251.198.1
	netmask 255.255.255.0
	network 138.251.198.0
	broadcast 138.251.198.255

```
Where 138.251.214.x is our route to the outside world, and 138.251.198.x our cloud subnet

iptables-L on 138.251.198.1 reports:
```
sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            ctstate ESTABLISHED 
ACCEPT     all  --  anywhere            !172.19.0.0/16       
ACCEPT     all  --  172.19.1.0/27        172.19.1.0/27       
admin-default  all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain admin-default (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             172.19.1.0/27       tcp dpt:ssh 

```

I also have dhcp server running on 138.251.198.1 with the following configuration:
```
#
# Sample configuration file for ISC dhcpd for Debian
#
# Attention: If /etc/ltsp/dhcpd.conf exists, that will be used as
# configuration file instead of this file.
#
# $Id: dhcpd.conf,v 1.1.1.1 2002/05/21 00:07:44 peloy Exp $
#

# The ddns-updates-style parameter controls whether or not the server will
# attempt to do a DNS update when a lease is confirmed. We default to the
# behavior of the version 2 packages ('none', since DHCP v2 didn't
# have support for DDNS.)
ddns-update-style none;

# option definitions common to all supported networks...
option domain-name "cs.st-andrews.ac.uk";
option domain-name-servers 138.251.206.2, 138.251.206.3;

default-lease-time 600;
max-lease-time 7200;

# If this DHCP server is the official DHCP server for the local
# network, the authoritative directive should be uncommented.
#authoritative;

# Use this to send dhcp log messages to a different log file (you also
# have to hack syslog.conf to complete the redirection).
log-facility local7;

# No service will be given on this subnet, but declaring it helps the 
# DHCP server to understand the network topology.

#subnet 10.152.187.0 netmask 255.255.255.0 {
#}

# This is a very basic subnet declaration.

#subnet 10.254.239.0 netmask 255.255.255.224 {
#  range 10.254.239.10 10.254.239.20;
#  option routers rtr-239-0-1.example.org, rtr-239-0-2.example.org;
#}

# This declaration allows BOOTP clients to get dynamic addresses,
# which we don't really recommend.

#subnet 10.254.239.32 netmask 255.255.255.224 {
#  range dynamic-bootp 10.254.239.40 10.254.239.60;
#  option broadcast-address 10.254.239.31;
#  option routers rtr-239-32-1.example.org;
#}

# A slightly different configuration for an internal subnet.
#subnet 10.5.5.0 netmask 255.255.255.224 {
#  range 10.5.5.26 10.5.5.30;
#  option domain-name-servers ns1.internal.example.org;
#  option domain-name "internal.example.org";
#  option routers 10.5.5.1;
#  option broadcast-address 10.5.5.31;
#  default-lease-time 600;
#  max-lease-time 7200;
#}

# Hosts which require special configuration options can be listed in
# host statements.   If no address is specified, the address will be
# allocated dynamically (if possible), but the host-specific information
# will still come from the host declaration.

#host passacaglia {
#  hardware ethernet 0:0:c0:5d:bd:95;
#  filename "vmunix.passacaglia";
#  server-name "toccata.fugue.com";
#}

# Fixed IP addresses can also be specified for hosts.   These addresses
# should not also be listed as being available for dynamic assignment.
# Hosts for which fixed IP addresses have been specified can boot using
# BOOTP or DHCP.   Hosts for which no fixed address is specified can only
# be booted with DHCP, unless there is an address range on the subnet
# to which a BOOTP client is connected which has the dynamic-bootp flag
# set.
#host fantasia {
#  hardware ethernet 08:00:07:26:c0:a5;
#  fixed-address fantasia.fugue.com;
#}

# You can declare a class of clients and then do address allocation
# based on that.   The example below shows a case where all clients
# in a certain class get addresses on the 10.17.224/24 subnet, and all
# other clients get addresses on the 10.0.29/24 subnet.

#class "foo" {
#  match if substring (option vendor-class-identifier, 0, 4) = "SUNW";
#}

#shared-network 224-29 {
#  subnet 10.17.224.0 netmask 255.255.255.0 {
#    option routers rtr-224.example.org;
#  }
#  subnet 10.0.29.0 netmask 255.255.255.0 {
#    option routers rtr-29.example.org;
#  }
#  pool {
#    allow members of "foo";
#    range 10.17.224.10 10.17.224.250;
#  }
#  pool {
#    deny members of "foo";
#    range 10.0.29.10 10.0.29.230;
#  }
#}

subnet 138.251.198.0 netmask 255.255.255.0 {
  range 138.251.198.100 138.251.198.254;
  option routers 138.251.198.1;
  option domain-name-servers 138.251.206.2, 138.251.206.3;
  option domain-name "cs.st-andrews.ac.uk";
}


```

On the node (138.251.198.11), the configuration file eucalyptus.conf reads:
```
#
# Eucalyptus configuration. 

####
# These are to instruct the init.d script on what to start.
####

# This variable points to where eucalyptus has been installed.
EUCALYPTUS="/"

# This is the username that you would like eucalyptus to run as
EUCA_USER="eucalyptus"

# Uncomment this field if you do not plan on using the dynamic block
# store functionality of Eucalyptus
# DISABLE_EBS="Y"

# Uncomment this field if you do not plan on using the dynamic DNS
# functionality of Eucalyptus
DISABLE_DNS="Y"

# This variable controls whether ws-security is enabled between
# eucalyptus components.  The default settings provide secure
# connections between the Cloud, Cluster, and Node Controllers and we
# recommend that this feature remains enabled.  If you wish to disable security,
# you must change this variable to "N" and manually configure the
# services.xml for both Cluster and Node Controllers (see documentation
# for more details).
ENABLE_WS_SECURITY="Y"

# This variable controls the level of logging output that appears in
# various eucalyptus log files.  The options are, in descending order
# of verbosity, 'DEBUG, INFO, WARN, ERROR, and
# FATAL'. The default is DEBUG (everything).
LOGLEVEL="DEBUG"

####
# These following are Cluster Controller configuration options.
####

# This is the port the Cluster Controller will be listening on.
CC_PORT="8774"

# This option configures the Cluster Controller's scheduling policy.
# Currently, this option can be set to GREEDY (first node that is
# found that can run the VM will be chosen), ROUNDROBIN (nodes are
# selected one after another until one is found that can run the VM),
# or POWERSAVE (nodes are put to sleep when they are not running VMs,
# and reawakened when new resources are required.  VMs will be placed
# on the first awake machine, followed by machines that are asleep).
SCHEDPOLICY="ROUNDROBIN"

# Powersave options.  POWER_IDLETHRESH is the number of seconds that a
# node can remain idle (i.e. no running VMs) before a powerdown is
# attempted.  POWER_WAKETHRESH is the number of seconds that
# Eucalyptus should wait after attempting a node wake-up before it
# will consider the node actually down (and not waking up).
POWER_IDLETHRESH="300"
POWER_WAKETHRESH="300"

# The list of Node Controllers the Cluster Controller will communicate with. 
#
# If you are running Rocks, you can run "rocks list host" to
# find out the list of machines available to you (in our case we are
# interested in the VM Container kind).
NODES=""

# The name of the Node Controller service. Change this if you want
# to plug in your own Node Controller service.
NC_SERVICE="axis2/services/EucalyptusNC"

####
# The following are Node Controller configuration options.
####

# This is the port the Node Controller will be listening on. 
NC_PORT="8775"

# The hypervisor that the Node Controller will interact with in order
# to manage virtual machines.  Currently, supported values are 'kvm'
# and 'xen'.
HYPERVISOR="kvm"

# The maximum amount of memory Eucalyptus is allowed to use on the node:
# if you leave this commented out, Eucalyptus will use all available
# memory, otherwise it will use at most this value for ALL running instances.
# MAX_MEM=2048

# The maximum number of CPU/cores Eucalyptus is allowed to use on the
# node (at the moment we don't differentiate between cores and CPU). If
# you leave this commented out, Eucalyptus will use all available
# CPU/cores it can find. 
# MAX_CORES="2"

# The size of the swap partition, in MB, for each instance started on the 
# node (default is 512MB).  If the maximum disk allowed for the instance 
# is not big enough to accommodate the swap together with the root partition, 
# then no swap is allocated.  If there is extra room left, then an "ephemeral" 
# partition will be created, available as /dev/sda3 inside the VM.
# SWAP_SIZE=512

# Setting this to 1 disables the cleanup of instance files (root, kernel,
# ramdisk) for failed and terminated instances.  This is not 
# recommended for normal use, but it can be useful in debugging VM startup.
# MANUAL_INSTANCES_CLEANUP=0

####
# The following are options for image storage on the Node Controller
####

# This variable points to a directory which is used by the Node Controller
# to store images of running instances as well as local cached copies of
# images.  The running images will be deleted after the instance is
# terminated, but the cached copies will persist, subject to LRU cache
# replacement and the NC_CACHE_SIZE size limit, below.  So, this
# partition should be at least as big as the cache size (or the maximum
# space needed by all images, whichever is bigger) plus the maximum space
# needed by the maximum number of instances allowed on the node.
# This directory should be local to the Node Controller (as
# opposed to a NFS share) for performance reasons.
INSTANCE_PATH="/var/lib/eucalyptus/instances"

# The maximum amount of disk space, in Megabytes, that Eucalyptus is 
# allowed to use in the cache directory (INSTANCES_PATH/eucalyptus/cache).
# A generous size is recommended.  Setting this to zero disables caching.
# NC_CACHE_SIZE=99999

####
# The following are networking options
####

# VNET_PRIVINTERFACE and VNET_PUBINTERFACE specify the local physical
# ethernet interfaces that eucalyptus should use to manage the VM
# network.  On the front-end, VNET_PRIVINTERFACE should be set to the
# device that is attached to the same ethernet network as your nodes.
# VNET_PUBINTERFACE should be set to the device which is connected to
# the 'public' network.  If you have only one interface, these should
# be set to the same value.  On the nodes, both should be set to
# either the name of the bridge that has been set up by Xen (xenbr0,
# eth0, etc), or the physical ethernet device that is attached to the
# xen bridge (peth0, peth1, etc), depending on your xen configuration.
VNET_PUBINTERFACE="br0"
VNET_PRIVINTERFACE="br0"
#VNET_PUBINTERFACE="eth0"
#VNET_PRIVINTERFACE="eth0"

# (node setting only) VNET_BRIDGE should be set to the name of the
# bridge that xen has configured.  This is typically named 'xenbr0,
# xenbr1, etc' on older Xen versions, and 'eth0, eth1, etc' on newer
# Xen versions.  The command 'brctl show' will give you more
# information on your local bridge setup.
VNET_BRIDGE="br0"

# This indicates where we have a dhcp server binary. We use it to provide
# the images with IPs: Eucalyptus provides its own configuration per
# instance. 
VNET_DHCPDAEMON="/usr/sbin/dhcpd3"

# Some systems have their DHCP daemon configured to run as a non-root
# user.  If this is the case, set the name of that user here (by
# default, Eucalyptus will set up DHCPD configuration files and
# directories as owned by root).
VNET_DHCPUSER="dhcpd"

# Following are example eucalyptus VM networking configurations.
# There are four modes to choose from (MANAGED, MANAGED-NOVLAN,
# SYSTEM, or STATIC) and each has its own sub-options.  The first
# modes (MANAGED, MANAGED-NOVLAN) configure eucalyptus to fully manage
# the VM networks, and enables the ability to use security groups and
# dynamic public IP assignment (with and without vlan tagging of
# security group networks, respectively).  VNET_SUBNET should be set
# to an IP subnet that is free for eucalyptus to use (i.e. no other
# system connected to your network directly is configured with
# addresses from this subnet).  VNET_NETMASK defines the size of the
# subnet.  VNET_DNS should be set to a DNS server that your systems
# use (usually safe to use the same DNS that is configured on the
# front-end).  VNET_ADDRSPERNET can be used to limit the number of
# instances that can be attached to each named security group
# simultaneously.  Finally, VNET_PUBLICIPS should be set to any public
# IPs, that are currently unused, that can be dynamically assigned to
# VMs.  Of these options, only VNET_PUBLICIPS can be left blank or
# undefined.  If you are running in multi-cluster mode (more than one
# CC), you should uncomment VNET_LOCALIP and set it to the local IP of
# the CC that is accessible by all other CCs in the system.  If
# VNET_LOCALIP is unset, the CC will try to determine the list of all
# IPs currently assigned to the machine at CC run time.  If your CC
# and CLC are on different machines, uncomment VNET_CLOUDIP and set it
# to your cloud-contoller's IP address (must be an address that can be
# reached by the CC).

VNET_MODE="MANAGED-NOVLAN"
VNET_SUBNET="138.251.198.0"
VNET_NETMASK="255.255.255.0"
VNET_DNS="138.251.206.2"
VNET_ADDRSPERNET="32"
VNET_PUBLICIPS="138.251.198.100-138.251.198.254"
VNET_LOCALIP="138.251.19.11"
VNET_CLOUDIP="138.251.198.1"

# If you would like eucalyptus to not manage the VM network at all,
# you can set VNET_MODE to SYSTEM.  In this mode, VM interfaces are
# attached directly to your physical ethernet, at which point they
# will typically invoke a DHCP client to aquire an IP address.  Use
# this mode if you wish to manage VM IPs yourself, or allow the VMs to
# pick up an IP from a non-eucalyptus managed DHCP server.
#VNET_MODE="SYSTEM"

# If VNET_MODE is set to STATIC, you can manually configure a set of
# IP addresses that will be allocated to VMs at boot time in a first
# come, first served manner.  VNET_SUBNET, VNET_NETMASK, and
# VNET_BROADCAST define your subnet (front-end must have an interface
# configured on this subnet).  VNET_ROUTER defines the subnet's
# gateway.  VNET_DNS is a nameserver address.  It is usually safe to
# get these settings by examining your front-end network settings and
# duplicating them here.  VNET_MACMAP is a list of mac address/IP
# address mappings that you would like to be allocated to VMs at run
# time (see example below for the format of this list).
#VNET_MODE="STATIC"
#VNET_SUBNET="192.168.1.0"
#VNET_NETMASK="255.255.255.0"
#VNET_BROADCAST="192.168.1.255"
#VNET_ROUTER="192.168.1.1"
#VNET_DNS="192.168.1.1"
#VNET_MACMAP="AA:DD:11:CE:FF:ED=192.168.1.2 AA:DD:11:CE:FF:EE=192.168.1.3"

```

Network is set up on node (138.251.198.11) as: 
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
        address 138.251.198.11
        network 138.251.198.0
        netmask 255.255.255.0
        broadcast 138.251.198.255
        gateway 138.251.198.1
        bridge_ports eth0
        bridge_stp off
        bridge_fd 0
        bridge_maxwait 0

```
I have tried running a VM manually using KVM on 138.251.198.11 and these network settings were sufficient to get network access.

Sorry for the amount of information. I really hope someone can help.

---

### Post by eqx311 on 2010-01-14
Hi,

- VNET_SUBNET should be private ip (10/8 or 192.168/16 ...)
- eucalyptus at coud controler will provide NAT for your virtuals instances (try iptables -t nat -L -vxn at CC)
- LOCALIP and CLOUDIP leave commented (if you are not running multiple walrus confo)
- Kill DHCPD3 before starting eucalyptus, it should start own instance with own confo
-* check out /var/run/eucalyptus/euca-dhcpd.conf, this is your new configuration
-* eucalyptus will automaticaly add IP address to your selected interface, so delete that subnet also
-* and if your eucalyptus will start-up dhcp daemon, give me know (ps uax|grep dhcpd3 after booting of eucalyptus) ... becouse mine is not working (won't startup with eucalyptus... DAMN)

btw, VNET_PRIVINTERFACE should be BRIDGE ... couse eucalyptus can add vtund tunnel into this "bridge"

I love this !!! :)

PS: Does anyone else has a problem with "not running dhcpd3" after BOOTING of Eucalyptus ? Give me know... stucked in here for 1 week
Using Ubuntu, Jaunty, 1.6.1~bzr1066-0euca1, amd64

sry for my bad english
cau

---

### Post by akanksha.joshi on 2010-01-22
Hi,

I am also having the same problem... While running instances on ubuntu 9.10 machine............ the instance is running but it is not getting an ip.................
showing allocaTED ip as 0.0.0.0/0
dhcp server in my machhine fails to run...............
can u plz help me..... why its happening?


> **eqx311 said:**
> Hi,

- VNET_SUBNET should be private ip (10/8 or 192.168/16 ...)
- eucalyptus at coud controler will provide NAT for your virtuals instances (try iptables -t nat -L -vxn at CC)
- LOCALIP and CLOUDIP leave commented (if you are not running multiple walrus confo)
- Kill DHCPD3 before starting eucalyptus, it should start own instance with own confo
-* check out /var/run/eucalyptus/euca-dhcpd.conf, this is your new configuration
-* eucalyptus will automaticaly add IP address to your selected interface, so delete that subnet also
-* and if your eucalyptus will start-up dhcp daemon, give me know (ps uax|grep dhcpd3 after booting of eucalyptus) ... becouse mine is not working (won't startup with eucalyptus... DAMN)

btw, VNET_PRIVINTERFACE should be BRIDGE ... couse eucalyptus can add vtund tunnel into this "bridge"

I love this !!! :)

PS: Does anyone else has a problem with "not running dhcpd3" after BOOTING of Eucalyptus ? Give me know... stucked in here for 1 week
Using Ubuntu, Jaunty, 1.6.1~bzr1066-0euca1, amd64

sry for my bad english
cau

---

### Post by jacknjill111 on 2010-01-22
> **akanksha.joshi said:**
> Hi,

I am also having the same problem... While running instances on ubuntu 9.10 machine............ the instance is running but it is not getting an ip.................
showing allocaTED ip as 0.0.0.0/0
dhcp server in my machhine fails to run...............
can u plz help me..... why its happening?

Could you please run  "watch -n5 euca-describe-instances" and report back with results. 

Also, could you please attach /var/log/eucalyptus/nc.log on the node controller

---

### Post by jpmathew on 2010-12-18
Hi JWS7:
I am not sure if this could be a typo:
You have in a configuration file written:
VNET_LOCALIP="138.251.19.11"
Just above that the comments says the following:

If you are running in multi-cluster mode (more than one # CC), you should uncomment VNET_LOCALIP and set it to the local IP of
# the CC that is accessible by all other CCs in the system.  If
# VNET_LOCALIP is unset, the CC will try to determine the list of all
# IPs currently assigned to the machine at CC run time.  If your CC
# and CLC are on different machines, uncomment VNET_CLOUDIP and set it
# to your cloud-contoller's IP address (must be an address that can be
# reached by the CC).

Since your CC is 138.251.198.1 and you have only one, why have it and that too with a wrong IP?
Let us know if this is a wrong or not
Cheers

---

