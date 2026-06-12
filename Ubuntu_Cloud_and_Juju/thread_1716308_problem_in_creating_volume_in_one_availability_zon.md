---
title: "problem in creating volume in one availability zone from a snapshot in another"
date: 2011-03-28
forum: Ubuntu Cloud and Juju
---

### Post by ivacau on 2011-03-28
I'm using Ubuntu 10.4.2 updated to the latest binaries, with Eucalyptus v1.6.

I have a cloud consisting of 5 servers in all: 1 clc/walrus, 1 cc/sc + 1 nc (cluster1-01), 1 
cc/sc + 1 nc (cluster1-02).  

ivacau@host0002:~$ sudo euca_conf --list-scs
registered storage controllers:
   cluster1-02  192.168.121.5 
   cluster1-01  192.168.121.1 
ivacau@host0002:~$ sudo euca_conf --list-clusters
registered clusters:
   cluster1-02  192.168.121.5 
   cluster1-01  192.168.121.1 
ivacau@host0002:~$ sudo euca_conf --list-nodes
registered nodes:
   192.168.127.1  cluster1-01  
   192.168.128.1  cluster1-02  

I am able to start instances in both clusters (availability zones) no problem.  I'm also able to create volumes, associate volume to instance, create snapshot from a volume and subsequently create a volume from the snapshot, all within one of the two clusters.  

ivacau@host0002:~$ euca-describe-volumes
VOLUME    vol-5F880657     1    snap-5F170646    cluster1-02    available    2011-03-25T08:10:26.986Z
VOLUME    vol-5F970659     1        cluster1-02    available    2011-03-25T07:45:44.709Z
VOLUME    vol-5F40064C     1    snap-58DE0616    cluster1-01    available    2011-03-25T04:49:04.251Z
VOLUME    vol-5F0B064A     1        cluster1-01    available    2011-03-25T03:00:16.941Z
VOLUME    vol-6000065F     1        cluster1-01    available    2011-03-25T04:11:33.592Z

However when I attempt to create a volume (say in cluster1-02) from a snapshot that originally resided in the other cluster (say cluster1-01), I get the following error:

ivacau@host0002:~$ euca-create-volume --snapshot snap-58DE0616 -z cluster1-02
Volume: Error while communicating with Storage Controller: CreateStorageVolume:Internal Error.

The same error is encountered if I invert the source and destination availability zone.

On the clc/walrus server, I can see the following exceptions in /var/log/eucalyptus/cloud-error.log:

