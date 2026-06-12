---
title: "tomcat startup script"
date: 2011-02-17
forum: Server Platforms
---

### Post by jamesbon on 2011-02-17
I am looking for a tomcat start up script on a Ubuntu machine.
My Ubuntu is 10.04 server.
The tomcat is 5.5.30. (My applications wont run on higher versions)
It is in /opt/apache-tomcat-5.5.31

I tried a script here

```

#!/bin/bash
#
# tomcat        
#
# chkconfig: 
# description:     Start up the Tomcat servlet engine.

# Source function library.
**. /lib/lsb/init-functions**
RETVAL=$?
CATALINA_HOME="/opt/apache-tomcat-5.5.31"
case "$1" in
 start)
        if [ -f $CATALINA_HOME/bin/startup.sh ];
          then
            echo $"Starting Tomcat"
        fi
        ;;
 stop)
        if [ -f $CATALINA_HOME/bin/shutdown.sh ];
          then
            echo $"Stopping Tomcat"
        fi
        ;;
 *)
        echo $"Usage: $0 {start|stop}"
        exit 1
        ;;
esac
exit $RETVAL
```but it did not worked when I tried 
/etc/init.d/tomcat start

---

### Post by koenn on 2011-02-17
> **jamesbon said:**
> ... but it did not worked when I tried 
/etc/init.d/tomcat start

err, maybe explain what you mean with "did not work well" ?

Also, afaik, your script can't do anything but show a message. Is that what you want it to do ?

---

### Post by jamesbon on 2011-02-17
Sorry I posted the wrong script this is the correct one
> 
#!/bin/bash
#
# tomcat        
#
# chkconfig: 
# description: 	Start up the Tomcat servlet engine.

# Source function library.
. /lib/lsb/init-functions


RETVAL=$?
CATALINA_HOME="/opt/apache-tomcat-5.5.31"
JAVA_HOME="/usr/lib/jvm/java-6-sun"

case "$1" in
 start)
        if [ -f $CATALINA_HOME/bin/startup.sh ];
          then
	    echo $"Starting Tomcat"
	/opt/apache-tomcat-5.5.31/bin/startup.sh

        fi
	;;
 stop)
        if [ -f $CATALINA_HOME/bin/shutdown.sh ];
          then
	    echo $"Stopping Tomcat"
	  /opt/apache-tomcat-5.5.31/bin/shutdown.sh
        fi
 	;;
 *)
 	echo $"Usage: $0 {start|stop}"
	exit 1
	;;
esac

exit $RETVAL

---

### Post by Azdour on 2011-02-18
Hi,

Here's a service script I use:

```

export JAVA_HOME=/usr/lib/jvm/java-6-openjdk

case $1 in
start)
        sh /home/system/tomcat/bin/startup.sh
        ;;
stop)
        sh /home/system/tomcat/bin/shutdown.sh
        ;;
restart)
        sh /home/system/tomcat/bin/shutdown.sh
        sh /home/system/tomcat/bin/startup.sh
        ;;
esac
exit

```

I had to export the JAVA_HOME and I use sh to launch the tomcat scripts

---

### Post by jamesbon on 2011-02-21
That did not worked for me.I got error sh command not found.
I also tried using without sh that also did not work.

If I do an ssh and 
> /opt/apache-tomcat-5.5.31/bin/startup.sh 
then only things started working.

I think you are right for some reason JAVA_HOME is not getting detected.
My script is 
> 
#!/bin/bash
#
# tomcat        
#
# chkconfig: 
# description: 	Start up the Tomcat servlet engine.

# Source function library.
. /lib/lsb/init-functions


RETVAL=$?
export CATALINA_HOME="/opt/apache-tomcat-5.5.31"
export JAVA_HOME="/usr/lib/jvm/java-6-sun"
export JAVA_OPTS='-server -Xms512m -Xmx1024m -XX:PermSize=128m -XX:MaxPermSize=512m -XX:NewSize=192m -XX:MaxNewSize=384m -Djava.awt.headless=true -Dhttp.agent=Sakai -Dorg.apache.jasper.compiler.Parser.STRICT_QUOTE_ESCAPING=false -Dsun.lang.ClassLoader.allowArraySyntax=true'

case "$1" in
 start)
        if [ -f $CATALINA_HOME/bin/startup.sh ];
          then
	    echo $"Starting Tomcat"
	/opt/apache-tomcat-5.5.31/bin/startup.sh
	fi
	;;
 stop)
        if [ -f $CATALINA_HOME/bin/shutdown.sh ];
          then
	    echo $"Stopping Tomcat"
	  /opt/apache-tomcat-5.5.31/bin/shutdown.sh
        fi
 	;;
 *)
 	echo $"Usage: $0 {start|stop}"
	exit 1
	;;
esac

exit $RETVAL
I had put a line > /etc/init.d/tomcat in rc.local but that did not worked.
I also tried putting following line

> /opt/apache-tomcat-5.5.31/bin/startup.sh

I manually had to ssh and start.

---

