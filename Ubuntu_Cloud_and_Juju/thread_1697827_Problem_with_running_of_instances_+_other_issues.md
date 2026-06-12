---
title: "Problem with running of instances + other issues"
date: 2011-03-01
forum: Ubuntu Cloud and Juju
---

### Post by snehalmasne on 2011-03-01
Hello there !

I'm sorry to ask help on this clichéd topic as I couldn't get proper solution yet.

I have done cloud setup with UEC x64 on single machine. Everything is OK till the running of instance. When I execute following command :


$ euca-run-instances -k mykey emi-XXXXXXXX -t c1.medium

and then

$ watch -n 5 euca-describe-instances


I get state as 'pending' for hours and hours. Plus sometimes it changes to 'terminated'   :( :(

My output of  tail /var/log/eucalyptus/nc.log  is :

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[Tue Mar  1 21:02:22 2011][003129][EUCADEBUG ] doDescribeInstances() invoked
[Tue Mar  1 21:02:28 2011][003129][EUCADEBUG ] doDescribeResource() invoked
[Tue Mar  1 21:02:28 2011][003129][EUCADEBUG ] doDescribeResource() invoked
[Tue Mar  1 21:02:29 2011][003129][EUCADEBUG ] doDescribeResource() invoked
[Tue Mar  1 21:02:49 2011][003129][EUCADEBUG ] doDescribeInstances() invoked
[Tue Mar  1 21:02:49 2011][003129][EUCADEBUG ] doDescribeInstances() invoked
[Tue Mar  1 21:02:49 2011][003129][EUCADEBUG ] doDescribeInstances() invoked
[Tue Mar  1 21:02:55 2011][003129][EUCADEBUG ] doDescribeResource() invoked
[Tue Mar  1 21:02:55 2011][003129][EUCADEBUG ] doDescribeResource() invoked
[Tue Mar  1 21:02:55 2011][003129][EUCADEBUG ] doDescribeResource() invoked


Obviously I cant ssh the instance until it runs.  :confused:



~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

My  cat /etc/network/interfaces output is :

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet manual

auto br0
iface br0 inet static
        address 172.16.88.223
        netmask 255.255.248.0
        network 172.16.88.0
        broadcast 172.16.95.255
        gateway 172.16.88.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 172.16.7.250 180.149.63.3
        dns-search server1.uohyd.ernet.in
        bridge_ports eth0
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


and cat /etc/eucalyptus/eucalyptus.conf output is :


~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

# /etc/eucalyptus/eucalyptus.conf
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
VNET_BRIDGE="br0"
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
NODES=""
VNET_ADDRSPERNET="10"
VNET_SUBNET="172.19.0.0"
VNET_NETMASK="255.255.0.0"
VNET_DNS="172.16.7.250"
VNET_PUBLICIPS="172.16.88.225-172.16.88.245"

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
#MAX_DISK="100"

##########################################################################
#
# Administrative overrides and customizations may go below, in accordance
# with the manpage for eucalyptus.conf(5).
#
# However, to modify Eucalyptus parameters, you are advised to use
# euca_conf, which will update eucalyptus.local.conf(5) and ensure
# smooth package upgrades.
#
# **NOTE**: To activate changes of these parameters on a CC, you must:
#           sudo restart eucalyptus-cc CLEAN=1
#           HOWEVER, if you do this, all currently running virtual
#           machines in this cluster will lose network connectivity.
#
##########################################################################




I tried searching on this issue but no success. I am clueless now. Please help me out.

Also tell me how 172.19.1.2 coming into picture and how to make instances visible outside LAN.

Thanks in advance !  :P


Regards,

[Snehal Masne]("http://www.TechProceed.com")

---

### Post by nbartolome on 2011-03-01
Use the hybridfox plugin instead of the command line.

Create a new user from the web interface and give it admin rights.

Using hybridfox, generate a new keypair for this new user and try running the instance as this new user.

Also watch /var/log/eucalyptus/nc.log on the NC while the instance is launching since that log seems to get updated all the time and just the last 10 lines of it might not be enough to work from.

Good luck.

---

### Post by scubablue on 2011-11-16
No luck with hybridfox get

An error occurred while calling DescribeInstances

---

