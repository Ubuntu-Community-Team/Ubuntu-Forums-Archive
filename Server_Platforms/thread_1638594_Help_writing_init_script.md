---
title: "Help writing init script"
date: 2010-12-05
forum: Server Platforms
---

### Post by sandyscott on 2010-12-05
Hi,

I'm trying to write a init.d script to daemonise a sagemath notebook server.

Here's what I've done so far, I've copied /etc/init.d/single for the structure, and tried to use dtach to provide a handle to access the process.

However, my main problem is issuing the signals to kill the process (Ctrl-C) from a bash script and exit dtach (Ctrl-`)

```

#! /bin/sh
### BEGIN INIT INFO
# Provides:          sagemath
# Required-Start:    $network
# Required-Stop:
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Controls the sagemath notebook server.
### END INIT INFO

PATH=/sbin:/bin

do_start () {
        log_action_msg "Starting sagemath notebook server"
        rm -f /home/sageserver/sagesocket
        dtach -c /home/sageserver/sagesocket script /dev/null
        /bin/su - sageserver -c /home/sageserver/startnotebook
        # need command to exit dtach
}

do_stop () {
        log_action_msg "Stopping sagemath notebook server"
        dtach -a /home/sageserver/sagesocket
        #need command to enter Ctrl-C
}

case "$1" in
  start)
        do_start
        ;;
  restart|reload|force-reload)
        do_stop
        do_start
        ;;
  stop)
        do_stop
        ;;
  *)
        echo "Usage: $0 start|stop|restart" >&2
        exit 3
        ;;
esac

```

I'd appreciate any suggestions to make this work - I'm not set on any particular way of doing it.

Thanks

Sandy Scott

---

### Post by rubylaser on 2010-12-06
Ctrl+c can be accomplished with...
```
kill -2 $!
``` after your sageserver calls.

Hope that helps.

---

