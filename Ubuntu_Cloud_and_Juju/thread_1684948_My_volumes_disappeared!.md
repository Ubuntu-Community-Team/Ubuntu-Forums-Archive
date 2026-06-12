---
title: "My volumes disappeared!"
date: 2011-02-09
forum: Ubuntu Cloud and Juju
---

### Post by Ohm's Lawyer on 2011-02-09
Hi all,
Well I've had my cloud up and running relatively problem free for the last couple of months, and so far it's been a blast. Occasionally, I'd notice when I'd run euca-describe-volumes, nothing would show up. It wouldn't effect my currently running instances, but I couldn't create a new volume or attach a volume to an instance when this would happen. Generally, I could just reboot my storage controller and everything would work just fine again.

All of a sudden last night, it happened again, but no matter how much I reboot, my volumes can't be described. However, when I get on my storage controller and check the eucalyptus/volumes directory, they are all still there. I can also check the eucalyptus-storage.scripts on my cloud controller and everything looks good there too.

Has anyone experienced this? Any ideas on how to fix it?

Thanks.

---

### Post by kim0 on 2011-02-10
Can you look into /var/log/eucalyptus/ for any interesting error messages and/or paste those files somewhere

---

### Post by Ohm's Lawyer on 2011-02-13
Thanks for the reply however, after much searching, I believe I've fixed my problem. When I initially installed my cloud I had a different cluster machine. Despite having unregistered it, the system maintained logs of its existence. So I just fgrep-ed the name of my old cluster and removed it where I saw it. That seems to have fixed the issue. 

I do have another question though. Would there be any reason why I couldn't have multiple clusters on one cloud? I'd like to have one standard cluster and one high performance. Is that feasible?

Thanks!

---

### Post by Ohm's Lawyer on 2011-02-13
So, I lied. It's not working. It just worked for a couple of days then happened again. Which logs would you like to see? There is a lot to sift through, but nothing is popping out to me right away.

---

### Post by kim0 on 2011-02-14
Perhaps
cloud-debug.log
cloud-error.log
cloud-output.log

on the SC machine

---

### Post by Ohm's Lawyer on 2011-02-14
Ok, well all 3 are pretty big. Here is a snippet of cloud-error.log

