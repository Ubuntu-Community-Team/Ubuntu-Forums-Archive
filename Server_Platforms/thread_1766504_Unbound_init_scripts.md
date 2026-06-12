---
title: "Unbound init scripts"
date: 2011-05-24
forum: Server Platforms
---

### Post by dorivard on 2011-05-24
Server info:

lsb_release -a
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.2 LTS
Release:	10.04
Codename:	lucid

Hi everyone,

I have a little issue here and I can't find what is the problem.
I wrote a script to add under /etc/init.d/ 

I usually use it this way:

/etc/init.d/unbound-edges (start|stop|restart)

What the script does is not really complicated, it's starting 3 instances of unbound having all their own configuration files.

I checked the /var/log/boot.log there is nothing in there that could tell me there is a fault while booting.
I can use the script to start the instances manually without a problem. The script does work manually for all the actions.

I did some echo in the script to see in the boot.log if I was hitting the script yes I see my prints into boot.log.

When I ran the command "update-rc.d unbound-edges defaults" it is returning:


update-rc.d: warning: /etc/init.d/unbound-edges missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 System start/stop links for /etc/init.d/unbound-edges already exist.

After a little googleling it seems the LSB compliances should not cause any problems. 

this is the script :



```

#!/bin/sh
# Start/stop/restart unbound-edge.

# Globals
EDGE_ARGU="Unbound Edge Number (1,2,3 or all)"
DESC="Edge Server"
DAEMON="/usr/sbin/unbound"

# See if the program is there at all.
if [ ! -f $DAEMON ]; then
	echo "Error - program is not installed. >&2"
	exit 5
fi

# Start the unbound_edge daemon:
unbound_edge_start() {
	if [ ! `id -u` = 0 ]; then
		echo "Error - insufficient privilege."
		exit 4
	fi
	if [ -x $DAEMON ]; then
		kill -0 `cat $PIDFILE 2> /dev/null` > /dev/null 2>&1
		if [ $? = 0 ]; then
			echo "$NAME program is running or service is OK."
			#exit 0 # if we leave the exit 0 it stop trying to start the others edges
		else
			echo "Starting $DESC"
			$DAEMON $DAEMON_OPTS
		fi
	else
		echo "Error - $DAEMON is not executeable. >&2"
		exit 6
	fi
}

# Stop stop the service:
unbound_edge_stop() {
	if [ ! `id -u` = 0 ]; then
		echo "Error - insufficient privilege."
		exit 4
	fi
	# I would just `killall unbound_edge' but the specs will not let me <bummer>.
	ps ax | grep "$PROCESS" > /dev/null
	if [ $? = 0 ]; then
		echo "Stopping $NAME daemon."
		kill -1 `cat $PIDFILE 2> /dev/null` > /dev/null 2>&1
		sleep 1
		kill -15 `cat $PIDFILE 2> /dev/null` > /dev/null 2>&1
		sleep 1
		# About time, for pulling out the big gun :-)
		kill -9 `cat $PIDFILE 2> /dev/null` > /dev/null 2>&1
	else
		echo "Program does not seem to be running."
		#exit 0
	fi
}

# Stop and restart the service if the service is already running,
# otherwise start the service:
unbound_edge_restart() {
	unbound_edge_stop
	sleep 1
	unbound_edge_start
}

# Print print the current status of the service:
unbound_edge_status() {
	echo -n "Status $NAME daemon: "
	# Only check for `grep', if they lack `ps' they have bigger problems.
	if ! command -v grep > /dev/null 2>&1; then
		echo "Program or service status is unknown."
		exit 4
	fi
	ps ax | grep "$PROCESS" > /dev/null
	if [ $? = 0 ]; then
		echo "program is running or service is OK."
		#exit 0
	else
		if [ -f $PIDFILE ]; then
			echo "program is dead and $PIDFILE file exists."
			exit 1
		else
			echo "program is stopped."
			exit 3
		fi
	fi
}

