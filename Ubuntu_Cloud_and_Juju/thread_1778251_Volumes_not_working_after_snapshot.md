---
title: "Volumes not working after snapshot"
date: 2011-06-08
forum: Ubuntu Cloud and Juju
---

### Post by Ohm's Lawyer on 2011-06-08
Hello all,
I'm having some issues with my volumes. I decided to back up my volumes yesterday, so I took snapshots of everything. Ever since, I've not been able to completely attach the volumes to my instances. I can run euca-attach-volume and everything appears fine. When I describe them, they are "in use" by the correct instance. However, when I log into the instance to mount the volume, there is no sdb to mount. This setup worked prior to the snapshot and abruptly stopped after.

My nc.log shows the following error:
```
[Wed Jun  8 10:48:37 2011][002177][EUCADEBUG ] doDescribeInstances(): instanceId=i-536E0989 publicIp=0.0.0.0 privateIp=172.11.1.2 mac=D0:0D:53:6E:09:89 vlan=10 networkIndex=2
[Wed Jun  8 10:48:43 2011][002177][EUCADEBUG ] doDescribeResource() invoked
[Wed Jun  8 10:48:44 2011][002177][EUCAINFO  ] doAttachVolume() invoked (id=i-536E0989 vol=vol-58A40619 remote=//,192.168.14.12,iqn.2009-06.com.eucalyptus.fluster:store38,aQLGNuL++57V/pfp/yn3ttCK5uJzIe66D/y7ciZVAxsdOU9owb5jSuY9f9wJOvQnr/eQTDjMjcW7C5nejTf9YpDBPfkjaRrd/i5P1axVMhp+B7kRzeUIoFfiCXvyn+2uOJA+jVRVOffoyrj03CxdAGUNjQvN7im8EUu8Es7Su/wwUnsWVcrkDB0pOE/CQTB+O5pqbZfOlmzBVvGczS8rzvBKTV54vhqzO+1kiEMM2CVfjygb1u7v4oZeix8eJ62I5d843UmCC5E50qkpR0f/ZidV/ZmdMNIlvnPtpFw05+2Lv6TcBdXwBI66mtwfZSk9X/ny1fFeIWG0junkkp8IGA== local=/dev/sdb)
[Wed Jun  8 10:48:44 2011][002177][EUCAINFO  ] connect_iscsi_target invoked (dev_string=//,192.168.14.12,iqn.2009-06.com.eucalyptus.fluster:store38,aQLGNuL++57V/pfp/yn3ttCK5uJzIe66D/y7ciZVAxsdOU9owb5jSuY9f9wJOvQnr/eQTDjMjcW7C5nejTf9YpDBPfkjaRrd/i5P1axVMhp+B7kRzeUIoFfiCXvyn+2uOJA+jVRVOffoyrj03CxdAGUNjQvN7im8EUu8Es7Su/wwUnsWVcrkDB0pOE/CQTB+O5pqbZfOlmzBVvGczS8rzvBKTV54vhqzO+1kiEMM2CVfjygb1u7v4oZeix8eJ62I5d843UmCC5E50qkpR0f/ZidV/ZmdMNIlvnPtpFw05+2Lv6TcBdXwBI66mtwfZSk9X/ny1fFeIWG0junkkp8IGA==)
[Wed Jun  8 10:50:51 2011][002177][EUCAERROR ] ERROR: connect_iscsi_target failed
[Wed Jun  8 10:50:51 2011][002177][EUCAERROR ] AttachVolume(): failed to connect to iscsi target
[Wed Jun  8 10:50:51 2011][002177][EUCAERROR ] ERROR: doAttachVolume() failed error=1
[Wed Jun  8 10:50:51 2011][002177][EUCADEBUG ] doDescribeResource() invoked
[Wed Jun  8 10:50:51 2011][002177][EUCADEBUG ] doDescribeInstances() invoked
```My cloud-error log is as follows:
```
10:49:22 ERROR [ReplyQueue:Address.16] org.mule.api.service.ServiceException: Component that caused exception is: Address. Message payload is of type: DisassociateAddressType
org.mule.api.service.ServiceException: Component that caused exception is: Address. Message payload is of type: DisassociateAddressType
        at org.mule.component.DefaultLifecycleAdapter.intercept(DefaultLifecycleAdapter.java:214)
        at org.mule.component.AbstractJavaComponent.invokeComponentInstance(AbstractJavaComponent.java:82)
        at org.mule.component.AbstractJavaComponent.doOnCall(AbstractJavaComponent.java:73)
        at org.mule.component.AbstractComponent.onCall(AbstractComponent.java:87)
        at org.mule.model.seda.SedaService$ComponentStageWorker.run(SedaService.java:533)
        at org.mule.work.WorkerContext.run(WorkerContext.java:310)
        at edu.emory.mathcs.backport.java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1061)
        at edu.emory.mathcs.backport.java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:575)
        at java.lang.Thread.run(Thread.java:636)
Caused by: com.eucalyptus.util.EucalyptusCloudException: Permission denied while trying to release address: 192.168.14.100
        at com.eucalyptus.address.Addresses.restrictedLookup(Addresses.java:186)
        at com.eucalyptus.address.AddressManager.DisassociateAddress(AddressManager.java:200)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
        at java.lang.reflect.Method.invoke(Method.java:616)
        at org.mule.model.resolvers.AbstractEntryPointResolver.invokeMethod(AbstractEntryPointResolver.java:147)
        at org.mule.model.resolvers.ReflectionEntryPointResolver.invoke(ReflectionEntryPointResolver.java:178)
        at org.mule.model.resolvers.DefaultEntryPointResolverSet.invoke(DefaultEntryPointResolverSet.java:50)
        at org.mule.component.DefaultLifecycleAdapter.intercept(DefaultLifecycleAdapter.java:202)
        ... 8 more


10:50:17 ERROR [RemoteBootstrapperClient:New I/O client boss #1] java.net.ConnectException: Connection refused
java.net.ConnectException: Connection refused
        at sun.nio.ch.SocketChannelImpl.checkConnect(Native Method)
        at sun.nio.ch.SocketChannelImpl.finishConnect(SocketChannelImpl.java:592)
        at org.jboss.netty.channel.socket.nio.NioClientSocketPipelineSink$Boss.connect(NioClientSocketPipelineSink.java:351)
        at org.jboss.netty.channel.socket.nio.NioClientSocketPipelineSink$Boss.processSelectedKeys(NioClientSocketPipelineSink.java:322)
        at org.jboss.netty.channel.socket.nio.NioClientSocketPipelineSink$Boss.run(NioClientSocketPipelineSink.java:247)
        at org.jboss.netty.util.internal.IoWorkerRunnable.run(IoWorkerRunnable.java:53)
        at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1110)
        at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:603)
        at java.lang.Thread.run(Thread.java:636)
        at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:603)
        at java.lang.Thread.run(Thread.java:636)
```cloud-debug.log gives me my standard:
```
10:49:57 ERROR [SystemClock:SystemClockTimer] java.lang.OutOfMemoryError: Java heap space java.lang.OutOfMemoryError: Java heap space
```Also, somewhere along my noodling around the logs, there was something about NO SPACE. Unfortunately I cant remember where I saw it or in what context. I've currently got 16gig of RAM, 24gig of swap, and 2TB of HDD space on the SC. 

