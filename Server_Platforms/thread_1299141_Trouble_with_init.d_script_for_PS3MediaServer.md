---
title: "Trouble with init.d script for PS3MediaServer"
date: 2009-10-23
forum: Server Platforms
---

### Post by cheddercaveman on 2009-10-23
Here is my script that I'm using...

```
#!/bin/sh

DIRNAME="/usr/local/src/ps3mediaserver-read-only/ps3mediaserver"
cd $DIRNAME

PMS_PIDFILE=/var/run/pms.pid
DESC="PS3 media server"
DAEMON=/usr/local/src/ps3mediaserver-read-only/ps3mediaserver/PMS.sh
NAME="ps3mediaserver"

case "$1" in
start)
start-stop-daemon --start -b -m --pidfile $PMS_PIDFILE --exec $DAEMON
;;
stop)
start-stop-daemon -K --pidfile $PMS_PIDFILE
;;
restart)
$0 stop
$0 start
;;
*)
echo "Usage: /etc/init.d/$NAME start|stop|restart}"
exit 1
;;

esac

```

I know that the PMS.sh is working fine, because I can kick it off manually, however I can not get it to actually start with any of the following...

```
sudo service ps3mediaserver start
```
```
sudo /etc/init.d/ps3mediaserver start
```

I ran this also after creating the file...
```
sudo update-rc.d ps3mediaserver defaults
```

I have another machine that is running that is using essentially the exact same script, only the files are in another location /home/user/ps3mediaserver-read-only/ps3mediaserver/ on that machine.

This machine is running Ubuntu Server 9.04 AMD64 for further reference.  I definitely am looking for any advice here on what might be going on, or if I maybe need to refresh anything, etc.

---

### Post by cheddercaveman on 2009-10-24
Shameless Bump?

---