case "$1" in
	'start')
	  if [ "$2" = "all" -o "$2" = "" ]; then
	    for edge in 1 2 3
	    do
	      #
        # This part should be the only one to change to write another init script
        #
        EDGE_NUMBER="$edge"
        NAME="unbound-edge-$EDGE_NUMBER"
        PROCESS="[u]nbound-edge-$EDGE_NUMBER"
        CONF="/etc/unbound/unbound-edge-$EDGE_NUMBER.conf"
        PIDFILE="/var/run/unbound-edge-$EDGE_NUMBER.pid"
        DAEMON_OPTS="-c $CONF"
        #
        # end of the editable part
        #
        unbound_edge_start
	    done
	    exit 0
		  REVAL=$?
	  else
	    RESULT=$(echo $2 | egrep ^[[:digit:]]+$)
	    if [ "$RESULT" != "" ]; then
	      #
        # This part should be the only one to change to write another init script
        #
        EDGE_NUMBER="$2"
        
        NAME="unbound-edge-$EDGE_NUMBER"
        PROCESS="[u]nbound-edge-$EDGE_NUMBER"
        CONF="/etc/unbound/unbound-edge-$EDGE_NUMBER.conf"
        PIDFILE="/var/run/unbound-edge-$EDGE_NUMBER.pid"
        DAEMON_OPTS="-c $CONF"
        #
        # end of the editable part
        #
        unbound_edge_start
        exit 0
		    REVAL=$?
		  else
		    echo "Please specify the $EDGE_ARGU"
		  fi
	  fi
		;;
	'stop')
		if [ "$2" = "all" -o "$2" = "" ]; then
	    for edge in 1 2 3
	    do
	      #
        # This part should be the only one to change to write another init script
        #
        EDGE_NUMBER="$edge"
        NAME="unbound-edge-$EDGE_NUMBER"
        PROCESS="[u]nbound-edge-$EDGE_NUMBER"
        CONF="/etc/unbound/unbound-edge-$EDGE_NUMBER.conf"
        PIDFILE="/var/run/unbound-edge-$EDGE_NUMBER.pid"
        DAEMON_OPTS="-c $CONF"
        #
        # end of the editable part
        #
        unbound_edge_stop
	    done
	    exit 0
	    REVAL=$?
	  else
	    RESULT=$(echo $2 | egrep ^[[:digit:]]+$)
	    if [ "$RESULT" != "" ]; then
	      #
        # This part should be the only one to change to write another init script
        #
        EDGE_NUMBER="$2"
        
        NAME="unbound-edge-$EDGE_NUMBER"
        PROCESS="[u]nbound-edge-$EDGE_NUMBER"
        CONF="/etc/unbound/unbound-edge-$EDGE_NUMBER.conf"
        PIDFILE="/var/run/unbound-edge-$EDGE_NUMBER.pid"
        DAEMON_OPTS="-c $CONF"
        #
        # end of the editable part
        #
        unbound_edge_stop
        exit 0
		    REVAL=$?
		  else
		    echo "Please specify the $EDGE_ARGU"
		  fi
	  fi
		;;
	'restart')
		if [ "$2" = "all" -o "$2" = "" ]; then
	    for edge in 1 2 3
	    do
	      #
        # This part should be the only one to change to write another init script
        #
        EDGE_NUMBER="$edge"
        NAME="unbound-edge-$EDGE_NUMBER"
        PROCESS="[u]nbound-edge-$EDGE_NUMBER"
        CONF="/etc/unbound/unbound-edge-$EDGE_NUMBER.conf"
        PIDFILE="/var/run/unbound-edge-$EDGE_NUMBER.pid"
        DAEMON_OPTS="-c $CONF"
        #
        # end of the editable part
        #
        unbound_edge_restart
	    done
	    exit 0
	    REVAL=$?
	  else
	    RESULT=$(echo $2 | egrep ^[[:digit:]]+$)
	    if [ "$RESULT" != "" ]; then
	      #
        # This part should be the only one to change to write another init script
        #
        EDGE_NUMBER="$2"
        
        NAME="unbound-edge-$EDGE_NUMBER"
        PROCESS="[u]nbound-edge-$EDGE_NUMBER"
        CONF="/etc/unbound/unbound-edge-$EDGE_NUMBER.conf"
        PIDFILE="/var/run/unbound-edge-$EDGE_NUMBER.pid"
        DAEMON_OPTS="-c $CONF"
        #
        # end of the editable part
        #
        unbound_edge_restart
        exit 0
		    REVAL=$?
		  else
		    echo "Please specify the $EDGE_ARGU"
		  fi
	  fi
		;;
	'status')
		if [ "$2" = "all" -o "$2" = "" ]; then
	    for edge in 1 2 3
	    do
	      #
        # This part should be the only one to change to write another init script
        #
        EDGE_NUMBER="$edge"
        NAME="unbound-edge-$EDGE_NUMBER"
        PROCESS="[u]nbound-edge-$EDGE_NUMBER"
        CONF="/etc/unbound/unbound-edge-$EDGE_NUMBER.conf"
        PIDFILE="/var/run/unbound-edge-$EDGE_NUMBER.pid"
        DAEMON_OPTS="-c $CONF"
        #
        # end of the editable part
        #
        unbound_edge_status
	    done
	    exit 0
	    REVAL=$?
	  else
	    RESULT=$(echo $2 | egrep ^[[:digit:]]+$)
	    if [ "$RESULT" != "" ]; then
	      #
        # This part should be the only one to change to write another init script
        #
        EDGE_NUMBER="$2"
        
        NAME="unbound-edge-$EDGE_NUMBER"
        PROCESS="[u]nbound-edge-$EDGE_NUMBER"
        CONF="/etc/unbound/unbound-edge-$EDGE_NUMBER.conf"
        PIDFILE="/var/run/unbound-edge-$EDGE_NUMBER.pid"
        DAEMON_OPTS="-c $CONF"
        #
        # end of the editable part
        #
        unbound_edge_status
        exit 0
		    REVAL=$?
		  else
		    echo "Please specify the $EDGE_ARGU"
		  fi
	  fi
		;;
	*)
		# Invalid or excess argument(s).
		echo "Usage: $0 start|stop|restart|reload|force-reload|status"
		REVAL=2