As for the heap space error, that's just something I've been dealing with by rebooting. My settings are:
```
CLOUD_OPTS="-Xms512m -Xmx512m -XX:MaxPermSize=256mm"
```I was actually intending to reinstall the SC after the backups were made, but this issue is making me a little nervous. Has anyone else had this issue, or know what's going on? Any help would be greatly appreciated.

Thanks in advance!

---

### Post by Ohm's Lawyer on 2011-06-08
I found the NO SPACE error, it was in cloud-error.log on the SC:

```
19:06:24 ERROR [SystemUtil:pool-9-thread-1] com.eucalyptus.util.ExecutionException: ///usr/lib/eucalyptus/euca_rootwrap losetup -d /dev/loop0  error: loop: can't delete device /dev/loop0: Device or resource busy

19:28:10 ERROR [SystemUtil:pool-8-thread-1] com.eucalyptus.util.ExecutionException: ///usr/lib/eucalyptus/euca_rootwrap dd if=//var/lib/eucalyptus/volumes/snap-5FAC0658 of=/dev/vg-t9naYA../lv-c5YuBw.. bs=1M  error: /bin/dd: writing `/dev/vg-t9naYA../lv-c5YuBw..': [COLOR=Red]No space left on device[/COLOR]
10241+0 records in
10240+0 records out
10737418240 bytes (11 GB) copied, 164.552 s, 65.3 MB/s

