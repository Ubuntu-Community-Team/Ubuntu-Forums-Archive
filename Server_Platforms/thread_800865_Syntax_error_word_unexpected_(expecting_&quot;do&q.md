---
title: "Syntax error: word unexpected (expecting &quot;do&quot;)"
date: 2008-05-20
forum: Server Platforms
---

### Post by lrsorey on 2008-05-20
Hello All,

I have a question regarding starting the RED5 Standalone Server
on Ubuntu 8.04 Server.

I have successfully run the latest Red5 trunk on Ubuntu 8.04  with Tomcat 6.0.16 but I am having trouble in getting RED5 to start as a standalone server.

Here is what I am encountering:

1. I do have export JAVA_HOME=/usr/lib/jvm/java-6-sun in my /.bashrc file

2. I have the following code in my red5.sh file located in the /usr/local/red5 folder:

for JAVA in ´$JAVA_HOME/bin/java´ ´/usr/lib/java-6-sun/bin/java´ ´/usr/lib/jvm/java-6-sun/bin/java´
do
  if [ -x $JAVA ]
  then
    break
  fi
 
done
 
if [ ! -x $JAVA ]
then
  echo "Unable to locate Java. Please set JAVA_HOME environment variable."
  exit
fi
 
# start Red5
echo "Starting Red5..."
exec $JAVA -Djava.security.manager -Djava.security.policy=conf/red5.policy -cp red5.jar:conf:$CLASSPATH org.red5.server.Standalone


When I run sh red5.sh I get the following error message:

lrsorey@fatdotubuntu:~$ cd /usr/local/red5
lrsorey@fatdotubuntu:/usr/local/red5$ sh red5.sh
red5.sh: 2: Syntax error: word unexpected (expecting "do")

The error message is looking for do but the do command appears on line
2 of the red5.sh

Does anyone have any ideas as to what could be causing this error?

Thanks,




I also also have a red5 file in the init.d folder as follows and I have compile this to be an auto start file:

# red5 auto-start
    #
    # description: Auto-starts red5
    # processname: red5
    # pidfile: /var/run/red5.pid

    export JAVA_HOME=/usr/lib/jvm/java-6-sun

    case $1 in
    start)
            sh /usr/local/red5/red5.sh
            ;;
    stop) 
            sh /usr/local/red5/red5-shutdown.sh
            ;;
    restart)
            sh /usr/local/red5/red5-shutdown.sh
            sh /usr/local/red5/red5.sh
            ;;
    esac  
    exit 0

---

### Post by koenn on 2008-05-20
the quoting in your your "for"-line is wrong, and makes that bash doesn't see the 'do' 

try 
```
for JAVA ib "$JAVA_HOME/bin/java /usr/lib/java-6-sun/bin/java /usr/lib/jvm/java-6-sun/bin/java"
do
```

---

