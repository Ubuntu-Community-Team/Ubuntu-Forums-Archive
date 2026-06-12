---
title: "Multiple Tomcat 6 instances"
date: 2009-05-20
forum: Server Platforms
---

### Post by s_baramov on 2009-05-20
I am running Ubuntu 8.10 server with the latest patches : 

```
$ uname -a
Linux cuxbuilder 2.6.27-11-server #1 SMP Wed Apr 1 21:53:55 UTC 2009 i686 GNU/Linux

```

I have installed tomcat 6 in the regular way using the apt-get. Disabled security in /etc/default/tomcat6. When I start the tomcat daemon: 

```
$ sudo /etc/init.d/tomcat6 start 
```

I get three separate tomcat processes. 
```

root     14969     1  0 08:20 ?        00:00:00 /usr/bin/jsvc -user tomcat6 -cp /usr/share/java/commons-daemon.jar:/usr/share/tomcat6/bin/bootstrap.jar -outfile SYSLOG -errfile SYSLOG -pidfile /var/run/tomcat6.pid -Djava.awt.headless=true -Xmx128M -Djava.endorsed.dirs=/usr/share/tomcat6/endorsed -Dcatalina.base=/var/lib/tomcat6 -Dcatalina.home=/usr/share/tomcat6 -Djava.io.tmpdir=/var/lib/tomcat6/temp -Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager -Djava.util.logging.config.file=/var/lib/tomcat6/conf/logging.properties org.apache.catalina.startup.Bootstrap
root     14970 14969  0 08:20 ?        00:00:00 /usr/bin/jsvc -user tomcat6 -cp /usr/share/java/commons-daemon.jar:/usr/share/tomcat6/bin/bootstrap.jar -outfile SYSLOG -errfile SYSLOG -pidfile /var/run/tomcat6.pid -Djava.awt.headless=true -Xmx128M -Djava.endorsed.dirs=/usr/share/tomcat6/endorsed -Dcatalina.base=/var/lib/tomcat6 -Dcatalina.home=/usr/share/tomcat6 -Djava.io.tmpdir=/var/lib/tomcat6/temp -Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager -Djava.util.logging.config.file=/var/lib/tomcat6/conf/logging.properties org.apache.catalina.startup.Bootstrap
tomcat6  14971 14969 15 08:20 ?        00:00:07 /usr/bin/jsvc -user tomcat6 -cp /usr/share/java/commons-daemon.jar:/usr/share/tomcat6/bin/bootstrap.jar -outfile SYSLOG -errfile SYSLOG -pidfile /var/run/tomcat6.pid -Djava.awt.headless=true -Xmx128M -Djava.endorsed.dirs=/usr/share/tomcat6/endorsed -Dcatalina.base=/var/lib/tomcat6 -Dcatalina.home=/usr/share/tomcat6 -Djava.io.tmpdir=/var/lib/tomcat6/temp -Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager -Djava.util.logging.config.file=/var/lib/tomcat6/conf/logging.properties org.apache.catalina.startup.Bootstrap
```

The parameters for the jsvc are identical on the all of the three process. Is this normal ?

---

### Post by rippfx on 2010-06-30
sorry for resurrecting an old topic but I'm looking at the same issue on my system.
It gets spawned by the parent PID and not sure if this is normal behavior. Weird thing is it starts off with one process then I see two then sometimes three... then it goes back to one and constantly repeats this process...
Any idea if this is normal tomcat behavior?

---