```
03:06:56 ERROR [ISCSIManager:Thread-11] com.eucalyptus.util.EucalyptusCloudException: tgtadm: this target already exists

03:06:56 ERROR [ISCSIManager:Thread-11] com.eucalyptus.util.EucalyptusCloudException: tgtadm: this logical unit number already exists

03:06:56 ERROR [ISCSIManager:Thread-11] com.eucalyptus.util.EucalyptusCloudException: tgtadm: this target already exists

03:07:28 ERROR [NioServerHandler:New I/O server worker #1-11] Internal Error.
java.io.IOException: Connection reset by peer
        at sun.nio.ch.FileDispatcher.read0(Native Method)
        at sun.nio.ch.SocketDispatcher.read(SocketDispatcher.java:39)
        at sun.nio.ch.IOUtil.readIntoNativeBuffer(IOUtil.java:251)
        at sun.nio.ch.IOUtil.read(IOUtil.java:224)
        at sun.nio.ch.SocketChannelImpl.read(SocketChannelImpl.java:254)
        at org.jboss.netty.buffer.HeapChannelBuffer.setBytes(HeapChannelBuffer.java:163)
        at org.jboss.netty.buffer.AbstractChannelBuffer.writeBytes(AbstractChannelBuffer.java:432)
        at org.jboss.netty.channel.socket.nio.NioWorker.read(NioWorker.java:312)
at org.jboss.netty.channel.socket.nio.NioWorker.processSelectedKeys(NioWorker.java:282)
        at org.jboss.netty.channel.socket.nio.NioWorker.run(NioWorker.java:203)
        at org.jboss.netty.util.internal.IoWorkerRunnable.run(IoWorkerRunnable.java:53)
        at org.jboss.netty.handler.execution.MemoryAwareThreadPoolExecutor$MemoryAwareRunnable.run(MemoryAwareThreadPoolExecutor.java:502)
        at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1110)
        at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:603)
        at java.lang.Thread.run(Thread.java:636)
03:08:23 ERROR [NioServerHandler:New I/O server worker #1-14] Internal Error.
java.io.IOException: Connection reset by peer
        at sun.nio.ch.FileDispatcher.read0(Native Method)
        at sun.nio.ch.SocketDispatcher.read(SocketDispatcher.java:39)
        at sun.nio.ch.IOUtil.readIntoNativeBuffer(IOUtil.java:251)
        at sun.nio.ch.IOUtil.read(IOUtil.java:224)
        at sun.nio.ch.SocketChannelImpl.read(SocketChannelImpl.java:254)
        at org.jboss.netty.buffer.HeapChannelBuffer.setBytes(HeapChannelBuffer.java:163)
        at org.jboss.netty.buffer.AbstractChannelBuffer.writeBytes(AbstractChannelBuffer.java:432)
        at org.jboss.netty.channel.socket.nio.NioWorker.read(NioWorker.java:312)
        at org.jboss.netty.channel.socket.nio.NioWorker.processSelectedKeys(NioWorker.java:282)
        at org.jboss.netty.channel.socket.nio.NioWorker.run(NioWorker.java:203)
        at org.jboss.netty.util.internal.IoWorkerRunnable.run(IoWorkerRunnable.java:53)
        at org.jboss.netty.handler.execution.MemoryAwareThreadPoolExecutor$MemoryAwareRunnable.run(MemoryAwareThreadPoolExecutor.java:502)
        at java.util.concurrent.ThreadPoolExecutor.runWorker(ThreadPoolExecutor.java:1110)
        at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:603)
        at java.lang.Thread.run(Thread.java:636)
03:14:58 ERROR [SystemUtil:Thread-13] com.eucalyptus.util.ExecutionException: ///usr/lib/eucalyptus/euca_rootwrap losetup /dev/loop4  error: loop: can't get info on device /dev/loop4: No such device or address
03:14:58 ERROR [SystemUtil:Thread-13] com.eucalyptus.util.ExecutionException: ///usr/lib/eucalyptus/euca_rootwrap losetup /dev/loop0  error: loop: can't get info on device /dev/loop0: No such device or address

03:14:58 ERROR [SystemUtil:Thread-13] com.eucalyptus.util.ExecutionException: ///usr/lib/eucalyptus/euca_rootwrap losetup /dev/loop2  error: loop: can't get info on device /dev/loop2: No such device or address

03:14:58 ERROR [SystemUtil:Thread-13] com.eucalyptus.util.ExecutionException: ///usr/lib/eucalyptus/euca_rootwrap losetup /dev/loop1  error: loop: can't get info on device /dev/loop1: No such device or address

03:14:59 ERROR [SystemUtil:Thread-13] com.eucalyptus.util.ExecutionException: ///usr/lib/eucalyptus/euca_rootwrap losetup /dev/loop5  error: loop: can't get info on device /dev/loop5: No such device or address

03:22:39 ERROR [SystemUtil:pool-8-thread-1] com.eucalyptus.util.ExecutionException: ///usr/lib/eucalyptus/euca_rootwrap tgtadm --lld iscsi --op show --mode target --tid 20  error:
11:55:46 ERROR [NioServerHandler:New I/O server worker #1-4] Internal Error.
java.lang.OutOfMemoryError: Java heap space
11:56:13 ERROR [NioServerHandler:New I/O server worker #1-17] Internal Error.
11:56:13 ERROR [NioServerHandler:New I/O server worker #1-17] Internal Error.
java.lang.OutOfMemoryError: Java heap space
        at org.jibx.runtime.impl.UnmarshallingContext.getUnmarshaller(Unknown Source)
        at org.jibx.runtime.impl.UnmarshallingContext.unmarshalElement(Unknown Source)
        at com.eucalyptus.binding.Binding.fromOM(Binding.java:235)
        at com.eucalyptus.ws.handlers.BindingHandler.incomingMessage(BindingHandler.java:116)
        at com.eucalyptus.ws.handlers.MessageStackHandler.handleUpstream(MessageStackHandler.java:127)
        at com.eucalyptus.ws.handlers.MessageStackHandler.handleUpstream(MessageStackHandler.java:134)
        at com.eucalyptus.ws.handlers.MessageStackHandler.handleUpstream(MessageStackHandler.java:134)
        at com.eucalyptus.ws.handlers.MessageStackHandler.handleUpstream(MessageStackHandler.java:134)
        at com.eucalyptus.ws.handlers.MessageStackHandler.handleUpstream(MessageStackHandler.java:134)
        at com.eucalyptus.ws.handlers.HeartbeatHandler$SimpleHeartbeatHandler.messageReceived(HeartbeatHandler.java:275)
        at com.eucalyptus.ws.server.NioServerHandler.messageReceived(NioServerHandler.java:127)
        at org.jboss.netty.handler.stream.ChunkedWriteHandler.handleUpstream(ChunkedWriteHandler.java:114)
        at org.jboss.netty.channel.Channels.fireMessageReceived(Channels.java:385)
        at org.jboss.netty.handler.codec.replay.ReplayingDecoder.unfoldAndfireMessageReceived(ReplayingDecoder.java:459)
11:57:03 ERROR [NioServerHandler:New I/O server worker #1-2] Internal Error.
java.lang.OutOfMemoryError: Java heap space
        at org.apache.xml.security.utils.UnsyncByteArrayOutputStream$1.initialValue(UnsyncByteArrayOutputStream.java:29)
        at java.lang.ThreadLocal.setInitialValue(ThreadLocal.java:160)
        at java.lang.ThreadLocal.get(ThreadLocal.java:150)
        at org.apache.xml.security.utils.UnsyncByteArrayOutputStream.<init>(UnsyncByteArrayOutputStream.java:37)
        at org.apache.xml.security.c14n.implementations.CanonicalizerBase.<init>(CanonicalizerBase.java:102)
        at org.apache.xml.security.c14n.implementations.Canonicalizer20010315Excl.<init>(Canonicalizer20010315Excl.java:70)
        at org.apache.xml.security.c14n.implementations.Canonicalizer20010315ExclOmitComments.<init>(Canonicalizer20010315ExclOmitComments.java:33)
        at sun.reflect.GeneratedConstructorAccessor54.newInstance(Unknown Source)
        at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
        at java.lang.reflect.Constructor.newInstance(Constructor.java:532)
        at java.lang.Class.newInstance0(Class.java:372)
        at java.lang.Class.newInstance(Class.java:325)
        at org.apache.xml.security.c14n.Canonicalizer.<init>(Canonicalizer.java:110)
        at org.apache.xml.security.c14n.Canonicalizer.getInstance(Canonicalizer.java:131)
        at org.apache.xml.security.signature.SignedInfo.signInOctectStream(SignedInfo.java:278)
        at org.apache.xml.security.signature.XMLSignature.checkSignatureValue(XMLSignature.java:611)
        at org.apache.xml.security.signature.XMLSignature.checkSignatureValue(XMLSignature.java:562)
        at com.eucalyptus.auth.util.WSSecurity.verifySignature(WSSecurity.java:157)
        at com.eucalyptus.ws.handlers.wssecurity.InternalWsSecHandler.incomingMessage(InternalWsSecHandler.java:120)
        at com.eucalyptus.ws.handlers.MessageStackHandler.handleUpstream(MessageStackHandler.java:127)
        at com.eucalyptus.ws.handlers.MessageStackHandler.handleUpstream(MessageStackHandler.java:134)
        at com.eucalyptus.ws.handlers.HeartbeatHandler$SimpleHeartbeatHandler.messageReceived(HeartbeatHandler.java:275)
        at com.eucalyptus.ws.server.NioServerHandler.messageReceived(NioServerHandler.java:127)
12:06:35 ERROR [SystemClock:SystemClockTimer] java.lang.OutOfMemoryError: Java heap space
java.lang.OutOfMemoryError: Java heap space
12:15:55 ERROR [SystemClock:SystemClockTimer] java.lang.OutOfMemoryError: Java heap space
java.lang.OutOfMemoryError: Java heap space
13:12:13 ERROR [SystemClock:SystemClockTimer] java.lang.OutOfMemoryError: Java heap space
java.lang.OutOfMemoryError: Java heap space
13:54:45 ERROR [SystemUtil:Thread-13] com.eucalyptus.util.ExecutionException: ///usr/lib/eucalyptus/euca_rootwrap losetup /dev/loop4  error: loop: can't get info on device /dev/loop4: No such device or address

13:54:45 ERROR [SystemUtil:Thread-13] com.eucalyptus.util.ExecutionException: ///usr/lib/eucalyptus/euca_rootwrap losetup /dev/loop3  error: loop: can't get info on device /dev/loop3: No such device or address

13:54:45 ERROR [SystemUtil:Thread-13] com.eucalyptus.util.ExecutionException: ///usr/lib/eucalyptus/euca_rootwrap losetup /dev/loop0  error: loop: can't get info on device /dev/loop0: No such device or address

13:54:45 ERROR [SystemUtil:Thread-13] com.eucalyptus.util.ExecutionException: ///usr/lib/eucalyptus/euca_rootwrap losetup /dev/loop2  error: loop: can't get info on device /dev/loop2: No such device or address

13:54:45 ERROR [SystemUtil:Thread-13] com.eucalyptus.util.ExecutionException: ///usr/lib/eucalyptus/euca_rootwrap losetup /dev/loop1  error: loop: can't get info on device /dev/loop1: No such device or address
13:54:45 ERROR [SystemUtil:Thread-13] com.eucalyptus.util.ExecutionException: ///usr/lib/eucalyptus/euca_rootwrap losetup /dev/loop1  error: loop: can't get info on device /dev/loop1: No such device or address

13:54:45 ERROR [SystemUtil:Thread-13] com.eucalyptus.util.ExecutionException: ///usr/lib/eucalyptus/euca_rootwrap losetup /dev/loop5  error: loop: can't get info on device /dev/loop5: No such device or address

14:03:07 ERROR [SystemUtil:pool-8-thread-1] com.eucalyptus.util.ExecutionException: ///usr/lib/eucalyptus/euca_rootwrap tgtadm --lld iscsi --op show --mode target --tid 21  error: tgtadm: can't find the target

15:17:23 ERROR [SystemUtil:pool-8-thread-2] com.eucalyptus.util.ExecutionException: ///usr/lib/eucalyptus/euca_rootwrap tgtadm --lld iscsi --op show --mode target --tid 22  error: tgtadm: can't find the target

15:38:43 ERROR [SystemUtil:pool-8-thread-3] com.eucalyptus.util.ExecutionException: ///usr/lib/eucalyptus/euca_rootwrap tgtadm --lld iscsi --op show --mode target --tid 23  error: tgtadm: can't find the target

```

