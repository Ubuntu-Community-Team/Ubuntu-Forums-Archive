---
title: "Setting up ccxstream as a daemon."
date: 2007-06-29
forum: Server Platforms
---

### Post by EnterDaMatrix on 2007-06-29
[http://sourceforge.net/project/showfiles.php?group_id=87054&package_id=97904](http://sourceforge.net/project/showfiles.php?group_id=87054&package_id=97904)

I have a small server in my basement that I use to stream to my computer (NFS) and ftp. Ccxstream is used to stream media to the Xbox Media Center (XBMC) over the Xbox Media Streaming Protocol (XBMSP). I have successfully compiled and ran ccxstream on my server over ssh and it works wonderfully. How can I set it up to automatically start as a daemon like my ftp and nfs services do?

---

### Post by PaulFr on 2007-06-29
If you want to start it up at boot time and not based on requests, then have a look at **/etc/init.d/cron**. I would suggest you
```
1. sudo cp /etc/init.d/cron /etc/init.d/ccxstream
2. sudo vim /etc/init.d/ccxstream
      <edit /etc/init.d/ccxstream to:
         - change all references to /usr/sbin/cron to <path to ccxstream>,
         - add any command line parameters needed
         - change all references to /var/run/crond.pid to /var/run/ccxstream.pid, and
         - remove LSBNAMES and $LSBNAMES references>
3. sudo ln /etc/rc2.d/S99ccxstream /etc/init.d/ccxstream
``` Instead of /etc/init.d/cron, you can use any simple script in /etc/init.d to do the steps above.

---

### Post by EnterDaMatrix on 2007-06-29
Thanks, this was very helpful. One problem though:

When I try to start the daemon, I get this error:

```
 sudo /etc/init.d/ccxstream start
 * Starting XBMSP server ccxstream
start-stop-daemon: invalid option -- f

```

I can't find where that would be wrong. The -f parameter tells ccxstream to fork to a background process. This seems logical. I haven't tried without the -f. Here is my init file:

```
#!/bin/sh
# Start/stop the ccxstream daemon.
#
### BEGIN INIT INFO
# Provides:          ccxstream
# Required-Start:    $syslog $time
# Required-Stop:     $syslog $time
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: XBMSP server
# Description:       ccxstream streams media to a modified Xbox using Xbox Media Center.
#                    The protocol is faster and more stable than XBMC's Samba integration
### END INIT INFO


test -f /usr/sbin/ccxstream || exit 0

. /lib/lsb/init-functions

case "$1" in
start)  log_daemon_msg "Starting XBMSP server" "ccxstream"
        start-stop-daemon --start --quiet --pidfile /var/run/ccxstream.pid --name ccxstream --startas /usr/sbin/ccxstream -f -F /var/run/ccxstream.pid -r /media/files
        log_end_msg $?
        ;;
stop)   log_daemon_msg "Stopping XBMSP server" "ccxstream"
        start-stop-daemon --stop --quiet --pidfile /var/run/ccxstream.pid --name ccxstream
        log_end_msg $?
        ;;
restart) log_daemon_msg "Restarting XBMSP server" "ccxstream"
        start-stop-daemon --stop --retry 5 --quiet --pidfile /var/run/ccxstream.pid --name ccxstream
        start-stop-daemon --start --quiet --pidfile /var/run/ccxstream.pid --name ccxstream --startas /usr/sbin/ccxstream -f -F /var/run/ccxstream.pid -r /media/files
        log_end_msg $?
        ;;
reload|force-reload) log_daemon_msg "Reloading configuration for XBMSP server" "ccxstream"
        # ccxstream reloads automatically
        log_end_msg 0
        ;;
*)      log_action_msg "Usage: /etc/init.d/ccxstream {start|stop|restart|reload|force-reload}"
        exit 2
        ;;
esac
exit 0

```

Oh, also I had to touch the S99ccxstream file because ln gave a does not exist error.

---

### Post by PaulFr on 2007-06-29
1. start-stop-daemon's man page states: Any arguments given after -- on the command line are passed unmodified to the program  being started.

So please introduce **--** (two dashes) before the ccxstream arguments.

```
start-stop-daemon ... --startas /usr/sbin/ccxstream -f -F /var/ru...
``` to
```
start-stop-daemon ... --startas /usr/sbin/ccxstream **--** -f -F /var/ru...
```

2. I apologize - I gave you the wrong command line. Please remove /etc/rc2.d/S99ccxstream and run the command ```
sudo ln -s /etc/init.d/ccxstream /etc/rc2.d/S99ccxstream
``` Hope this helps.

---

### Post by EnterDaMatrix on 2007-07-02
Thank you. After these steps it works flawlessly. The speeds to xbox are awesome, and it is extremely stable.

---

