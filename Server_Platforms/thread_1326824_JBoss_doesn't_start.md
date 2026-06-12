---
title: "JBoss doesn't start"
date: 2009-11-14
forum: Server Platforms
---

### Post by delta_i on 2009-11-14
Hi, all!

I have installed JBoss (4.2.3 GA) according to instructions given here:

[http://chiralsoftware.com/linux-system-administration/jboss-server-deployment.seam](http://chiralsoftware.com/linux-system-administration/jboss-server-deployment.seam)

but I can't connect to it on any address and port I can think of. When running run.sh I get the following message:

=========================================================================

  JBoss Bootstrap Environment

  JBOSS_HOME: /usr/local/jboss

  JAVA: java

  JAVA_OPTS: -Dprogram.name=run.sh -Xms128m -Xmx512m -Dsun.rmi.dgc.client.gcInterval=3600000 -Dsun.rmi.dgc.server.gcInterval=3600000 -Djava.net.preferIPv4Stack=true

  CLASSPATH: /usr/local/jboss/bin/run.jar

=========================================================================

... and it just hangs there. What could be the problem? Where should I look for logs? I have opened both port 80 and 8080 for input in the firewall but that didn't help. Any suggestions would be appreciated.

I have installed following JBoss related packages using the package manager:
 jbossas4
 libjboss-common-java
 libjboss-j2ee-java
 libjboss-naming-java
 libjboss-profiler-java
 libjboss-serialization-java
 libjboss-server-java
 libjboss-webservices-java

I have also installed Sun Java 6 (-bin and -jre packages) and I run on Ubuntu 9.10.

Regards.

---

### Post by delta_i on 2009-11-15
OK, so I have solved the problem. After some forum digging I realised I might be running some other version of Java than the one I was expecting so I ran update-alternatives and sure enough...

```

root@ubuntu:/usr/local/jboss# update-alternatives --config java
There are 2 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                  Priority   Status
------------------------------------------------------------
 *0            /usr/bin/gij-4.4                       1044      auto mode
  1            /usr/bin/gij-4.4                       1044      manual mode
  2            /usr/lib/jvm/java-6-sun/jre/bin/java   63        manual mode

Press enter to keep the current choice
[*], or type selection number: 2
```Switching to the alternative 2 resolved the issue.

Kind regards,
/delta_i

---