The other two, cloud-debug.log and cloud-output.log don't look too interesting.

cloud-debug.log
```
16:53:34 DEBUG [Context:New I/O server worker #1-12] :1297727614103:Context:CONTEXT_CREATE:dfd8fd6e-ca13-4b53-977b-0b52154757b2:[id: 0x60e11e64, /192.168.14.10:43620 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
16:53:34 DEBUG [Context:New I/O server worker #1-12] :1297727614113:Context:CONTEXT_USER:dfd8fd6e-ca13-4b53-977b-0b52154757b2:admin:MessageStackHandler.handleUpstream.127
16:53:54 DEBUG [Context:New I/O server worker #1-13] :1297727634070:Context:CONTEXT_CREATE:47a944f4-85fc-4e10-81ca-5c697756cec9:[id: 0x3f24187a, /192.168.14.10:43655 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
16:53:54 DEBUG [Context:New I/O server worker #1-13] :1297727634080:Context:CONTEXT_USER:47a944f4-85fc-4e10-81ca-5c697756cec9:admin:MessageStackHandler.handleUpstream.127
16:54:14 DEBUG [Context:New I/O server worker #1-14] :1297727654113:Context:CONTEXT_CREATE:702d5920-f1c8-4fa8-a9cb-c6f691de49aa:[id: 0x7d74099d, /192.168.14.10:43758 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
16:54:14 DEBUG [Context:New I/O server worker #1-14] :1297727654122:Context:CONTEXT_USER:702d5920-f1c8-4fa8-a9cb-c6f691de49aa:admin:MessageStackHandler.handleUpstream.127
16:54:34 DEBUG [Context:New I/O server worker #1-15] :1297727674110:Context:CONTEXT_CREATE:fcf66423-6a6d-4776-a005-d82ec0e90453:[id: 0x7d3d9f96, /192.168.14.10:60750 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
16:56:34 DEBUG [Context:New I/O server worker #1-4] :1297727794134:Context:CONTEXT_USER:432a12d9-8036-48f0-a213-08795492a559:admin:MessageStackHandler.handleUpstream.127
16:56:54 DEBUG [Context:New I/O server worker #1-5] :1297727814075:Context:CONTEXT_CREATE:0baae7e8-2185-4f85-8e3c-a47337672c6c:[id: 0x6b530ead, /192.168.14.10:33049 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
16:56:54 DEBUG [Context:New I/O server worker #1-5] :1297727814085:Context:CONTEXT_USER:0baae7e8-2185-4f85-8e3c-a47337672c6c:admin:MessageStackHandler.handleUpstream.127
16:57:14 DEBUG [Context:New I/O server worker #1-6] :1297727834115:Context:CONTEXT_CREATE:46bf3f18-0886-4f77-9a7f-43a0d5f4f2cd:[id: 0x4eb386eb, /192.168.14.10:33152 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
16:57:14 DEBUG [Context:New I/O server worker #1-6] :1297727834130:Context:CONTEXT_USER:46bf3f18-0886-4f77-9a7f-43a0d5f4f2cd:admin:MessageStackHandler.handleUpstream.127
16:57:34 DEBUG [Context:New I/O server worker #1-7] :1297727854146:Context:CONTEXT_CREATE:c23e5b28-23b7-4eb8-b94f-37d206bfaaf2:[id: 0x17cd5904, /192.168.14.10:33242 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
16:59:34 DEBUG [Context:New I/O server worker #1-13] :1297727974128:Context:CONTEXT_USER:d5decf33-7571-47ac-b49e-edeed1f0d800:admin:MessageStackHandler.handleUpstream.127
16:59:54 DEBUG [Context:New I/O server worker #1-14] :1297727994119:Context:CONTEXT_CREATE:9e3067cf-dcb6-44b2-8ad7-d0ef4234198a:[id: 0x641f1e5d, /192.168.14.10:48840 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
16:59:54 DEBUG [Context:New I/O server worker #1-14] :1297727994129:Context:CONTEXT_USER:9e3067cf-dcb6-44b2-8ad7-d0ef4234198a:admin:MessageStackHandler.handleUpstream.127
17:00:14 DEBUG [Context:New I/O server worker #1-15] :1297728014080:Context:CONTEXT_CREATE:70756f99-e19b-4c29-a40f-e97c1fc9d2e6:[id: 0x5169220b, /192.168.14.10:48953 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
17:00:14 DEBUG [Context:New I/O server worker #1-15] :1297728014115:Context:CONTEXT_USER:70756f99-e19b-4c29-a40f-e97c1fc9d2e6:admin:MessageStackHandler.handleUpstream.127
17:00:34 DEBUG [Context:New I/O server worker #1-16] :1297728034116:Context:CONTEXT_CREATE:0c99bd67-6634-40eb-ab22-2ed6a91eb75c:[id: 0x1eeb4a8d, /192.168.14.10:49029 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
17:02:54 DEBUG [Context:New I/O server worker #1-6] :1297728174147:Context:CONTEXT_USER:3b95541d-364b-47e8-a0ba-3f91943fcfc3:admin:MessageStackHandler.handleUpstream.127
17:03:14 DEBUG [Context:New I/O server worker #1-7] :1297728194130:Context:CONTEXT_CREATE:57bca644-c8d6-4072-9f2c-9469a61fb7b5:[id: 0x71a0a728, /192.168.14.10:49688 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
17:03:14 DEBUG [Context:New I/O server worker #1-7] :1297728194139:Context:CONTEXT_USER:57bca644-c8d6-4072-9f2c-9469a61fb7b5:admin:MessageStackHandler.handleUpstream.127
17:03:34 DEBUG [Context:New I/O server worker #1-8] :1297728214076:Context:CONTEXT_CREATE:3323d743-dc5b-452e-b6ed-b76702c65c3d:[id: 0x07589a13, /192.168.14.10:49759 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
17:03:34 DEBUG [Context:New I/O server worker #1-8] :1297728214085:Context:CONTEXT_USER:3323d743-dc5b-452e-b6ed-b76702c65c3d:admin:MessageStackHandler.handleUpstream.127
17:03:54 DEBUG [Context:New I/O server worker #1-9] :1297728234120:Context:CONTEXT_CREATE:7a290a00-2366-4eb8-92a7-7262392e3ae6:[id: 0x0fbc0ee2, /192.168.14.10:49814 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
17:03:54 DEBUG [Context:New I/O server worker #1-9] :1297728234130:Context:CONTEXT_USER:7a290a00-2366-4eb8-92a7-7262392e3ae6:admin:MessageStackHandler.handleUpstream.127
17:06:34 DEBUG [Context:New I/O server worker #1-17] :1297728394142:Context:CONTEXT_CREATE:0cbe5550-f588-4310-8c54-da3dc7ef70e5:[id: 0x306514ef, /192.168.14.10:37500 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
17:06:34 DEBUG [Context:New I/O server worker #1-17] :1297728394151:Context:CONTEXT_USER:0cbe5550-f588-4310-8c54-da3dc7ef70e5:admin:MessageStackHandler.handleUpstream.127
17:06:54 DEBUG [Context:New I/O server worker #1-1] :1297728414105:Context:CONTEXT_CREATE:e677d582-8c04-406e-a968-8dd5aad9b4a2:[id: 0x4ad18495, /192.168.14.10:37555 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
17:06:54 DEBUG [Context:New I/O server worker #1-1] :1297728414115:Context:CONTEXT_USER:e677d582-8c04-406e-a968-8dd5aad9b4a2:admin:MessageStackHandler.handleUpstream.127
17:07:14 DEBUG [Context:New I/O server worker #1-2] :1297728434135:Context:CONTEXT_CREATE:e0b1dbd2-1cf1-4efe-abf2-6a78fba2ca4d:[id: 0x5e50755c, /192.168.14.10:37674 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
17:07:14 DEBUG [Context:New I/O server worker #1-2] :1297728434145:Context:CONTEXT_USER:e0b1dbd2-1cf1-4efe-abf2-6a78fba2ca4d:admin:MessageStackHandler.handleUpstream.127
17:07:34 DEBUG [Context:New I/O server worker #1-3] :1297728454081:Context:CONTEXT_CREATE:f5baad6b-8cb6-4d8c-a797-d5c8ab630672:[id: 0x67cc90fb, /192.168.14.10:37745 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
17:09:14 DEBUG [Context:New I/O server worker #1-8] :1297728554141:Context:CONTEXT_USER:15948505-c95f-49ee-b644-3a249e3a8366:admin:MessageStackHandler.handleUpstream.127
17:09:34 DEBUG [Context:New I/O server worker #1-9] :1297728574125:Context:CONTEXT_CREATE:ed019538-27ef-4a84-9015-a70fe0f90e52:[id: 0x68b62603, /192.168.14.10:36938 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
17:09:34 DEBUG [Context:New I/O server worker #1-9] :1297728574134:Context:CONTEXT_USER:ed019538-27ef-4a84-9015-a70fe0f90e52:admin:MessageStackHandler.handleUpstream.127
17:09:54 DEBUG [Context:New I/O server worker #1-10] :1297728594114:Context:CONTEXT_CREATE:5da1f3e8-8d6f-4262-af3c-1854a41bc344:[id: 0x471139f6, /192.168.14.10:36993 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
17:09:54 DEBUG [Context:New I/O server worker #1-10] :1297728594124:Context:CONTEXT_USER:5da1f3e8-8d6f-4262-af3c-1854a41bc344:admin:MessageStackHandler.handleUpstream.127
```
....and it just goes on like that every couple of seconds throughout the day

