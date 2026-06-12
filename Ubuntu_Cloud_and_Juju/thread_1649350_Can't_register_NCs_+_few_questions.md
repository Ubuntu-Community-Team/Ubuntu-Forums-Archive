---
title: "Can't register NCs + few questions"
date: 2010-12-20
forum: Ubuntu Cloud and Juju
---

### Post by miszko on 2010-12-20
Welcome,

Sorry for my bad english.

I've 3 servers.
A) 1x desktop computer with basic configuration - working as CC, CLC, SC and WS
B) Two servers working as NC, with VT-x technologies and 24GB RAM per server


Server A have a two ethernet cards. First is for internet connection (address for example 192.168.209.x), second (eth1) are for LAN (IP 192.168.10.1) where NC working.

On first server (A), I installed Ubuntu using this tutorial
[https://help.ubuntu.com/community/UEC/CDInstall](https://help.ubuntu.com/community/UEC/CDInstall)

On servers B, when instalation proces prompt the IP address of CC I point the IP address 192.168.10.1. Everything goes ok. 
Server B1 - IP 192.168.10.2
Server B2 - IP 192.168.10.3

After all work done and system goes up, Ive checked if the NCs are registered (with euca_conf --list-nodes).
All seems to be ok. I made new VT machines and install on it ubuntu 10.04. 

But when I restart server A or B(nodes) server configuration crash. Server A can't register nodes (first I'm checking with --list-nodes, nothing in response), Im trying manually register NC (with --register-nodes 192.168.20.2 and .3). Everything goes ok, keys are synchronized, but euca_conf --list-nodes don't list the NC, euca-describe-avavibility-zones shows no free resources. 

Questions:
- What I'm doing wrong? Why I can't register nodes?

- Server time and synchronization between server is very important? I installed and configured NTP service on Server A, but on Serves B I don't install any NTP services. (EDIT: I'm just installed NTP service on B servers and configure NTP. I'm restarted daemon and try to register NC but anything changed.)

- Second question. It is possible to make ONE big new VT machine (over this two NC's server) and when I'm connect new one NC automatically deploy VT machine on the new one. Easier: I want to make one big VT machine over all NCs. In time I want to connect new NCs, and use new resources on VT machine.

Thanks for any answers.
I'm open for any proposals if I'm wrong ;)

Greetings

---

### Post by raymdt on 2010-12-20
Hi mszko,
i'm a bad english speaker too.. :P

-Server time synchronization is very important.
-have you tried to make a clean restart(CLEAN=1) after registering the NC's ?