19:28:10 ERROR [SystemUtil:pool-8-thread-1] com.eucalyptus.util.ExecutionException: ///usr/lib/eucalyptus/euca_rootwrap tgtadm --lld iscsi --op show --mode target --tid 59  error: tgtadm: can't find the target

20:32:06 ERROR [BlockStorage:pool-9-thread-1] com.eucalyptus.util.EucalyptusCloudException: Unable to find snapshot: snap-5FAC0658
```

---

### Post by Ohm's Lawyer on 2011-06-08
I also found the following two logs that look like they might be important:

/var/log/eucalyptus/httpd-nc_error_log on the Node Controller

```
iscsiadm: No active sessions.
iscsiadm: No active sessions.
iscsiadm: No active sessions.
iscsiadm: No active sessions.
iscsiadm: No active sessions.
/bin/dd if=/dev/zero of=/var/lib/eucalyptus/instances//admin/i-40B10895/disk bs=1M seek=5192 count=1 >/dev/null 2>&1
WARNING: you are attempting to use /sbin/parted to operate on (mkpartfs) a file system.
/sbin/parted's file system manipulation code is not as robust as what you'll find in
dedicated, file-system-specific packages like e2fsprogs.  We recommend
you use /sbin/parted only to manipulate partition tables, whenever possible.
Support for performing most operations on most types of file systems
will be removed in an upcoming release.
/sbin/parted --script /var/lib/eucalyptus/instances//admin/i-40B10895/disk mkpartfs primary ext2 6291520s 9209520s
WARNING: you are attempting to use /sbin/parted to operate on (mkpartfs) a file system.
/sbin/parted's file system manipulation code is not as robust as what you'll find in
dedicated, file-system-specific packages like e2fsprogs.  We recommend
you use /sbin/parted only to manipulate partition tables, whenever possible.
Support for performing most operations on most types of file systems
will be removed in an upcoming release.
/sbin/parted --script /var/lib/eucalyptus/instances//admin/i-40B10895/disk mkpartfs primary linux-swap 9209521s 100%
iscsiadm: Connection to Discovery Address 192.168.14.12 closed
iscsiadm: Login I/O error, failed to receive a PDU
iscsiadm: retrying discovery login to 192.168.14.12
iscsiadm: Connection to Discovery Address 192.168.14.12 closed
iscsiadm: Login I/O error, failed to receive a PDU
iscsiadm: retrying discovery login to 192.168.14.12
iscsiadm: Connection to Discovery Address 192.168.14.12 failed
iscsiadm: Login I/O error, failed to receive a PDU
iscsiadm: retrying discovery login to 192.168.14.12
iscsiadm: Connection to Discovery Address 192.168.14.12 closed
iscsiadm: Login I/O error, failed to receive a PDU
iscsiadm: retrying discovery login to 192.168.14.12
iscsiadm: Connection to Discovery Address 192.168.14.12 failed
iscsiadm: Login I/O error, failed to receive a PDU
iscsiadm: retrying discovery login to 192.168.14.12
iscsiadm: connection login retries (reopen_max) 5 exceeded
iscsiadm: Could not perform SendTargets discovery.
iscsiadm: Could not login to [iface: default, target: iqn.2009-06.com.eucalyptus.fluster:store50, portal: 192.168.14.12,3260]:
iscsiadm: initiator reported error (8 - connection timed out)
iscsiadm: No active sessions.
iscsiadm: No active sessions.
iscsiadm: No active sessions.
iscsiadm: No active sessions.
iscsiadm: No active sessions.
```


/var/log/messages on Node Controller

```
Jun  8 10:44:29 monc1 kernel: [   10.965864] type=1400 audit(1307555069.911:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1211 comm="apparmor_parser"
Jun  8 10:44:29 monc1 kernel: [   10.966260] type=1400 audit(1307555069.911:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1211 comm="apparmor_parser"
Jun  8 10:44:29 monc1 kernel: [   10.979251] type=1400 audit(1307555069.921:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/libvirtd" pid=1213 comm="apparmor_parser"
Jun  8 10:44:29 monc1 kernel: [   10.994608] type=1400 audit(1307555069.941:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1215 comm="apparmor_parser"
Jun  8 10:44:32 monc1 libvirtd: 10:44:32.010: warning : networkAddIptablesRules:850 : Could not add rule to fixup DHCP response checksums on network 'default'.
Jun  8 10:44:32 monc1 libvirtd: 10:44:32.010: warning : networkAddIptablesRules:851 : May need to update iptables package & kernel to support CHECKSUM rule.
Jun  8 10:44:37 monc1 kernel: [   18.572436] e1000e: eth1 NIC Link is Up 100 Mbps Full Duplex, Flow Control: RX/TX
Jun  8 10:44:37 monc1 kernel: [   18.572441] e1000e 0000:06:00.1: eth1: 10/100 speed: disabling TSO
Jun  8 10:44:37 monc1 kernel: [   18.574651] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
Jun  8 10:44:38 monc1 kernel: [   19.457836] Loading iSCSI transport class v2.0-870.
Jun  8 10:44:38 monc1 kernel: [   19.486897] iscsi: registered transport (tcp)
Jun  8 10:44:38 monc1 kernel: [   19.523760] br0: port 1(eth0) entering forwarding state
Jun  8 10:44:38 monc1 kernel: [   19.609206] iscsi: registered transport (iser)
Jun  8 10:44:48 monc1 kernel: [   28.744939] ip6_tables: (C) 2000-2006 Netfilter Core Team
Jun  8 10:44:48 monc1 libvirtd: 10:44:48.241: warning : qemudStartup:1832 : Unable to create cgroup for driver: No such device or address
Jun  8 10:44:48 monc1 kernel: [   29.319030] lo: Disabled Privacy Extensions
Jun  8 10:44:48 monc1 libvirtd: 10:44:48.766: warning : lxcStartup:1895 : Unable to create cgroup for driver: No such device or address
Jun  8 10:44:48 monc1 kernel: [   29.506240] aoe: AoE v47 initialised.
Jun  8 10:48:09 monc1 libvirtd: 10:48:09.099: warning : qemudParsePCIDeviceStrs:1422 : Unexpected exit status '1', qemu probably failed
Jun  8 10:48:09 monc1 kernel: [  229.989867] audit_printk_skb: 3 callbacks suppressed
Jun  8 10:48:09 monc1 kernel: [  229.989871] type=1400 audit(1307555289.386:13): apparmor="STATUS" operation="profile_load" name="libvirt-19c5471e-321a-7e77-347f-35c6cf83f3ec" pid=2668 comm="apparmor_parser"
Jun  8 10:48:10 monc1 libvirtd: 10:48:10.018: warning : qemudParsePCIDeviceStrs:1422 : Unexpected exit status '1', qemu probably failed
Jun  8 10:48:10 monc1 kernel: [  230.606658] device vnet0 entered promiscuous mode
Jun  8 10:48:10 monc1 kernel: [  230.606704] br0: new device vnet0 does not support netpoll (disabling)
Jun  8 10:48:10 monc1 kernel: [  230.608603] br0: port 2(vnet0) entering learning state
Jun  8 10:48:10 monc1 kernel: [  230.608608] br0: port 2(vnet0) entering learning state
Jun  8 10:48:19 monc1 kernel: [  239.620011] br0: port 2(vnet0) entering forwarding state
Jun  8 10:48:48 monc1 kernel: [  269.550750] scsi4 : iSCSI Initiator over TCP/IP
Jun  8 13:42:28 monc1 libvirtd: 13:42:28.677: warning : qemudParsePCIDeviceStrs:1422 : Unexpected exit status '1', qemu probably failed
Jun  8 13:42:28 monc1 kernel: [10689.372496] type=1400 audit(1307565748.772:14): apparmor="STATUS" operation="profile_load" name="libvirt-cbf94137-6907-84fc-a2cf-9d6f2a66a2aa" pid=23500 comm="apparmor_parser"
Jun  8 13:42:29 monc1 libvirtd: 13:42:29.357: warning : qemudParsePCIDeviceStrs:1422 : Unexpected exit status '1', qemu probably failed
Jun  8 13:42:29 monc1 kernel: [10689.945846] device vnet1 entered promiscuous mode
Jun  8 13:42:29 monc1 kernel: [10689.947754] br0: port 3(vnet1) entering learning state
Jun  8 13:42:29 monc1 kernel: [10689.947759] br0: port 3(vnet1) entering learning state
Jun  8 13:42:38 monc1 kernel: [10698.960014] br0: port 3(vnet1) entering forwarding state
Jun  8 13:43:12 monc1 kernel: [10732.749558] scsi5 : iSCSI Initiator over TCP/IP
```

---

### Post by Ohm's Lawyer on 2011-06-14
It seems that for whatever reason, the 20th reboot was the magic number. Everything just magically started working again. Perhaps it was the threat of a fresh install. Who knows....UEC...<sigh>

---

