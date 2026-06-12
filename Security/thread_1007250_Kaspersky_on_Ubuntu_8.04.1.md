---
title: "Kaspersky on Ubuntu 8.04.1"
date: 2008-12-10
forum: Security
---

### Post by ientzy on 2008-12-10
Hello,

I have Ubuntu 8.04.1 and Kaspersky 5.7-26 and I compile the Kaspersky module, he start, i check the status of antivirus and agent from Administration Tool kit from a windows workstation, he work fine until first restart. After that Agent start, but antivirus don`t start. If i try to start manually with /etc/init.d/kav4ws -start i got this error:

Cannot create pid file: /var/run/kav4ws/kavmonitor.pid: No such file or directory
kavmonitor not started: system error


I check the folder /var/run/ and I don`t find any kav4ws folder. I think the OS delete the dir.
What can be the problem? Way he delete the director?

Please help me.

Thanks.

---

### Post by hyper_ch on 2008-12-10
why do you run antivirus on linux anyway?

---

### Post by ientzy on 2008-12-10
> **hyper_ch said:**
> why do you run antivirus on linux anyway?

I need him because i use the workstation in to a company and I have license for kaspersky.

---

### Post by ilrudie on 2008-12-10
Try creating the directory (with the *mkdir* command) and then try starting the daemon.  If that still doesn't work create the pid file (with the *touch* command) and then try starting the daemon.  Let us know if this doesn't work.

---

### Post by ientzy on 2008-12-10
> **ilrudie said:**
> Try creating the directory (with the *mkdir* command) and then try starting the daemon.  If that still doesn't work create the pid file (with the *touch* command) and then try starting the daemon.  Let us know if this doesn't work.

He start but after first restart dir was deleted. Anything else?

---

### Post by ilrudie on 2008-12-10
Put a check in the init script.  If the directory doesn't exist create it.  You could also look in the config files or in the init script and change the path where the pid file is created.  You could also look in the init script for the part that removes the pid file and see if/why its removing the folder as well.

---

### Post by ientzy on 2008-12-10
> **ilrudie said:**
> Put a check in the init script.  If the directory doesn't exist create it.

I`m new in linux, i don`t know to much, like that. Can you help me?

name of dir is "kav4ws"


Thanks

---

### Post by ilrudie on 2008-12-10
Post the contents of the init script

---

### Post by ientzy on 2008-12-11
> **ilrudie said:**
> Post the contents of the init script

This script is in /etc/init.d/kas4ws?
IF is this please tell me to find him and posting here.


Thanks allot.

---

### Post by ilrudie on 2008-12-11
The script is /etc/init.d/kas4ws.  Just run 'cat /etc/init.d/kas4ws' and copy the output.

---

