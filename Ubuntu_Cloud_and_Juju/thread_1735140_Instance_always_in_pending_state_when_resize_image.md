---
title: "Instance always in pending state when resize image before publishing"
date: 2011-04-21
forum: Ubuntu Cloud and Juju
---

### Post by thaond on 2011-04-21
Hi all,

I downloaded image form [http://uec-images.ubuntu.com/maverick/current/](http://uec-images.ubuntu.com/maverick/current/) and resized before uploading by 
uec-publish-tarball --resize 5G maverick-server-uec-amd64.tar.gz my-bucket amd64 
command line
But the instance is always in pending state.
Follow is the UEC configuration and logs file:
**UEC Configuration**
[INDENT]Setup
UEC 10.10
Deployed in 2 servers: 1 for CLC + CC and another for NC
KVM
Network mode: MANAGED[/INDENT]
**eucalyptus.conf on CC:**
> # Affects: CC, NC
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
#NODES=""
VNET_ADDRSPERNET="32"
VNET_NETMASK="255.255.0.0"
VNET_SUBNET="192.168.0.0"
VNET_DNS="192.168.2.2"
VNET_PUBLICIPS="192.168.2.10-192.168.2.50"

# Affects: NC
NC_PORT="8775"
HYPERVISOR="kvm"
MANUAL_INSTANCES_CLEANUP=0
INSTANCE_PATH="/var/lib/eucalyptus/instances/"
USE_VIRTIO_NET="0"
USE_VIRTIO_DISK="1"
USE_VIRTIO_ROOT="0"
#MAX_MEM=2048
#MAX_CORES="2"
#MAX_DISK="100"
****eucalyptus.conf on NC:
> # Affects: CC, NC
# See: **NOTE** below
ENABLE_WS_SECURITY="Y"
LOGLEVEL="DEBUG"
VNET_PUBINTERFACE="eth0"
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
VNET_ADDRSPERNET="10"
# Affects: NC
NC_PORT="8775"
HYPERVISOR="kvm"
MANUAL_INSTANCES_CLEANUP=1
INSTANCE_PATH="/var/lib/eucalyptus/instances/"
USE_VIRTIO_NET="0"

**cc.log**
> Thu Apr 21 11:18:40 2011][012859][EUCADEBUG ] DEBUG: requested URI [http://192.168.3.3:8775/axis2/services/EucalyptusNC](http://192.168.3.3:8775/axis2/services/EucalyptusNC)
[Thu Apr 21 11:18:40 2011][012859][EUCADEBUG ] 	ncClientCall(ncDescribeResource): ppid=9053 client calling 'ncDescribeResource'
[Thu Apr 21 11:18:40 2011][012859][EUCADEBUG ] 	ncClientCall(ncDescribeResource): ppid=9053 done calling 'ncDescribeResource' with exit code '0'
[Thu Apr 21 11:18:40 2011][009053][EUCADEBUG ] ncClientCall(ncDescribeResource): done clientrc=0 opFail=0
[Thu Apr 21 11:18:40 2011][009053][EUCADEBUG ] refresh_resources(): received data from node=192.168.3.3 mem=132030/129982 disk=523182/522635 cores=32/28
[Thu Apr 21 11:18:40 2011][009053][EUCADEBUG ] refresh_resources(): done
[Thu Apr 21 11:18:40 2011][009053][EUCAINFO  ] refresh_instances(): called
[Thu Apr 21 11:18:40 2011][009053][EUCADEBUG ] ncClientCall(ncDescribeInstances): called ncURL=http://192.168.3.3:8775/axis2/services/EucalyptusNC timeout=20
[Thu Apr 21 11:18:40 2011][012860][EUCADEBUG ] DEBUG: requested URI [http://192.168.3.3:8775/axis2/services/EucalyptusNC](http://192.168.3.3:8775/axis2/services/EucalyptusNC)
[Thu Apr 21 11:18:40 2011][012860][EUCADEBUG ] 	ncClientCall(ncDescribeInstances): ppid=9053 client calling 'ncDescribeInstances'
[Thu Apr 21 11:18:40 2011][012860][EUCADEBUG ] 	ncClientCall(ncDescribeInstances): ppid=9053 done calling 'ncDescribeInstances' with exit code '0'
[Thu Apr 21 11:18:40 2011][009053][EUCADEBUG ] ncClientCall(ncDescribeInstances): done clientrc=0 opFail=0
[Thu Apr 21 11:18:40 2011][009053][EUCADEBUG ] refresh_instances(): describing instance i-3FBD075D, Pending, 0
[Thu Apr 21 11:18:40 2011][009053][EUCADEBUG ] find_instanceCache(): found instance in cache 'i-3FBD075D/192.168.2.10/192.168.1.2'
[Thu Apr 21 11:18:40 2011][009053][EUCADEBUG ] refresh_instances(): storing instance state: i-3FBD075D/Pending/192.168.2.10/192.168.1.2
[Thu Apr 21 11:18:40 2011][009053][EUCADEBUG ] print_ccInstance(): refresh_instances():  instanceId=i-3FBD075D reservationId=r-44EB08FA emiId=emi-2E961C4B kernelId=eki-8E0413A1 ramdiskId=eri-CA161479 emiURL=http://192.168.2.2:8773/services/Walrus/formis-soa/wso2is-3.0.1-c3.0.1-ubuntu-10.04-server-64bit-kvm.img.manifest.xml kernelURL=http://192.168.2.2:8773/services/Walrus/formis-soa/vmlinuz-2.6.32-24-server.manifest.xml ramdiskURL=http://192.168.2.2:8773/services/Walrus/formis-soa/initrd.img-2.6.32-24-server.manifest.xml state=Pending ts=1303357756 ownerId=admin keyName=ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQCgbQ/tsE7nbMtWRFcF+CJ/kuhKgFnhXOSSxXh8JnB64ROa60iFSmOYax+Y3tj9tHBHyo9eDsu+ZSKdlsOYl5UA9dkHoJRFLuP6ZoefMRwCSqohaGj3e7Yo+X5NQPUvMywYfflvFBHdzTRouPnQBpD4fyMTfefk0gZ78qsU9qqucy9E1jmzn/XYGrWQ+aEuQFFN8QhHOGTzdh8b5+BJLl/I1e8AYXKrEvQv6qjdL/xsmlh97ESbyTvTfnnS3SQu8GPGkURfY+60wrSvAYbpGwTxj52dMPISQuxdRZ+bDeQzMv3A0Xz8DSc4hfbZe9KIsGfuveBPeycvoCu+VtdQhY+9 admin@eucalyptus ccnet={privateIp=192.168.1.2 publicIp=192.168.2.10 privateMac=D0:0D:3F:BD:07:5D vlan=10 networkIndex=2} ccvm={cores=4 mem=2048 disk=35} ncHostIdx=0 serviceTag=http://192.168.3.3:8775/axis2/services/EucalyptusNC userData= launchIndex=0 volumesSize=0 volumes={} groupNames={default }
[Thu Apr 21 11:18:40 2011][009053][EUCADEBUG ] refresh_instances(): done
[Thu Apr 21 11:18:40 2011][009053][EUCADEBUG ] monitor_thread(): done

cloud-error.log
> 11:19:09 ERROR [RestfulMarshallingHandler:ReplyQueue.16] java.lang.NullPointerException
java.lang.NullPointerException
	at com.eucalyptus.binding.Binding.toOM(Binding.java:161)
	at com.eucalyptus.ws.handlers.RestfulMarshallingHandler.outgoingMessage(RestfulMarshallingHandler.java:134)
	at com.eucalyptus.ws.handlers.MessageStackHandler.handleDownstream(MessageStackHandler.java:93)
	at org.jboss.netty.channel.DefaultChannelPipeline.sendDownstream(DefaultChannelPipeline.java:590)
	at org.jboss.netty.channel.DefaultChannelPipeline$DefaultChannelHandlerContext.sendDownstream(DefaultChannelPipeline.java:796)
	at com.eucalyptus.ws.handlers.MessageStackHandler.handleDownstream(MessageStackHandler.java:102)
	at org.jboss.netty.channel.DefaultChannelPipeline.sendDownstream(DefaultChannelPipeline.java:590)
	at org.jboss.netty.channel.DefaultChannelPipeline$DefaultChannelHandlerContext.sendDownstream(DefaultChannelPipeline.java:796)
	at com.eucalyptus.ws.handlers.ServiceSinkHandler.sendDownstreamNewEvent(ServiceSinkHandler.java:189)
	at com.eucalyptus.ws.handlers.ServiceSinkHandler.handleDownstream(ServiceSinkHandler.java:155)
	at org.jboss.netty.channel.DefaultChannelPipeline.sendDownstream(DefaultChannelPipeline.java:590)
	at org.jboss.netty.channel.DefaultChannelPipeline.sendDownstream(DefaultChannelPipeline.java:585)
	at org.jboss.netty.channel.Channels.write(Channels.java:876)
	at org.jboss.netty.channel.Channels.write(Channels.java:824)
	at com.eucalyptus.ws.util.ReplyQueue.handle(ReplyQueue.java:116)
	at sun.reflect.GeneratedMethodAccessor189.invoke(Unknown Source)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.mule.model.resolvers.AbstractEntryPointResolver.invokeMethod(AbstractEntryPointResolver.java:147)
	at org.mule.model.resolvers.ReflectionEntryPointResolver.invoke(ReflectionEntryPointResolver.java:127)
	at org.mule.model.resolvers.DefaultEntryPointResolverSet.invoke(DefaultEntryPointResolverSet.java:50)
	at org.mule.component.DefaultLifecycleAdapter.intercept(DefaultLifecycleAdapter.java:202)
	at org.mule.component.AbstractJavaComponent.invokeComponentInstance(AbstractJavaComponent.java:82)
	at org.mule.component.AbstractJavaComponent.doOnCall(AbstractJavaComponent.java:73)
	at org.mule.component.AbstractComponent.onCall(AbstractComponent.java:87)
	at org.mule.model.seda.SedaService$ComponentStageWorker.run(SedaService.java:533)
	at org.mule.work.WorkerContext.run(WorkerContext.java:310)
	at edu.emory.mathcs.backport.java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1061)
	at edu.emory.mathcs.backport.java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:575)
	at java.lang.Thread.run(Thread.java:636)