23:56:06 [NioResponseHandler:Hashed wheel timer #1]  ERROR Caught exception in asynchronous response handler.
org.jboss.netty.handler.timeout.ReadTimeoutException
    at org.jboss.netty.handler.timeout.ReadTimeoutHandler.<clinit>(ReadTimeoutHandler.java:59)
    at com.eucalyptus.ws.util.ChannelUtil.addPipelineMonitors(ChannelUtil.java:108)
    at com.eucalyptus.cluster.handlers.AbstractClusterMessageDispatcher.getPipeline(AbstractClusterMessageDispatcher.java:109)
    at com.eucalyptus.ws.client.NioBootstrap.connect(NioBootstrap.java:177)
    at com.eucalyptus.ws.client.NioBootstrap.connect(NioBootstrap.java:163)
    at com.eucalyptus.cluster.handlers.AbstractClusterMessageDispatcher.write(AbstractClusterMessageDispatcher.java:129)
    at com.eucalyptus.cluster.handlers.ClusterCertificateHandler.trigger(ClusterCertificateHandler.java:32)
    at com.eucalyptus.cluster.handlers.ClusterCertificateHandler.fireEvent(ClusterCertificateHandler.java:57)
    at com.eucalyptus.event.ReentrantListenerRegistry.fireEvent(ReentrantListenerRegistry.java:80)
    at com.eucalyptus.event.ReentrantListenerRegistry.fireEvent(ReentrantListenerRegistry.java:65)
    at com.eucalyptus.event.ListenerRegistry.fireEvent(ListenerRegistry.java:69)
    at com.eucalyptus.cluster.ClusterBootstrapper.load(ClusterBootstrapper.java:140)
    at com.eucalyptus.bootstrap.SystemBootstrapper.load(SystemBootstrapper.java:175)
23:56:06 [RemoteDispatcher:Volume.10]  ERROR com.eucalyptus.util.EucalyptusClusterException: Exception in NIO request.
com.eucalyptus.util.EucalyptusClusterException: Exception in NIO request.
    at com.eucalyptus.ws.handlers.NioResponseHandler.getResponse(NioResponseHandler.java:115)
    at com.eucalyptus.ws.client.NioClient.send(NioClient.java:113)
    at com.eucalyptus.ws.client.RemoteDispatcher.send(RemoteDispatcher.java:110)
    at com.eucalyptus.ws.client.ServiceDispatcher.send(ServiceDispatcher.java:80)
    at edu.ucsb.eucalyptus.cloud.ws.VolumeManager.CreateVolume(VolumeManager.java:170)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:616)
    at org.mule.model.resolvers.AbstractEntryPointResolver.invokeMethod(AbstractEntryPointResolver.java:147)
    at org.mule.model.resolvers.ReflectionEntryPointResolver.invoke(ReflectionEntryPointResolver.java:178)
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
Caused by: org.jboss.netty.handler.timeout.ReadTimeoutException
    at org.jboss.netty.handler.timeout.ReadTimeoutHandler.<clinit>(ReadTimeoutHandler.java:59)
    at com.eucalyptus.ws.util.ChannelUtil.addPipelineMonitors(ChannelUtil.java:108)
    at com.eucalyptus.cluster.handlers.AbstractClusterMessageDispatcher.getPipeline(AbstractClusterMessageDispatcher.java:109)
    at com.eucalyptus.ws.client.NioBootstrap.connect(NioBootstrap.java:177)
    at com.eucalyptus.ws.client.NioBootstrap.connect(NioBootstrap.java:163)
    at com.eucalyptus.cluster.handlers.AbstractClusterMessageDispatcher.write(AbstractClusterMessageDispatcher.java:129)
    at com.eucalyptus.cluster.handlers.ClusterCertificateHandler.trigger(ClusterCertificateHandler.java:32)
    at com.eucalyptus.cluster.handlers.ClusterCertificateHandler.fireEvent(ClusterCertificateHandler.java:57)
    at com.eucalyptus.event.ReentrantListenerRegistry.fireEvent(ReentrantListenerRegistry.java:80)
    at com.eucalyptus.event.ReentrantListenerRegistry.fireEvent(ReentrantListenerRegistry.java:65)
    at com.eucalyptus.event.ListenerRegistry.fireEvent(ListenerRegistry.java:69)
    at com.eucalyptus.cluster.ClusterBootstrapper.load(ClusterBootstrapper.java:140)
    at com.eucalyptus.bootstrap.SystemBootstrapper.load(SystemBootstrapper.java:175)
23:56:06 [DefaultServiceExceptionStrategy:Volume.10]  ERROR 
********************************************************************************
Message               : Component that caused exception is: Volume. Message payload is of type: CreateVolumeType
Type                  : org.mule.api.service.ServiceException
Code                  : MULE_ERROR--2
Payload               : <?xml version="1.0" encoding="UTF-8"?>
<euca:CreateVolume xmlns:euca="http://msgs.eucalyptus.ucsb.edu">
  <euca:BlockVolumeMessage>
    <euca:correlationId>c5b404ad-f63c-4038-8c21-5fe0f282d81f</euca:correlationId>
    <euca:userId>admin</euca:userId>
    <euca:effectiveUserId>eucalyptus</euca:effectiveUserId>
  </euca:BlockVolumeMessage>
  <euca:snapshotId>snap-58DE0616</euca:snapshotId>
  <euca:availabilityZone>cluster1-02</euca:availabilityZone>