### Post by ientzy on 2008-12-12
```
#!/bin/sh

# Basic support for IRIX style chkconfig
# chkconfig: 2345 50 30
# description: Kaspersky Anti-Virus on-access scanner

### BEGIN INIT INFO
# Required-Start: $syslog
# Default-Start: 2 3 5
# Default-Stop:  0 1 6
# Description: Kaspersky Anti-Virus on-access scanner
### END INIT INFO

BIN='/opt/kaspersky/kav4ws/sbin/kav4ws-kavmonitor'
CONF='/etc/opt/kaspersky/kav4ws.conf'

if [ -s $CONF ] ; then
    PID_FILE=`awk '{if($1 ~/monitor.path/){sec="monitor"}; if($1 ~/^\s*PidFile/ && sec=="monitor") {print $1; sec=""}}' "$CONF" </dev/null | cut -d'=' -f2`
fi

rc=0

rc() {
    err=""
    case $rc in
    0)
	;;
    30)
	err="system error"
	;;
    64)
	err="license error" 
	;;
    65)
	err="configuration file could not found"
	;;
    66)
        err="error configuration parameter"
	;;
    70)
        err="the component is damaged"
	;;
    ### Additional error codes
    120)
	err="pid file not found"
	;;
    121)
	err="probably is dead but pid file not deleted"
	;;
    122)
	err="pid file is empty"
	;;
    123)
	err="operation timeout"
	;;
    201)
	err="signal sending error"
	;;
    *)
	err="unknown code $rc"
    esac
    if [ -n "$err" ] ; then
	if [ -n "$1" ] ; then
	    echo "$1: $err"
	else
	    echo "$err"
	fi
    fi
}

get_kavpid() {
    if [ -s "$CONF" ] ; then
	if [ -n "$PID_FILE" -a -f "$PID_FILE" ] ; then
    	    PID=`head "$PID_FILE" 2> /dev/null`
	    if [ -z "$PID" ] ; then
		# echo "pid file is empty"
		return 122
	    fi
    	    echo $PID
    	    return 0
	else
    	    # echo "pid file not found"
	    return 120
	fi
    else
        # echo "Config file not found"
        return 65
    fi
}

start() {	
    if [ -x $BIN ];then
	if $0 status >/dev/null ; then
	    echo 'kavmonitor already started'
	    rc=0
	else
	    ${BIN} -C "${CONF}"
	    rc=$?
	    if [ $rc -eq 0 ] ; then
		echo 'kavmonitor started'
	    else
		rc "kavmonitor not started"
	    fi
	fi
    else
	echo "$BIN was not found"
	rc=5
    fi
}
	
stop() {
    if $0 status >/dev/null ; then
	PID=`get_kavpid`
	rc=$?
	if [ $rc -eq 0 ] ; then
	    if kill "$PID"
	    then
		wait=0
		while [ -f "$PID_FILE" -a $wait -le 30 ]; do
		    sleep 1
		    wait=$(($wait + 1))
		done
		if [ -f "$PID_FILE" ] ; then
		    rc=123
		fi
	    else
		rc=201
	    fi	
	fi

        if [ $rc -eq 0 ] ; then
    	    echo 'kavmonitor stopped'
	else
	    rc "kavmonitor could not be stopped"
        fi
    else
	echo 'kavmonitor already stopped'
	rc=0
    fi

    return $rc
}	

restart() {
    stop
    start
}	  
	
reload() {
    PID=`get_kavpid`
    rc=$?
    if [ $rc -eq 0 ] ; then
	if ! kill -HUP "$PID" 2>/dev/null 
	then
	    rc=201
        fi
    fi
    if [ $rc -eq 0 ] ; then
	echo 'kavmonitor reloaded'
    else
	rc "kavmonitor could not be reloaded"
    fi
    return $rc
}	  

reload_avbase() {
    PID=`get_kavpid`
    rc=$?
    if [ $rc -eq 0 ] ; then
	if ! kill -USR1 "$PID" 2>/dev/null
	then
	    rc=201
        fi
    fi
    if [ $rc -eq 0 ] ; then
	echo 'kavmonitor AV bases reloaded'
    else
        rc "kavmonitor could not reload AV bases"
    fi
    return $rc
}

status() {
    pid=`get_kavpid`
    rc=$?
    if [ $rc -eq 0 ] ; then
	kill -0 "$pid" 2>/dev/null
	if test $? -eq 0 ; then
	    status="running"
	    rc=0
	else
	    status="dead"
	    rc=1
	fi
    else
	status="stopped"
	rc=3
    fi
    echo "Kaspersky Anti-Virus on access scanner is $status."
}

case "$1" in

start)
    start
    ;;
stop)
    stop
    ;;
status)
    status
    ;;
restart)
    restart
    ;;
reload)
    reload
    ;;
reload_avbase)
    reload_avbase
    ;;	
*)
    echo "Usage: `basename $0` {start|stop|status|restart|reload|reload_avbase}" >&2
    exit 1
    ;;
esac

exit $rc
```

---

