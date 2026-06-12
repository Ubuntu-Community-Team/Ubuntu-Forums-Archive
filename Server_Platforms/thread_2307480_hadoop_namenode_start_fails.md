---
title: "hadoop namenode start fails"
date: 2015-12-25
forum: Server Platforms
---

### Post by arunsadhasivam on 2015-12-25
when starting name node  i am getting below error.

>hadoop-daemon.sh start namenoe
java.io.IOException: Failed on local exception: java.net.SocketException: Permission denied; Host Details : local host is: "localhost"; destination 
host is: (unknown):0; 
    at org.apache.hadoop.net.NetUtils.wrapException(NetUtils.java:764)
    at org.apache.hadoop.ipc.Server.bind(Server.java:419)
    at org.apache.hadoop.ipc.Server$Listener.<init>(Server.java:561)
    at org.apache.hadoop.ipc.Server.<init>(Server.java:2166)
    at org.apache.hadoop.ipc.RPC$Server.<init>(RPC.java:897)
    at org.apache.hadoop.ipc.ProtobufRpcEngine$Server.<init>(ProtobufRpcEngine.java:505)
    at org.apache.hadoop.ipc.ProtobufRpcEngine.getServer(ProtobufRpcEngine.java:480)
    at org.apache.hadoop.ipc.RPC$Builder.build(RPC.java:742)
    at org.apache.hadoop.hdfs.server.namenode.NameNodeRpcServer.<init>(NameNodeRpcServer.java:311)
    at org.apache.hadoop.hdfs.server.namenode.NameNode.createRpcServer(NameNode.java:614)
    at org.apache.hadoop.hdfs.server.namenode.NameNode.initialize(NameNode.java:587)
    at org.apache.hadoop.hdfs.server.namenode.NameNode.<init>(NameNode.java:751)
    at org.apache.hadoop.hdfs.server.namenode.NameNode.<init>(NameNode.java:735)
    at org.apache.hadoop.hdfs.server.namenode.NameNode.createNameNode(NameNode.java:1407)
    at org.apache.hadoop.hdfs.server.namenode.NameNode.main(NameNode.java:1473)
Caused by: java.net.SocketException: Permission denied
    at sun.nio.ch.Net.bind0(Native Method)
    at sun.nio.ch.Net.bind(Net.java:444)
    at sun.nio.ch.Net.bind(Net.java:436)
    at sun.nio.ch.ServerSocketChannelImpl.bind(ServerSocketChannelImpl.java:214)
    at sun.nio.ch.ServerSocketAdaptor.bind(ServerSocketAdaptor.java:74)
    at org.apache.hadoop.ipc.Server.bind(Server.java:402)
    ... 13 more
2015-12-26 00:12:07,910 INFO org.apache.hadoop.util.ExitUtil: Exiting with status 1
2015-12-26 00:12:07,912 INFO org.apache.hadoop.hdfs.server.namenode.Nam


Alos host entry
i tried to map all ip but no use same error please help me to resolve this issue. below is host entry
127.0.0.1       localhost
127.0.1.1       ubuntu
192.168.1.1     ubuntu
192.168.1.2     ubuntu
192.168.1.3     ubuntu
192.168.56.1    ubuntu
# The following lines are desirable for IPv6 capable hosts
#::1     localhost ip6-localhost ip6-loopback
#ff02::1 ip6-allnodes
#ff02::2 ip6-allrouters

---

### Post by DuckHook on 2015-12-26
Can't help you because your question is way beyond my expertise.

Hadoop is a high-level app and questions about it won't likely be answered on a New Users Forum. Perhaps you might ask a moderator to move it to General Help or Servers where such gurus visit.

---

