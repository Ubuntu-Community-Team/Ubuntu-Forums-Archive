---
title: "Installing Cassandra 0.6.2 (unstable) on Ubuntu 10.04"
date: 2010-06-28
forum: Server Platforms
---

### Post by quantleap on 2010-06-28
Hi Ubuntu lovers!

I'm trying to install Cassandra on my Ubuntu 10. I followed the instructions to [install cassandra on ubuntu]("http://dustyreagan.com/installing-cassandra-on-ubuntu-linux/") with the patches mentioned on [how to install scala, akka and cassandra]("http://roestenburg.agilesquad.com/2010/06/akka-081-and-cassandra-062.html") (which is my real target).

So basically i took the packages from the unstable

```
deb http://www.apache.org/dist/cassandra/debian unstable main
deb-src http://www.apache.org/dist/cassandra/debian unstable main
```and then tried to setup the jmx port in the init.d/cassandra script to 10036.

The funny thing is, the script seems to lose track of the pid , because even when i try to stop a server which is not even running, it will try to start a new one.

```

quantleap@igloo:~$ cassandra stop
 INFO 19:34:16,013 Auto DiskAccessMode determined to be standard
 INFO 19:34:18,550 Deleted /var/lib/cassandra/data/system/LocationInfo-9-Data.db
 INFO 19:34:18,551 Deleted /var/lib/cassandra/data/system/LocationInfo-10-Data.db
 INFO 19:34:18,554 Deleted /var/lib/cassandra/data/system/LocationInfo-11-Data.db
 INFO 19:34:18,555 Deleted /var/lib/cassandra/data/system/LocationInfo-12-Data.db
 INFO 19:34:18,559 Sampling index for /var/lib/cassandra/data/system/LocationInfo-13-Data.db
 INFO 19:34:18,947 Replaying /var/lib/cassandra/commitlog/CommitLog-1277650923708.log
 INFO 19:34:19,135 Creating new commitlog segment /var/lib/cassandra/commitlog/CommitLog-1277750059135.log
 INFO 19:34:19,785 LocationInfo has reached its threshold; switching in a fresh Memtable at CommitLogContext(file='/var/lib/cassandra/commitlog/CommitLog-1277750059135.log', position=133)
 INFO 19:34:19,786 Enqueuing flush of Memtable(LocationInfo)@9744175
 INFO 19:34:19,787 Writing Memtable(LocationInfo)@9744175
 INFO 19:34:20,741 Completed flushing /var/lib/cassandra/data/system/LocationInfo-14-Data.db
 INFO 19:34:20,882 Log replay complete
 INFO 19:34:21,073 Saved Token found: 68303451176189267349861467225997138262
 INFO 19:34:21,073 Saved ClusterName found: Test Cluster
 INFO 19:34:21,097 Starting up server gossip
 INFO 19:34:21,292 Binding thrift service to localhost/127.0.0.1:9160


quantleap@igloo:~$ ps -fea | grep cassandra
quantleap       1878     1  2 19:34 pts/0    00:00:02 /usr/bin/java -Xdebug -Xms128M -Xmx1G -XX:TargetSurvivorRatio=90 -XX:+AggressiveOpts -XX:+UseParNewGC -XX:+UseConcMarkSweepGC -XX:+CMSParallelRemarkEnabled -XX:+HeapDumpOnOutOfMemoryError -XX:SurvivorRatio=128 -XX:MaxTenuringThreshold=0 -Dcom.sun.management.jmxremote.port=10036 -Dcom.sun.management.jmxremote.ssl=false -Dcom.sun.management.jmxremote.authenticate=false -Dstorage-config=/etc/cassandra -cp /etc/cassandra:/usr/share/cassandra/antlr-3.1.3.jar:/usr/share/cassandra/apache-cassandra-.jar:/usr/share/cassandra/apache-cassandra.jar:/usr/share/cassandra/avro-1.2.0-dev.jar:/usr/share/cassandra/clhm-production.jar:/usr/share/cassandra/commons-cli-1.1.jar:/usr/share/cassandra/commons-codec-1.2.jar:/usr/share/cassandra/commons-collections-3.2.1.jar:/usr/share/cassandra/commons-lang-2.4.jar:/usr/share/cassandra/google-collections-1.0.jar:/usr/share/cassandra/hadoop-core-0.20.1.jar:/usr/share/cassandra/high-scale-lib.jar:/usr/share/cassandra/jackson-core-asl-1.4.0.jar:/usr/share/cassandra/jackson-mapper-asl-1.4.0.jar:/usr/share/cassandra/jline-0.9.94.jar:/usr/share/cassandra/json-simple-1.1.jar:/usr/share/cassandra/libthrift-r917130.jar:/usr/share/cassandra/log4j-1.2.14.jar:/usr/share/cassandra/slf4j-api-1.5.8.jar:/usr/share/cassandra/slf4j-log4j12-1.5.8.jar org.apache.cassandra.thrift.CassandraDaemon

```
Even worse, trying to actually stop it, will only make it try to step on it
```

quantleap@igloo:~$ cassandra stop
quantleap@igloo:~$ Error: Exception thrown by the agent : java.rmi.server.ExportException: Port already in use: 10036; nested exception is: 
    java.net.BindException: Address already in use

```

the only way i can actually stop the process is by killing it.

Has anybody else seen this problem? More importantly, do you know how to fix it?

Cheers

---

### Post by quantleap on 2010-06-28
i tried using the "stable" package, but it doesn't install any configuration in /etc/cassandra, and even adding the log4j.properties and storage-conf.xml manuall, still doesn't start, and has the same port 8080 problem

[https://launchpad.net/~cassandra-ubuntu/+archive/stable](https://launchpad.net/~cassandra-ubuntu/+archive/stable)

---

