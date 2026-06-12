---
title: "Danted not starting at bootup/startup (SOLVED)"
date: 2009-02-02
forum: Server Platforms
---

### Post by kbutcher5 on 2009-02-02
I couldn't type in this thread, as it is locked: [http://ubuntuforums.org/showthread.php?t=660937](http://ubuntuforums.org/showthread.php?t=660937)
So i am typing the answer here.

What you have to do to fix it, is rather simple:
```

update-rc.d -f danted remove { this removes dante from the startup queue
update-rc.d danted start 99 2 3 4 5 . stop 99 0 1 6 . { this inserts dante into the startup queue, with a high revision number

```
The problem is namely, that dante boots up way too fast for the network units to follow, and dante NEEDS the defined interfaces up, or it simply doesn't start.
So to be absolutely sure, that dante get's all the time it needs, you put a sleep on it.
This is done like this:
Open up /etc/init.d/danted.conf with your favorite editor and find this (note that the arrow is where i inserted the sleep command):
```

case "$1" in
  start)
        echo -n "Starting $DESC: "
------> sleep 60
        touch_pidfile
        start-stop-daemon --start --quiet --pidfile $PIDFILE \
                --exec $DAEMON -- -D
        echo "$NAME."
        ;;

```
Sleep 60 = 60 seconds = 1 minute

---

### Post by kbutcher5 on 2009-02-04
If anyone needs a how to, to set up dante, then here is a guide that works great as a reference:
[http://lukedoomer.blogspot.com/2008/04/set-up-socks-5-server-on-ubuntu.html](http://lukedoomer.blogspot.com/2008/04/set-up-socks-5-server-on-ubuntu.html)

---