Befor registrering the NC's you have to change the eucalyptus user's password (on NC's)

```

# passwd eucalyptus

```delete the password after registration

```

#passwd -d eucalyptus

```Can you try these commands an post the output

```

#euca_conf --discover-nodes

``````

#euca_conf --register-nodes **NC1 **NC2

```Additionally the content of /etc/eucalyptus/eucalyptus.con and eucalyptus.local.conf

Regards

---

### Post by miszko on 2010-12-20
Thanks for reply.

I'm registering NCs, restarting service (with CLEAN=1) and no changes.

/etc/eucalyptus/eucalyptus.conf
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

After --register-nodes nothing change in NODE="", same here in eucalyptus.local.conf (whatever I'm done (example euca_conf --register-nodes), no changes)

/etc/eucaluptus/eucalyptus.local.conf
```
# /etc/eucalyptus/eucalyptus.local.conf

# This file is read and written by euca_conf(8)
# WARNING: You should *never* edit this file directly.

# To modify Eucalyptus parameters, either use euca_conf(8), or
# edit /etc/eucalyptus/eucalyptus.conf according to eucalyptus.conf(5).


# network configuration from the input configuration file
VNET_MODE="MANAGED-NOVLAN"
VNET_SUBNET="172.19.0.0"
VNET_NETMASK="255.255.0.0"
VNET_DNS="193.105.125.181"
VNET_ADDRSPERNET="32"
VNET_PUBLICIPS="192.168.209.210-192.168.209.230"

```

BTW, on NCs I'm installed and configured NTP service (I need synchronize time with Server A or all servers (A and B nodes) can be synchronized with external NTP server?)

---

### Post by raymdt on 2010-12-20
Hi ,
the config files seen to be ok.

Did you change the password on the NC's befor registrering???

can you post the output of 

    [B] #euca_conf --discover-nodes      
     #euca_conf --register-nodes **NC1 **NC2 [/B]

and the file** /var/log/eucalyptus/registration.log**  as attachment.

Regards

---

### Post by miszko on 2010-12-20
Log from --discover-nodes

```
New node found on fe80::222:19ff:fe64:178f; add it? [Yn] Y

INFO: We expect all nodes to have eucalyptus installed in //var/lib/eucalyptus/keys for key synchronization.

Trying rsync to sync keys with "fe80::222:19ff:fe64:1639"...ssh: Could not resolve hostname fe80: Name or service not known
rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(601) [sender=3.0.7]
failed.


Trying scp to sync keys to: eucalyptus@fe80::222:19ff:fe64:1639://var/lib/eucalyptus/keys/...
ssh: Could not resolve hostname fe80: Name or service not known
lost connection
failed.

ERROR: could not synchronize keys with fe80::222:19ff:fe64:1639!
The configuration will not have this node.
Hint: to setup passwordless login to the nodes as user eucalyptus, you can
run the following commands on node fe80::222:19ff:fe64:1639:
sudo -u eucalyptus mkdir -p ~eucalyptus/.ssh
sudo -u eucalyptus tee ~eucalyptus/.ssh/authorized_keys > /dev/null <<EOT
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC3iDh4+58Eg2KTvKtVZwRA7CcW3UwlSfboR3BQQi9vc1v74cbDeW83s6l9yKuQRgH7Di+pB5dho4VbqilpycGTTlgq++HGZMKnSUUgaof7/LWS/StThUOMLyf5+9a8XMoBZFHnvje8vAx5aNaA4lvyAQN2JIujDJ4qhmImOyTm1wJ6FwxyWEhLJCLX3HUKlifnKwozkXpQcNJ59LRYk5kG1jSHMX7XRSVkwnEQW7DGD54dPcamW8WAgfwj8BrEV6EwRaEut5iqxo/xjRl/GnPGcmHUwFQiLNqhG3S93q0BF5DsUOD3MgCPWIzk1+YESAhgd/NePaXGiFYBKFq+zJE/ eucalyptus@chmurka
EOT

Be sure that authorized_keys is not group/world readable or writable

Trying rsync to sync keys with "fe80::222:19ff:fe64:178f"...ssh: Could not resolve hostname fe80: Name or service not known
rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(601) [sender=3.0.7]
failed.


Trying scp to sync keys to: eucalyptus@fe80::222:19ff:fe64:178f://var/lib/eucalyptus/keys/...
ssh: Could not resolve hostname fe80: Name or service not known
lost connection
failed.

ERROR: could not synchronize keys with fe80::222:19ff:fe64:178f!
The configuration will not have this node.
Hint: to setup passwordless login to the nodes as user eucalyptus, you can
run the following commands on node fe80::222:19ff:fe64:178f:
sudo -u eucalyptus mkdir -p ~eucalyptus/.ssh
sudo -u eucalyptus tee ~eucalyptus/.ssh/authorized_keys > /dev/null <<EOT
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC3iDh4+58Eg2KTvKtVZwRA7CcW3UwlSfboR3BQQi9vc1v74cbDeW83s6l9yKuQRgH7Di+pB5dho4VbqilpycGTTlgq++HGZMKnSUUgaof7/LWS/StThUOMLyf5+9a8XMoBZFHnvje8vAx5aNaA4lvyAQN2JIujDJ4qhmImOyTm1wJ6FwxyWEhLJCLX3HUKlifnKwozkXpQcNJ59LRYk5kG1jSHMX7XRSVkwnEQW7DGD54dPcamW8WAgfwj8BrEV6EwRaEut5iqxo/xjRl/GnPGcmHUwFQiLNqhG3S93q0BF5DsUOD3MgCPWIzk1+YESAhgd/NePaXGiFYBKFq+zJE/ eucalyptus@chmurka
EOT

Be sure that authorized_keys is not group/world readable or writable

```
It seems a problem with DNS.
Nameserver 8.8.8.8 (Google) in /etc/resolv.conf

But when I register nodes using IP, looks good.

```
miszko@chmurka:~$ sudo euca_conf --register-nodes 192.168.20.2

INFO: We expect all nodes to have eucalyptus installed in //var/lib/eucalyptus/keys for key synchronization.

Trying rsync to sync keys with "192.168.20.2"...done.

miszko@chmurka:~$ sudo euca_conf --register-nodes 192.168.20.3

INFO: We expect all nodes to have eucalyptus installed in //var/lib/eucalyptus/keys for key synchronization.

Trying rsync to sync keys with "192.168.20.3"...done.

```

I've clean up all /var/log/eucalyptus logs files, and this is it after restart.
```

2010-12-20 14:27:40+01:00 | 4505 -> Calling storage myueccluster storage 192.168.209.185
2010-12-20 14:27:40+01:00 | 4503 -> Calling walrus Walrus 192.168.209.185
2010-12-20 14:27:40+01:00 | 4506 -> Calling walrus Walrus 192.168.209.185
2010-12-20 14:27:40+01:00 | 4504 -> Calling cluster myueccluster 192.168.209.185
2010-12-20 14:27:40+01:00 | 4502 -> Calling storage myueccluster storage 192.168.209.185
2010-12-20 14:27:40+01:00 | 4507 -> Calling cluster myueccluster 192.168.209.185
2010-12-20 14:27:40+01:00 | 4520 -> Calling node cluster1 node #2 192.168.20.2
2010-12-20 14:27:40+01:00 | 4526 -> Calling node cluster1 node 192.168.20.3
2010-12-20 14:27:40+01:00 | 4520 -> Node is not a candidate for local cluster.
2010-12-20 14:27:40+01:00 | 4526 -> Node is not a candidate for local cluster.
2010-12-20 14:27:42+01:00 | 4502 -> Cluster myueccluster doesn't exist, retrying in 10 seconds.
2010-12-20 14:27:42+01:00 | 4505 -> Cluster myueccluster doesn't exist, retrying in 10 seconds.

```

If I do --register-nodes no new entry shows in this file.

What means?
```
2010-12-20 14:27:40+01:00 | 4520 -> Node is not a candidate for local cluster.
```

---

### Post by raymdt on 2010-12-21
Hi,
you should first fix the problem with your dns and networksettings.
Why dou you use Google dns for the cloud??
your CLC seems to find NC'c with IPv6 or there are another NC's in your network.
you have to use the Ip's  to register node.

**Eucalyptus is not asking for the password while synchronizing the Keys.  This means that you didn't change the eucalyptus user's password(read my last post) befor  registering the Node**

what is the output of 
euca_conf --list-clusters, --list-walruses, --list-scs  ???

check the files  cc.log(on CLC) and nc.log(on NC'S) to see if the CC communicates with NC's
Search for the line "NODES" in your eucalyptus.conf file and check if it contains the nodes you registered

Look at this [http://open.eucalyptus.com/wiki/EucalyptusTroubleshooting_v1.6](http://open.eucalyptus.com/wiki/EucalyptusTroubleshooting_v1.6)

---

### Post by miszko on 2010-12-21
euca_conf --list-clusters --list-walruses --list-scs

```

registered clusters:
   myueccluster  192.168.209.185
registered walruses:
   Walrus  192.168.209.185
registered storage controllers:
   myueccluster  192.168.209.185

```


This is small part of cc.log, messages are repeated
```
[001267][EUCADEBUG ] ncClientCall(ncDescribeInstances): done clientrc=0 opFail=0
[001267][EUCADEBUG ] refresh_instances(): node 192.168.20.3 idle since 1292876104: (305/300) secon$
[001267][EUCADEBUG ] refresh_instances(): done
[001267][EUCADEBUG ] monitor_thread(): done
[030694][EUCADEBUG ] init_thread(): init=1 B58ED000 5CDA1000 62E9B000 62E20000
[030694][EUCAWARN  ] vnetInitTunnels(): in MANAGED-NOVLAN mode, priv interface 'eth1' must be a br$
[030694][EUCAINFO  ] DescribePublicAddresses(): called
[030694][EUCADEBUG ] DescribePublicAddresses(): params: userId=eucalyptus
[030694][EUCADEBUG ] DescribePublicAddresses(): done
[001267][EUCADEBUG ] monitor_thread(): running
[001267][EUCAINFO  ] refresh_resources(): called
[001267][EUCADEBUG ] ncClientCall(ncDescribeResource): called ncURL=http://192.168.20.2:8775/axis2$
[001341][EUCADEBUG ] DEBUG: requested URI http://192.168.20.2:8775/axis2/services/EucalyptusNC
[001341][EUCADEBUG ]  ncClientCall(ncDescribeResource): ppid=1267 client calling 'ncDescribeResour$
[001341][EUCADEBUG ]  ncClientCall(ncDescribeResource): ppid=1267 done calling 'ncDescribeResource$
[001267][EUCADEBUG ] ncClientCall(ncDescribeResource): done clientrc=0 opFail=0
[001267][EUCADEBUG ] refresh_resources(): received data from node=192.168.20.2 mem=24557/24557 dis$
[001267][EUCADEBUG ] ncClientCall(ncDescribeResource): called ncURL=http://192.168.20.3:8775/axis2$
[001345][EUCADEBUG ] DEBUG: requested URI http://192.168.20.3:8775/axis2/services/EucalyptusNC
[001345][EUCADEBUG ]  ncClientCall(ncDescribeResource): ppid=1267 client calling 'ncDescribeResour$
[001345][EUCADEBUG ]  ncClientCall(ncDescribeResource): ppid=1267 done calling 'ncDescribeResource$
[001267][EUCADEBUG ] ncClientCall(ncDescribeResource): done clientrc=0 opFail=0
[001267][EUCADEBUG ] refresh_resources(): received data from node=192.168.20.3 mem=24557/24557 dis$
[001267][EUCADEBUG ] refresh_resources(): done
[001267][EUCAINFO  ] refresh_instances(): called
[001267][EUCADEBUG ] ncClientCall(ncDescribeInstances): called ncURL=http://192.168.20.2:8775/axis$
[001346][EUCADEBUG ] DEBUG: requested URI http://192.168.20.2:8775/axis2/services/EucalyptusNC
[001346][EUCADEBUG ]  ncClientCall(ncDescribeInstances): ppid=1267 client calling 'ncDescribeInsta$
[001346][EUCADEBUG ]  ncClientCall(ncDescribeInstances): ppid=1267 done calling 'ncDescribeInstanc$
[001267][EUCADEBUG ] ncClientCall(ncDescribeInstances): done clientrc=0 opFail=0
[001267][EUCADEBUG ] refresh_instances(): node 192.168.20.2 idle since 0: (1292876415/300) seconds
[001267][EUCADEBUG ] ncClientCall(ncDescribeInstances): called ncURL=http://192.168.20.3:8775/axis$
[001347][EUCADEBUG ] DEBUG: requested URI http://192.168.20.3:8775/axis2/services/EucalyptusNC
[001347][EUCADEBUG ]  ncClientCall(ncDescribeInstances): ppid=1267 client calling 'ncDescribeInsta$
[001347][EUCADEBUG ]  ncClientCall(ncDescribeInstances): ppid=1267 done calling 'ncDescribeInstanc$
[001267][EUCADEBUG ] ncClientCall(ncDescribeInstances): done clientrc=0 opFail=0
[001267][EUCADEBUG ] refresh_instances(): node 192.168.20.3 idle since 0: (1292876415/300) seconds
[001267][EUCADEBUG ] refresh_instances(): done
[001267][EUCADEBUG ] monitor_thread(): done
[Mon Dec 20 21:20:19 2010][030662][EUCADEBUG ] init_thread(): init=1 AF86F000 56D23000 5CE1D000 5CDA2000

```

It seems that CC communicate with NCs.

nc.log don't exist.

---

### Post by miszko on 2010-12-21
Big thanks to you, raymdt! 

Ok, problem solved. I had bad configuration with clusters and nodes can't register to this cluster.  I clean up all logs and start watching what's wrong. Now it looks that
```
registered clusters:
   cluster1  192.168.209.185
registered walruses:
   walrus  192.168.209.185
registered storage controllers:
   cluster1  192.168.209.185
registered nodes:
   192.168.20.2  cluster1
   192.168.20.3  cluster1

```

euca_describe-avaibility-zones verbose
```
AVAILABILITYZONE        cluster1        192.168.209.185
AVAILABILITYZONE        |- vm types     free / max   cpu   ram  disk
AVAILABILITYZONE        |- m1.small     0008 / 0008   1    192     2
AVAILABILITYZONE        |- c1.medium    0008 / 0008   1    256     5
AVAILABILITYZONE        |- m1.large     0004 / 0004   2    512    10
AVAILABILITYZONE        |- m1.xlarge    0004 / 0004   2   1024    20
AVAILABILITYZONE        |- c1.xlarge    0002 / 0002   4   2048    20

```

---

### Post by raymdt on 2010-12-21
Thanks for the feedback ;)

---

### Post by wdaniels on 2011-01-16
> **miszko said:**
> Ok, problem solved. I had bad configuration with clusters and nodes can't register to this cluster.

Hi miszko, can you elaborate on the configuration problem you found here?

I am facing similar issues...my node appears to register OK, but then is not shown with "euca_conf --list-nodes" (the other 3 components are listed OK) and the node resources are not shown with euca_describe-avaibility-zones verbose (all zero).

I can't find anything in any logs to explain it.

---

