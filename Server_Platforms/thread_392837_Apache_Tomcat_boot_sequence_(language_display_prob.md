---
title: "Apache Tomcat boot sequence (language display problem)"
date: 2007-03-25
forum: Server Platforms
---

### Post by phantom32i on 2007-03-25
I am using Ubuntu 6.10 with Tomcat and MySql.
The problem i am having is displaying properly UTF-8 font. (Chinese)

Everything is set up properly but everytime the server is rebooted. the font will not display correctly unless I restart Tomcat.
It seems the problem is with Tomcat booting first and by resetting Tomcat after everything has started solves the language display problem

Does anyone have a solution.

[http://www.memmo.com](http://www.memmo.com)
you can use guest/guest to login to memmo or memmotalk

Thanks

---

### Post by phantom32i on 2007-03-25
here is the script

#!/bin/sh
#file:tomcat.sh
CLASSPATH=/opt/zimbra/jdk1.5.0_08/lib
JAVA_HOME=/opt/zimbra/jdk1.5.0_08
CATALINA_OPTS="-Djava.awt.headless=true"
JAVA_OPTS="-Xms256m -Xmx256m"

export CLASSPATH
export JAVA_HOME
export CATALINA_OPTS
export JAVA_OPTS

case "$1" in
 start)
   echo "Starting tomcat5..."
   /apps/tomcat/bin/startup.sh
   ;;
 stop)
   echo "Stopping tomcat5..."
   /apps/tomcat/bin/shutdown.sh
   ;;
 *)
   echo "Usage tomcat.sh start/stop"
   exit 1;;
esac

#tomcat.sh end

---

### Post by phantom32i on 2007-03-26
Anyone there.. please help...

---

### Post by phantom32i on 2007-03-26
Here is more detail if anyone can help!!!

I need some advice on setting up Linux so i can display language correctly.
We r using Ubuntu 6.10 with Apache Tomcat and MySql.

Chinese characters can display correctly in our storage section only if we restart Tomcat after server is up.
Tony says it is because Tomcat somehow starts before mysql therefore we have to restart tomcat so it starts after database in order to display Chinese Characters correctly.

Do you know how to either
1) change the script so that Tomcat and start after mysql
or
2) another fix that does not require tomcat to be restarted everytime our server is up.

**You can view this problem at**
[http://www.memmo.com](http://www.memmo.com)

Start memmo by clicking on "memmo" icon on left bar and use the following tim/tim to sign in.

go to "storage section" in order to see the problem

---

