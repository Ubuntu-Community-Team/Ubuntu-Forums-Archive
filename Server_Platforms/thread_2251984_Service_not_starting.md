---
title: "Service not starting"
date: 2014-11-08
forum: Server Platforms
---

### Post by geohei on 2014-11-08
Hi.

12.04 LTS Server

/etc/init.d/minecraft
```
#!/bin/sh
#/etc/init.d/minecraft

### BEGIN INIT INFO
# Provides:          minecraft
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Controls the minecraft server
# Description:       Controls the minecraft server
### END INIT INFO

# configuration
# Replace the location path with the folder containing your CraftBukkit.jar or minecraft_server.jar file
LOCATION="/root/minecraft"
#Replace CraftBukkit with the name of the .jar file you use
MINECRAFT="craftbukkit-1.6.2-R1.0.jar"
# Path to your java executable (or just "java" if it's already in your $PATH)
JAVA="/opt/jre1.8.0/bin/java"
#Java Options - Replace with options that are sane and stable for your server
JAVAOPTS="-Xmx1024M -jar"

# determine whether or not Minecraft is already running
RUNNING=`screen -ls | grep minecraft`
cd $LOCATION

case "$1" in
        "start")
                if [ "$RUNNING" = "" ]
                then
                        screen -dmS minecraft $JAVA $JAVAOPTS $MINECRAFT -o true
                fi
                ;;

        "stop")
                screen -x minecraft -p 0 -X stuff "say Stopping server! Try again later. Thanks!$(printf \\r)"
                sleep 2
                screen -x minecraft -p 0 -X stuff "stop$(printf \\r)"
                ;;

        "restart")
                screen -x minecraft -p 0 -X stuff "say Restarting server! Will be back in a few seconds. Thanks!$(printf \\r)"
                sleep 2
                screen -x minecraft -p 0 -X stuff "stop$(printf \\r)"
                RUNNING=`screen -ls | grep minecraft`
                until [ "$RUNNING" = "" ]
                do
                        RUNNING=`screen -ls | grep minecraft`
                done
                screen -dmS minecraft $JAVA $JAVAOPTS $MINECRAFT nogui
                ;;

        "view")
                screen -x minecraft
                ;;

        "sv")
                if [ "$RUNNING" = "" ]
                then
                        screen -dmS minecraft $JAVA $JAVAOPTS $MINECRAFT nogui
                fi
                sleep 1
                screen -x minecraft
                ;;

        *)
                echo "Usage: $0 {start|stop|restart|view|sv(start & view)}"
                ;;

        esac

exit 0
```

When the computer reboots, the script doesn't start. However starting it manually works! What's wrong?
```
root@gan:~# screen -ls
No Sockets found in /var/run/screen/S-root.

root@gan:~# service minecraft start
root@gan:~# screen -ls
There is a screen on:
        4100.minecraft  (11/08/2014 12:00:19 PM)        (Detached)
1 Socket in /var/run/screen/S-root.
```

---

### Post by geohei on 2014-11-08
Forgot ...

```
update-rc.d minecraft defaults
```

Sorry !!!

---

### Post by Bucky Ball on 2014-11-08
*Thread moved to **Server Platforms**.*

---

