---
title: "Pureftpd and umask"
date: 2007-04-22
forum: Server Platforms
---

### Post by darkrad on 2007-04-22
Hello, i need to change the permission of the files created by an ftpuser of pureftd. Actually it's:

-rw-r--r--
i need to change it to:
-rw-rw-r--
since i wish to access to the upped file with an username of the same group of the ftp user.

I read the documentation and i'm supposed to edit the umask setting.. but i don't know where to change it since pureftpd starts automatically so i can't even edit the command line to add the umask attribute.
Any help is greatly appreciated
Thanks

---

### Post by darkrad on 2007-04-22
the following is the startup script of /etc/init.d/pure-ftpd, maybe can help


```
#! /bin/sh
#
# pure-ftpd     starts and stops the pure-ftpd ftp daemon

PATH=/sbin:/bin:/usr/sbin:/usr/bin
NAME=pure-ftpd
DESC="ftp server"
: ${SSDAEMONLOGOPTS:="--quiet"}
UPLOADDAEMON=/usr/sbin/pure-uploadscript
UDNAME=pure-uploadscript
UDDESC="ftp upload handler"
WRAPPER=/usr/sbin/pure-ftpd-wrapper

# try to figure with suffix this script is called,
# $0 might be a symlink pointing to this script
if [ -h $0 ]; then
        ME=`/bin/readlink $0`
else
        ME=$0
fi

SUFFIX=`basename $ME | sed -ne 's/^pure-ftpd-\(.*\)/\1/p'`
if [ "$SUFFIX" ] ; then
        DAEMON=/usr/sbin/pure-ftpd-$SUFFIX
else
        DAEMON=/usr/sbin/pure-ftpd
fi

export STANDALONE_OR_INETD=inetd
export VIRTUALCHROOT=
test -r /etc/default/pure-ftpd-common && . /etc/default/pure-ftpd-common

if [ "$VIRTUALCHROOT" = "true" ]; then
        if [ "$SUFFIX" ]; then
                SUFFIX="$SUFFIX-virtualchroot"
        else
                SUFFIX="virtualchroot"
        fi
fi

test -x $DAEMON || exit 0
test -x $WRAPPER || exit 0

set -e

start_uploadscript() {
        if [ "$UPLOADSCRIPT" -a "$STANDALONE_OR_INETD" != inetd ] && \
                egrep -i '^[    ]*(yes|1|on)[   ]*' /etc/pure-ftpd/conf/CallUploadScript > /dev/null 2>&1
        then
                UOPTS=""
                test "$UPLOADUID" && UOPTS="$UOPTS -u $UPLOADUID"
                test "$UPLOADGID" && UOPTS="$UOPTS -g $UPLOADGID"
                echo -n "$1 $UDDESC: "
                start-stop-daemon --start $SSDAEMONLOGOPTS --oknodo \
                        --exec $UPLOADDAEMON -- -r "$UPLOADSCRIPT" -B $UOPTS
                echo "$UDNAME."

        fi
}

case "$1" in
  start)
        test "$STANDALONE_OR_INETD" = standalone || exit 0
        echo -n "Starting $DESC: "
        start-stop-daemon --start $SSDAEMONLOGOPTS --pidfile /var/run/pure-ftpd/pure-ftpd.pid \
                --exec $WRAPPER -- $SUFFIX
        start_uploadscript Starting
        ;;
  stop)
        echo -n "Stopping $DESC: "
        start-stop-daemon --stop $SSDAEMONLOGOPTS --oknodo \
                --pidfile /var/run/pure-ftpd/pure-ftpd.pid
        start-stop-daemon --stop $SSDAEMONLOGOPTS --oknodo --exec $UPLOADDAEMON
        echo "$NAME."
        ;;
  restart|force-reload)
        test "$STANDALONE_OR_INETD" = standalone || exit 0
        echo -n "Restarting $DESC: "
        start-stop-daemon --stop $SSDAEMONLOGOPTS --oknodo \
                --pidfile /var/run/pure-ftpd/pure-ftpd.pid
        start-stop-daemon --stop $SSDAEMONLOGOPTS --oknodo --exec $UPLOADDAEMON
        sleep 1
        start-stop-daemon --start $SSDAEMONLOGOPTS --pidfile \
                /var/run/pure-ftpd/pure-ftpd.pid --exec $WRAPPER -- $SUFFIX
        start_uploadscript Restarting
        ;;
  *)
        N=/etc/init.d/$NAME
        echo "Usage: $N {start|stop|restart|force-reload}" >&2
        exit 1
        ;;
esac

exit 0
```

i'm googling from hours but i really have no clue on how to modify it to add the umask thing.
please help.

---

### Post by darkrad on 2007-04-22
ok i found that i need to create Umask file into /etc/pure-ftpd/conf directory and write inside:

113 022

that is the umask for file and for dir.
113 should make a file 664 so rw for user and group, if i'm not wrong.
then i restart pure-ftp:

```
sudo /etc/init.d/pure-ftpd restart
Restarting ftp server: Running: /usr/sbin/pure-ftpd -l puredb:/etc/pure-ftpd/pureftpd.pdb -l puredb:/etc/pure-ftpd/pureftpd.pdb -u 1000 -E -U 113:022 -O clf:/var/log/pure-ftpd/transfer.log -B
```

and the -U is there so the change is taken.
But when i upload a file it's still -rw-r--r-- :confused: 
Why?

---

### Post by darkrad on 2007-04-22
hmm seems that the "restart" and "stop" command didn't anything. i had to kill the process manually and start it manually. Now attributes seems created in the right way.

---

