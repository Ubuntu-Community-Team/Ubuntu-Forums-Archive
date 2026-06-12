---
title: "EUC storage volume will not attach after upgrade to 10.04"
date: 2010-04-28
forum: Server Platforms
---

### Post by deathwashd on 2010-04-28
Eversince I upgraded my  CLC/Walrus/CC/SC and NC machines to from 9.10 to 10.04, I have been unable get my persistent storage working.

A short summary of my 2-server setup:

**CLC/Walrus/CC/SC:**
external IP on eth0
private IP on eth1 : 172.17.0.1

**NC:  **private IP 172.17.0.100

**Instances** run on 192.168.2.x range

when I run this on the CC:
euca-attach-volume -i i-4A6F0839 -d sdb vol-330A04B9
the volume remains available and not in-use.

This is te output of my logfiles when trying to attach storage:

**NC.log **
libvirt: operation failed: adding scsi disk failed /dev/etherd/e0.2: failed to add file=/dev/etherd/e0.2,if=scsi code 9

**CC.log**
[Wed Apr 28 00:45:04 2010][001158][EUCAWARN  ] vnetInitTunnels(): in MANAGED-NOVLAN mode, priv interface 'eth1' must be a bridge, tunneling disabled
[Wed Apr 28 00:45:04 2010][001158][EUCAINFO  ] AttachVolume(): called
[Wed Apr 28 00:45:04 2010][001158][EUCADEBUG ] AttachVolume(): params: userId=admin, volumeId=vol-5A480630, instanceId=i-4A6F0839, remoteDev=/dev/etherd/e0.4, localDev=sdb
[Wed Apr 28 00:45:04 2010][001158][EUCADEBUG ] find_instanceCache(): found instance in cache 'i-4A6F0839/77.73.98.233/192.168.2.2'
[Wed Apr 28 00:45:04 2010][001158][EUCAINFO  ] AttachVolume(): calling attach volume (i-4A6F0839/vol-5A480630) on (172.17.0.100)
[Wed Apr 28 00:45:04 2010][030410][EUCADEBUG ]  calling AttachVol on NC: 172.17.0.100
[Wed Apr 28 00:45:04 2010][030410][EUCAERROR ] ERROR: AttachVolume returned an error
[Wed Apr 28 00:45:04 2010][001158][EUCADEBUG ]  call complete (pid/rc): 30410/1
[Wed Apr 28 00:45:04 2010][001158][EUCAERROR ] AttachVolume(): call to NC failed: instanceId=i-4A6F0839
[Wed Apr 28 00:45:04 2010][001158][EUCADEBUG ] AttachVolume(): done.
[Wed Apr 28 00:45:04 2010][001158][EUCAERROR ] vnetAttachTunnels(): bad input params
[Wed Apr 28 00:45:04 2010][001158][EUCADEBUG ] maintainNetworkState(): failed to attach tunnels for vlan 10 during maintainNetworkState()
[Wed Apr 28 00:45:04 2010][001158][EUCAERROR ] shawn(): network state maintainance failed
[Wed Apr 28 00:45:04 2010] ERROR: doAttachVolume() returned FAIL

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

any help would be very welcome,  I cannot get this to work after serveral days of trying

---

### Post by robertlight on 2010-10-18
Did you ever solve your SC problem?  I have a similar problem and a similar setup.

Any ideas would be much appreciated.

Thanks.

  -Bob

---