esac

```

I just don't see why it is not booting on startup.

Thank you.

---

### Post by Toz on 2011-05-24
> **dorivard said:**
> 
When I ran the command "update-rc.d unbound-edges defaults" it is returning:


update-rc.d: warning: /etc/init.d/unbound-edges missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
update-rc.d has two execution modes. The mode you used requires the presence of an LSB header script to instruct it how to create the necessary links. Have a look at [http://wiki.debian.org/LSBInitScripts](http://wiki.debian.org/LSBInitScripts) for information about creating an LSB header script (or look at existing scripts in /etc/init.d). The other mode allows you to manually create the startup scripts ala:```
update-rc.d unbound-edges start 99 2 3 4 5 . stop 99 0 1 6 .
```Have a look at **man update-rc.d** for a complete description.


> System start/stop links for /etc/init.d/unbound-edges already exist.
What does the following command return?```
ls -l /etc/rc* | grep -i unbound-edges
```

---

### Post by dorivard on 2011-05-24
The command returns:


```

ls -l /etc/rc* | grep -i unbound-edges
lrwxrwxrwx 1 root root  23 2011-05-12 10:16 K20unbound-edges -> ../init.d/unbound-edges
lrwxrwxrwx 1 root root  23 2011-05-12 10:16 K20unbound-edges -> ../init.d/unbound-edges
lrwxrwxrwx 1 root root  23 2011-05-12 10:16 S20unbound-edges -> ../init.d/unbound-edges
lrwxrwxrwx 1 root root  23 2011-05-12 10:16 S20unbound-edges -> ../init.d/unbound-edges
lrwxrwxrwx 1 root root  23 2011-05-12 10:16 S20unbound-edges -> ../init.d/unbound-edges
lrwxrwxrwx 1 root root  23 2011-05-12 10:16 S20unbound-edges -> ../init.d/unbound-edges
lrwxrwxrwx 1 root root  23 2011-05-12 10:16 K20unbound-edges -> ../init.d/unbound-edges

