---
title: "JRE crash &quot;an irrecoverable stack overflow has occurred&quot;"
date: 2012-01-06
forum: Server Platforms
---

### Post by ffixcollector on 2012-01-06
When trying to run the PS3MediaServer app, I get 
```
An irrecoverable stack overflow has occurred.
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007fb604c51bd6, pid=1445, tid=140419658548992
#
# JRE version: 6.0_20-b20
# Java VM: OpenJDK 64-Bit Server VM (19.0-b09 mixed mode linux-amd64 compressed oops)
# Derivative: IcedTea6 1.9.10
# Distribution: Ubuntu 10.04.1 LTS, package 6b20-1.9.10-0ubuntu1~10.04.2
# Problematic frame:
# C  [jna5446313872804572983.tmp+0x6bd6]  newJavaString+0x1b6
#
# An error report file with more information is saved as:
# /tmp/hs_err_pid1445.log
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   https://bugs.launchpad.net/ubuntu/+source/openjdk-6/
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#

```
Crashing the system. the output of /tmp/hs_err_pid1445.log is;
```
#
# A fatal error has been detected by the Java Runtime Environment:
#
#  SIGSEGV (0xb) at pc=0x00007fb604c51bd6, pid=1445, tid=140419658548992
#
# JRE version: 6.0_20-b20
# Java VM: OpenJDK 64-Bit Server VM (19.0-b09 mixed mode linux-amd64 compressed oops)
# Derivative: IcedTea6 1.9.10
# Distribution: Ubuntu 10.04.1 LTS, package 6b20-1.9.10-0ubuntu1~10.04.2
# Problematic frame:
# C  [jna5446313872804572983.tmp+0x6bd6]  newJavaString+0x1b6
#
# If you would like to submit a bug report, please include
# instructions how to reproduce the bug and visit:
#   https://bugs.launchpad.net/ubuntu/+source/openjdk-6/
# The crash happened outside the Java Virtual Machine in native code.
# See problematic frame for where to report the bug.
#

---------------  T H R E A D  ---------------

Current thread (0x00007fb600035000):  JavaThread "New I/O server worker #1-4" [_thread_in_native, id=1495, stack(0x00007fb5ffce0000,0x00007fb5ffde1000)]

siginfo:si_signo=SIGSEGV: si_errno=0, si_code=2 (SEGV_ACCERR), si_addr=0x00007fb5ffce0000

Registers:
RAX=0x000000000000006f, RBX=0x00007fb5fdb11028, RCX=0x0000000000055808, RDX=0x00000000000d4753
RSP=0x00007fb5ffc34ff0, RBP=0x00007fb5ffdddef0, RSI=0x00007fb5ffc34ff0, RDI=0x0000000000055809
R8 =0x000000000000000a, R9 =0x000000000000000a, R10=0x0000000000000065, R11=0x000000000000006e
R12=0x0000000000000000, R13=0x00000000c72f3728, R14=0x00007fb5ffdddf88, R15=0x00007fb600035000
RIP=0x00007fb604c51bd6, EFL=0x0000000000010206, CSGSFS=0x0000000000000033, ERR=0x0000000000000006
  TRAPNO=0x000000000000000e

Register to memory mapping:

RAX=0x000000000000006f
0x000000000000006f is pointing to unknown location

RBX=0x00007fb5fdb11028
0x00007fb5fdb11028 is pointing to unknown location

RCX=0x0000000000055808
0x0000000000055808 is pointing to unknown location

RDX=0x00000000000d4753
0x00000000000d4753 is pointing to unknown location

RSP=0x00007fb5ffc34ff0
0x00007fb5ffc34ff0 is pointing into the stack for thread: 0x0000000001e4c800
"pool-3-thread-1" prio=10 tid=0x0000000001e4c800 nid=0x5c9 waiting on condition [0x00007fb5ffcde000]
   java.lang.Thread.State: TIMED_WAITING (parking)

RBP=0x00007fb5ffdddef0
0x00007fb5ffdddef0 is pointing into the stack for thread: 0x00007fb600035000
"New I/O server worker #1-4" prio=10 tid=0x00007fb600035000 nid=0x5d7 runnable [0x00007fb5ffddd000]
   java.lang.Thread.State: RUNNABLE

RSI=0x00007fb5ffc34ff0
0x00007fb5ffc34ff0 is pointing into the stack for thread: 0x0000000001e4c800
"pool-3-thread-1" prio=10 tid=0x0000000001e4c800 nid=0x5c9 waiting on condition [0x00007fb5ffcde000]
   java.lang.Thread.State: TIMED_WAITING (parking)

RDI=0x0000000000055809
0x0000000000055809 is pointing to unknown location

R8 =0x000000000000000a
0x000000000000000a is pointing to unknown location

R9 =0x000000000000000a
0x000000000000000a is pointing to unknown location

R10=0x0000000000000065
0x0000000000000065 is pointing to unknown location

R11=0x000000000000006e
0x000000000000006e is pointing to unknown location

R12=0x0000000000000000
0x0000000000000000 is pointing to unknown location

R13=0x00000000c72f3728
{method} 
 - klass: {other class}

R14=0x00007fb5ffdddf88
0x00007fb5ffdddf88 is pointing into the stack for thread: 0x00007fb600035000
"New I/O server worker #1-4" prio=10 tid=0x00007fb600035000 nid=0x5d7 runnable [0x00007fb5ffddd000]
   java.lang.Thread.State: RUNNABLE

R15=0x00007fb600035000
"New I/O server worker #1-4" prio=10 tid=0x00007fb600035000 nid=0x5d7 runnable [0x00007fb5ffddd000]
   java.lang.Thread.State: RUNNABLE


Top of Stack: (sp=0x00007fb5ffc34ff0)
0x00007fb5ffc34ff0:   0065006e00650047 000a006c00610072
0x00007fb5ffc35000:   006e0075006f0043 0020002000200074
0x00007fb5ffc35010:   0020002000200020 0020002000200020
0x00007fb5ffc35020:   0020002000200020 0020002000200020
0x00007fb5ffc35030:   0020002000200020 0020002000200020
0x00007fb5ffc35040:   00320020003a0020 0053000a00380037
0x00007fb5ffc35050:   0061006500720074 0075006f0043006d
0x00007fb5ffc35060:   002000200074006e 0020002000200020
0x00007fb5ffc35070:   0020002000200020 0020002000200020
0x00007fb5ffc35080:   0020002000200020 0020002000200020
0x00007fb5ffc35090:   000a00310020003a 0065007200740053
0x00007fb5ffc350a0:   0069004b006d0061 002000200064006e
0x00007fb5ffc350b0:   0020002000200020 0020002000200020
0x00007fb5ffc350c0:   0020002000200020 0020002000200020
0x00007fb5ffc350d0:   0020002000200020 00470020003a0020
0x00007fb5ffc350e0:   00720065006e0065 0053000a006c0061
0x00007fb5ffc350f0:   0061006500720074 006e0069004b006d
0x00007fb5ffc35100:   00740053002f0064 0067006e00690072
0x00007fb5ffc35110:   0020002000200020 0020002000200020
0x00007fb5ffc35120:   0020002000200020 0020002000200020
0x00007fb5ffc35130:   006500470020003a 006100720065006e
0x00007fb5ffc35140:   00740053000a006c 006d006100650072
0x00007fb5ffc35150:   0064006e0069004b 0020002000440049
0x00007fb5ffc35160:   0020002000200020 0020002000200020
0x00007fb5ffc35170:   0020002000200020 0020002000200020
0x00007fb5ffc35180:   003a002000200020 0041000a00300020
0x00007fb5ffc35190:   006f006900640075 006e0075006f0043
0x00007fb5ffc351a0:   0020002000200074 0020002000200020
0x00007fb5ffc351b0:   0020002000200020 0020002000200020
0x00007fb5ffc351c0:   0020002000200020 0020002000200020
0x00007fb5ffc351d0:   000a00310020003a 0069006400750041
0x00007fb5ffc351e0:   006f0046005f006f 00740061006d0072 

Instructions: (pc=0x00007fb604c51bd6)
0x00007fb604c51bc6:   83 e6 f0 85 d2 7e 14 31 ff 31 c9 8b 04 8b ff c7
0x00007fb604c51bd6:   66 89 04 4e 48 ff c1 39 fa 75 f0 48 8b 4d d8 48 

Stack: [0x00007fb5ffce0000,0x00007fb5ffde1000],  sp=0x00007fb5ffc34ff0,  free space=18014398509481299k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
C  [jna5446313872804572983.tmp+0x6bd6]  newJavaString+0x1b6
j  com.sun.jna.Pointer._getString(JZ)Ljava/lang/String;+0
j  com.sun.jna.Pointer.getString(JZ)Ljava/lang/String;+7
j  com.sun.jna.Function.invokeString(I[Ljava/lang/Object;Z)Ljava/lang/String;+24
j  com.sun.jna.Function.invoke([Ljava/lang/Object;Ljava/lang/Class;Z)Ljava/lang/Object;+557
j  com.sun.jna.Function.invoke(Ljava/lang/Class;[Ljava/lang/Object;Ljava/util/Map;)Ljava/lang/Object;+214
j  com.sun.jna.Library$Handler.invoke(Ljava/lang/Object;Ljava/lang/reflect/Method;[Ljava/lang/Object;)Ljava/lang/Object;+341
j  net.pms.dlna.$Proxy0.Inform(Lcom/sun/jna/Pointer;)Lcom/sun/jna/WString;+16
j  net.pms.dlna.MediaInfo.Inform()Ljava/lang/String;+7
j  net.pms.dlna.MediaInfoParser.parse(Lnet/pms/dlna/DLNAMediaInfo;Lnet/pms/dlna/InputFile;I)V+41
j  net.pms.configuration.FormatConfiguration.parse(Lnet/pms/dlna/DLNAMediaInfo;Lnet/pms/dlna/InputFile;Lnet/pms/formats/Format;I)V+92
j  net.pms.formats.Format.parse(Lnet/pms/dlna/DLNAMediaInfo;Lnet/pms/dlna/InputFile;ILnet/pms/configuration/RendererConfiguration;)V+22
j  net.pms.dlna.RealFile.resolve()V+244
j  net.pms.dlna.DLNAResource.run()V+8
j  net.pms.dlna.RealFile.isValid()Z+108
j  net.pms.dlna.DLNAResource.addChild(Lnet/pms/dlna/DLNAResource;)V+68
j  net.pms.dlna.MapFile.manageFile(Ljava/io/File;)V+354
j  net.pms.dlna.MapFile.analyzeChildren(I)Z+110
j  net.pms.dlna.DLNAResource.discoverWithRenderer(Lnet/pms/configuration/RendererConfiguration;I)V+29
j  net.pms.dlna.DLNAResource.getDLNAResources(Ljava/lang/String;ZIILnet/pms/configuration/RendererConfiguration;)Ljava/util/List;+58
j  net.pms.network.RequestV2.answer(Lorg/jboss/netty/handler/codec/http/HttpResponse;Lorg/jboss/netty/channel/MessageEvent;ZLnet/pms/external/StartStopListenerDelegate;)Lorg/jboss/netty/channel/ChannelFuture;+2956
j  net.pms.network.RequestHandlerV2.writeResponse(Lorg/jboss/netty/channel/MessageEvent;Lnet/pms/network/RequestV2;Ljava/net/InetAddress;)V+138
j  net.pms.network.RequestHandlerV2.messageReceived(Lorg/jboss/netty/channel/ChannelHandlerContext;Lorg/jboss/netty/channel/MessageEvent;)V+1517
j  org.jboss.netty.channel.SimpleChannelUpstreamHandler.handleUpstream(Lorg/jboss/netty/channel/ChannelHandlerContext;Lorg/jboss/netty/channel/ChannelEvent;)V+13
j  org.jboss.netty.channel.DefaultChannelPipeline.sendUpstream(Lorg/jboss/netty/channel/DefaultChannelPipeline$DefaultChannelHandlerContext;Lorg/jboss/netty/channel/ChannelEvent;)V+9
j  org.jboss.netty.channel.DefaultChannelPipeline$DefaultChannelHandlerContext.sendUpstream(Lorg/jboss/netty/channel/ChannelEvent;)V+22
j  org.jboss.netty.handler.stream.ChunkedWriteHandler.handleUpstream(Lorg/jboss/netty/channel/ChannelHandlerContext;Lorg/jboss/netty/channel/ChannelEvent;)V+82
j  org.jboss.netty.channel.DefaultChannelPipeline.sendUpstream(Lorg/jboss/netty/channel/DefaultChannelPipeline$DefaultChannelHandlerContext;Lorg/jboss/netty/channel/ChannelEvent;)V+9
j  org.jboss.netty.channel.DefaultChannelPipeline$DefaultChannelHandlerContext.sendUpstream(Lorg/jboss/netty/channel/ChannelEvent;)V+22
j  org.jboss.netty.handler.codec.http.HttpChunkAggregator.messageReceived(Lorg/jboss/netty/channel/ChannelHandlerContext;Lorg/jboss/netty/channel/MessageEvent;)V+155
j  org.jboss.netty.channel.SimpleChannelUpstreamHandler.handleUpstream(Lorg/jboss/netty/channel/ChannelHandlerContext;Lorg/jboss/netty/channel/ChannelEvent;)V+13
j  org.jboss.netty.channel.DefaultChannelPipeline.sendUpstream(Lorg/jboss/netty/channel/DefaultChannelPipeline$DefaultChannelHandlerContext;Lorg/jboss/netty/channel/ChannelEvent;)V+9
j  org.jboss.netty.channel.DefaultChannelPipeline$DefaultChannelHandlerContext.sendUpstream(Lorg/jboss/netty/channel/ChannelEvent;)V+22
j  org.jboss.netty.channel.Channels.fireMessageReceived(Lorg/jboss/netty/channel/ChannelHandlerContext;Ljava/lang/Object;Ljava/net/SocketAddress;)V+16
j  org.jboss.netty.handler.codec.replay.ReplayingDecoder.unfoldAndfireMessageReceived(Lorg/jboss/netty/channel/ChannelHandlerContext;Ljava/lang/Object;Ljava/net/SocketAddress;)V+114
j  org.jboss.netty.handler.codec.replay.ReplayingDecoder.callDecode(Lorg/jboss/netty/channel/ChannelHandlerContext;Lorg/jboss/netty/channel/Channel;Lorg/jboss/netty/buffer/ChannelBuffer;Ljava/net/SocketAddress;)V+178
j  org.jboss.netty.handler.codec.replay.ReplayingDecoder.messageReceived(Lorg/jboss/netty/channel/ChannelHandlerContext;Lorg/jboss/netty/channel/MessageEvent;)V+78
j  org.jboss.netty.channel.SimpleChannelUpstreamHandler.handleUpstream(Lorg/jboss/netty/channel/ChannelHandlerContext;Lorg/jboss/netty/channel/ChannelEvent;)V+13
j  org.jboss.netty.channel.DefaultChannelPipeline.sendUpstream(Lorg/jboss/netty/channel/DefaultChannelPipeline$DefaultChannelHandlerContext;Lorg/jboss/netty/channel/ChannelEvent;)V+9
j  org.jboss.netty.channel.DefaultChannelPipeline.sendUpstream(Lorg/jboss/netty/channel/ChannelEvent;)V+44
j  org.jboss.netty.channel.Channels.fireMessageReceived(Lorg/jboss/netty/channel/Channel;Ljava/lang/Object;Ljava/net/SocketAddress;)V+16
j  org.jboss.netty.channel.Channels.fireMessageReceived(Lorg/jboss/netty/channel/Channel;Ljava/lang/Object;)V+3
j  org.jboss.netty.channel.socket.nio.NioWorker.read(Ljava/nio/channels/SelectionKey;)Z+178
j  org.jboss.netty.channel.socket.nio.NioWorker.processSelectedKeys(Ljava/util/Set;)V+52
j  org.jboss.netty.channel.socket.nio.NioWorker.run()V+93
j  org.jboss.netty.util.ThreadRenamingRunnable.run()V+55
j  org.jboss.netty.util.internal.DeadLockProofWorker$1.run()V+14
j  java.util.concurrent.ThreadPoolExecutor.runWorker(Ljava/util/concurrent/ThreadPoolExecutor$Worker;)V+46
j  java.util.concurrent.ThreadPoolExecutor$Worker.run()V+5
j  java.lang.Thread.run()V+11
v  ~StubRoutines::call_stub
V  [libjvm.so+0x431958]
V  [libjvm.so+0x4307f8]
V  [libjvm.so+0x4313b3]
V  [libjvm.so+0x4314d7]
V  [libjvm.so+0x482b10]
V  [libjvm.so+0x6e806b]
V  [libjvm.so+0x5e42e2]

Java frames: (J=compiled Java code, j=interpreted, Vv=VM code)
j  com.sun.jna.Pointer._getString(JZ)Ljava/lang/String;+0
j  com.sun.jna.Pointer.getString(JZ)Ljava/lang/String;+7
j  com.sun.jna.Function.invokeString(I[Ljava/lang/Object;Z)Ljava/lang/String;+24
j  com.sun.jna.Function.invoke([Ljava/lang/Object;Ljava/lang/Class;Z)Ljava/lang/Object;+557
j  com.sun.jna.Function.invoke(Ljava/lang/Class;[Ljava/lang/Object;Ljava/util/Map;)Ljava/lang/Object;+214
j  com.sun.jna.Library$Handler.invoke(Ljava/lang/Object;Ljava/lang/reflect/Method;[Ljava/lang/Object;)Ljava/lang/Object;+341
j  net.pms.dlna.$Proxy0.Inform(Lcom/sun/jna/Pointer;)Lcom/sun/jna/WString;+16
j  net.pms.dlna.MediaInfo.Inform()Ljava/lang/String;+7
j  net.pms.dlna.MediaInfoParser.parse(Lnet/pms/dlna/DLNAMediaInfo;Lnet/pms/dlna/InputFile;I)V+41
j  net.pms.configuration.FormatConfiguration.parse(Lnet/pms/dlna/DLNAMediaInfo;Lnet/pms/dlna/InputFile;Lnet/pms/formats/Format;I)V+92
j  net.pms.formats.Format.parse(Lnet/pms/dlna/DLNAMediaInfo;Lnet/pms/dlna/InputFile;ILnet/pms/configuration/RendererConfiguration;)V+22
j  net.pms.dlna.RealFile.resolve()V+244
j  net.pms.dlna.DLNAResource.run()V+8
j  net.pms.dlna.RealFile.isValid()Z+108
j  net.pms.dlna.DLNAResource.addChild(Lnet/pms/dlna/DLNAResource;)V+68
j  net.pms.dlna.MapFile.manageFile(Ljava/io/File;)V+354
j  net.pms.dlna.MapFile.analyzeChildren(I)Z+110
j  net.pms.dlna.DLNAResource.discoverWithRenderer(Lnet/pms/configuration/RendererConfiguration;I)V+29
j  net.pms.dlna.DLNAResource.getDLNAResources(Ljava/lang/String;ZIILnet/pms/configuration/RendererConfiguration;)Ljava/util/List;+58
j  net.pms.network.RequestV2.answer(Lorg/jboss/netty/handler/codec/http/HttpResponse;Lorg/jboss/netty/channel/MessageEvent;ZLnet/pms/external/StartStopListenerDelegate;)Lorg/jboss/netty/channel/ChannelFuture;+2956
j  net.pms.network.RequestHandlerV2.writeResponse(Lorg/jboss/netty/channel/MessageEvent;Lnet/pms/network/RequestV2;Ljava/net/InetAddress;)V+138
j  net.pms.network.RequestHandlerV2.messageReceived(Lorg/jboss/netty/channel/ChannelHandlerContext;Lorg/jboss/netty/channel/MessageEvent;)V+1517
j  org.jboss.netty.channel.SimpleChannelUpstreamHandler.handleUpstream(Lorg/jboss/netty/channel/ChannelHandlerContext;Lorg/jboss/netty/channel/ChannelEvent;)V+13
j  org.jboss.netty.channel.DefaultChannelPipeline.sendUpstream(Lorg/jboss/netty/channel/DefaultChannelPipeline$DefaultChannelHandlerContext;Lorg/jboss/netty/channel/ChannelEvent;)V+9
j  org.jboss.netty.channel.DefaultChannelPipeline$DefaultChannelHandlerContext.sendUpstream(Lorg/jboss/netty/channel/ChannelEvent;)V+22
j  org.jboss.netty.handler.stream.ChunkedWriteHandler.handleUpstream(Lorg/jboss/netty/channel/ChannelHandlerContext;Lorg/jboss/netty/channel/ChannelEvent;)V+82
j  org.jboss.netty.channel.DefaultChannelPipeline.sendUpstream(Lorg/jboss/netty/channel/DefaultChannelPipeline$DefaultChannelHandlerContext;Lorg/jboss/netty/channel/ChannelEvent;)V+9
j  org.jboss.netty.channel.DefaultChannelPipeline$DefaultChannelHandlerContext.sendUpstream(Lorg/jboss/netty/channel/ChannelEvent;)V+22
j  org.jboss.netty.handler.codec.http.HttpChunkAggregator.messageReceived(Lorg/jboss/netty/channel/ChannelHandlerContext;Lorg/jboss/netty/channel/MessageEvent;)V+155
j  org.jboss.netty.channel.SimpleChannelUpstreamHandler.handleUpstream(Lorg/jboss/netty/channel/ChannelHandlerContext;Lorg/jboss/netty/channel/ChannelEvent;)V+13
j  org.jboss.netty.channel.DefaultChannelPipeline.sendUpstream(Lorg/jboss/netty/channel/DefaultChannelPipeline$DefaultChannelHandlerContext;Lorg/jboss/netty/channel/ChannelEvent;)V+9
j  org.jboss.netty.channel.DefaultChannelPipeline$DefaultChannelHandlerContext.sendUpstream(Lorg/jboss/netty/channel/ChannelEvent;)V+22
j  org.jboss.netty.channel.Channels.fireMessageReceived(Lorg/jboss/netty/channel/ChannelHandlerContext;Ljava/lang/Object;Ljava/net/SocketAddress;)V+16
j  org.jboss.netty.handler.codec.replay.ReplayingDecoder.unfoldAndfireMessageReceived(Lorg/jboss/netty/channel/ChannelHandlerContext;Ljava/lang/Object;Ljava/net/SocketAddress;)V+114
j  org.jboss.netty.handler.codec.replay.ReplayingDecoder.callDecode(Lorg/jboss/netty/channel/ChannelHandlerContext;Lorg/jboss/netty/channel/Channel;Lorg/jboss/netty/buffer/ChannelBuffer;Ljava/net/SocketAddress;)V+178
j  org.jboss.netty.handler.codec.replay.ReplayingDecoder.messageReceived(Lorg/jboss/netty/channel/ChannelHandlerContext;Lorg/jboss/netty/channel/MessageEvent;)V+78
j  org.jboss.netty.channel.SimpleChannelUpstreamHandler.handleUpstream(Lorg/jboss/netty/channel/ChannelHandlerContext;Lorg/jboss/netty/channel/ChannelEvent;)V+13
j  org.jboss.netty.channel.DefaultChannelPipeline.sendUpstream(Lorg/jboss/netty/channel/DefaultChannelPipeline$DefaultChannelHandlerContext;Lorg/jboss/netty/channel/ChannelEvent;)V+9
j  org.jboss.netty.channel.DefaultChannelPipeline.sendUpstream(Lorg/jboss/netty/channel/ChannelEvent;)V+44
j  org.jboss.netty.channel.Channels.fireMessageReceived(Lorg/jboss/netty/channel/Channel;Ljava/lang/Object;Ljava/net/SocketAddress;)V+16
j  org.jboss.netty.channel.Channels.fireMessageReceived(Lorg/jboss/netty/channel/Channel;Ljava/lang/Object;)V+3
j  org.jboss.netty.channel.socket.nio.NioWorker.read(Ljava/nio/channels/SelectionKey;)Z+178
j  org.jboss.netty.channel.socket.nio.NioWorker.processSelectedKeys(Ljava/util/Set;)V+52
j  org.jboss.netty.channel.socket.nio.NioWorker.run()V+93
j  org.jboss.netty.util.ThreadRenamingRunnable.run()V+55
j  org.jboss.netty.util.internal.DeadLockProofWorker$1.run()V+14
j  java.util.concurrent.ThreadPoolExecutor.runWorker(Ljava/util/concurrent/ThreadPoolExecutor$Worker;)V+46
j  java.util.concurrent.ThreadPoolExecutor$Worker.run()V+5
j  java.lang.Thread.run()V+11
v  ~StubRoutines::call_stub

---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
  0x00000000023ee000 JavaThread "Thread-19" [_thread_blocked, id=1524, stack(0x00007fb6057ae000,0x00007fb6058af000)]
  0x0000000002173000 JavaThread "Thread-16" [_thread_blocked, id=1510, stack(0x00007fb6055ac000,0x00007fb6056ad000)]
=>0x00007fb600035000 JavaThread "New I/O server worker #1-4" [_thread_in_native, id=1495, stack(0x00007fb5ffce0000,0x00007fb5ffde1000)]
  0x00007fb600034000 JavaThread "New I/O server worker #1-2" [_thread_in_native, id=1492, stack(0x00007fb5fedb4000,0x00007fb5feeb5000)]
  0x00007fb60004a800 JavaThread "New I/O server worker #1-1" [_thread_in_native, id=1491, stack(0x00007fb5feeb5000,0x00007fb5fefb6000)]
  0x00007fb6000ef000 JavaThread "DestroyJavaVM" [_thread_blocked, id=1447, stack(0x00007fb612fe5000,0x00007fb6130e6000)]
  0x00007fb6000ee800 JavaThread "Thread-11" [_thread_in_native, id=1483, stack(0x00007fb5ff0b7000,0x00007fb5ff1b8000)]
  0x00007fb600073000 JavaThread "Thread-10" [_thread_blocked, id=1482, stack(0x00007fb5ff1b8000,0x00007fb5ff2b9000)]
  0x0000000001e4c800 JavaThread "pool-3-thread-1" [_thread_blocked, id=1481, stack(0x00007fb5ffbdf000,0x00007fb5ffce0000)]
  0x0000000001f62800 JavaThread "New I/O server worker #1-3" [_thread_in_native, id=1480, stack(0x00007fb5ffade000,0x00007fb5ffbdf000)]
  0x00007fb600050000 JavaThread "New I/O server boss #1 ([id: 0x15d07c3f, /192.168.1.250:5001])" [_thread_in_native, id=1478, stack(0x00007fb5ffde1000,0x00007fb5ffee2000)]
  0x00007fb600001000 JavaThread "Thread-4" daemon [_thread_blocked, id=1472, stack(0x00007fb604d61000,0x00007fb604e62000)]
  0x00007fb6082f8800 JavaThread "TimerQueue" daemon [_thread_blocked, id=1468, stack(0x00007fb604e62000,0x00007fb604f63000)]
  0x00007fb60822a000 JavaThread "AWT-EventQueue-0" [_thread_blocked, id=1466, stack(0x00007fb6056ad000,0x00007fb6057ae000)]
  0x00007fb608238800 JavaThread "AWT-Shutdown" [_thread_blocked, id=1465, stack(0x00007fb6058af000,0x00007fb6059b0000)]
  0x00007fb608205800 JavaThread "AWT-XAWT" daemon [_thread_in_native, id=1459, stack(0x00007fb6059b0000,0x00007fb605ab1000)]
  0x00007fb6081a6000 JavaThread "Java2D Disposer" daemon [_thread_blocked, id=1458, stack(0x00007fb605ec1000,0x00007fb605fc2000)]
  0x00007fb608004800 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=1456, stack(0x00007fb60c158000,0x00007fb60c259000)]
  0x00007fb608001800 JavaThread "CompilerThread1" daemon [_thread_blocked, id=1455, stack(0x00007fb60c259000,0x00007fb60c35a000)]
  0x0000000001dbd800 JavaThread "CompilerThread0" daemon [_thread_blocked, id=1454, stack(0x00007fb60c35a000,0x00007fb60c45b000)]
  0x0000000001dbc000 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=1453, stack(0x00007fb60c45b000,0x00007fb60c55c000)]
  0x0000000001d9c000 JavaThread "Finalizer" daemon [_thread_blocked, id=1452, stack(0x00007fb60c59b000,0x00007fb60c69c000)]
  0x0000000001d94800 JavaThread "Reference Handler" daemon [_thread_blocked, id=1451, stack(0x00007fb60c69c000,0x00007fb60c79d000)]

Other Threads:
  0x0000000001d8d800 VMThread [stack: 0x00007fb60c79d000,0x00007fb60c89e000] [id=1450]
  0x00007fb608007000 WatcherThread [stack: 0x00007fb60c057000,0x00007fb60c158000] [id=1457]

VM state:not at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread: None

Heap
 PSYoungGen      total 27904K, used 14101K [0x00000000f0000000, 0x00000000f1f20000, 0x0000000100000000)
  eden space 23936K, 42% used [0x00000000f0000000,0x00000000f09eac40,0x00000000f1760000)
  from space 3968K, 99% used [0x00000000f1b40000,0x00000000f1f1ab68,0x00000000f1f20000)
  to   space 3968K, 0% used [0x00000000f1760000,0x00000000f1760000,0x00000000f1b40000)
 PSOldGen        total 63872K, used 1314K [0x00000000d0000000, 0x00000000d3e60000, 0x00000000f0000000)
  object space 63872K, 2% used [0x00000000d0000000,0x00000000d0148900,0x00000000d3e60000)
 PSPermGen       total 29696K, used 29518K [0x00000000c5a00000, 0x00000000c7700000, 0x00000000d0000000)
  object space 29696K, 99% used [0x00000000c5a00000,0x00000000c76d39d8,0x00000000c7700000)

Dynamic libraries:
00400000-00409000 r-xp 00000000 fb:00 48108140                           /usr/lib/jvm/java-6-openjdk/jre/bin/java
00608000-00609000 r--p 00008000 fb:00 48108140                           /usr/lib/jvm/java-6-openjdk/jre/bin/java
00609000-0060a000 rw-p 00009000 fb:00 48108140                           /usr/lib/jvm/java-6-openjdk/jre/bin/java
01d20000-0290e000 rw-p 00000000 00:00 0                                  [heap]
c5a00000-c7700000 rw-p 00000000 00:00 0 
c7700000-d0000000 rw-p 00000000 00:00 0 
d0000000-d3e60000 rw-p 00000000 00:00 0 
d3e60000-f0000000 rw-p 00000000 00:00 0 
f0000000-f1f20000 rw-p 00000000 00:00 0 
f1f20000-100000000 rw-p 00000000 00:00 0 
7fb5fdb11000-7fb5fe5b1000 rw-p 00000000 00:00 0 
7fb5feab1000-7fb5feab4000 ---p 00000000 00:00 0 
7fb5feab4000-7fb5febb2000 rw-p 00000000 00:00 0 
7fb5febb2000-7fb5febb5000 ---p 00000000 00:00 0 
7fb5febb5000-7fb5fecb3000 rw-p 00000000 00:00 0 
7fb5fecb3000-7fb5fecb6000 ---p 00000000 00:00 0 
7fb5fecb6000-7fb5fedb4000 rw-p 00000000 00:00 0 
7fb5fedb4000-7fb5fedb7000 ---p 00000000 00:00 0 
7fb5fedb7000-7fb5feeb5000 rw-p 00000000 00:00 0 
7fb5feeb5000-7fb5feeb8000 ---p 00000000 00:00 0 
7fb5feeb8000-7fb5fefb6000 rw-p 00000000 00:00 0 
7fb5fefb6000-7fb5fefb9000 ---p 00000000 00:00 0 
7fb5fefb9000-7fb5ff0b7000 rw-p 00000000 00:00 0 
7fb5ff0b7000-7fb5ff0ba000 ---p 00000000 00:00 0 
7fb5ff0ba000-7fb5ff1b8000 rw-p 00000000 00:00 0 
7fb5ff1b8000-7fb5ff1bb000 ---p 00000000 00:00 0 
7fb5ff1bb000-7fb5ff2b9000 rw-p 00000000 00:00 0 
7fb5ff2b9000-7fb5ff2bb000 r-xp 00000000 fb:00 52956674                   /lib/libnss_mdns4.so.2
7fb5ff2bb000-7fb5ff4ba000 ---p 00002000 fb:00 52956674                   /lib/libnss_mdns4.so.2
7fb5ff4ba000-7fb5ff4bb000 r--p 00001000 fb:00 52956674                   /lib/libnss_mdns4.so.2
7fb5ff4bb000-7fb5ff4bc000 rw-p 00002000 fb:00 52956674                   /lib/libnss_mdns4.so.2
7fb5ff4bc000-7fb5ff4d2000 r-xp 00000000 fb:00 52953120                   /lib/libresolv-2.11.1.so
7fb5ff4d2000-7fb5ff6d1000 ---p 00016000 fb:00 52953120                   /lib/libresolv-2.11.1.so
7fb5ff6d1000-7fb5ff6d2000 r--p 00015000 fb:00 52953120                   /lib/libresolv-2.11.1.so
7fb5ff6d2000-7fb5ff6d3000 rw-p 00016000 fb:00 52953120                   /lib/libresolv-2.11.1.so
7fb5ff6d3000-7fb5ff6d5000 rw-p 00000000 00:00 0 
7fb5ff6d5000-7fb5ff6da000 r-xp 00000000 fb:00 52953113                   /lib/libnss_dns-2.11.1.so
7fb5ff6da000-7fb5ff8d9000 ---p 00005000 fb:00 52953113                   /lib/libnss_dns-2.11.1.so
7fb5ff8d9000-7fb5ff8da000 r--p 00004000 fb:00 52953113                   /lib/libnss_dns-2.11.1.so
7fb5ff8da000-7fb5ff8db000 rw-p 00005000 fb:00 52953113                   /lib/libnss_dns-2.11.1.so
7fb5ff8db000-7fb5ff8dd000 r-xp 00000000 fb:00 52956675                   /lib/libnss_mdns4_minimal.so.2
7fb5ff8dd000-7fb5ffadc000 ---p 00002000 fb:00 52956675                   /lib/libnss_mdns4_minimal.so.2
7fb5ffadc000-7fb5ffadd000 r--p 00001000 fb:00 52956675                   /lib/libnss_mdns4_minimal.so.2
7fb5ffadd000-7fb5ffade000 rw-p 00002000 fb:00 52956675                   /lib/libnss_mdns4_minimal.so.2
7fb5ffade000-7fb5ffae1000 ---p 00000000 00:00 0 
7fb5ffae1000-7fb5ffbdf000 rw-p 00000000 00:00 0 
7fb5ffbdf000-7fb5ffbe2000 ---p 00000000 00:00 0 
7fb5ffbe2000-7fb5ffce1000 rw-p 00000000 00:00 0 
7fb5ffce1000-7fb5ffce3000 ---p 00000000 00:00 0 
7fb5ffce3000-7fb5ffde1000 rw-p 00000000 00:00 0 
7fb5ffde1000-7fb5ffde4000 ---p 00000000 00:00 0 
7fb5ffde4000-7fb5ffee2000 rw-p 00000000 00:00 0 
7fb5ffee2000-7fb600000000 r--p 00000000 fb:00 46533791                   /usr/lib/locale/en_US.utf8/LC_COLLATE
7fb600000000-7fb600573000 rw-p 00000000 00:00 0 
7fb600573000-7fb604000000 ---p 00000000 00:00 0 
7fb6040aa000-7fb6044d0000 r-xp 00000000 fb:00 46412146                   /usr/lib/libmediainfo.so.0.0.0
7fb6044d0000-7fb6046cf000 ---p 00426000 fb:00 46412146                   /usr/lib/libmediainfo.so.0.0.0
7fb6046cf000-7fb6046d9000 r--p 00425000 fb:00 46412146                   /usr/lib/libmediainfo.so.0.0.0
7fb6046d9000-7fb6046e0000 rw-p 0042f000 fb:00 46412146                   /usr/lib/libmediainfo.so.0.0.0
7fb6046e0000-7fb6046e1000 rw-p 00000000 00:00 0 
7fb6046e1000-7fb6047d7000 r-xp 00000000 fb:00 46401037                   /usr/lib/libstdc++.so.6.0.13
7fb6047d7000-7fb6049d7000 ---p 000f6000 fb:00 46401037                   /usr/lib/libstdc++.so.6.0.13
7fb6049d7000-7fb6049de000 r--p 000f6000 fb:00 46401037                   /usr/lib/libstdc++.so.6.0.13
7fb6049de000-7fb6049e0000 rw-p 000fd000 fb:00 46401037                   /usr/lib/libstdc++.so.6.0.13
7fb6049e0000-7fb6049f5000 rw-p 00000000 00:00 0 
7fb6049f5000-7fb604a49000 r-xp 00000000 fb:00 46412144                   /usr/lib/libzen.so.0.0.0
7fb604a49000-7fb604c49000 ---p 00054000 fb:00 46412144                   /usr/lib/libzen.so.0.0.0
7fb604c49000-7fb604c4a000 r--p 00054000 fb:00 46412144                   /usr/lib/libzen.so.0.0.0
7fb604c4a000-7fb604c4b000 rw-p 00055000 fb:00 46412144                   /usr/lib/libzen.so.0.0.0
7fb604c4b000-7fb604c60000 r-xp 00000000 fb:00 46137359                   /tmp/jna5446313872804572983.tmp
7fb604c60000-7fb604d5f000 ---p 00015000 fb:00 46137359                   /tmp/jna5446313872804572983.tmp
7fb604d5f000-7fb604d61000 rw-p 00014000 fb:00 46137359                   /tmp/jna5446313872804572983.tmp
7fb604d61000-7fb604d64000 ---p 00000000 00:00 0 
7fb604d64000-7fb604e62000 rw-p 00000000 00:00 0 
7fb604e62000-7fb604e65000 ---p 00000000 00:00 0 
7fb604e65000-7fb604f63000 rw-p 00000000 00:00 0 
7fb604f63000-7fb604f6b000 r-xp 00000000 fb:00 48108103                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libnio.so
7fb604f6b000-7fb60516a000 ---p 00008000 fb:00 48108103                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libnio.so
7fb60516a000-7fb60516b000 r--p 00007000 fb:00 48108103                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libnio.so
7fb60516b000-7fb60516c000 rw-p 00008000 fb:00 48108103                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libnio.so
7fb60516c000-7fb605176000 r-xp 00000000 fb:00 48108096                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libjpeg.so
7fb605176000-7fb605375000 ---p 0000a000 fb:00 48108096                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libjpeg.so
7fb605375000-7fb605376000 r--p 00009000 fb:00 48108096                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libjpeg.so
7fb605376000-7fb605377000 rw-p 0000a000 fb:00 48108096                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libjpeg.so
7fb605377000-7fb6053a9000 r-xp 00000000 fb:00 48108099                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/liblcms.so
7fb6053a9000-7fb6055a8000 ---p 00032000 fb:00 48108099                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/liblcms.so
7fb6055a8000-7fb6055a9000 r--p 00031000 fb:00 48108099                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/liblcms.so
7fb6055a9000-7fb6055aa000 rw-p 00032000 fb:00 48108099                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/liblcms.so
7fb6055aa000-7fb6055ac000 rw-p 00000000 00:00 0 
7fb6055ac000-7fb6055af000 ---p 00000000 00:00 0 
7fb6055af000-7fb6056ad000 rw-p 00000000 00:00 0 
7fb6056ad000-7fb6056b0000 ---p 00000000 00:00 0 
7fb6056b0000-7fb6057ae000 rw-p 00000000 00:00 0 
7fb6057ae000-7fb6057b1000 ---p 00000000 00:00 0 
7fb6057b1000-7fb6058af000 rw-p 00000000 00:00 0 
7fb6058af000-7fb6058b2000 ---p 00000000 00:00 0 
7fb6058b2000-7fb6059b0000 rw-p 00000000 00:00 0 
7fb6059b0000-7fb6059b3000 ---p 00000000 00:00 0 
7fb6059b3000-7fb605ab1000 rw-p 00000000 00:00 0 
7fb605ab1000-7fb605ab6000 r-xp 00000000 fb:00 46405478                   /usr/lib/libXfixes.so.3.1.0
7fb605ab6000-7fb605cb5000 ---p 00005000 fb:00 46405478                   /usr/lib/libXfixes.so.3.1.0
7fb605cb5000-7fb605cb6000 r--p 00004000 fb:00 46405478                   /usr/lib/libXfixes.so.3.1.0
7fb605cb6000-7fb605cb7000 rw-p 00005000 fb:00 46405478                   /usr/lib/libXfixes.so.3.1.0
7fb605cb7000-7fb605cc0000 r-xp 00000000 fb:00 46405482                   /usr/lib/libXcursor.so.1.0.2
7fb605cc0000-7fb605ebf000 ---p 00009000 fb:00 46405482                   /usr/lib/libXcursor.so.1.0.2
7fb605ebf000-7fb605ec0000 r--p 00008000 fb:00 46405482                   /usr/lib/libXcursor.so.1.0.2
7fb605ec0000-7fb605ec1000 rw-p 00009000 fb:00 46405482                   /usr/lib/libXcursor.so.1.0.2
7fb605ec1000-7fb605ec4000 ---p 00000000 00:00 0 
7fb605ec4000-7fb605fc2000 rw-p 00000000 00:00 0 
7fb605fc2000-7fb605fd8000 r-xp 00000000 fb:00 52953143                   /lib/libgcc_s.so.1
7fb605fd8000-7fb6061d7000 ---p 00016000 fb:00 52953143                   /lib/libgcc_s.so.1
7fb6061d7000-7fb6061d8000 r--p 00015000 fb:00 52953143                   /lib/libgcc_s.so.1
7fb6061d8000-7fb6061d9000 rw-p 00016000 fb:00 52953143                   /lib/libgcc_s.so.1
7fb6061d9000-7fb606259000 r-xp 00000000 fb:00 46403228                   /usr/lib/libfreetype.so.6.3.22
7fb606259000-7fb606459000 ---p 00080000 fb:00 46403228                   /usr/lib/libfreetype.so.6.3.22
7fb606459000-7fb60645e000 r--p 00080000 fb:00 46403228                   /usr/lib/libfreetype.so.6.3.22
7fb60645e000-7fb60645f000 rw-p 00085000 fb:00 46403228                   /usr/lib/libfreetype.so.6.3.22
7fb60645f000-7fb6064a6000 r-xp 00000000 fb:00 48108085                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libfontmanager.so
7fb6064a6000-7fb6066a5000 ---p 00047000 fb:00 48108085                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libfontmanager.so
7fb6066a5000-7fb6066a8000 r--p 00046000 fb:00 48108085                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libfontmanager.so
7fb6066a8000-7fb6066a9000 rw-p 00049000 fb:00 48108085                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libfontmanager.so
7fb6066a9000-7fb6066bb000 rw-p 00000000 00:00 0 
7fb6066bb000-7fb6066c0000 r-xp 00000000 fb:00 46407660                   /usr/lib/libXdmcp.so.6.0.0
7fb6066c0000-7fb6068bf000 ---p 00005000 fb:00 46407660                   /usr/lib/libXdmcp.so.6.0.0
7fb6068bf000-7fb6068c0000 r--p 00004000 fb:00 46407660                   /usr/lib/libXdmcp.so.6.0.0
7fb6068c0000-7fb6068c1000 rw-p 00005000 fb:00 46407660                   /usr/lib/libXdmcp.so.6.0.0
7fb6068c1000-7fb6068c3000 r-xp 00000000 fb:00 46407658                   /usr/lib/libXau.so.6.0.0
7fb6068c3000-7fb606ac3000 ---p 00002000 fb:00 46407658                   /usr/lib/libXau.so.6.0.0
7fb606ac3000-7fb606ac4000 r--p 00002000 fb:00 46407658                   /usr/lib/libXau.so.6.0.0
7fb606ac4000-7fb606ac5000 rw-p 00003000 fb:00 46407658                   /usr/lib/libXau.so.6.0.0
7fb606ac5000-7fb606ae0000 r-xp 00000000 fb:00 46407662                   /usr/lib/libxcb.so.1.1.0
7fb606ae0000-7fb606cdf000 ---p 0001b000 fb:00 46407662                   /usr/lib/libxcb.so.1.1.0
7fb606cdf000-7fb606ce0000 r--p 0001a000 fb:00 46407662                   /usr/lib/libxcb.so.1.1.0
7fb606ce0000-7fb606ce1000 rw-p 0001b000 fb:00 46407662                   /usr/lib/libxcb.so.1.1.0
7fb606ce1000-7fb606cf0000 r-xp 00000000 fb:00 46405486                   /usr/lib/libXi.so.6.1.0
7fb606cf0000-7fb606eef000 ---p 0000f000 fb:00 46405486                   /usr/lib/libXi.so.6.1.0
7fb606eef000-7fb606ef0000 r--p 0000e000 fb:00 46405486                   /usr/lib/libXi.so.6.1.0
7fb606ef0000-7fb606ef1000 rw-p 0000f000 fb:00 46405486                   /usr/lib/libXi.so.6.1.0
7fb606ef1000-7fb606ef6000 r-xp 00000000 fb:00 46411833                   /usr/lib/libXtst.so.6.1.0
7fb606ef6000-7fb6070f6000 ---p 00005000 fb:00 46411833                   /usr/lib/libXtst.so.6.1.0
7fb6070f6000-7fb6070f7000 r--p 00005000 fb:00 46411833                   /usr/lib/libXtst.so.6.1.0
7fb6070f7000-7fb6070f8000 rw-p 00006000 fb:00 46411833                   /usr/lib/libXtst.so.6.1.0
7fb6070f8000-7fb607101000 r-xp 00000000 fb:00 46405452                   /usr/lib/libXrender.so.1.3.0
7fb607101000-7fb607300000 ---p 00009000 fb:00 46405452                   /usr/lib/libXrender.so.1.3.0
7fb607300000-7fb607301000 r--p 00008000 fb:00 46405452                   /usr/lib/libXrender.so.1.3.0
7fb607301000-7fb607302000 rw-p 00009000 fb:00 46405452                   /usr/lib/libXrender.so.1.3.0
7fb607302000-7fb607433000 r-xp 00000000 fb:00 46407664                   /usr/lib/libX11.so.6.3.0
7fb607433000-7fb607633000 ---p 00131000 fb:00 46407664                   /usr/lib/libX11.so.6.3.0
7fb607633000-7fb607634000 r--p 00131000 fb:00 46407664                   /usr/lib/libX11.so.6.3.0
7fb607634000-7fb607638000 rw-p 00132000 fb:00 46407664                   /usr/lib/libX11.so.6.3.0
7fb607638000-7fb607649000 r-xp 00000000 fb:00 46408221                   /usr/lib/libXext.so.6.4.0
7fb607649000-7fb607848000 ---p 00011000 fb:00 46408221                   /usr/lib/libXext.so.6.4.0
7fb607848000-7fb607849000 r--p 00010000 fb:00 46408221                   /usr/lib/libXext.so.6.4.0
7fb607849000-7fb60784a000 rw-p 00011000 fb:00 46408221                   /usr/lib/libXext.so.6.4.0
7fb60784a000-7fb607896000 r-xp 00000000 fb:00 48108230                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/xawt/libmawt.so
7fb607896000-7fb607a96000 ---p 0004c000 fb:00 48108230                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/xawt/libmawt.so
7fb607a96000-7fb607a97000 r--p 0004c000 fb:00 48108230                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/xawt/libmawt.so
7fb607a97000-7fb607a9a000 rw-p 0004d000 fb:00 48108230                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/xawt/libmawt.so
7fb607a9a000-7fb607a9b000 rw-p 00000000 00:00 0 
7fb607a9b000-7fb607b3d000 r-xp 00000000 fb:00 48108083                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libawt.so
7fb607b3d000-7fb607d3d000 ---p 000a2000 fb:00 48108083                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libawt.so
7fb607d3d000-7fb607d3e000 r--p 000a2000 fb:00 48108083                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libawt.so
7fb607d3e000-7fb607d49000 rw-p 000a3000 fb:00 48108083                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libawt.so
7fb607d49000-7fb607d6e000 rw-p 00000000 00:00 0 
7fb607d6e000-7fb607d83000 r-xp 00000000 fb:00 48108102                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libnet.so
7fb607d83000-7fb607f82000 ---p 00015000 fb:00 48108102                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libnet.so
7fb607f82000-7fb607f83000 r--p 00014000 fb:00 48108102                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libnet.so
7fb607f83000-7fb607f84000 rw-p 00015000 fb:00 48108102                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libnet.so
7fb607f84000-7fb608000000 r--s 013de000 fb:00 48108324                   /usr/share/pms-linux/pms.jar
7fb608000000-7fb608f4d000 rw-p 00000000 00:00 0 
7fb608f4d000-7fb60c000000 ---p 00000000 00:00 0 
7fb60c025000-7fb60c026000 r--p 00000000 fb:00 46533789                   /usr/lib/locale/en_US.utf8/LC_NUMERIC
7fb60c026000-7fb60c027000 r--p 00000000 fb:00 46533790                   /usr/lib/locale/en_US.utf8/LC_TIME
7fb60c027000-7fb60c028000 r--p 00000000 fb:00 46533792                   /usr/lib/locale/en_US.utf8/LC_MONETARY
7fb60c028000-7fb60c029000 r--p 00000000 fb:00 46533794                   /usr/lib/locale/en_US.utf8/LC_MESSAGES/SYS_LC_MESSAGES
7fb60c029000-7fb60c02a000 r--p 00000000 fb:00 46533795                   /usr/lib/locale/en_US.utf8/LC_PAPER
7fb60c02a000-7fb60c02b000 r--p 00000000 fb:00 46533796                   /usr/lib/locale/en_US.utf8/LC_NAME
7fb60c02b000-7fb60c02c000 r--p 00000000 fb:00 46533797                   /usr/lib/locale/en_US.utf8/LC_ADDRESS
7fb60c02c000-7fb60c032000 r--s 000fc000 fb:00 46793093                   /usr/lib/jvm/java-6-openjdk/jre/lib/resources.jar
7fb60c032000-7fb60c03b000 r--s 00000000 fb:00 34081655                   /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le64.cache-3
7fb60c03b000-7fb60c044000 r--s 00000000 fb:00 34083483                   /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le64.cache-3
7fb60c044000-7fb60c04e000 r--s 00000000 fb:00 34081637                   /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le64.cache-3
7fb60c04e000-7fb60c057000 r--s 00000000 fb:00 34081655                   /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le64.cache-3
7fb60c057000-7fb60c058000 ---p 00000000 00:00 0 
7fb60c058000-7fb60c158000 rw-p 00000000 00:00 0 
7fb60c158000-7fb60c15b000 ---p 00000000 00:00 0 
7fb60c15b000-7fb60c259000 rw-p 00000000 00:00 0 
7fb60c259000-7fb60c25c000 ---p 00000000 00:00 0 
7fb60c25c000-7fb60c35a000 rw-p 00000000 00:00 0 
7fb60c35a000-7fb60c35d000 ---p 00000000 00:00 0 
7fb60c35d000-7fb60c45b000 rw-p 00000000 00:00 0 
7fb60c45b000-7fb60c45e000 ---p 00000000 00:00 0 
7fb60c45e000-7fb60c55c000 rw-p 00000000 00:00 0 
7fb60c55c000-7fb60c59b000 r--p 00000000 fb:00 46533788                   /usr/lib/locale/en_US.utf8/LC_CTYPE
7fb60c59b000-7fb60c59e000 ---p 00000000 00:00 0 
7fb60c59e000-7fb60c69c000 rw-p 00000000 00:00 0 
7fb60c69c000-7fb60c69f000 ---p 00000000 00:00 0 
7fb60c69f000-7fb60c79d000 rw-p 00000000 00:00 0 
7fb60c79d000-7fb60c79e000 ---p 00000000 00:00 0 
7fb60c79e000-7fb60cba1000 rw-p 00000000 00:00 0 
7fb60cba1000-7fb60cba3000 r--s 0001d000 fb:00 46793081                   /usr/lib/jvm/java-6-openjdk/jre/lib/plugin.jar
7fb60cba3000-7fb60cba8000 r--s 00045000 fb:00 46793085                   /usr/lib/jvm/java-6-openjdk/jre/lib/netx.jar
7fb60cba8000-7fb60cbdb000 rw-p 00000000 00:00 0 
7fb60cbdb000-7fb60cd6a000 r--s 038c4000 fb:00 46793096                   /usr/lib/jvm/java-6-openjdk/jre/lib/rt.jar
7fb60cd6a000-7fb60cd92000 rw-p 00000000 00:00 0 
7fb60cd92000-7fb60cd93000 ---p 00000000 00:00 0 
7fb60cd93000-7fb60ce93000 rw-p 00000000 00:00 0 
7fb60ce93000-7fb60ce94000 ---p 00000000 00:00 0 
7fb60ce94000-7fb60cfa3000 rw-p 00000000 00:00 0 
7fb60cfa3000-7fb60cfe7000 rw-p 00000000 00:00 0 
7fb60cfe7000-7fb60d007000 rw-p 00000000 00:00 0 
7fb60d007000-7fb60d0e7000 rw-p 00000000 00:00 0 
7fb60d0e7000-7fb60d0f6000 rw-p 00000000 00:00 0 
7fb60d0f6000-7fb60d13a000 rw-p 00000000 00:00 0 
7fb60d13a000-7fb60d15a000 rw-p 00000000 00:00 0 
7fb60d15a000-7fb60d23a000 rw-p 00000000 00:00 0 
7fb60d23a000-7fb60d24a000 rw-p 00000000 00:00 0 
7fb60d24a000-7fb60d2ba000 rw-p 00000000 00:00 0 
7fb60d2ba000-7fb60d2bb000 rw-p 00000000 00:00 0 
7fb60d2bb000-7fb60d52b000 rwxp 00000000 00:00 0 
7fb60d52b000-7fb6102bb000 rw-p 00000000 00:00 0 
7fb6102bb000-7fb6102c2000 r-xp 00000000 fb:00 48108109                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libzip.so
7fb6102c2000-7fb6104c1000 ---p 00007000 fb:00 48108109                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libzip.so
7fb6104c1000-7fb6104c2000 r--p 00006000 fb:00 48108109                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libzip.so
7fb6104c2000-7fb6104c3000 rw-p 00007000 fb:00 48108109                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libzip.so
7fb6104c3000-7fb6104cf000 r-xp 00000000 fb:00 52953114                   /lib/libnss_files-2.11.1.so
7fb6104cf000-7fb6106ce000 ---p 0000c000 fb:00 52953114                   /lib/libnss_files-2.11.1.so
7fb6106ce000-7fb6106cf000 r--p 0000b000 fb:00 52953114                   /lib/libnss_files-2.11.1.so
7fb6106cf000-7fb6106d0000 rw-p 0000c000 fb:00 52953114                   /lib/libnss_files-2.11.1.so
7fb6106d0000-7fb6106da000 r-xp 00000000 fb:00 52953116                   /lib/libnss_nis-2.11.1.so
7fb6106da000-7fb6108d9000 ---p 0000a000 fb:00 52953116                   /lib/libnss_nis-2.11.1.so
7fb6108d9000-7fb6108da000 r--p 00009000 fb:00 52953116                   /lib/libnss_nis-2.11.1.so
7fb6108da000-7fb6108db000 rw-p 0000a000 fb:00 52953116                   /lib/libnss_nis-2.11.1.so
7fb6108db000-7fb6108e3000 r-xp 00000000 fb:00 52953112                   /lib/libnss_compat-2.11.1.so
7fb6108e3000-7fb610ae2000 ---p 00008000 fb:00 52953112                   /lib/libnss_compat-2.11.1.so
7fb610ae2000-7fb610ae3000 r--p 00007000 fb:00 52953112                   /lib/libnss_compat-2.11.1.so
7fb610ae3000-7fb610ae4000 rw-p 00008000 fb:00 52953112                   /lib/libnss_compat-2.11.1.so
7fb610ae4000-7fb610aec000 r-xp 00000000 fb:00 48108111                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/native_threads/libhpi.so
7fb610aec000-7fb610ceb000 ---p 00008000 fb:00 48108111                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/native_threads/libhpi.so
7fb610ceb000-7fb610cec000 r--p 00007000 fb:00 48108111                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/native_threads/libhpi.so
7fb610cec000-7fb610ced000 rw-p 00008000 fb:00 48108111                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/native_threads/libhpi.so
7fb610ced000-7fb610d04000 r-xp 00000000 fb:00 52953111                   /lib/libnsl-2.11.1.so
7fb610d04000-7fb610f03000 ---p 00017000 fb:00 52953111                   /lib/libnsl-2.11.1.so
7fb610f03000-7fb610f04000 r--p 00016000 fb:00 52953111                   /lib/libnsl-2.11.1.so
7fb610f04000-7fb610f05000 rw-p 00017000 fb:00 52953111                   /lib/libnsl-2.11.1.so
7fb610f05000-7fb610f07000 rw-p 00000000 00:00 0 
7fb610f07000-7fb610f34000 r-xp 00000000 fb:00 48108092                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libjava.so
7fb610f34000-7fb611133000 ---p 0002d000 fb:00 48108092                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libjava.so
7fb611133000-7fb611134000 r--p 0002c000 fb:00 48108092                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libjava.so
7fb611134000-7fb611137000 rw-p 0002d000 fb:00 48108092                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libjava.so
7fb611137000-7fb611146000 r-xp 00000000 fb:00 48108108                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libverify.so
7fb611146000-7fb611345000 ---p 0000f000 fb:00 48108108                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libverify.so
7fb611345000-7fb611347000 r--p 0000e000 fb:00 48108108                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libverify.so
7fb611347000-7fb611348000 rw-p 00010000 fb:00 48108108                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/libverify.so
7fb611348000-7fb61134f000 r-xp 00000000 fb:00 52953121                   /lib/librt-2.11.1.so
7fb61134f000-7fb61154e000 ---p 00007000 fb:00 52953121                   /lib/librt-2.11.1.so
7fb61154e000-7fb61154f000 r--p 00006000 fb:00 52953121                   /lib/librt-2.11.1.so
7fb61154f000-7fb611550000 rw-p 00007000 fb:00 52953121                   /lib/librt-2.11.1.so
7fb611550000-7fb6115d2000 r-xp 00000000 fb:00 52953109                   /lib/libm-2.11.1.so
7fb6115d2000-7fb6117d1000 ---p 00082000 fb:00 52953109                   /lib/libm-2.11.1.so
7fb6117d1000-7fb6117d2000 r--p 00081000 fb:00 52953109                   /lib/libm-2.11.1.so
7fb6117d2000-7fb6117d3000 rw-p 00082000 fb:00 52953109                   /lib/libm-2.11.1.so
7fb6117d3000-7fb612059000 r-xp 00000000 fb:00 48108113                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/server/libjvm.so
7fb612059000-7fb612258000 ---p 00886000 fb:00 48108113                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/server/libjvm.so
7fb612258000-7fb6122ce000 r--p 00885000 fb:00 48108113                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/server/libjvm.so
7fb6122ce000-7fb6122e9000 rw-p 008fb000 fb:00 48108113                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/server/libjvm.so
7fb6122e9000-7fb612322000 rw-p 00000000 00:00 0 
7fb612322000-7fb61249c000 r-xp 00000000 fb:00 52953105                   /lib/libc-2.11.1.so
7fb61249c000-7fb61269b000 ---p 0017a000 fb:00 52953105                   /lib/libc-2.11.1.so
7fb61269b000-7fb61269f000 r--p 00179000 fb:00 52953105                   /lib/libc-2.11.1.so
7fb61269f000-7fb6126a0000 rw-p 0017d000 fb:00 52953105                   /lib/libc-2.11.1.so
7fb6126a0000-7fb6126a5000 rw-p 00000000 00:00 0 
7fb6126a5000-7fb6126a7000 r-xp 00000000 fb:00 52953108                   /lib/libdl-2.11.1.so
7fb6126a7000-7fb6128a7000 ---p 00002000 fb:00 52953108                   /lib/libdl-2.11.1.so
7fb6128a7000-7fb6128a8000 r--p 00002000 fb:00 52953108                   /lib/libdl-2.11.1.so
7fb6128a8000-7fb6128a9000 rw-p 00003000 fb:00 52953108                   /lib/libdl-2.11.1.so
7fb6128a9000-7fb6128ad000 r-xp 00000000 fb:00 48108080                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/jli/libjli.so
7fb6128ad000-7fb612aac000 ---p 00004000 fb:00 48108080                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/jli/libjli.so
7fb612aac000-7fb612aad000 r--p 00003000 fb:00 48108080                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/jli/libjli.so
7fb612aad000-7fb612aae000 rw-p 00004000 fb:00 48108080                   /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/jli/libjli.so
7fb612aae000-7fb612ac6000 r-xp 00000000 fb:00 52953119                   /lib/libpthread-2.11.1.so
7fb612ac6000-7fb612cc5000 ---p 00018000 fb:00 52953119                   /lib/libpthread-2.11.1.so
7fb612cc5000-7fb612cc6000 r--p 00017000 fb:00 52953119                   /lib/libpthread-2.11.1.so
7fb612cc6000-7fb612cc7000 rw-p 00018000 fb:00 52953119                   /lib/libpthread-2.11.1.so
7fb612cc7000-7fb612ccb000 rw-p 00000000 00:00 0 
7fb612ccb000-7fb612ce1000 r-xp 00000000 fb:00 52953324                   /lib/libz.so.1.2.3.3
7fb612ce1000-7fb612ee0000 ---p 00016000 fb:00 52953324                   /lib/libz.so.1.2.3.3
7fb612ee0000-7fb612ee1000 r--p 00015000 fb:00 52953324                   /lib/libz.so.1.2.3.3
7fb612ee1000-7fb612ee2000 rw-p 00016000 fb:00 52953324                   /lib/libz.so.1.2.3.3
7fb612ee2000-7fb612f02000 r-xp 00000000 fb:00 52953099                   /lib/ld-2.11.1.so
7fb612f02000-7fb612f03000 r--p 00000000 fb:00 46533798                   /usr/lib/locale/en_US.utf8/LC_TELEPHONE
7fb612f03000-7fb612f04000 r--p 00000000 fb:00 46533799                   /usr/lib/locale/en_US.utf8/LC_MEASUREMENT
7fb612f04000-7fb612f05000 r--p 00000000 fb:00 46533800                   /usr/lib/locale/en_US.utf8/LC_IDENTIFICATION
7fb612f05000-7fb612f06000 r--p 00000000 00:00 0 
7fb612f06000-7fb612f0f000 r--s 00000000 fb:00 34083483                   /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le64.cache-3
7fb612f0f000-7fb612f19000 r--s 00000000 fb:00 34081637                   /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le64.cache-3
7fb612f19000-7fb612f1c000 r--s 0000f000 fb:00 47317030                   /usr/lib/jvm/java-6-openjdk/jre/lib/ext/pulse-java.jar
7fb612f1c000-7fb612f25000 r--s 00065000 fb:00 47585416                   /usr/share/java/gnome-java-bridge.jar
7fb612f25000-7fb612f2f000 rw-p 00000000 00:00 0 
7fb612f2f000-7fb612fe5000 rw-p 00000000 00:00 0 
7fb612fe5000-7fb612fe8000 ---p 00000000 00:00 0 
7fb612fe8000-7fb6130eb000 rw-p 00000000 00:00 0 
7fb6130eb000-7fb6130ee000 r--s 0007d000 fb:00 46793077                   /usr/lib/jvm/java-6-openjdk/jre/lib/jsse.jar
7fb6130ee000-7fb6130f5000 r--s 00000000 fb:00 46402110                   /usr/lib/gconv/gconv-modules.cache
7fb6130f5000-7fb6130fd000 rw-s 00000000 fb:00 46137357                   /tmp/hsperfdata_ffixcollector/1445
7fb6130fd000-7fb6130fe000 rw-p 00000000 00:00 0 
7fb6130fe000-7fb6130ff000 r--p 00000000 00:00 0 
7fb6130ff000-7fb613101000 rw-p 00000000 00:00 0 
7fb613101000-7fb613102000 r--p 0001f000 fb:00 52953099                   /lib/ld-2.11.1.so
7fb613102000-7fb613103000 rw-p 00020000 fb:00 52953099                   /lib/ld-2.11.1.so
7fb613103000-7fb613104000 rw-p 00000000 00:00 0 
7fff2385a000-7fff2386f000 rw-p 00000000 00:00 0                          [stack]
7fff238fd000-7fff238fe000 r-xp 00000000 00:00 0                          [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]

VM Arguments:
jvm_args: -Xmx768M -Xss1024k -Dfile.encoding=UTF-8 -Djava.net.preferIPv4Stack=true 
java_command: net.pms.PMS
Launcher Type: SUN_STANDARD

Environment Variables:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
LD_LIBRARY_PATH=/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/server:/usr/lib/jvm/java-6-openjdk/jre/lib/amd64:/usr/lib/jvm/java-6-openjdk/jre/../lib/amd64
SHELL=/bin/bash
DISPLAY=localhost:11.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x7240c0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x7240c0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x5e08f0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: [libjvm.so+0x5e08f0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGXFSZ: [libjvm.so+0x5e08f0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x5e08f0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x5e0000], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x5e2a70], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x5e2a70], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x5e2a70], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x5e2a70], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:Ubuntu 10.04 (lucid)
uname:Linux 2.6.32-33-server #72-Ubuntu SMP Fri Jul 29 21:21:55 UTC 2011 x86_64
libc:glibc 2.11.1 NPTL 2.11.1 
rlimit: STACK 8192k, CORE 0k, NPROC infinity, NOFILE 1024, AS infinity
load average:0.28 0.16 0.09

/proc/meminfo:
MemTotal:        6126024 kB
MemFree:         5597656 kB
Buffers:           16996 kB
Cached:           177416 kB
SwapCached:            0 kB
Active:           220440 kB
Inactive:         131552 kB
Active(anon):     157680 kB
Inactive(anon):      540 kB
Active(file):      62760 kB
Inactive(file):   131012 kB
Unevictable:           0 kB
Mlocked:               0 kB
SwapTotal:      17944568 kB
SwapFree:       17944568 kB
Dirty:               400 kB
Writeback:             0 kB
AnonPages:        157576 kB
Mapped:            31496 kB
Shmem:               644 kB
Slab:              22564 kB
SReclaimable:      11164 kB
SUnreclaim:        11400 kB
KernelStack:        1576 kB
PageTables:         4956 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:    21007580 kB
Committed_AS:     317468 kB
VmallocTotal:   34359738367 kB
VmallocUsed:       34912 kB
VmallocChunk:   34359699748 kB
HardwareCorrupted:     0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:        8064 kB
DirectMap2M:     6283264 kB


CPU:total 2 (1 cores per cpu, 1 threads per core) family 15 model 4 stepping 10, cmov, cx8, fxsr, mmx, sse, sse2, sse3

Memory: 4k page, physical 6126024k(5597656k free), swap 17944568k(17944568k free)

vm_info: OpenJDK 64-Bit Server VM (19.0-b09) for linux-amd64 JRE (1.6.0_20-b20), built on Nov  8 2011 18:27:16 by "buildd" with gcc 4.4.3

time: Fri Jan  6 21:05:37 2012
elapsed time: 32 seconds

```

Any Ideas?

---

