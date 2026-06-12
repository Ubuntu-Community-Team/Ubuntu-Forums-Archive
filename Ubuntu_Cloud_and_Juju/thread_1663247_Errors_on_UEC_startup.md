---
title: "Errors on UEC startup"
date: 2011-01-09
forum: Ubuntu Cloud and Juju
---

### Post by wcorey on 2011-01-09
Let's face the default Eucalyptus log settings (DEBUG) generate a mind boggling amount of noise. The first thing I did was set it to INFO. DEBUG is fine when its in development, not deployed in production.

It generates a mind boggling amount of data in INFO mode as well, just much more manaagable. Once I find the log4j properties file for it I'll get more meaningful output (date) but what I thought I'd do to help facilitate debugging of why things that should work don't I thought I'd delete the logs and restart UEC on the cloud/cc/sc/walrus server. 

The file cloud-error.log contains the following:
10:54:16 ERROR [SystemUtil:Thread-23] com.eucalyptus.util.ExecutionException: ///usr/lib/eucalyptus/euca_rootwrap losetup /dev/loop0  error: loop: can't get info on device /dev/loop0: No such device or address

10:54:17 ERROR [ISCSIManager:Thread-23] com.eucalyptus.util.EucalyptusCloudException: tgtadm: invalid request

10:54:20 ERROR [NioServerHandler:New I/O server worker #1-1] Internal Error.
com.eucalyptus.ws.ServiceNotReadyException: System has not yet completed booting.
	at com.eucalyptus.ws.server.NioServerHandler.messageReceived(NioServerHandler.java:107)
	at org.jboss.netty.handler.stream.ChunkedWriteHandler.handleUpstream(ChunkedWriteHandler.java:114)
	at org.jboss.netty.channel.Channels.fireMessageReceived(Channels.java:385)
	at org.jboss.netty.handler.codec.replay.ReplayingDecoder.unfoldAndfireMessageReceived(ReplayingDecoder.java:459)
	at org.jboss.netty.handler.codec.replay.ReplayingDecoder.callDecode(ReplayingDecoder.java:443)
	at org.jboss.netty.handler.codec.replay.ReplayingDecoder.messageReceived(ReplayingDecoder.java:381)
	at com.eucalyptus.ws.handlers.http.NioSslHandler.handleUpstream(NioSslHandler.java:31)
	at org.jboss.netty.channel.Channels.fireMessageReceived(Channels.java:342)
	at org.jboss.netty.channel.Channels.fireMessageReceived(Channels.java:329)
	at org.jboss.netty.channel.socket.nio.NioWorker.read(NioWorker.java:330)
	at org.jboss.netty.channel.socket.nio.NioWorker.processSelectedKeys(NioWorker.java:282)
	at org.jboss.netty.channel.socket.nio.NioWorker.run(NioWorker.java:203)
	at org.jboss.netty.util.internal.IoWorkerRunnable.run(IoWorkerRunnable.java:53)
	at org.jboss.netty.handler.execution.MemoryAwareThreadPoolExecutor$MemoryAwareRunnable.run(MemoryAwareThreadPoolExecutor.java:502)
	at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1110)
	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:603)
	at java.lang.Thread.run(Thread.java:636)


The file cloud-output.log had lots. I looked into that and discovered errors.