```

from a cat /var/log/boot.log I retrieve these lines

```

Starting DVDNS Edge Server
Starting DVDNS Edge Server
Starting DVDNS Edge Server

```

then when the computer is restarted if I do "ps ax | grep unbound" I get none of them.

I also tried the command line you suggested "update-rc.d unbound-edges start 99 2 3 4 5 . stop 99 0 1 6 ."
```

update-rc.d: warning: /etc/init.d/unbound-edges missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 System start/stop links for /etc/init.d/unbound-edges already exist.

```

Reboot and still no go with my script, but still see the boot.log with the same entries as previously.

I'll look at adding the LSB init script requirements, but I supposed it will take me some times

Thank you for the help.

---

### Post by Toz on 2011-05-24
Hold off on the LSB script headers for a bit. What does:```
locate S20unbound-edges
```return?

Also, does this program require that other services (ie. networking) be up and running first?

---

### Post by dorivard on 2011-05-24
It does require unbound core service to be started but this one is started and start before the script is even launched as per what I can see in the boot.log

the command return:
```

locate S20unbound-edges
/etc/rc2.d/S20unbound-edges
/etc/rc3.d/S20unbound-edges
/etc/rc4.d/S20unbound-edges
/etc/rc5.d/S20unbound-edges

```

Here is the cat /var/log/boot.log
```

/dev/sda1: clean, 72345/464208 files, 541295/1855232 blocks (check in 4 mounts)
 * Starting AppArmor profiles                                            [ OK ] 
   Checking acpi hot plug                                              done
Starting VMware Tools services in the virtual machine:
   Switching to guest configuration:                                   done
   Guest operating system daemon:                                      done
   Virtual Printing daemon:                                            done
 * Starting recursive DNS server unbound                                 [ OK ] 
Starting DVDNS Edge Server
Starting DVDNS Edge Server
Starting DVDNS Edge Server

```

Just to mention we already tried to move the init script later on,
we at some point put it to start /etc/rc2.d/S99unbound-edges but it didn't give us any success.

Thank you!

---

### Post by Toz on 2011-05-24
What I find really interesting is that if you run the script manually then it works. If you use the init scripts it doesn't. To me this says that although the script itself is fine, something is preventing it from executing properly during the init phase. I would have to say that something else hasn't initialized properly yet and then this script, although it runs, fails (possibly the core services haven't fully initialized yet?). Two suggestions:

1. Add a sleep command to the beginning of the init script. Start with sleep 60s to have it wait 60 seconds before it executes. There has to be something that it is dependent on that hasn't initiated yet. If it works with 60s, start decreasing the value until the find the "sweet spot".

2. The ubound command can take a -v parameter to be more verbose. I would suggest adding -vvv to the command to see if it spits out some more info. Change the line```
DAEMON="/usr/sbin/unbound"
``` to read:```
DAEMON="/usr/sbin/unbound -vvv"
``` and see if there is more info in the log files as to why its failing.

---

### Post by dorivard on 2011-05-25
@Toz: thank you for the help it is really appreciated.

I found in the /var/log/syslog a line after setting it up to the verbose mode that looks like this : 

```

May 24 16:05:49 1-dns-slave unbound: [845:0] error: pythonmod: cannot initialize core module: unboundmodule.py

```

What I did after that was to put /usr/bin/printenv at top of the script and then I compare which environment variables were not set between the boot and the manual launch of the script 

After the comparison I added at the beginning of the script all the missing environments variables and now it is starting while booting.

Thank you.

---

