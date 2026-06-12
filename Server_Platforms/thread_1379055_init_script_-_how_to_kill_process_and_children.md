---
title: "init script - how to kill process and children?"
date: 2010-01-12
forum: Server Platforms
---

### Post by djeyewater on 2010-01-12
I have an init script for starting php-fcgi using spawn-fcgi on CentOS, and I'm trying to make it work on Ubuntu.

I can get php to start using the script, but it won't kill the processes when I tell it to stop. I'm using Ubuntu 9.10, the script looks like this:
```
#!/bin/sh
#
# fcgi     Startup script for fcgi
#
# processname: fcgi
# Taken from http://redmine.lighttpd.net/projects/lighttpd/wiki/Example:fastcgiCentosInitScript

# Source function library
. /lib/lsb/init-functions

FCGI_DAEMON="/home/djeyewater/webapps/spawn-fcgi/bin/spawn-fcgi" 
FCGI_PROGRAM="/home/djeyewater/webapps/php_fcgi/bin/php-cgi"
FCGI_SOCKET="/home/djeyewater/webapps/spawn-fcgi/php-fastcgi.sock" 
FCGI_PIDFILE="/home/djeyewater/webapps/spawn-fcgi/spawn-fcgi.pid"
PHP_FCGI_CHILDREN=2
PHP_FCGI_MAX_REQUESTS=500
prog="fcgi" 

export PHP_FCGI_CHILDREN PHP_FCGI_MAX_REQUESTS

RETVAL=0

start() {
        echo -n $"Starting $prog: " 
        $FCGI_DAEMON -s $FCGI_SOCKET -C $PHP_FCGI_CHILDREN -P $FCGI_PIDFILE -- $FCGI_PROGRAM -c /home/djeyewater/webapps/php_fcgi/lib/php.ini
        RETVAL=$?
        echo
        [ $RETVAL -eq 0 ] && touch /home/djeyewater/webapps/spawn-fcgi/$prog
        return $RETVAL
}

stop() {
        echo -n $"Stopping $prog: " 
        rm -f $FCGI_PIDFILE $FCGI_SOCKET
        killproc $FCGI_PROGRAM
        RETVAL=$?
        echo
        [ $RETVAL -eq 0 ] && rm -f /home/djeyewater/webapps/spawn-fcgi/$prog
        return $RETVAL
}

case "$1" in
        start)
                start
                ;;
        stop)
                stop
                ;;
        restart)
                stop
                start
                ;;
        condrestart)
                if [ -f /home/djeyewater/webapps/spawn-fcgi/$prog ]; then
                        stop
                        start
                fi
                ;;
        *)
                echo $"Usage: $0 {start|stop|restart|condrestart}" 
                RETVAL=1
esac

exit $RETVAL
```
Can anyone advise me on how to modify the script to get stop working?

Thanks

Dave

---

