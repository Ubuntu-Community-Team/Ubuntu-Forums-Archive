---
title: "After reboot, cannot attach volumes."
date: 2010-09-10
forum: Ubuntu Cloud and Juju
---

### Post by mead.david on 2010-09-10
Hi,

I'm cross posting this message that I submitted to the Eucalyptus forums with hope that someone might have a solution.



                       I am having a frustrating time getting volumes to attach to an instance on a previously working cloud.   
 We have a uec 10.04 cloud with 3 systems, one  cc/sc/walrus and 2 ncs. 



 Due to the cc/sc/walrus only having 1GB of memory we were having  performance issues, so I did an upgrade to 3GB.  While I was doing this,  I also updated all of the packages on the three servers.


 Following the reboot, when trying to connect a volume to an instance I was getting this error:


 [I][Fri Sep 10 09:00:54 2010][001145][EUCADEBUG ]  maintainNetworkState(): failed to attach tunnels for vlan 10 during  maintainNetworkState()
[Fri Sep 10 09:00:54 2010][001145][EUCAERROR ] shawn(): network state maintainance failed
[Fri Sep 10 09:00:54 2010][001107][EUCAERROR ] vnetAttachTunnels(): bad input params
[Fri Sep 10 09:00:54 2010][001107][EUCADEBUG ] maintainNetworkState():  failed to attach tunnels for vlan 10 during maintainNetworkState()
[Fri Sep 10 09:00:54 2010][001107][EUCAERROR ] shawn(): network state maintainance failed
[Fri Sep 10 09:00:54 2010][001109][EUCAERROR ] vnetAttachTunnels(): bad input params
[Fri Sep 10 09:00:54 2010][001109][EUCADEBUG ] maintainNetworkState():  failed to attach tunnels for vlan 10 during maintainNetworkState()
[Fri Sep 10 09:00:54 2010][001109][EUCAERROR ] shawn(): network state maintainance failed
[Fri Sep 10 09:00:56 2010][002051][EUCADEBUG ] monitor_thread(): running
[Fri Sep 10 09:00:56 2010][002051][EUCAINFO  ] refresh_resources(): called
[Fri Sep 10 09:00:56 2010][002051][EUCADEBUG ] refresh_resources(): calling [http://172.24.157.148:8775/axis2/services/EucalyptusNC](http://172.24.157.148:8775/axis2/services/EucalyptusNC)
[Fri Sep 10 09:00:56 2010][002051][EUCADEBUG ] refresh_resources(): time left for next op: 30
[Fri Sep 10 09:00:56 2010][002051][EUCADEBUG ] refresh_resources():  node=172.24.157.148 mem=16199/15943 disk=3413084/3412562 cores=8/7
[Fri Sep 10 09:00:56 2010][002051][EUCADEBUG ] refresh_resources(): calling [http://172.24.157.247:8775/axis2/services/EucalyptusNC](http://172.24.157.247:8775/axis2/services/EucalyptusNC)
[Fri Sep 10 09:00:56 2010][002051][EUCADEBUG ] refresh_resources(): time left for next op: 60
[Fri Sep 10 09:00:56 2010][002051][EUCADEBUG ] refresh_resources():  node=172.24.157.247 mem=16210/16210 disk=522481/522481 cores=8/8
[Fri Sep 10 09:00:56 2010][002051][EUCADEBUG ] refresh_resources(): done
[Fri Sep 10 09:00:56 2010][002051][EUCAINFO  ] refresh_instances(): called
[Fri Sep 10 09:00:56 2010][002051][EUCADEBUG ] refresh_instances(): timeout(30/60) len
[Fri Sep 10 09:00:56 2010][002051][EUCADEBUG ] refresh_instances(): timeout(30/60) inst
[Fri Sep 10 09:00:56 2010][002051][EUCADEBUG ] refresh_instances(): describing instance i-3859065D, Extant, 0
[Fri Sep 10 09:00:56 2010][002051][EUCADEBUG ] find_instanceCache():  found instance in cache 'i-3859065D/172.24.156.110/172.19.1.2'
[Fri Sep 10 09:00:56 2010][002051][EUCADEBUG ] ccInstance_to_ncInstance(): setting volumesSize: 0
[Fri Sep 10 09:00:56 2010][002051][EUCADEBUG ] refresh_instances():  storing instance state: i-3859065D/Extant/172.24.156.110/172.19.1.2
[Fri Sep 10 09:00:56 2010][002051][EUCADEBUG ] refresh_instances(): timeout(60/60) len
[Fri Sep 10 09:00:56 2010][002051][EUCADEBUG ] refresh_instances(): node 172.24.157.247 idle since 1284127158: (98/300) seconds
[Fri Sep 10 09:00:56 2010][002051][EUCADEBUG ] refresh_instances(): done
[Fri Sep 10 09:00:56 2010][002051][EUCADEBUG ] monitor_thread(): done
[Fri Sep 10 09:01:00 2010][001110][EUCAWARN  ] vnetInitTunnels(): in  MANAGED-NOVLAN mode, priv interface 'eth0' must be a bridge, tunneling  disabled
[Fri Sep 10 09:01:00 2010][001110][EUCAINFO  ] DescribeNetworks(): called
[Fri Sep 10 09:01:00 2010][001110][EUCADEBUG ] DescribeNetworks(): params: userId=eucalyptus, nameserver=172.24.157.92, ccsLen=1
[Fri Sep 10 09:01:00 2010][001110][EUCADEBUG ] vnetSetCCS(): input CC=172.24.157.92
[Fri Sep 10 09:01:00 2010][001110][EUCADEBUG ] vnetSetCCS(): setting localIpId: 0
[Fri Sep 10 09:01:00 2010][001171][EUCAINFO  ] DescribeResources(): called
[Fri Sep 10 09:01:00 2010][001171][EUCADEBUG ] DescribeResources(): params: userId=eucalyptus, vmLen=5
[Fri Sep 10 09:01:00 2010][001171][EUCAWARN  ] vnetInitTunnels(): in  MANAGED-NOVLAN mode, priv interface 'eth0' must be a bridge, tunneling  disabled
[Fri Sep 10 09:01:00 2010][001171][EUCAINFO  ] DescribeResources(): resources 15/16 15/16 14/14 6/6 2/2
[Fri Sep 10 09:01:00 2010][001171][EUCADEBUG ] DescribeResources(): done
[Fri Sep 10 09:01:00 2010][001170][EUCAINFO  ] DescribeInstances(): called
[Fri Sep 10 09:01:00 2010][001170][EUCADEBUG ] DescribeInstances(): params: userId=eucalyptus, instIdsLen=0
[Fri Sep 10 09:01:00 2010][001170][EUCAWARN  ] vnetInitTunnels(): in  MANAGED-NOVLAN mode, priv interface 'eth0' must be a bridge, tunneling  disabled
[Fri Sep 10 09:01:00 2010][001170][EUCADEBUG ] DescribeInstances():  returning: instanceId=i-3859065D, state=Extant, publicIp=172.24.156.110,  privateIp=172.19.1.2, volumesSize=0
[Fri Sep 10 09:01:00 2010][001170][EUCADEBUG ] DescribeInstances(): done
[Fri Sep 10 09:01:00 2010][001108][EUCAWARN  ] vnetInitTunnels(): in  MANAGED-NOVLAN mode, priv interface 'eth0' must be a bridge, tunneling  disabled
[Fri Sep 10 09:01:00 2010][001108][EUCAINFO  ] DescribePublicAddresses(): called
[Fri Sep 10 09:01:00 2010][001108][EUCADEBUG ] DescribePublicAddresses(): params: userId=eucalyptus
[Fri Sep 10 09:01:00 2010][001108][EUCADEBUG ] DescribePublicAddresses(): done
[Fri Sep 10 09:01:00 2010][001110][EUCADEBUG ] DescribeNetworks(): done
[Fri Sep 10 09:01:00 2010][001171][EUCAERROR ] vnetAttachTunnels(): bad input params
[Fri Sep 10 09:01:00 2010][001171][EUCADEBUG ] maintainNetworkState():  failed to attach tunnels for vlan 10 during maintainNetworkState()
[Fri Sep 10 09:01:00 2010][001171][EUCAERROR ] shawn(): network state maintainance failed
[Fri Sep 10 09:01:00 2010][001170][EUCAERROR ] vnetAttachTunnels(): bad input params
[Fri Sep 10 09:01:00 2010][001170][EUCADEBUG ] maintainNetworkState():  failed to attach tunnels for vlan 10 during maintainNetworkState()
[Fri Sep 10 09:01:00 2010][001170][EUCAERROR ] shawn(): network state maintainance failed
[Fri Sep 10 09:01:00 2010][001110][EUCAERROR ] vnetAttachTunnels(): bad input params
[Fri Sep 10 09:01:00 2010][001110][EUCADEBUG ] maintainNetworkState():  failed to attach tunnels for vlan 10 during maintainNetworkState()
[Fri Sep 10 09:01:00 2010][001110][EUCAERROR ] shawn(): network state maintainance failed
[Fri Sep 10 09:01:02 2010][002051][EUCADEBUG ] monitor_thread(): running
[Fri Sep 10 09:01:02 2010][002051][EUCAINFO  ] refresh_resources(): called
[Fri Sep 10 09:01:02 2010][002051][EUCADEBUG ] refresh_resources(): calling [http://172.24.157.148:8775/axis2/services/EucalyptusNC](http://172.24.157.148:8775/axis2/services/EucalyptusNC)
[Fri Sep 10 09:01:02 2010][002051][EUCADEBUG ] refresh_resources(): time left for next op: 30
[Fri Sep 10 09:01:02 2010][002051][EUCADEBUG ] refresh_resources():  node=172.24.157.148 mem=16199/15943 disk=3413084/3412562 cores=8/7
[Fri Sep 10 09:01:02 2010][002051][EUCADEBUG ] refresh_resources(): calling [http://172.24.157.247:8775/axis2/services/EucalyptusNC](http://172.24.157.247:8775/axis2/services/EucalyptusNC)
[Fri Sep 10 09:01:02 2010][002051][EUCADEBUG ] refresh_resources(): time left for next op: 60
[Fri Sep 10 09:01:02 2010][002051][EUCADEBUG ] refresh_resources():  node=172.24.157.247 mem=16210/16210 disk=522481/522481 cores=8/8
[Fri Sep 10 09:01:02 2010][002051][EUCADEBUG ] refresh_resources(): done
[Fri Sep 10 09:01:02 2010][002051][EUCAINFO  ] refresh_instances(): called
[Fri Sep 10 09:01:02 2010][002051][EUCADEBUG ] refresh_instances(): timeout(30/60) len
[Fri Sep 10 09:01:02 2010][002051][EUCADEBUG ] refresh_instances(): timeout(30/60) inst
[Fri Sep 10 09:01:02 2010][002051][EUCADEBUG ] refresh_instances(): describing instance i-3859065D, Extant, 0
[Fri Sep 10 09:01:02 2010][002051][EUCADEBUG ] find_instanceCache():  found instance in cache 'i-3859065D/172.24.156.110/172.19.1.2'
[Fri Sep 10 09:01:02 2010][002051][EUCADEBUG ] ccInstance_to_ncInstance(): setting volumesSize: 0
[Fri Sep 10 09:01:02 2010][002051][EUCADEBUG ] refresh_instances():  storing instance state: i-3859065D/Extant/172.24.156.110/172.19.1.2
[Fri Sep 10 09:01:02 2010][002051][EUCADEBUG ] refresh_instances(): timeout(60/60) len
[Fri Sep 10 09:01:02 2010][002051][EUCADEBUG ] refresh_instances(): node 172.24.157.247 idle since 1284127158: (104/300) seconds
[Fri Sep 10 09:01:02 2010][002051][EUCADEBUG ] refresh_instances(): done
[Fri Sep 10 09:01:02 2010][002051][EUCADEBUG ] monitor_thread(): done
[Fri Sep 10 09:01:06 2010][001107][EUCAWARN  ] vnetInitTunnels(): in  MANAGED-NOVLAN mode, priv interface 'eth0' must be a bridge, tunneling  disabled
[Fri Sep 10 09:01:06 2010][001107][EUCAINFO  ] DescribeNetworks(): called
[Fri Sep 10 09:01:06 2010][001107][EUCADEBUG ] DescribeNetworks(): params: userId=eucalyptus, nameserver=172.24.157.92, ccsLen=1[/I]

 Since the error seemed to be looking for a bridge, I found instructions on how to create a bridge here:
 [https://help.ubuntu.com/community/UEC/PackageInstall](https://help.ubuntu.com/community/UEC/PackageInstall)
 

and updated eucalyptus.conf from:
VNET_PRIVINTERFACE="eth0"
to:
VNET_PRIVINTERFACE="br0"
 and restarted eucalyptus.
 

After this, things seem to get further.  On the node controllers, I now get the error:


 [I]doAttachVolume() invoked (id=i-45010781 vol=vol-59FC0630 remote=/dev/etherd/e0.3 local=/dev/sdc)
[Thu Sep  9 15:16:27 2010][007887][EUCAERROR ] libvirt: cannot set  ownership on /dev/etherd/e0.3: No such file or directory (code=38)
[Thu Sep  9 15:16:27 2010][007887][EUCAERROR ] virDomainAttachDevice() failed (err=-1) XML=
[Thu Sep  9 15:16:27 2010][007887][EUCAERROR ] ERROR: doAttachVolume() failed error=1[/I]


 I cannot find any reference to this error, and I not sure where to go from here?
Was my first change the wrong thing to do? 



 Thanks,
 David Mead
Mayo Clinic

---

### Post by Rusty au Lait on 2010-09-10
Why did you add a bridge now? It seems your VM network subsystem got messed up. Has the VNET_MODE been changed? Maybe this link helps [https://help.ubuntu.com/community/UEC/Topologies](https://help.ubuntu.com/community/UEC/Topologies). I am still in a place where a fresh and clean install is still an easy process for me.

---

