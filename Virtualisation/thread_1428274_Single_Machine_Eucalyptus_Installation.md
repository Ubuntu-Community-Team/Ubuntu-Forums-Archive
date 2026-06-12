---
title: "Single Machine Eucalyptus Installation"
date: 2010-03-12
forum: Virtualisation
---

### Post by p_d_austin on 2010-03-12
Is there a how to guide for installing Eucalyptus on a single machine.

I'm using Ubuntu 9.10 server installation with a single Ethernet card and no fancy network configuration. I installed the latest versions of all software as of today.

I've been trying to follow these instructions but the instances start, go to pending and terminate after that.

[https://help.ubuntu.com/community/UEC/PackageInstall](https://help.ubuntu.com/community/UEC/PackageInstall)

I have the node installed on the local machine and I've tried both SYSTEM and STATIC network configuration.

I had an error at some point that the virtual disk size in small wasn't big enough even to run the basic Ubuntu 9.10 - Karmic Koala (i386). I increased the size and got past that error.

VNET_MODE="STATIC"
VNET_SUBNET="192.168.1.0"
VNET_NETMASK="255.255.255.0"
VNET_BROADCAST="192.168.1.255"
VNET_ROUTER="192.168.1.1"
VNET_DNS="192.168.1.1"
VNET_MACMAP="AA:DD:11:CE:FF:ED=192.168.1.200 AA:DD:11:CE:FF:EE=192.168.1.201"

In the nc.log I'm getting

[Fri Mar 12 11:27:04 2010][003309][EUCAERROR ] ERROR: doTerminateInstance() failed error=101

In the cc.log I'm getting the following errors

[Fri Mar 12 11:45:47 2010][001243][EUCAERROR ] bad input params to vnetAttachTunnels()
[Fri Mar 12 11:45:47 2010][001243][EUCAWARN  ] failed to attach tunnels for vlan 10 on bridge eth0
[Fri Mar 12 11:45:48 2010][001243][EUCAWARN  ] in MANAGED-NOVLAN mode, priv interface 'eth0' must be a bridge, tunneling disabled
[Fri Mar 12 11:45:48 2010][001263][EUCAWARN  ] cannot add ip 169.254.169.254

Fri Mar 12 11:45:49 2010][001263][EUCAERROR ] bad input params to vnetAttachTunnels()
[Fri Mar 12 11:45:49 2010][001263][EUCAWARN  ] failed to attach tunnels for vlan 10 on bridge eth0
[Fri Mar 12 11:45:49 2010][001263][EUCAERROR ] could not bring up new device eth0 with ip 172.19.1.1
[Fri Mar 12 11:45:49 2010][001263][EUCAWARN  ] failed to add gateway IP to device eth0
[Fri Mar 12 11:45:49 2010][001263][EUCAWARN  ] in MANAGED-NOVLAN mode, priv interface 'eth0' must be a bridge, tunneling disabled

Which are showing IP addresses not configured for this eucalyptus configuration and it seems to be trying a MANAGED-NOVLAN config even though the config uses STATIC.

If anyone has a howto get such a basic setup running on a single machine that would be great.

Thanks,
Paul

---

### Post by kiranmurari on 2010-03-22
Hi,

From the log you posted:
> [Fri Mar 12 11:45:47 2010][001243][EUCAERROR ] bad input params to vnetAttachTunnels()
[Fri Mar 12 11:45:47 2010][001243][EUCAWARN ] failed to attach tunnels for vlan 10 on bridge eth0
[Fri Mar 12 11:45:48 2010][001243][EUCAWARN ] in MANAGED-NOVLAN mode, priv
interface 'eth0' must be a bridge, tunneling disabled
[Fri Mar 12 11:45:48 2010][001263][EUCAWARN ] cannot add ip 169.254.169.254      Some of the error messages seen in the logs are for advanced features that may not apply to your needs. In particular the above error is related to vtun usage, which is used for multi-cluster.

But are you having problems in running your instances and accessing them?
Please see the below link for details on setting up everything on a single machine.
[http://kiranmurari.wordpress.com/2010/03/19/22/](http://kiranmurari.wordpress.com/2010/03/19/22/)
   
Hope this helps.

---

### Post by px43 on 2010-04-07
Hey p_d_austin, did you have much luck getting your setup working?

If you haven't seen it yet, this thread is related
[http://ubuntuforums.org/showthread.php?t=1402602](http://ubuntuforums.org/showthread.php?t=1402602)

---

