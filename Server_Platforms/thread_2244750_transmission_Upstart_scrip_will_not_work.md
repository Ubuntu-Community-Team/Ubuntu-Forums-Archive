---
title: "transmission Upstart scrip will not work"
date: 2014-09-18
forum: Server Platforms
---

### Post by jpaytoncfd on 2014-09-18
I have transmission installed but when I try to start it with upstart ```
sudo service transmission-daemon start
``` it fails to read the config file. If I remove the config file it will start but it will not write a new settings file. theres a permission error. 

If I run transmission from the command line it work fine and if I call the init script directly it works great too. It only wont work when I run it with service start. I'm not really sure where to start. It runs as my primary user, all the permission should be fine but I tried changing ownership and setting everything to 777. 

Can anyone tell me where to look next?

```
#!/bin/sh -e### BEGIN INIT INFO
# Provides:          transmission-daemon
# Required-Start:    $local_fs $remote_fs $network
# Required-Stop:     $local_fs $remote_fs $network
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start or stop the transmission-daemon.
# Description:       Enable service provided by transmission-daemon.
### END INIT INFO


NAME=transmission-daemon
DAEMON=/usr/bin/$NAME
USER=xbmc
STOP_TIMEOUT=30


export PATH="${PATH:+$PATH:}/sbin"


[ -x $DAEMON ] || exit 0


[ -e /etc/default/$NAME ] && . /etc/default/$NAME


. /lib/lsb/init-functions


start_daemon () {
    if [ $ENABLE_DAEMON != 1 ]; then
        log_progress_msg "(disabled)"
        log_end_msg 255 || true
    else    
        start-stop-daemon --start \
        --chuid $USER \
        $START_STOP_OPTIONS \
        --exec $DAEMON -- $OPTIONS || log_end_msg $?
        log_end_msg 0
    fi
}


case "$1" in
    start)
        log_daemon_msg "Starting bittorrent daemon" "$NAME"
        start_daemon
        ;;
    stop)
        log_daemon_msg "Stopping bittorrent daemon" "$NAME"
        start-stop-daemon --stop --quiet \
            --exec $DAEMON --retry $STOP_TIMEOUT \
            --oknodo || log_end_msg $?
        log_end_msg 0
        ;;
    reload)
        log_daemon_msg "Reloading bittorrent daemon" "$NAME"
        start-stop-daemon --stop --quiet \
            --exec $DAEMON \
            --oknodo --signal 1 || log_end_msg $?
        log_end_msg 0
        ;;
    restart|force-reload)
        log_daemon_msg "Restarting bittorrent daemon" "$NAME"
        start-stop-daemon --stop --quiet \
            --exec $DAEMON --retry $STOP_TIMEOUT \
            --oknodo || log_end_msg $?
        start_daemon
        ;;
    status)
        status_of_proc "$DAEMON" "$NAME" && exit 0 || exit $?
        ;;
    *)
        log_action_msg "Usage: /etc/init.d/$NAME {start|stop|reload|force-reload|restart|status}" || true
        exit 2
        ;;
esac


exit 0

```

---

