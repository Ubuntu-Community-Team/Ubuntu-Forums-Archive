---
title: "Cassandra Database Error"
date: 2013-05-13
forum: Virtualisation
---

### Post by kirankh7 on 2013-05-13
Hi am starting cassandra Multinode Cluster from my environment am not good at cassandra its throwing one error message on my console Like 

/lib/jamm-0.2.5.jar
 INFO 10:48:59,526 JNA not found. Native methods will be disabled.
 INFO 10:48:59,689 Loading settings from file:/cassendra/apache-cassandra-1.2.2/conf/cassandra.yaml
 INFO 10:49:01,663 32bit JVM detected.  It is recommended to run Cassandra on a 64bit JVM for better performance.
ERROR 10:49:01,698 Fatal configuration error
org.apache.cassandra.exceptions.ConfigurationException: Missing required directive CommitLogSync
    at org.apache.cassandra.config.DatabaseDescriptor.loadYaml(DatabaseDescriptor.java:154)
    at org.apache.cassandra.config.DatabaseDescriptor.<clinit>(DatabaseDescriptor.java:122)
    at org.apache.cassandra.service.CassandraDaemon.setup(CassandraDaemon.java:150)
    at org.apache.cassandra.service.CassandraDaemon.activate(CassandraDaemon.java:366)
    at org.apache.cassandra.service.CassandraDaemon.main(CassandraDaemon.java:409)
Missing required directive CommitLogSync
Fatal configuration error; unable to start server.  See log for stacktrace.






if any one have any idea about this please let me know
Thanks

---

### Post by joy4 on 2014-04-08
I've a four node apache cassandra community 1.2 cluster in single datacenter with a seed.
All configurations are similar in cassandra.yaml file.
The following issues are faced, please help.

1] Though fourth node isn't listed in nodetool ring or status command,  system.log displayed only this node isn't communicating via gossip  protoccol with other nodes.
However both jmx & telnet port is enabled with proper listen/seed address configured.

2] Though Opscenter is able to recognize all four nodes, the agents are not getting installed from opscenter.
However same JVM version is installed as well as JAVA_HOME is also set in all four nodes.

Further observed that problematic node has Ubuntu 64-Bit & other nodes are Ubuntu 32-Bit, can it be the reason?

---

