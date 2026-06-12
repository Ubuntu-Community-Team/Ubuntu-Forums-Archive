---
title: "Trouble with writing Upstart script for Alfresco (Tomcat 6)"
date: 2011-09-23
forum: Server Platforms
---

### Post by kudellski on 2011-09-23
I've been going through the Upstart cookbook quite a bit, but I'm still a confused on how to get this working properly. My script so far:

```
# alfresco - Alfresco Enterprise Content Management

description     "Alfresco Enterprise Content Management server"

#start on started mysql
start on runlevel [2345]
stop on runlevel [!2345]

expect fork

env JAVA_HOME="/usr/lib/jvm/java-6-sun"
env JAVA_OPTS="-Xms1000m -Xmx1500m -XX:MaxPermSize=600m -server -Djava.security.krb5.conf=/etc/krb5.conf"
env TOMCAT_HOME="/opt/alfresco/tomcat"
env PID_FILE="/var/run/alfresco.pid"

script
exec start-stop-daemon --make-pidfile --pidfile $PID_FILE --background --start \
--exec $JAVA_HOME/bin/java -- $JAVA_OPTS \
-Djava.util.logging.config.file=$TOMCAT_HOME/conf/logging.properties \
-Djava.util.logging.manager=org.apache.juli.ClassLoaderLogManager \
-Djava.endorsed.dirs=$TOMCAT_HOME/endorsed \
-Dcatalina.base=$TOMCAT_HOME \
-Dcatalina.home=$TOMCAT_HOME \
-Djava.io.tmpdir=$TOMCAT_HOME/temp \
-classpath $TOMCAT_HOME/bin/bootstrap.jar \
org.apache.catalina.startup.Bootstrap start
end script

pre-start script
        if pidof soffice.bin; then
                killall soffice.bin;
        fi
end script

post-stop script
        if pidof soffice.bin; then
                killall soffice.bin;
        fi
        if [ -e $PID_FILE ]; then
                rm $PID_FILE
        fi
end script


```

When set the vars and cut and paste that command after exec it works perfectly. When I try to start this script I get:
```

Sep 23 16:25:20 alftest01 init: alfresco main process (7012) terminated with status 3
```

So I'm not sure why it's not starting in the script. I suspect that it's trying to manage the wrong PID, but I'm unsure how to force it to the PID start-stop-daemon is creating, which is the one I want.

Older versions of Upstart had a "pid file" and "pid timeout" stanza, which seems perfect for what I want to do.

How is this done now?

---