cloud-output.log
```
16:40:54 DEBUG 140  Context                | :1297726854121:Context:CONTEXT_CREATE:2db538cb-3ebe-4b31-a935-a34b1de7dc68:[id: 0x3b09afa4, /192.168.14.10:41383 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
16:40:54 DEBUG 140  Context                | :1297726854131:Context:CONTEXT_USER:2db538cb-3ebe-4b31-a935-a34b1de7dc68:admin:MessageStackHandler.handleUpstream.127
16:41:14 DEBUG 140  Context                | :1297726874145:Context:CONTEXT_CREATE:f449a1df-0009-40ad-ad5e-c0ed7c4e1de8:[id: 0x3d831968, /192.168.14.10:41486 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
16:41:14 DEBUG 140  Context                | :1297726874155:Context:CONTEXT_USER:f449a1df-0009-40ad-ad5e-c0ed7c4e1de8:admin:MessageStackHandler.handleUpstream.127
16:41:34 DEBUG 140  Context                | :1297726894117:Context:CONTEXT_CREATE:9577dfad-6e77-49ae-be26-110ed602d8e2:[id: 0x520141e0, /192.168.14.10:41605 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
16:41:34 DEBUG 140  Context                | :1297726894127:Context:CONTEXT_USER:9577dfad-6e77-49ae-be26-110ed602d8e2:admin:MessageStackHandler.handleUpstream.127
16:41:54 DEBUG 140  Context                | :1297726914115:Context:CONTEXT_CREATE:2237ed3c-c65e-4a6a-a57b-f22b17c84801:[id: 0x4d58d73f, /192.168.14.10:41628 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
16:44:14 DEBUG 140  Context                | :1297727054086:Context:CONTEXT_USER:a248319e-d778-4cd7-a8d6-4c638cef7e42:admin:MessageStackHandler.handleUpstream.127
16:44:34 DEBUG 140  Context                | :1297727074132:Context:CONTEXT_CREATE:b22aab33-ba0d-4ef8-ac5b-e95a7b2bb1c7:[id: 0x5d7c84f5, /192.168.14.10:40092 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
16:44:34 DEBUG 140  Context                | :1297727074142:Context:CONTEXT_USER:b22aab33-ba0d-4ef8-ac5b-e95a7b2bb1c7:admin:MessageStackHandler.handleUpstream.127
16:44:54 DEBUG 140  Context                | :1297727094075:Context:CONTEXT_CREATE:e2c58eb4-337d-4af7-a086-a8f8706dc541:[id: 0x37200365, /192.168.14.10:40115 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
16:44:54 DEBUG 140  Context                | :1297727094084:Context:CONTEXT_USER:e2c58eb4-337d-4af7-a086-a8f8706dc541:admin:MessageStackHandler.handleUpstream.127
16:45:14 DEBUG 140  Context                | :1297727114105:Context:CONTEXT_CREATE:1a87e6b3-c56a-468a-894c-5e620755f9ee:[id: 0x3b158b74, /192.168.14.10:40221 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
16:45:14 DEBUG 140  Context                | :1297727114125:Context:CONTEXT_USER:1a87e6b3-c56a-468a-894c-5e620755f9ee:admin:MessageStackHandler.handleUpstream.127
16:47:54 DEBUG 140  Context                | :1297727274076:Context:CONTEXT_CREATE:8f921efe-4c11-413c-9c59-1eec0480303f:[id: 0x7a51513a, /192.168.14.10:40853 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
16:47:54 DEBUG 140  Context                | :1297727274085:Context:CONTEXT_USER:8f921efe-4c11-413c-9c59-1eec0480303f:admin:MessageStackHandler.handleUpstream.127
16:48:14 DEBUG 140  Context                | :1297727294074:Context:CONTEXT_CREATE:a443a3d8-a9c2-4c78-a7c0-49847d3ee82d:[id: 0x2a3fc830, /192.168.14.10:40956 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
16:48:14 DEBUG 140  Context                | :1297727294084:Context:CONTEXT_USER:a443a3d8-a9c2-4c78-a7c0-49847d3ee82d:admin:MessageStackHandler.handleUpstream.127
16:48:34 DEBUG 140  Context                | :1297727314104:Context:CONTEXT_CREATE:3dcc19be-c9c0-4adb-8199-66dd43c8101e:[id: 0x1ff1cb6f, /192.168.14.10:41075 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
16:48:34 DEBUG 140  Context                | :1297727314114:Context:CONTEXT_USER:3dcc19be-c9c0-4adb-8199-66dd43c8101e:admin:MessageStackHandler.handleUpstream.127
16:48:54 DEBUG 140  Context                | :1297727334103:Context:CONTEXT_CREATE:ccef3741-c10e-4578-99da-3c53241780b8:[id: 0x1a0e70ab, /192.168.14.10:41098 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
16:51:14 DEBUG 140  Context                | :1297727474149:Context:CONTEXT_USER:5d497480-f7cf-43b6-b5c0-0d37469b170d:admin:MessageStackHandler.handleUpstream.127
16:51:34 DEBUG 140  Context                | :1297727494118:Context:CONTEXT_CREATE:8f2d1e90-ec87-40bc-9f46-3413ab73aaa8:[id: 0x2961c770, /192.168.14.10:43137 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
16:51:34 DEBUG 140  Context                | :1297727494128:Context:CONTEXT_USER:8f2d1e90-ec87-40bc-9f46-3413ab73aaa8:admin:MessageStackHandler.handleUpstream.127
16:51:54 DEBUG 140  Context                | :1297727514154:Context:CONTEXT_CREATE:edfb9a00-1e30-47ca-a1ca-5dfd74a34470:[id: 0x39148a9d, /192.168.14.10:43165 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
16:51:54 DEBUG 140  Context                | :1297727514163:Context:CONTEXT_USER:edfb9a00-1e30-47ca-a1ca-5dfd74a34470:admin:MessageStackHandler.handleUpstream.127
16:52:14 DEBUG 140  Context                | :1297727534081:Context:CONTEXT_CREATE:6a776e08-857c-46eb-b866-d7aed77ffbf1:[id: 0x5c024a6e, /192.168.14.10:43268 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
16:52:14 DEBUG 140  Context                | :1297727534090:Context:CONTEXT_USER:6a776e08-857c-46eb-b866-d7aed77ffbf1:admin:MessageStackHandler.handleUpstream.127
16:54:54 DEBUG 140  Context                | :1297727694113:Context:CONTEXT_CREATE:64f00922-db50-4119-b362-298573c62730:[id: 0x4ac6ef9a, /192.168.14.10:60789 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
16:54:54 DEBUG 140  Context                | :1297727694123:Context:CONTEXT_USER:64f00922-db50-4119-b362-298573c62730:admin:MessageStackHandler.handleUpstream.127
16:55:14 DEBUG 140  Context                | :1297727714117:Context:CONTEXT_CREATE:ac18189c-c12b-4535-80e0-630acfebc46b:[id: 0x40a64736, /192.168.14.10:60895 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
16:55:14 DEBUG 140  Context                | :1297727714126:Context:CONTEXT_USER:ac18189c-c12b-4535-80e0-630acfebc46b:admin:MessageStackHandler.handleUpstream.127
16:55:34 DEBUG 140  Context                | :1297727734130:Context:CONTEXT_CREATE:a38dca71-b22d-47ca-bb93-b33b81dfadee:[id: 0x0bc1c8b7, /192.168.14.10:60995 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
16:55:34 DEBUG 140  Context                | :1297727734139:Context:CONTEXT_USER:a38dca71-b22d-47ca-bb93-b33b81dfadee:admin:MessageStackHandler.handleUpstream.127
16:55:54 DEBUG 140  Context                | :1297727754071:Context:CONTEXT_CREATE:467b2d3f-cc1c-42a6-9977-5902140bfe1b:[id: 0x1555078e, /192.168.14.10:32804 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
16:58:14 DEBUG 140  Context                | :1297727894083:Context:CONTEXT_USER:9480a94f-b745-4fa2-94a4-a0898077b4c1:admin:MessageStackHandler.handleUpstream.127
16:58:34 DEBUG 140  Context                | :1297727914076:Context:CONTEXT_CREATE:a62c0427-8122-4bbe-943f-ccde31b014a5:[id: 0x6b8d53a2, /192.168.14.10:33482 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
16:58:34 DEBUG 140  Context                | :1297727914085:Context:CONTEXT_USER:a62c0427-8122-4bbe-943f-ccde31b014a5:admin:MessageStackHandler.handleUpstream.127
16:58:54 DEBUG 140  Context                | :1297727934080:Context:CONTEXT_CREATE:c0e74688-a394-47f0-92e8-49f863d17594:[id: 0x125d7e49, /192.168.14.10:33536 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
16:58:54 DEBUG 140  Context                | :1297727934090:Context:CONTEXT_USER:c0e74688-a394-47f0-92e8-49f863d17594:admin:MessageStackHandler.handleUpstream.127
16:59:14 DEBUG 140  Context                | :1297727954127:Context:CONTEXT_CREATE:3af6d47e-90d0-44e5-94e5-1317b712939c:[id: 0x10bc0cea, /192.168.14.10:33642 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
16:59:14 DEBUG 140  Context                | :1297727954136:Context:CONTEXT_USER:3af6d47e-90d0-44e5-94e5-1317b712939c:admin:MessageStackHandler.handleUpstream.127
17:01:54 DEBUG 140  Context                | :1297728114128:Context:CONTEXT_CREATE:9ab8e9ed-2590-48b1-baa0-608cd49265b1:[id: 0x2dfa6d0a, /192.168.14.10:49324 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
17:01:54 DEBUG 140  Context                | :1297728114138:Context:CONTEXT_USER:9ab8e9ed-2590-48b1-baa0-608cd49265b1:admin:MessageStackHandler.handleUpstream.127
17:02:14 DEBUG 140  Context                | :1297728134129:Context:CONTEXT_CREATE:58840daf-15fd-40b1-b750-abaa0d33c93e:[id: 0x4255a961, /192.168.14.10:49443 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
17:02:14 DEBUG 140  Context                | :1297728134139:Context:CONTEXT_USER:58840daf-15fd-40b1-b750-abaa0d33c93e:admin:MessageStackHandler.handleUpstream.127
17:02:34 DEBUG 140  Context                | :1297728154133:Context:CONTEXT_CREATE:b2563c1f-8d4a-466f-9a0f-b405d187f163:[id: 0x16aae0e3, /192.168.14.10:49514 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
17:02:34 DEBUG 140  Context                | :1297728154142:Context:CONTEXT_USER:b2563c1f-8d4a-466f-9a0f-b405d187f163:admin:MessageStackHandler.handleUpstream.127
17:02:54 DEBUG 140  Context                | :1297728174137:Context:CONTEXT_CREATE:3b95541d-364b-47e8-a0ba-3f91943fcfc3:[id: 0x70132878, /192.168.14.10:49569 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
17:05:14 DEBUG 140  Context                | :1297728314171:Context:CONTEXT_USER:69c85675-d5f7-4068-81c2-5bff9b30b1df:admin:MessageStackHandler.handleUpstream.127
17:05:34 DEBUG 140  Context                | :1297728334119:Context:CONTEXT_CREATE:3a93d0b4-7ef8-4408-bb6b-a64ff547fde9:[id: 0x00b2698e, /192.168.14.10:37255 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
17:05:34 DEBUG 140  Context                | :1297728334129:Context:CONTEXT_USER:3a93d0b4-7ef8-4408-bb6b-a64ff547fde9:admin:MessageStackHandler.handleUpstream.127
17:05:54 DEBUG 140  Context                | :1297728354073:Context:CONTEXT_CREATE:fa658762-f0b7-4e8d-bebd-f51950a226b9:[id: 0x3052c128, /192.168.14.10:37310 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
17:05:54 DEBUG 140  Context                | :1297728354083:Context:CONTEXT_USER:fa658762-f0b7-4e8d-bebd-f51950a226b9:admin:MessageStackHandler.handleUpstream.127
17:06:14 DEBUG 140  Context                | :1297728374095:Context:CONTEXT_CREATE:5942994a-0cb2-4cc4-9204-f553940144a4:[id: 0x6c4e0d81, /192.168.14.10:37429 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
17:06:14 DEBUG 140  Context                | :1297728374105:Context:CONTEXT_USER:5942994a-0cb2-4cc4-9204-f553940144a4:admin:MessageStackHandler.handleUpstream.127
17:08:54 DEBUG 140  Context                | :1297728534105:Context:CONTEXT_CREATE:ab71d943-a180-4360-b8a1-18c65081779e:[id: 0x353d092c, /192.168.14.10:38046 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
17:08:54 DEBUG 140  Context                | :1297728534115:Context:CONTEXT_USER:ab71d943-a180-4360-b8a1-18c65081779e:admin:MessageStackHandler.handleUpstream.127
17:09:14 DEBUG 140  Context                | :1297728554115:Context:CONTEXT_CREATE:15948505-c95f-49ee-b644-3a249e3a8366:[id: 0x5c178eab, /192.168.14.10:38165 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
17:09:14 DEBUG 140  Context                | :1297728554141:Context:CONTEXT_USER:15948505-c95f-49ee-b644-3a249e3a8366:admin:MessageStackHandler.handleUpstream.127
17:09:34 DEBUG 140  Context                | :1297728574125:Context:CONTEXT_CREATE:ed019538-27ef-4a84-9015-a70fe0f90e52:[id: 0x68b62603, /192.168.14.10:36938 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
17:09:34 DEBUG 140  Context                | :1297728574134:Context:CONTEXT_USER:ed019538-27ef-4a84-9015-a70fe0f90e52:admin:MessageStackHandler.handleUpstream.127
17:09:54 DEBUG 140  Context                | :1297728594114:Context:CONTEXT_CREATE:5da1f3e8-8d6f-4262-af3c-1854a41bc344:[id: 0x471139f6, /192.168.14.10:36993 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
17:12:14 DEBUG 140  Context                | :1297728734142:Context:CONTEXT_USER:c384395a-45c5-4fa2-8ad4-c2746dc58046:admin:MessageStackHandler.handleUpstream.127
17:12:34 DEBUG 140  Context                | :1297728754135:Context:CONTEXT_CREATE:8ee813c4-a077-498b-a2a7-7741acc04967:[id: 0x14e2912a, /192.168.14.10:37676 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
17:12:34 DEBUG 140  Context                | :1297728754145:Context:CONTEXT_USER:8ee813c4-a077-498b-a2a7-7741acc04967:admin:MessageStackHandler.handleUpstream.127
17:12:54 DEBUG 140  Context                | :1297728774126:Context:CONTEXT_CREATE:f2122e5f-2a1c-458b-98d2-0520222aedd7:[id: 0x22f8218b, /192.168.14.10:37731 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
17:12:54 DEBUG 140  Context                | :1297728774136:Context:CONTEXT_USER:f2122e5f-2a1c-458b-98d2-0520222aedd7:admin:MessageStackHandler.handleUpstream.127
17:13:14 DEBUG 140  Context                | :1297728794159:Context:CONTEXT_CREATE:0e56e162-f56a-4191-91ba-5286dbcc9ac2:[id: 0x44b2a877, /192.168.14.10:37850 => /192.168.14.12:8773]:NioHttpDecoder.decode.129
17:13:14 DEBUG 140  Context                | :1297728794169:Context:CONTEXT_USER:0e56e162-f56a-4191-91ba-5286dbcc9ac2:admin:MessageStackHandler.handleUpstream.127
```
...and again the pattern repeats itself very few seconds.

