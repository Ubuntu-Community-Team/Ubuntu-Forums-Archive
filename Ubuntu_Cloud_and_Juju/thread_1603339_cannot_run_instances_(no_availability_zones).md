---
title: "cannot run instances (no availability zones)"
date: 2010-10-22
forum: Ubuntu Cloud and Juju
---

### Post by icorey on 2010-10-22
I installed Ubuntu Enterprise Cloud 10.10 with Eucalyptus 2.0 on some computers and I'm having an issue with registering the nodes.  I run sudo euca_conf --register-nodes "ip1 ip2..." and Eucalyptus adds the nodes to known hosts and doesn't report any errors, but when I run sudo euca_conf --list-nodes, no nodes are reported and euca-describe-availability-zones lists no resources.

```
$ euca-describe-availability-zones verbose
AVAILABILITYZONE	netip_cluster1	192.168.1.2
AVAILABILITYZONE	|- vm types	free / max   cpu   ram  disk
AVAILABILITYZONE	|- m1.small	0000 / 0000   1    192     2
AVAILABILITYZONE	|- c1.medium	0000 / 0000   1    256     5
AVAILABILITYZONE	|- m1.large	0000 / 0000   2    512    10
AVAILABILITYZONE	|- m1.xlarge	0000 / 0000   2   1024    20
AVAILABILITYZONE	|- c1.xlarge	0000 / 0000   4   2048    20
```

As such, when I run euca-run-instances, I get a "Not enough resources" error.  I checked out a number of things, but I can't figure out what the issue is.  One thing that might be relevant, the eucalyptus user can ssh into the node controllers from the cloud controller, but it can't ssh into the cloud controller from the node controller.

Also, a number of commands such as euca-deregister-cluster, euca-describe-walruses, and euca-describe-storage-controllers crash with Python errors like "No module named euca_admin" or "No module names euca_admin.walruses".

Any help would be greatly appreciated.

Some info about what we're trying to do:
Hypervisor: KVM
Network topology: [http://imagebin.ca/img/2A7XBxG.png](http://imagebin.ca/img/2A7XBxG.png)
Networking mode: MANAGED
VNET_PUBINTERFACE="eth0"
VNET_PRIVINTERFACE="eth1"

eucalyptus.conf
```
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
VNET_PUBINTERFACE="eth0"
VNET_PRIVINTERFACE="eth1"
VNET_MODE="MANAGED"

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
# euca_conf(8), which will update eucalyptus.local.conf(5) and ensure
# smooth package upgrades.
#
# **NOTE**: To activate changes of these parameters on a CC, you must:
#           sudo restart eucalyptus-cc CLEAN=1
#           HOWEVER, if you do this, all currently running virtual
#           machines in this cluster will lose network connectivity.
#
##########################################################################
```

and eucalyptus.local.conf
```
# /etc/eucalyptus/eucalyptus.local.conf

# This file is read and written by euca_conf(8)
# WARNING: You should *never* edit this file directly.

# To modify Eucalyptus parameters, either use euca_conf(8), or
# edit /etc/eucalyptus/eucalyptus.conf according to eucalyptus.conf(5).


# network configuration from the input configuration file
VNET_MODE="MANAGED"
VNET_SUBNET="172.19.0.0"
VNET_NETMASK="255.255.0.0"
VNET_DNS="192.168.2.1"
VNET_ADDRSPERNET="32"
VNET_PUBLICIPS="192.168.2.100-192.168.2.253"
```

---

### Post by reinhard-d on 2010-11-28
Same problem here, same topology. 

I made progress by setting up a bridge on the VNET_PRIVINTERFACE and can launch instances, but they stay pending. 

> # euca-describe-clusters
Traceback (most recent call last):
  File "/usr/sbin/euca-describe-clusters", line 4, in <module>
    from euca_admin.clusters import Cluster
ImportError: No module named euca_admin.clusters
I observed that the interface for walrus, sc and cluster is the PUBLIC one although that is reachable from the private segment: 

> #euca_conf --list-clusters
registered clusters:
   Cagluster  192.168.192.16
> #euca_conf --list-nodes
registered nodes:
   192.168.190.3  Cagluster   i-3DC70747  i-469907CA
Suggestions welcome

---

### Post by Rusty au Lait on 2010-11-28
> **icorey said:**
> 
One thing that might be relevant, the eucalyptus user can ssh into the node controllers from the cloud controller, but it can't ssh into the cloud controller from the node controller.


which user? When I log into the CLC to do some administration work I have a user account of my own. This user should be able to log into each computer in the system (CLC, CC, WC, NC, SC) and back if need be. If you can not log into the CC from the NC, it may be a key in the ~/.ssh/known_hosts file that prevents you from gaining access. If you mean the user eucalyptus then you are treading on dangerous grounds. Eucalyptus uses that user name.

> Also, a number of commands such as euca-deregister-cluster, euca-describe-walruses, and euca-describe-storage-controllers crash with Python errors like "No module named euca_admin" or "No module names euca_admin.walruses".
I've had it happen to me now and then. Sometimes I just did not source the eucarc . ~/.euca/eucarc
It also happens when my client host can't reach the CLC do to network problems.
More than one admin user account?
When you clear this up try to deregister the nodes and start again.

> Some info about what we're trying to do:
Hypervisor: KVM
Network topology: [http://imagebin.ca/img/2A7XBxG.png](http://imagebin.ca/img/2A7XBxG.png)
Networking mode: MANAGED
VNET_PUBINTERFACE="eth0"
VNET_PRIVINTERFACE="eth1"
Sorry, I still can not manage MANAGED mode.
Ciao

---

