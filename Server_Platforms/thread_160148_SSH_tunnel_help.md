---
title: "SSH tunnel help"
date: 2006-04-14
forum: Server Platforms
---

### Post by haxx0r07 on 2006-04-14
Ok I'm creating a ssh tunnel to forward a port from a server behind a firewall to a server outside the firewall. BTW both servers are running Ubuntu 
I'm tunneling the whole network (only about 10 computers ) with a transparent squid proxy. I have everything working, but I only want to have this tunnel up for certin hours of the day. Ok I was told to use cron for this. This is where I need help, to create the tunnel out to the external server I use the command " ssh -f -N " my problem is when the time comes to shutdown the tunnel. I dont know how to do that, I can manually kill the tunnel by finding its pid and using the kill command, but I want to be able to do this with a cron file. 

Any Ideas
Thanks in advance Haxx0r07

---

### Post by cilynx on 2006-04-14
If the tunnel is the only ssh session on the machine, you can do a 'killall ssh' from cron when need be.  If it's not, use "ps aux | grep "ssh -f -N" and trim down the result with a regexp to get just the pid and kill that.  This is all done reasonably easily in a bash script.  If you need to see it out, let me know.  I figure I'll let you take a stab at it first.

---

### Post by fdoving on 2006-04-14
I would suggest doing it the Ubuntu/debian way using 'start-stop-daemon'.


Simple example:
To start:
```

start-stop-daemon --exec /usr/local/bin/script.sh --make-pidfile --pidfile /var/run/script.pid --start

```

To stop:
```

start-stop-daemon --pidfile /var/run/script.pid --signal 6 --stop

```


NOTE: By default start-stop-daemon sends signal 15 to stop processes. I've used '--signal 6' just to show you how you can send other signals if the process doesn't die on a signal 15.

For more detailed information you can read the manual page for start-stop-daemon.
```

man start-stop-daemon

```

- Frode

---

### Post by cilynx on 2006-04-14
You know...I never even though of using start-stop-daemon for stuff like this.  Many a line of perl that would have spared.  Man, I'm brilliant.  Thanks --

---

### Post by haxx0r07 on 2006-04-14
Ok I'll try using the start-stop-daemon. I won't be able to try it till I get back to school monday. So I repost how things go then.

---

### Post by haxx0r07 on 2006-04-18
The start-stop-daemon worked just like I wanted it to my only problem is what if the tunnel dosen't start the pid file is still created. So is there a way for me to make sure the tunnel is stared correctly?

This is my start script I built it off the debian skeleton script.


```
#! /bin/sh

set -e

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
NAME=ssh_tunnel
DAEMON=/usr/bin/ssh
PIDFILE=/var/run/$NAME.pid
SCRIPTNAME=/etc/init.d/$NAME

# Gracefully exit if the package has been removed.
test -x $DAEMON || exit 0

#
#       Function that starts the daemon/service.
#
d_start() {
	#Renames the shorewall rules file to redirect all local web traffic through the tunnel.
        mv /etc/shorewall/rules /etc/shorewall/rules_orgional
        mv /etc/shorewall/rules_redirect /etc/shorewall/rules
        /etc/init.d/shorewall restart

        start-stop-daemon --exec /usr/bin/ssh --make-pidfile --pidfile $PIDFILE --start  --  -f -N -l user -L \
                xxx.xxx.xxx.xxx:xxxx:xxx.xxx.xxx.xxx:xxxx -p xxx xxx.xxx.xxx.xxx || echo -n " already running"
}


#
#       Function that stops the daemon/service.
#
d_stop() {
	#Renames the shorewall to redirect all local web to the gateway.
        mv /etc/shorewall/rules /etc/shorewall/rules_redirect
        mv /etc/shorewall/rules_orgional /etc/shorewall/rules
        /etc/init.d/shorewall restart

        start-stop-daemon --pidfile $PIDFILE --stop || echo -n " not running"
}

case "$1" in
  start)
        echo -n "Starting the $NAME "
        d_start
        echo "."
        ;;
  stop)
        echo -n "Stopping the $NAME "
        d_stop
        echo "."
        ;;
  restart)
        echo -n "Restarting  the $NAME"
        d_stop
        sleep 5
        d_start
        echo "."
        ;;
  *)
        echo "Usage: $SCRIPTNAME {start|stop|restart}" >&2
        exit 3
        ;;
esac

exit 0

```

---

### Post by haxx0r07 on 2006-04-19
Anyone?

---

### Post by fvu on 2007-09-07
You can also use `ssh sleep' to start the tunnel.  The tunnel will auto-exit if you close the program utilizing the tunnel.  For example, the tunnel below will auto-close after `mysqldump' finishes:

```
#!/bin/bash
# Archive wiki

set -o errexit  # Exit on error
set -o nounset  # Trigger error when expanding unset variables

dumpfile=wiki_mysqldump.sql.gz

        # Cd to this script's dir
cd "$(dirname "$(which "$0")")"
        # Remove possible dumpfile
[ -f $dumpfile ] && rm $dumpfile   # Set up SSH tunnel.  Options:
    # -f  Background ssh
    # -L  Forward local port `3307' to remote port `localhost:3306'
    # NOTE: Remote command `sleep 9' will auto-exit tunnel if not activated within 9 seconds
ssh -f -L 3307:localhost:3306 ssh_username@ssh_hostname sleep 9
    # Dump wiki database via ssh tunnel
mysqldump --password=mypassword --host=127.0.0.1 --port=3307 --user=mysql_username --verbose wikidb | gzip -9 > $dumpfile 2>&1
```

For more information, see:
[http://www.fvue.nl/wiki/MediaWiki_database_backup_via_SSH_tunnel](http://www.fvue.nl/wiki/MediaWiki_database_backup_via_SSH_tunnel)


Freddy Vulto
[http://fvue.nl](http://fvue.nl)

---

### Post by zackr on 2008-01-23
I'm having a lot of trouble with this.

What I need instead of a database dump is an update of the remote database from the local one. 
```

#!/bin/sh
ssh -L 3307:127.0.0.1:3306 isaac@67.x.x.x -p 2321 sleep 9
mysqldump --opt bmtronics_development --host=localhost --user=... | mysql --user=... --password=... --host=127.0.0.1 --port=3307 -C bmtronics_production

```
Above is the code I'm using. The SSH authentication is fine. Everything works as it seems to run the first part of mysqldump fine. Then when it tried the second half, uploading, it says it cannot connecto to 127.0.0.1.

Now, on the remote server I have IPTables set up, but it allows the SSH tunnel. So that isn't a problem. I also have the remote database listening on 127.0.0.1. Should I check anything else on the remote mysql server?? Also, how can I be sure the tunnel is working fine and the loopback isn't all screwed up?

---