It also bears noting that at this particular moment it is working, but it has gone down several times in the last day or two, and rebooting the SC seems to get it going again.

Thanks again for taking a look at it.

---

### Post by kim0 on 2011-02-16
I think it's running out of Memory! that can explain why it's sometimes working sometimes not. What's the ram on that machine

---

### Post by raymdt on 2011-02-18
Hi,
additionally you can try to increase the java heap size then restart all Eucalyptus  services.

It should be something like
```

java -Xms512m -Xmx512m
```
I don't know if it helps.

Don't forget to check your RAM as kim0 said.

---

### Post by Ohm's Lawyer on 2011-02-21
I've currently got 16gig of RAM and 24gig of swap

---

### Post by Ohm's Lawyer on 2011-02-21
> **raymdt said:**
> Hi,
additionally you can try to increase the java heap size then restart all Eucalyptus  services.


Are you talking about in eucalyptus.conf?

changing
```
CLOUD_OPTS="-Xmx512m"
```
to 
```
CLOUD_OPTS="-Xms512m -Xmx512m"
```

Should I do this on just the sc, or all machines?

---

### Post by kim0 on 2011-02-22
I have bad experience with Xmx :) nothing scientific, but I'd recommend you make sure the physical box has at least 2G RAM (better 4G) as mentioned in 