nc.log
> [Thu Apr 21 11:19:11 2011][015250][EUCADEBUG ] doDescribeResource() invoked
[Thu Apr 21 11:19:11 2011][015250][EUCADEBUG ] doDescribeInstances() invoked
[Thu Apr 21 11:19:11 2011][015250][EUCADEBUG ] doDescribeInstances(): instanceId=i-3FBD075D publicIp=0.0.0.0 privateIp=192.168.1.2 mac=D0:0D:3F:BD:07:5D vlan=10 networkIndex=2
[Thu Apr 21 11:19:17 2011][015250][EUCADEBUG ] doDescribeResource() invoked
[Thu Apr 21 11:19:17 2011][015250][EUCADEBUG ] doDescribeInstances() invoked
[Thu Apr 21 11:19:17 2011][015250][EUCADEBUG ] doDescribeInstances(): instanceId=i-3FBD075D publicIp=0.0.0.0 privateIp=192.168.1.2 mac=D0:0D:3F:BD:07:5D vlan=10 networkIndex=2
[Thu Apr 21 11:19:23 2011][015250][EUCADEBUG ] doDescribeResource() invoked
[Thu Apr 21 11:19:23 2011][015250][EUCADEBUG ] doDescribeInstances() invoked
[Thu Apr 21 11:19:23 2011][015250][EUCADEBUG ] doDescribeInstances(): instanceId=i-3FBD075D publicIp=0.0.0.0 privateIp=192.168.1.2 mac=D0:0D:3F:BD:07:5D vlan=10 networkIndex=2
[Thu Apr 21 11:19:29 2011][015250][EUCADEBUG ] doDescribeResource() invoked
[Thu Apr 21 11:19:29 2011][015250][EUCADEBUG ] doDescribeInstances() invoked
[Thu Apr 21 11:19:30 2011][015250][EUCADEBUG ] doDescribeInstances(): instanceId=i-3FBD075D publicIp=0.0.0.0 privateIp=192.168.1.2 mac=D0:0D:3F:BD:07:5D vlan=10 networkIndex=2
[Thu Apr 21 11:19:36 2011][015250][EUCADEBUG ] doDescribeResource() invoked
[Thu Apr 21 11:19:36 2011][015250][EUCADEBUG ] doDescribeInstances() invoked
[Thu Apr 21 11:19:36 2011][015250][EUCADEBUG ] doDescribeInstances(): instanceId=i-3FBD075D publicIp=0.0.0.0 privateIp=192.168.1.2 mac=D0:0D:3F:BD:07:5D vlan=10 networkIndex=2
[Thu Apr 21 11:19:42 2011][015250][EUCADEBUG ] doDescribeResource() invoked
[Thu Apr 21 11:19:42 2011][015250][EUCADEBUG ] doDescribeInstances() invoked
[Thu Apr 21 11:19:42 2011][015250][EUCADEBUG ] doDescribeInstances(): instanceId=i-3FBD075D publicIp=0.0.0.0 privateIp=192.168.1.2 mac=D0:0D:3F:BD:07:5D vlan=10 networkIndex=2
[Thu Apr 21 11:19:48 2011][015250][EUCADEBUG ] doDescribeResource() invoked
[Thu Apr 21 11:19:48 2011][015250][EUCADEBUG ] doDescribeInstances() invoked
[Thu Apr 21 11:19:48 2011][015250][EUCADEBUG ] doDescribeInstances(): instanceId=i-3FBD075D publicIp=0.0.0.0 privateIp=192.168.1.2 mac=D0:0D:3F:BD:07:5D vlan=10 networkIndex=2

Can you suggest me solutions?
Thanks in advanced !

---