</euca:CreateVolume>
JavaDoc               : [http://mule.mulesource.org/docs/apidocs/org/mule/api/service/ServiceException.html](http://mule.mulesource.org/docs/apidocs/org/mule/api/service/ServiceException.html)
********************************************************************************
Exception stack is:
1. Error while communicating with Storage Controller: CreateStorageVolume:Internal Error. (com.eucalyptus.util.EucalyptusCloudException)
  edu.ucsb.eucalyptus.cloud.ws.VolumeManager:182 (null)
2. Component that caused exception is: Volume. Message payload is of type: CreateVolumeType (org.mule.api.service.ServiceException)
  org.mule.component.DefaultLifecycleAdapter:214 ([http://mule.mulesource.org/docs/apidocs/org/mule/api/service/ServiceException.html](http://mule.mulesource.org/docs/apidocs/org/mule/api/service/ServiceException.html))
********************************************************************************
Root Exception stack trace:
com.eucalyptus.util.EucalyptusCloudException: Error while communicating with Storage Controller: CreateStorageVolume:Internal Error.
    at edu.ucsb.eucalyptus.cloud.ws.VolumeManager.CreateVolume(VolumeManager.java:182)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:616)
    at org.mule.model.resolvers.AbstractEntryPointResolver.invokeMethod(AbstractEntryPointResolver.java:147)
    at org.mule.model.resolvers.ReflectionEntryPointResolver.invoke(ReflectionEntryPointResolver.java:178)
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

********************************************************************************

23:56:06 [DefaultServiceExceptionStrategy:Volume.10]  ERROR Message being processed is: org.mule.transport.DefaultMessageAdapter/org.mule.transport.DefaultMessageAdapter@105a9{id=acd6fb00-593a-11e0-80e4-e3ba4516fe20, payload=edu.ucsb.eucalyptus.msgs.CreateVolumeType, correlationId=acd6fb00-593a-11e0-80e4-e3ba4516fe20, correlationGroup=-1, correlationSeq=-1, encoding=UTF-8, exceptionPayload=org.mule.message.DefaultExceptionPayload@11aaec3}


on the example given, the 'source' storage controller for cluster1-01 (i.e. containing the snapshot) has the no relevant exceptions in /var/log/eucalyptus/cloud-error.log at the time the euca-create-volume command is given.

The 'destination' storage controller for cluster1-02 (i.e. where the volume is being attempted to be stored) has the following exceptions in /var/log/eucalyptus/cloud-error.log:



23:55:38 [DefaultServiceExceptionStrategy:New I/O server worker #1-29]  ERROR 
********************************************************************************
Message               : Component that caused exception is: StorageInternal. Message payload is of type: CreateStorageVolumeType
Type                  : org.mule.api.service.ServiceException
Code                  : MULE_ERROR--2
Payload               : <?xml version="1.0" encoding="UTF-8"?>
<euca:CreateStorageVolume xmlns:euca="http://msgs.eucalyptus.ucsb.edu">
  <euca:StorageRequest>
    <euca:correlationId>7f31b339-10eb-4e1e-8d93-286ade1bdb0f</euca:correlationId>
    <euca:userId>admin</euca:userId>
    <euca:effectiveUserId>eucalyptus</euca:effectiveUserId>
  </euca:StorageRequest>
  <euca:volumeId>vol-5F8E065B</euca:volumeId>
  <euca:snapshotId>snap-58DE0616</euca:snapshotId>
</euca:CreateStorageVolume>
JavaDoc               : [http://mule.mulesource.org/docs/apidocs/org/mule/api/service/ServiceException.html](http://mule.mulesource.org/docs/apidocs/org/mule/api/service/ServiceException.html)
********************************************************************************
Exception stack is:
1. The specified entity was not found (edu.ucsb.eucalyptus.cloud.NoSuchEntityException)
  edu.ucsb.eucalyptus.cloud.ws.BlockStorage:544 (null)
2. Component that caused exception is: StorageInternal. Message payload is of type: CreateStorageVolumeType (org.mule.api.service.ServiceException)
  org.mule.component.DefaultLifecycleAdapter:214 ([http://mule.mulesource.org/docs/apidocs/org/mule/api/service/ServiceException.html](http://mule.mulesource.org/docs/apidocs/org/mule/api/service/ServiceException.html))
********************************************************************************
Root Exception stack trace:
edu.ucsb.eucalyptus.cloud.NoSuchEntityException: The specified entity was not found
    at edu.ucsb.eucalyptus.cloud.ws.BlockStorage.CreateStorageVolume(BlockStorage.java:544)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:616)
    at org.mule.model.resolvers.AbstractEntryPointResolver.invokeMethod(AbstractEntryPointResolver.java:147)
    at org.mule.model.resolvers.ReflectionEntryPointResolver.invoke(ReflectionEntryPointResolver.java:178)
    at org.mule.model.resolvers.DefaultEntryPointResolverSet.invoke(DefaultEntryPointResolverSet.java:50)
    at org.mule.component.DefaultLifecycleAdapter.intercept(DefaultLifecycleAdapter.java:202)
    at org.mule.component.AbstractJavaComponent.invokeComponentInstance(AbstractJavaComponent.java:82)
    at org.mule.component.AbstractJavaComponent.doOnCall(AbstractJavaComponent.java:73)
    at org.mule.component.AbstractComponent.onCall(AbstractComponent.java:87)
    at org.mule.model.seda.SedaService.doSend(SedaService.java:234)
    at org.mule.service.AbstractService.sendEvent(AbstractService.java:510)
    at org.mule.DefaultMuleSession.sendEvent(DefaultMuleSession.java:351)
    at org.mule.routing.inbound.DefaultInboundRouterCollection.send(DefaultInboundRouterCollection.java:196)
    at org.mule.routing.inbound.DefaultInboundRouterCollection.route(DefaultInboundRouterCollection.java:164)
    at org.mule.transport.AbstractMessageReceiver$DefaultInternalMessageListener.onMessage(AbstractMessageReceiver.java:604)
    at org.mule.transport.AbstractMessageReceiver.routeMessage(AbstractMessageReceiver.java:346)
    at org.mule.transport.AbstractMessageReceiver.routeMessage(AbstractMessageReceiver.java:269)
    at org.mule.transport.AbstractMessageReceiver.routeMessage(AbstractMessageReceiver.java:262)
    at com.eucalyptus.ws.handlers.ServiceSinkHandler.handleUpstream(ServiceSinkHandler.java:203)
    at org.jboss.netty.channel.DefaultChannelPipeline.sendUpstream(DefaultChannelPipeline.java:567)
    at org.jboss.netty.channel.DefaultChannelPipeline$DefaultChannelHandlerContext.sendUpstream(DefaultChannelPipeline.java:803)
    at com.eucalyptus.ws.handlers.MessageStackHandler.handleUpstream(MessageStackHandler.java:133)
    at org.jboss.netty.channel.DefaultChannelPipeline.sendUpstream(DefaultChannelPipeline.java:567)
    at org.jboss.netty.channel.DefaultChannelPipeline$DefaultChannelHandlerContext.sendUpstream(DefaultChannelPipeline.java:803)
    at com.eucalyptus.ws.handlers.MessageStackHandler.handleUpstream(MessageStackHandler.java:133)
    at org.jboss.netty.channel.DefaultChannelPipeline.sendUpstream(DefaultChannelPipeline.java:567)
    at org.jboss.netty.channel.DefaultChannelPipeline$DefaultChannelHandlerContext.sendUpstream(DefaultChannelPipeline.java:803)
    at com.eucalyptus.ws.handlers.MessageStackHandler.handleUpstream(MessageStackHandler.java:133)
    at org.jboss.netty.channel.DefaultChannelPipeline.sendUpstream(DefaultChannelPipeline.java:567)
    at org.jboss.netty.channel.DefaultChannelPipeline$DefaultChannelHandlerContext.sendUpstream(DefaultChannelPipeline.java:803)
    at com.eucalyptus.ws.handlers.MessageStackHandler.handleUpstream(MessageStackHandler.java:133)
    at org.jboss.netty.channel.DefaultChannelPipeline.sendUpstream(DefaultChannelPipeline.java:567)
    at org.jboss.netty.channel.DefaultChannelPipeline$DefaultChannelHandlerContext.sendUpstream(DefaultChannelPipeline.java:803)
    at com.eucalyptus.ws.handlers.MessageStackHandler.handleUpstream(MessageStackHandler.java:133)
    at org.jboss.netty.channel.DefaultChannelPipeline.sendUpstream(DefaultChannelPipeline.java:567)
    at org.jboss.netty.channel.DefaultChannelPipeline$DefaultChannelHandlerContext.sendUpstream(DefaultChannelPipeline.java:803)
    at com.eucalyptus.ws.server.NioServerHandler.messageReceived(NioServerHandler.java:119)
    at org.jboss.netty.channel.SimpleChannelUpstreamHandler.handleUpstream(SimpleChannelUpstreamHandler.java:87)
    at org.jboss.netty.channel.DefaultChannelPipeline.sendUpstream(DefaultChannelPipeline.java:567)
    at org.jboss.netty.channel.DefaultChannelPipeline$DefaultChannelHandlerContext.sendUpstream(DefaultChannelPipeline.java:803)
    at org.jboss.netty.handler.stream.ChunkedWriteHandler.handleUpstream(ChunkedWriteHandler.java:114)
    at org.jboss.netty.channel.DefaultChannelPipeline.sendUpstream(DefaultChannelPipeline.java:567)
    at org.jboss.netty.channel.DefaultChannelPipeline$DefaultChannelHandlerContext.sendUpstream(DefaultChannelPipeline.java:803)
    at org.jboss.netty.channel.Channels.fireMessageReceived(Channels.java:385)
    at org.jboss.netty.handler.codec.replay.ReplayingDecoder.unfoldAndfireMessageReceived(ReplayingDecoder.java:459)
    at org.jboss.netty.handler.codec.replay.ReplayingDecoder.callDecode(ReplayingDecoder.java:443)
    at org.jboss.netty.handler.codec.replay.ReplayingDecoder.messageReceived(ReplayingDecoder.java:381)
    at org.jboss.netty.channel.SimpleChannelUpstreamHandler.handleUpstream(SimpleChannelUpstreamHandler.java:87)
    at org.jboss.netty.channel.DefaultChannelPipeline.sendUpstream(DefaultChannelPipeline.java:567)
    at org.jboss.netty.channel.DefaultChannelPipeline$DefaultChannelHandlerContext.sendUpstream(DefaultChannelPipeline.java:803)
    at org.jboss.netty.handler.timeout.ReadTimeoutHandler.messageReceived(ReadTimeoutHandler.java:146)
    at org.jboss.netty.channel.SimpleChannelUpstreamHandler.handleUpstream(SimpleChannelUpstreamHandler.java:87)
    at org.jboss.netty.channel.DefaultChannelPipeline.sendUpstream(DefaultChannelPipeline.java:567)
    at org.jboss.netty.channel.DefaultChannelPipeline$DefaultChannelHandlerContext.sendUpstream(DefaultChannelPipeline.java:803)
    at org.jboss.netty.handler.timeout.IdleStateHandler.messageReceived(IdleStateHandler.java:214)
    at org.jboss.netty.channel.SimpleChannelUpstreamHandler.handleUpstream(SimpleChannelUpstreamHandler.java:87)
    at org.jboss.netty.channel.DefaultChannelPipeline.sendUpstream(DefaultChannelPipeline.java:567)
    at org.jboss.netty.channel.DefaultChannelPipeline$DefaultChannelHandlerContext.sendUpstream(DefaultChannelPipeline.java:803)
    at org.jboss.netty.channel.SimpleChannelHandler.messageReceived(SimpleChannelHandler.java:159)
    at com.eucalyptus.ws.handlers.ChannelStateMonitor.messageReceived(ChannelStateMonitor.java:61)
    at org.jboss.netty.channel.SimpleChannelHandler.handleUpstream(SimpleChannelHandler.java:105)
    at org.jboss.netty.channel.DefaultChannelPipeline.sendUpstream(DefaultChannelPipeline.java:567)
    at org.jboss.netty.channel.DefaultChannelPipeline.sendUpstream(DefaultChannelPipeline.java:562)
    at org.jboss.netty.channel.Channels.fireMessageReceived(Channels.java:342)
    at org.jboss.netty.channel.Channels.fireMessageReceived(Channels.java:329)
    at org.jboss.netty.channel.socket.nio.NioWorker.read(NioWorker.java:330)
    at org.jboss.netty.channel.socket.nio.NioWorker.processSelectedKeys(NioWorker.java:282)
    at org.jboss.netty.channel.socket.nio.NioWorker.run(NioWorker.java:203)
    at org.jboss.netty.util.ThreadRenamingRunnable.run(ThreadRenamingRunnable.java:110)
    at org.jboss.netty.util.internal.IoWorkerRunnable.run(IoWorkerRunnable.java:53)
    at org.jboss.netty.handler.execution.MemoryAwareThreadPoolExecutor$MemoryAwareRunnable.run(MemoryAwareThreadPoolExecutor.java:502)
    at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1110)
    at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:603)
    at java.lang.Thread.run(Thread.java:636)

********************************************************************************


 I'm assuming that the use case of what I'm attempting to do (i.e. copying a volume from one availability zone to another via a snapshot) is allowed by Eucalyptus.

Can anyone indicate what could be wrong?  Apologise for the long post.

---

### Post by kim0 on 2011-03-29
Update: Removing wrong info .. Thanks Obino

---

### Post by ivacau on 2011-03-29
Hi Kim0

thanks for your reply.  I was misled by the requirement to identify the zone when creating a volume from a snapshot, thinking that it implied the usecase was plausible.  If the destination cluster is the same as the one in which the snapshot resides, it may be seen as somewhat superfluous to need to specify the cluster, as the cloud already knows the location cluster of the snapshot.

In any case yes there are other ways of getting a volume across - I could also use standard linux userspace tools.  I had been trying to utilise the standard euca2ools to achieve the intended outcome, which would have been nice.

Thanks again for your input.

---

### Post by obino on 2011-03-29
Hello,

actually that's an operation that should work, that is that's the proper way to move volumes from one zone to the other.

The error you are seeing seems a connectivity issues: how are your clusters setup? Can both SCs see walrus and vice-versa? You can check this going on one machine (say one SC) then try to telnet <host> 8773 and see if it connects. You should try this for each SC to Walrus. The 2 SCs do not need to see/talk to each other.

cheers
graziano

---

### Post by kim0 on 2011-03-30
Thanks Obino for helping! @ivacau trust Obino :)

---

### Post by ivacau on 2011-03-30
@ Kim0

no worries.  We're all on a learning curve!

@ Graziano

thanks for replying.  I'm happy to 'meet' you - I've seen and referred to some of your many contributions in the Eucalyptus forums in my own evaluation.

To answer your question, the main components clc, walrus, cc and sc communicate over one broadcast domain (192.168.121.0/24).  The cc/sc machines are dual-homed, and communicate through their second interface to the node controllers - one broadcast domain and one node controller each for cluster1-01 (192.168.127.0/24) and cluster1-02 (192.168.128.0/24).

Both storage controllers are able to communicate with walrus.  The 'telnet <walrus_IP> 8773' test confirms connectivity with Walrus is possible.

Since you asked me to test connectivity to Walrus, and your other comment that the scs don't communicate directly, I would conclude that Walrus is (should be) involved in the inter-zone transfer.  I investigated the Walrus server a bit further and found that the Walrus filesystem was running out of space, so I though this could be the problem (although I did not see complaints in the cloud log files).  I've replatformed Walrus since to provide ample space for a copy of the snapshot or new volume to be created on Walrus, however the result is exactly the same.  I can create a volume from a snapshot if both are within the same cluster, but not if they're on different ones.

I'd be grateful if you could guide me further.

---

### Post by ivacau on 2011-03-31
has anyone managed to copy volumes from one cluster to another in a multi-cluster setup, or found a problem similar to mine?  Graziano has indicated that this should be possible.

---

### Post by obino on 2011-03-31
Hello,

to explain Walrus involvement. Since the SC are 'local' only to a cluster (zone), the way to move volumes across zones (as you are doing) is to take a snapshot, then create a volume in the other zone. Walrus is where the snapshots resides: this allows the snapshots to be visible by any SC, since Walrus needs to be publicly available.

Would you mind to file a launchpad for this? I suspect we may have some regression here.

cheers
graziano

---

### Post by ivacau on 2011-03-31
Hi Graziano

ok.  Will do.

One strange thing I've noticed: in the cloud-output.log of the host on which the destination storage controller is located, a huge quantity of lines similar to the following appear, at about the time that the snapshots are generated.  Does this indicate a crash of some kind?

10:01:33 DEBUG content                   | Wire.java:84 >> "[0x1f][0x8b][0x8][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0xed][0xc1][0x1][0x1][0x0][0x0][0x0][0x82] [0xff][0xaf]nH@[0x1][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0][0x0]|[0x18]a[0x85][0xf8]J[0x0][0x90][0x1][0x0]"

Also, following your description of the process, I've located the two copies of the snapshot, which are created sequentially first on the sc (/var/lib/eucalyptus/volumes) and then on walrus (/var/lib/eucalyptus/bukkits).  I was surprised to note that the size of the snapshot file is different on the sc and walrus, using both 'ls -l' and 'du'.  I would have expected them to be identical (unless only a compressed version is stored on walrus).  Is it possible that the snapshot copy to walrus is incomplete for some reason, even if euca-describe-snapshots reports 100% completion?

I'll file into Launchpad anyway as suggested.

regards
Ivan

---

### Post by ivacau on 2011-03-31
Filed into Launchpad at [https://answers.launchpad.net/ubuntu/+source/aoetools/+question/151227](https://answers.launchpad.net/ubuntu/+source/aoetools/+question/151227).  I'll continue posting there.

thanks for your help so far

---

### Post by obino on 2011-04-01
Thanks. It does seem odd indeed what you see in the logs. I'll leave someone more expert than me in the Walrus and SC code to comments on the bug.

cheers
graziano

---

### Post by ivacau on 2011-04-11
Haven't yet received a reply on Launchpad.  Not being very familiar with Launchpad, I initially mistakenly posted the question against the 'aoetools' package, but I've changed this to 'eucalyptus'.  Is this the right package to quote this issue against?

---

### Post by kim0 on 2011-04-12
If it looks like a bug, perhaps filing a bug would be more appropriate

---

### Post by ivacau on 2011-04-12
thanks kim0.  I've created a new bug at [https://bugs.launchpad.net/eucalyptus/+bug/758712](https://bugs.launchpad.net/eucalyptus/+bug/758712)

---