I believe it is actually up and running but not sure if what I am going to paste in foretells a future issue. Note the system util error in the middle and preceding warning message.
10:54:15  INFO 163  StorageProperties      | Setting WALRUS_URL to: [http://192.168.0.11:8773/services/Walrus](http://192.168.0.11:8773/services/Walrus)
10:54:15  INFO 121  BlockStorageStatistics | Service: StorageController Version: 2.0.0 Volumes: 1 Space Used: 10737418240
10:54:15  INFO 277  OverlayManager         | cluster1
10:54:15  INFO 43   ServiceEventListener   | Registered service dispatchers: storage@localhost vm://StorageInternal [LocalConfiguration uri=http://192.168.0.11:8773/services/Storage c=storage name=storage hostName=192.168.0.11 port=8773 servicePath=/services/Storage id=null version=0 lastUpdate=null]
10:54:15  INFO 110  rviceVerifyBootstrapper| :1294588455916:ServiceVerifyBootstrapper:COMPONENT_INFO:cluster:true
10:54:15  INFO 110  Component              | :1294588455919:Component:COMPONENT_SERVICE_START:cluster:cluster1:[http://192.168.0.11:8774/axis2/services/EucalyptusCC](http://192.168.0.11:8774/axis2/services/EucalyptusCC)
10:54:15  INFO 110  ClusterBuilder         | :1294588455920:ClusterBuilder:COMPONENT_SERVICE_START:cluster:cluster1:[http://192.168.0.11:8774/axis2/services/EucalyptusCC](http://192.168.0.11:8774/axis2/services/EucalyptusCC)
10:54:15  INFO 110  entrantListenerRegistry| :1294588455955:ReentrantListenerRegistry:LISTENER_REGISTERED:Class:com.eucalyptus.cluster.handlers.ClusterCertificateHandler
10:54:15  INFO 110  entrantListenerRegistry| :1294588455956:ReentrantListenerRegistry:LISTENER_REGISTERED:Class:com.eucalyptus.cluster.handlers.ClusterCertificateHandler
10:54:15  INFO 110  entrantListenerRegistry| :1294588455956:ReentrantListenerRegistry:LISTENER_REGISTERED:Class:com.eucalyptus.cluster.handlers.ClusterCertificateHandler
10:54:16  WARN 134  Tracker                | /usr/lib/python2.6/dist-packages/BitTorrent/track.py:17: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
                                           |   from sha import sha
10:54:16 ERROR 94   SystemUtil             | com.eucalyptus.util.ExecutionException: ///usr/lib/eucalyptus/euca_rootwrap losetup /dev/loop0  error: loop: can't get info on device /dev/loop0: No such device or address
10:54:16  INFO 228  OverlayManager         | losetup /dev/loop0 //var/lib/eucalyptus/volumes/vol-531A05EE
10:54:16  INFO 229  OverlayManager         | 
10:54:16  INFO 230  OverlayManager         | 
10:54:16  INFO 43   ServiceEventListener   | Registered service dispatchers: cluster@192.168.0.11 vm://ClusterEndpoint [ClusterConfiguration minVlan=10 maxVlan=4095 name=cluster1 hostName=192.168.0.11 port=8774 servicePath=/axis2/services/EucalyptusCC id=ff8081812c93ee56012c93eebd650016 version=1 lastUpdate=null]
10:54:16  INFO 110  rviceVerifyBootstrapper| :1294588456478:ServiceVerifyBootstrapper:COMPONENT_INFO:db:true
10:54:16  INFO 110  Bootstrap              | :1294588456478:Bootstrap:BOOTSTRAPPER_START:RemoteServicesInit:com.eucalyptus.ws.DeferredPropertiesBootstrapper
10:54:16  INFO 110  Bootstrap              | :1294588456488:Bootstrap:BOOTSTRAP_STAGE_COMPLETE:RemoteServicesInit
10:54:16  INFO 110  Bootstrap              | :1294588456488:Bootstrap:BOOTSTRAP_STAGE_AGENDA:UserCredentialsInit:LOAD
10:54:16  INFO 110  Bootstrap              | :1294588456488:Bootstrap:BOOTSTRAP_STAGE_AGENDA:UserCredentialsInit:com.eucalyptus.auth.DatabaseAuthBootstrapper

That snippet may be too out of context so I will attempt to attach the entire file.

As I said, it may be they aren't true errors just something that needs to be addressed, like the deprecation warning. also, at the end of the file thee is this.

I have no clue, from the log entry, what this means:
10:54:20  INFO 110  Transition$anonymously | :1294588460461:anonymously:TRANSITION_PREPARE:Transition:from:LOADED:to:STARTED:com.eucalyptus.component.Component
10:54:20  INFO 110  Transition$anonymously | :1294588460462:anonymously:TRANSITION_COMMIT:Transition:from:LOADED:to:STARTED:com.eucalyptus.component.Component
10:54:20  INFO 110  Transition$anonymously | :1294588460462:anonymously:TRANSITION_POST:Transition:from:LOADED:to:STARTED:com.eucalyptus.component.Component
10:54:22  INFO 150  Registration           | Using registrationId: 4bb60079-ce4d-4632-93e3-b5f220b4674a
10:54:22  WARN 162  Registration           | 
                                           | key='4bb60079-ce4d-4632-93e3-b5f220b4674a'
                                           | id='69df4b84-b37d-4727-a1a1-5fe44c33b2c6'
                                           | result=57b855b9cae855601850ffca1c31f170ec0fa377e9a55e656a6bbe6e6e1b689839bb776107d18ddf12b3e792037908d980de5d1be7a80de385fa16eabb58134ea663b9f2a88e9e122b9518c49d2f285884f51a09b0e40a9eed3583fcb419217b18d7f87ce2f1902e8368a40f0b8665d98c89f8aedc4a4e7176564a748227b79e5b329dc4ec65ed422cb49615806f1dbd271afd4f48485db991965715972a9905f35df399cefff5698ac32855ef81a9b998ebfb195c96045315676d16bec70433871910e136159c082e42989d97ebc8b039ef468ef06ffac26a1e3a3e503bbe54497b8b834af16c214bfcdae0fe82b860330d2ad3e0d05a81ce2e78b1cdf541d2


There is a files permission issue in the other files.

So if someone could take a look, perhaps these are resolved in 11.04 or 2.02 or maybe they are new. Any other information you need I'll be happy to provide. It never occurred to me until now to zero out the logs and see what is in them right after startup. 

I am curious about the warnings that eth1 must be a bridge. UEC installs out of the box in ManagedNoVLAN which requires the nodes to be hung off eth1, correct? Does this answer my other question about the node controller server being network orphaned?

TIA,

Walt

---