### Post by ilrudie on 2008-12-15
> **ientzy said:**
> ```
#!/bin/sh

# Basic support for IRIX style chkconfig
# chkconfig: 2345 50 30
# description: Kaspersky Anti-Virus on-access scanner

### BEGIN INIT INFO
# Required-Start: $syslog
# Default-Start: 2 3 5
# Default-Stop:  0 1 6
# Description: Kaspersky Anti-Virus on-access scanner
### END INIT INFO

BIN='/opt/kaspersky/kav4ws/sbin/kav4ws-kavmonitor'
CONF='/etc/opt/kaspersky/kav4ws.conf'

if [ -s $CONF ] ; then
    PID_FILE=`awk '{if($1 ~/monitor.path/){sec="monitor"}; if($1 ~/^\s*PidFile/ && sec=="monitor") {print $1; sec=""}}' "$CONF" </dev/null | cut -d'=' -f2`
fi

rc=0

rc() {
    err=""
    case $rc in
    0)
    ;;
    30)
    err="system error"
    ;;
    64)
    err="license error" 
    ;;
    65)
    err="configuration file could not found"
    ;;
    66)
        err="error configuration parameter"
    ;;
    70)
        err="the component is damaged"
    ;;
    ### Additional error codes
    120)
    err="pid file not found"
    ;;
    121)
    err="probably is dead but pid file not deleted"
    ;;
    122)
    err="pid file is empty"
    ;;
    123)
    err="operation timeout"
    ;;
    201)
    err="signal sending error"
    ;;
    *)
    err="unknown code $rc"
    esac
    if [ -n "$err" ] ; then
    if [ -n "$1" ] ; then
        echo "$1: $err"
    else
        echo "$err"
    fi
    fi
}

get_kavpid() {
    if [ -s "$CONF" ] ; then
    if [ -n "$PID_FILE" -a -f "$PID_FILE" ] ; then
            PID=`head "$PID_FILE" 2> /dev/null`
        if [ -z "$PID" ] ; then
        # echo "pid file is empty"
        return 122
        fi
            echo $PID
            return 0
    else
            # echo "pid file not found"
        return 120
    fi
    else
        # echo "Config file not found"
        return 65
    fi
}

start() {    
    if [ -x $BIN ];then
    if $0 status >/dev/null ; then
        echo 'kavmonitor already started'
        rc=0
    else
        [COLOR=Red]/bin/mkdir -p /var/run/kav4ws 2>/dev/null[/COLOR]
        ${BIN} -C "${CONF}"
        rc=$?
        if [ $rc -eq 0 ] ; then
        echo 'kavmonitor started'
        else
        rc "kavmonitor not started"
        fi
    fi
    else
    echo "$BIN was not found"
    rc=5
    fi
}
    
stop() {
    if $0 status >/dev/null ; then
    PID=`get_kavpid`
    rc=$?
    if [ $rc -eq 0 ] ; then
        if kill "$PID"
        then
        wait=0
        while [ -f "$PID_FILE" -a $wait -le 30 ]; do
            sleep 1
            wait=$(($wait + 1))
        done
        if [ -f "$PID_FILE" ] ; then
            rc=123
        fi
        else
        rc=201
        fi    
    fi

        if [ $rc -eq 0 ] ; then
            echo 'kavmonitor stopped'
    else
        rc "kavmonitor could not be stopped"
        fi
    else
    echo 'kavmonitor already stopped'
    rc=0
    fi

    return $rc
}    

restart() {
    stop
    start
}      
    
reload() {
    PID=`get_kavpid`
    rc=$?
    if [ $rc -eq 0 ] ; then
    if ! kill -HUP "$PID" 2>/dev/null 
    then
        rc=201
        fi
    fi
    if [ $rc -eq 0 ] ; then
    echo 'kavmonitor reloaded'
    else
    rc "kavmonitor could not be reloaded"
    fi
    return $rc
}      

reload_avbase() {
    PID=`get_kavpid`
    rc=$?
    if [ $rc -eq 0 ] ; then
    if ! kill -USR1 "$PID" 2>/dev/null
    then
        rc=201
        fi
    fi
    if [ $rc -eq 0 ] ; then
    echo 'kavmonitor AV bases reloaded'
    else
        rc "kavmonitor could not reload AV bases"
    fi
    return $rc
}

status() {
    pid=`get_kavpid`
    rc=$?
    if [ $rc -eq 0 ] ; then
    kill -0 "$pid" 2>/dev/null
    if test $? -eq 0 ; then
        status="running"
        rc=0
    else
        status="dead"
        rc=1
    fi
    else
    status="stopped"
    rc=3
    fi
    echo "Kaspersky Anti-Virus on access scanner is $status."
}

case "$1" in

start)
    start
    ;;
stop)
    stop
    ;;
status)
    status
    ;;
restart)
    restart
    ;;
reload)
    reload
    ;;
reload_avbase)
    reload_avbase
    ;;    
*)
    echo "Usage: `basename $0` {start|stop|status|restart|reload|reload_avbase}" >&2
    exit 1
    ;;
esac

exit $rc
```

Try adding /bin/mkdir -p /var/run/kav4ws 2>/dev/null to start.  I put the change in red in the script.  Its not very nice but hopefully it fixes your specific issue.

---

### Post by ientzy on 2009-02-18
> **ilrudie said:**
> Try adding /bin/mkdir -p /var/run/kav4ws 2>/dev/null to start.  I put the change in red in the script.  Its not very nice but hopefully it fixes your specific issue.

Thank alot, work fine.

---