[https://help.ubuntu.com/community/UEC/CDInstall](https://help.ubuntu.com/community/UEC/CDInstall)

---

### Post by raymdt on 2011-02-22
Hi,
please read this.
[http://open.eucalyptus.com/wiki/EucalyptusKnownBugs_v2.0](http://open.eucalyptus.com/wiki/EucalyptusKnownBugs_v2.0)

try to reinstall Eucalyptus if that article don't help.
Please give a feeback.

---

### Post by Ohm's Lawyer on 2011-02-27
Well, I certainly have more than the suggested RAM. Currently running 16G on each machine. As far as the article, I seem to be doing ok. I'm not showing any errors related to space. I currently have a few TB for the volumes and only using a few gigs.

I did try modifying the xmx and xms values, and so far everything seems to be working. We'll see what happens down the road, but for now it's doing well.

Thanks guys!

---

### Post by Ohm's Lawyer on 2011-03-06
So it's happened again. It appears this is definately a Java Heap space error. When I check the cloud-debug.log on my storage controller, I get the following error:

```
17:08:40 DEBUG [Context:New I/O server worker #1-13] :1299024520981:Context:CONTEXT_USER:17d4872c-ece7-41e8-899f-2a7de08b85c9:admin:MessageStackHandler.handleUpstream.127
06:43:40 ERROR [SystemClock:SystemClockTimer] java.lang.OutOfMemoryError: Java heap space
java.lang.OutOfMemoryError: Java heap space
06:44:59 ERROR [SystemClock:SystemClockTimer] java.lang.OutOfMemoryError: Java heap space
java.lang.OutOfMemoryError: Java heap space
```

But if I bump the heap up any more, it causes a world of other problems. Currently on my eucalyptus.conf I have the following set for my heap
```
CLOUD_OPTS="-Xms512m -Xmx512m -XX:MaxPermSize=256mm"
```

As stated previously,
> I've currently got 16gig of RAM and 24gig of swap
So I don't think I'm running out of RAM

I'm not entirely sure what my next step should be. Any ideas? Does anyone know if there is an open ticket on this issue?

Thanks again in advance.

---

### Post by estepix on 2011-07-29
Hi I was having a similar problem.

On this Eucalyptus thread, there is a lot of info about a similar problem.

[http://open.eucalyptus.com/forum/20-storage-controller-lost-data-everytime-after-reboot](http://open.eucalyptus.com/forum/20-storage-controller-lost-data-everytime-after-reboot)

At the very bottom, a couple of solutions are provided.

Here is my own recipe:
Although this is something that needs to be done every time your SC  server is restarted, it seems to me faster than reinstalling the  application and a clean work around to the problem. I have being trying  it for a while and seems to be working perfectly. By the way, I've added  the "/run/lock" part as it also seems to happen every time I restart  the server.
 Delete all iSCSI targets
 tgtadm --mode target --op delete --tid=
 Activate lvm2 volumes
 vgscan
 vgchange -ay
 Also, after rebooting the OS we will need to run this command:
mkdir /run/lock
 Otherwise we will get this error on cloud-error.log
00:25:26 ERROR [SystemUtil:pool-8-thread-1]  com.eucalyptus.util.ExecutionException:  ///usr/lib/eucalyptus/euca_rootwrap pvcreate /dev/loop6  error:    /var/lock/lvm: mkdir failed: No such file or directory
  File-based locking initialisation failed. 
 Restart SC service
 /etc/init.d/eucalyptus-cloud restart

---

### Post by Ohm's Lawyer on 2011-08-03
Thanks for all of the help. Basically, since it was a recurring problem, I just scrapped everything and put up a fresh 11.04 cloud. It seems to have done the trick so far.

---

