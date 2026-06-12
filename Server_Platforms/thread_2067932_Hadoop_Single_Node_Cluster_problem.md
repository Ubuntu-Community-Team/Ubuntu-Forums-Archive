---
title: "Hadoop Single Node Cluster problem"
date: 2012-10-08
forum: Server Platforms
---

### Post by Crafty Kisses on 2012-10-08
Hey guys Montana here,

I have configured Hadoop for single node cluster, when I run my URLS, the .jsp's they work which means Hadoop is working but upon booting Hadoop by formatting a new distributed filesystem 
```
bin/hadoop namenode -format
```
I get an SSH error, but then when I actually start Hadoop
```
 bin/start-dfs.sh
```
Which should also handle the "${HADOOP_CONF_DIR}" + before I go any further I want to post my Hadoop config, I have the default configuration for Hadoop right now which is
```
<?xml version="1.0"?>
<?xml-stylesheet type="text/xsl" href="configuration.xsl"?>
<configuration>
<property>
  <name>hadoop.tmp.dir</name>
  <value>/tmp/hadoop-${user.name}</value>
</property>
<property>
  <name>fs.default.name</name>
  <value>hdfs://localhost:54310</value>
</property>
<property>
  <name>mapred.job.tracker</name>
  <value>hdfs://localhost:54311</value>
</property>
<property> 
  <name>dfs.replication</name>
  <value>8</value>
</property>
<property>
  <name>mapred.child.java.opts</name>
  <value>-Xmx512m</value>
</property>
</configuration>
```
So then
```
/usr/lib/hbase/bin/start-hbase.sh
```
I get this error:
```
Apache Hadoop is not in the sudoers file. This incident will be reported.
```
I've obviously installed HBASE for the Hadoop single node cluster. I've purged and reinstalled HBASE, but to no avail.

---

