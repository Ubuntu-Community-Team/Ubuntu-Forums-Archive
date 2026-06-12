---
title: "Ubuntu Cloud Instances Not Starting"
date: 2010-04-02
forum: Server Platforms
---

### Post by Petrock6 on 2010-04-02
Hi,

I've got 3 computers (1 controller, 2 nodes all running on Eucalyptus + Ubuntu 9.10 server edition) and basically, whenever I run an instance, under euca-describe-instances, the instance will say "pending", then "running" (for about 3-5 seconds), then "shutting-down", and then "terminated".

Both systems are AMD-64, connected

(As a side note, when I run euca-run-instances, it will ask me to use --addressing private, which I do NOT WANT)

Please help me, I have been stumped, I've google'd it many times, however most don't help.

Here's what all I can give you:

ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 00:30:67:2d:a9:f4
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::230:67ff:fe2d:a9f4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:152972 errors:0 dropped:0 overruns:0 frame:0
          TX packets:91138 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:208161334 (208.1 MB)  TX bytes:25176581 (25.1 MB)
          Interrupt:26 Base address:0x6000

eth0:metadata Link encap:Ethernet  HWaddr 00:30:67:2d:a9:f4
          inet addr:169.254.169.254  Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:26 Base address:0x6000

eth0:priv Link encap:Ethernet  HWaddr 00:30:67:2d:a9:f4
          inet addr:172.19.1.1  Bcast:172.19.1.31  Mask:255.255.255.224
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:26 Base address:0x6000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:167752 errors:0 dropped:0 overruns:0 frame:0
          TX packets:167752 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:249683778 (249.6 MB)  TX bytes:249683778 (249.6 MB)

```

euca-describe-availability-zones verbose (I had to shut off one system)
```

saustin@Cluster-Master:~$ euca-describe-availability-zones verbose
AVAILABILITYZONE        Bentley-Cluster 192.168.1.2
AVAILABILITYZONE        |- vm types     free / max   cpu   ram  disk
AVAILABILITYZONE        |- m1.small     0001 / 0001   1    128     2
AVAILABILITYZONE        |- c1.medium    0001 / 0001   1    256     5
AVAILABILITYZONE        |- m1.large     0000 / 0000   2    512    10
AVAILABILITYZONE        |- m1.xlarge    0000 / 0000   2   1024    20
AVAILABILITYZONE        |- c1.xlarge    0000 / 0000   4   2048    20

```

Last few lines of cloud-error.log
```

********************************************************************************
Message               : Component that caused exception is: FinishedVerify. Message payload is of type: VmAllocationInfo
Type                  : org.mule.api.service.ServiceException
Code                  : MULE_ERROR--2
Payload               : edu.ucsb.eucalyptus.cloud.VmAllocationInfo@197013db
JavaDoc               : http://mule.mulesource.org/docs/apidocs/org/mule/api/service/ServiceException.html
********************************************************************************
Exception stack is:
1. Not enough resources available: addresses (try --addressing private) (com.eucalyptus.util.EucalyptusCloudException)
  edu.ucsb.eucalyptus.cloud.ws.VmAdmissionControl:132 (null)
2. Component that caused exception is: FinishedVerify. Message payload is of type: VmAllocationInfo (org.mule.api.service.ServiceException)
  org.mule.component.DefaultLifecycleAdapter:214 (http://mule.mulesource.org/docs/apidocs/org/mule/api/service/ServiceException.html)
********************************************************************************
Root Exception stack trace:
com.eucalyptus.util.EucalyptusCloudException: Not enough resources available: addresses (try --addressing private)
        at edu.ucsb.eucalyptus.cloud.ws.VmAdmissionControl.evaluate(VmAdmissionControl.java:132)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
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

********************************************************************************

12:29:16 [DefaultServiceExceptionStrategy:FinishedVerify.4]  ERROR Message being processed is: org.mule.transport.DefaultMessageAdapter/org.mule.transport.DefaultMessageAdapter@421d881d{id=a400c3b3-3e85-11df-b872-0db297393a3e, payload=edu.ucsb.eucalyptus.cloud.VmAllocationInfo, correlationId=a400c3b3-3e85-11df-b872-0db297393a3e, correlationGroup=-1, correlationSeq=-1, encoding=UTF-8, exceptionPayload=org.mule.message.DefaultExceptionPayload@20d349d4}
12:29:26 [ClusterAllocator:New I/O client worker #2-1]  ERROR Number of running VMs is greater than number of assigned addresses!
```


Thanks!

---

### Post by Petrock6 on 2010-04-02
Anyyone?

---

### Post by wickwire on 2010-04-27
Hi there,

it seems you're using SYSTEM MODE to manage the IP addresses of your instances. You can check these settings in the eucalyptus.conf, node side. I think this means that your cloud host is leaving it to your LAN router to manage and assign IP addresses to each running instance that comes up. 

Try checking this setting, may change it to MANAGED so that the cloud host be the one to assign the IP addresses to each running instance...

---

