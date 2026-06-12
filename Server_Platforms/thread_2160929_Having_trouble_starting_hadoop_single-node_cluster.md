---
title: "Having trouble starting hadoop single-node cluster"
date: 2013-07-08
forum: Server Platforms
---

### Post by Crafty Kisses on 2013-07-08
Hey guys it's Montana, when I try to start a Hadoop cluster in Ubuntu from the shell I get the following error:

```
hduser@montana-G31M-S2L:/usr/local/hadoop$ /usr/local/hadoop/bin/start-all.sh
/usr/local/hadoop/libexec/../conf/hadoop-env.sh: line 9: export: `/usr/lib/jvm/jdk1.7.0_09': not a valid identifier
Warning: $HADOOP_HOME is deprecated
localhost: /usr/local/hadoop/libexec/../conf/hadoop-env.sh: line 9: export: `/usr/lib/jvm/jdk1.7.0_09': not a valid identifier
localhost: Error: JAVA_HOME is not set.
/usr/local/hadoop/libexec/../conf/hadoop-env.sh: line 9: export: `/usr/lib/jvm/jdk1.7.0_09': not a valid identifier
jobtracker running as process 8066. Stop it first.
localhost: starting tasktracker, logging to /usr/local/hadoop/libexec/../logs/hadoop-hduser-tasktracker-duleep-G31M-S2L.out
localhost: /usr/local/hadoop/libexec/../conf/hadoop-env.sh: line 9: export: `/usr/lib/jvm/jdk1.7.0_09': not a valid identifier
localhost: Error: JAVA_HOME is not set.
```

The obvious thing to look for in this case is the kernel routing table (which appears to be fine). I checked the contents of ```
$HADOOP_HOME/conf/hadoop-env.sh
```

The JAVA_HOME export line - looked like it had a trailing quote, but didn't. For reference, this is what my old .conf looked like

```
export JAVA_HOME=/usr/lib/jvm/jdk1.7.0_07-i586
```

I can pastebin my whole hadoop conf, but it is a SINGLE node cluster, so it shouldn't be that difficult to solve, I have a Kubuntu/BSD box running hadoop fine. Running IPv6 of course. SSH correctly setup, etc etc. Heres my kernel routing table just for looks

```
       # netstat -nr
           Kernel routing table
           Destination     Gateway         Genmask         Flags Metric Ref Use
           127.0.0.1       *               255.255.255.255 UH    1      0
           191.72.1.0      *               255.255.255.0   U     1      0
           191.72.2.0      191.72.1.1      255.255.255.0   UGN   1      0
```

---

