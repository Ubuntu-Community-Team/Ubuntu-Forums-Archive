---
title: "chkconfig on Ubuntu"
date: 2013-09-27
forum: Server Platforms
---

### Post by sidd_nakade on 2013-09-27
I have created a startup service for tomcat using chkconfig (runlevel 2345) , the service is starting ok but is not able to access fonts.
Once i kill the service and start it manually then it is able to access the fonts correctly.

I also tried adding this service in cron tab instead of chkconfig, the service works Ok [it is able to access fonts] if started via cron tab.
 
thanks for the help
Sidd

---

### Post by hawkmage on 2013-09-27
Ubuntu uses Upstart to control the startup of services.  The chkconfig command is designed around the SystemV init.d scripts.

Unfortunately the Tomcat that ins in the Ubuntu package sources still relies on the SystemV /etc/init.d scripts and not Upstart.  I have see some Upstart examples for tomcat but none of them look to be all that flexible.

---

### Post by sidd_nakade on 2013-09-28
I am using my own Tomcat and startup script..
here is the code for startup script  /etc/init.d/tomcat

---------------------------

#!/bin/bash
# description: Tomcat Start Stop Restart
# processname: tomcat
# chkconfig: 35 99 80


echo "***** set environment vairables for Java, catalina etc ********"
CATALINA_HOME=/usr/local/tomcat
JAVA_HOME=/usr/local/java
CATALINA_OPTS="-Xms1024m -Xmx2560m  -XX:MaxPermSize=1024m"
export CATALINA_HOME  CATALINA_OPTS JAVA_HOME


case $1 in
start)
sh $CATALINA_HOME/bin/startup.sh & 
;;
stop)
sh $CATALINA_HOME/bin/shutdown.sh
;;
restart)
sh $CATALINA_HOME/bin/shutdown.sh
sh $CATALINA_HOME/bin/startup.sh
;;
esac
exit 0

---

### Post by sidd_nakade on 2013-09-28
What is the boot sequence for Ubuntu.
how are the fonts initialized ??

---

