---
title: "Iptables and rebooting..."
date: 2006-02-02
forum: Server Platforms
---

### Post by eviltwin on 2006-02-02
Hi,

Something silly I have noticed about debian/ubuntu is that you seem to lose all iptables settings on reboot. This can't be right, can it? If it is then could I have someone help me create a script (probably based off the one from fedora or some such distro) to ammend this problem?

Many thanks,
Graham

---

### Post by alamba on 2006-02-02
are you able to reload/restart iptables without a reboot?

Akshay

---

### Post by eviltwin on 2006-02-02
What exactyl do you mean by this?

---

### Post by sco01 on 2006-02-02
Yes, this anoyed me like hell. I created a script called iptables in /etc/init.d/ with the following content (I got it from [http://www.cae.wisc.edu/site/public/?title=iptables-scriptex):](http://www.cae.wisc.edu/site/public/?title=iptables-scriptex):)

```

#!/bin/sh

IPTABLES=/sbin/iptables

case "$1" in
start)
        echo -n "Starting IP Firewall and NAT..."
        # echo "1" > /proc/sys/net/ipv4/ip_forward
        # echo "1" > /proc/sys/net/ipv4/tcp_syncookies

        # Clear old rules
        $IPTABLES -X
        $IPTABLES -F
        $IPTABLES -Z
#---------------------------------------------------------------------------------------------------------------
        # INPUT Rules - Add to this section the ports you wish to explicitly allow connections on
        #       Below are some common services that are commonly used
        #       Comment out the lines to disable access to these services
        #       The port numbers for other services you may wish to allow can be found in the /etc/services file

        #drop ssh atempts if more than four in a minute
        iptables -I INPUT -p tcp --dport 22 -i eth0 -m state --state NEW -m recent  --set
        iptables -I INPUT -p tcp --dport 22 -i eth0 -m state --state NEW -m recent  --update --seconds 60 --hitcount 4 -j DROP



        #$IPTABLES -A INPUT -i eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT      #Allows connections you start

        #$IPTABLES -A INPUT -i eth0 -p tcp --dport 21 -j ACCEPT #Allow FTP Connections

        #$IPTABLES -A INPUT -i eth0 -p tcp --dport 21 -j ACCEPT #Allow FTP Connections
        #$IPTABLES -A INPUT -i eth0 -p udp --dport 21 -j ACCEPT

        #$IPTABLES -A INPUT -i eth0 -p tcp --dport 22 -j ACCEPT  #SSH Connections

        #$IPTABLES -A INPUT -i eth0 -p tcp --dport 80 -j ACCEPT  #HTTP Connections

        #$IPTABLES -A INPUT -i eth0 -p tcp --dport 443 -j ACCEPT  #SSL Connections

        #$IPTABLES -A INPUT -i eth0 -p tcp --dport 137 -j ACCEPT #SAMBA related ports
        #$IPTABLES -A INPUT -i eth0 -p tcp --dport 138 -j ACCEPT
        #$IPTABLES -A INPUT -i eth0 -p tcp --dport 139 -j ACCEPT
        #$IPTABLES -A INPUT -i eth0 -p udp --dport 138 -j ACCEPT
        #$IPTABLES -A INPUT -i eth0 -p udp --dport 139 -j ACCEPT

        # Allow pings, but reject the rest
        #$IPTABLES -A INPUT -i eth0 -p icmp -j ACCEPT
        #$IPTABLES -A INPUT -i eth0 -j REJECT
#--------------------------------------------------------------------------------------
        echo "done."
        ;;
stop)
        echo -n "Stopping IP Firewall..."
        #Clear old rules
        $IPTABLES -X
        $IPTABLES -F
        $IPTABLES -Z

        # Input Rules
        $IPTABLES -A INPUT -i eth0 -m state --state ESTABLISHED,related -j ACCEPT
        $IPTABLES -A INPUT -i eth0 -j REJECT
        echo "done."
        ;;

restart)
        echo -n "Restarting IP Firewall..."
        $0 stop > /dev/null
        sleep 1
        $0 start > /dev/null
        ;;

*)
        echo "Usage: $0 {start|stop|restart}"
        ;;


```

Edit it to your needs and then make it executable:

```
sudo chmod +x /etc/init.d/iptables
```

And thanks to MartinG (in this thread: [http://www.ubuntuforums.org/showthread.php?t=123185):](http://www.ubuntuforums.org/showthread.php?t=123185):) Assuming the system will be operating in runlevel 2, place a link to your script in /etc/rc2.d. Then rename it by adding a prefix Sxx, where xx is a number between 01 and 99. The value of xx determines the order of starting of all the services listed in rc2.d, so pick a number with reference to what else is there; probably a fairly low number for a security thing like this. I'd pick 15 on my system.

So execute the following from /etc/rc2.d

```
 sudo ln -s /etc/init.d/iptables ./S15iptables
```



Why isn't this part of the standard config? Should it be this hard? Anyway, I hope this helps.

//Stefan

---

### Post by robert_pectol on 2006-02-03
Just to clarify... Iptables is NOT a firewall!  It's merely a tool used for configuring the packet inspection/filtering capabilities (Netfilter) in the kernel.  Most Linux firewalls consist of a set of policies and rules which get loaded in the kernel, usually by employing a tool such as Iptables, to configure each of them.  This makes it easy to write a firewall script for Linux (as shown in previous post).  Hope that helps!

---

### Post by eviltwin on 2006-02-03
[QUOTE=robert_pectol]Just to clarify... Iptables is NOT a firewall!  It's merely a tool used for configuring the packet inspection/filtering capabilities (Netfilter) in the kernel.  Most Linux firewalls consist of a set of policies and rules which get loaded in the kernel, usually by employing a tool such as Iptables, to configure each of them.  This makes it easy to write a firewall script for Linux (as shown in previous post).  Hope that helps![/QUOTE]
Well yes, if you want to be technical about it ;)

I just want a script that I will use iptables-save and iptables-restore at apporopriate events, it doesn't matter... I'll just go off and make my own, won't take me very long at all. Perhaps something I will do at lunch. I'll post it here when I'm done so you can see what I meant by what I wanted.

Thanks anyway,
Graham

EDIT: Just finished the sciprt, it's a little messy so if someone with init script know-how could help me tidy away he lines with echo commands in them (not the right way to do things I think) then I would be appreciative.

```
#!/bin/sh
#
# iptables	Start iptables firewall
#
# description:	Starts, stops and saves iptables firewall
#		Based on the Fedora 4 iptables script
#
# config: /etc/network/iptables
# config: /etc/network/iptables-config

# Source function library.
. /lib/lsb/init-functions

IPTABLES=iptables
IPTABLES_DATA=/etc/network/$IPTABLES
IPTABLES_CONFIG=/etc/network/${IPTABLES}-config
IPV=${IPTABLES%tables} # ip for ipv4 | ip6 for ipv6
PROC_IPTABLES_NAMES=/proc/net/${IPV}_tables_names
VAR_SUBSYS_IPTABLES=/var/lock/subsys/$IPTABLES

if [ ! -x /sbin/$IPTABLES ]; then
    log_warning_msg "/sbin/$IPTABLES does not exist."
    exit 0
fi

if [ ! -x /sbin/$IPTABLES-save ]; then
    log_warning_msg "/sbin/$IPTABLES-save does not exist."
    exit 0
fi

if [ ! -x /sbin/$IPTABLES-restore ]; then
    log_warning_msg "/sbin/$IPTABLES-restore does not exist."
    exit 0
fi

if lsmod 2>/dev/null | grep -q ipchains ; then
    log_warning_msg "ipchains and $IPTABLES can not be used together."
    exit 0
fi

# Old or new modutils
/sbin/modprobe --version 2>&1 | grep -q module-init-tools \
    && NEW_MODUTILS=1 \
    || NEW_MODUTILS=0

# Default firewall configuration:
IPTABLES_MODULES=""
IPTABLES_MODULES_UNLOAD="yes"
IPTABLES_ON_STOP="no"
IPTABLES_SAVE_ON_RESTART="no"
IPTABLES_SAVE_COUNTER="no"
IPTABLES_STATUS_NUMERIC="yes"

# Load firewall configuration.
[ -f "$IPTABLES_CONFIG" ] && . "$IPTABLES_CONFIG"

rmmod_r() {
    # Unload module with all referring modules.
    # At first all referring modules will be unloaded, then the module itself.
    local mod=$1
    local ret=0
    local ref=

    # Get referring modules.
    # New modutils have another output format.
    [ $NEW_MODUTILS = 1 ] \
	&& ref=`lsmod | awk "/^${mod}/ { print \\\$4; }" | tr ',' ' '` \
	|| ref=`lsmod | grep ^${mod} | cut -d "[" -s -f 2 | cut -d "]" -s -f 1`

    # recursive call for all referring modules
    for i in $ref; do
	rmmod_r $i
	let ret+=$?;
    done

    # Unload module.
    # The extra test is for 2.6: The module might have autocleaned,
    # after all referring modules are unloaded.
    if grep -q "^${mod}" /proc/modules ; then
	modprobe -r $mod > /dev/null 2>&1
	let ret+=$?;
    fi

    return $ret
}

flush_n_delete() {
    # Flush firewall rules and delete chains.
    [ -e "$PROC_IPTABLES_NAMES" ] || return 1

    # Check if firewall is configured (has tables)
    tables=`cat $PROC_IPTABLES_NAMES 2>/dev/null`
    [ -z "$tables" ] && return 1

    log_begin_msg "Flushing firewall rules: "
    ret=0
    # For all tables
    for i in $tables; do
        # Flush firewall rules.
	$IPTABLES -t $i -F;
	let ret+=$?;

        # Delete firewall chains.
	$IPTABLES -t $i -X;
	let ret+=$?;

	# Set counter to zero.
	$IPTABLES -t $i -Z;
	let ret+=$?;
    done

    log_end_msg $ret
    return $ret
}

set_policy() {
    # Set policy for configured tables.
    policy=$1

    # Check if iptable module is loaded
    [ ! -e "$PROC_IPTABLES_NAMES" ] && return 1

    # Check if firewall is configured (has tables)
    tables=`cat $PROC_IPTABLES_NAMES 2>/dev/null`
    [ -z "$tables" ] && return 1

    log_begin_msg "Setting chains to policy $policy: "
    ret=0
    for i in $tables; do
	echo -n "$i "
	case "$i" in
	    filter)
                $IPTABLES -t filter -P INPUT $policy \
		    && $IPTABLES -t filter -P OUTPUT $policy \
		    && $IPTABLES -t filter -P FORWARD $policy \
		    || let ret+=1
		;;
	    nat)
		$IPTABLES -t nat -P PREROUTING $policy \
		    && $IPTABLES -t nat -P POSTROUTING $policy \
		    && $IPTABLES -t nat -P OUTPUT $policy \
		    || let ret+=1
		;;
	    mangle)
	        $IPTABLES -t mangle -P PREROUTING $policy \
		    && $IPTABLES -t mangle -P POSTROUTING $policy \
		    && $IPTABLES -t mangle -P INPUT $policy \
		    && $IPTABLES -t mangle -P OUTPUT $policy \
		    && $IPTABLES -t mangle -P FORWARD $policy \
		    || let ret+=1
		;;
	    *)
	        let ret+=1
		;;
        esac
    done

    log_end_msg $ret
    return $ret
}

start() {
    # Do not start if there is no config file.
    [ -f "$IPTABLES_DATA" ] || return 1

    log_begin_msg "Applying $IPTABLES firewall rules: "

    OPT=
    [ "x$IPTABLES_SAVE_COUNTER" = "xyes" ] && OPT="-c"

    $IPTABLES-restore $OPT $IPTABLES_DATA
    if [ $? -eq 0 ]; then
	log_end_msg $?
    else
	log_end_msg $?; return 1
    fi
    
    # Load additional modules (helpers)
    if [ -n "$IPTABLES_MODULES" ]; then
	log_begin_msg "Loading additional $IPTABLES modules: "
	ret=0
	for mod in $IPTABLES_MODULES; do
	    echo -n "$mod "
	    modprobe $mod > /dev/null 2>&1
	    let ret+=$?;
	done
	log_end_msg $ret
    fi
    
    touch $VAR_SUBSYS_IPTABLES
    return $ret
}

stop() {
    # Do not stop if iptables module is not loaded.
    [ -e "$PROC_IPTABLES_NAMES" ] || return 1

    flush_n_delete
    set_policy ACCEPT
    
    if [ "x$IPTABLES_MODULES_UNLOAD" = "xyes" ]; then
	log_begin_msg "Unloading $IPTABLES modules: "
	ret=0
	rmmod_r ${IPV}_tables
	let ret+=$?;
	rmmod_r ${IPV}_conntrack
	let ret+=$?;
	log_end_msg $ret
    fi
    
    rm -f $VAR_SUBSYS_IPTABLES
    return $ret
}

save() {
    # Check if iptable module is loaded
    [ ! -e "$PROC_IPTABLES_NAMES" ] && return 1

    # Check if firewall is configured (has tables)
    tables=`cat $PROC_IPTABLES_NAMES 2>/dev/null`
    [ -z "$tables" ] && return 1

    log_begin_msg "Saving firewall rules to $IPTABLES_DATA: "

    OPT=
    [ "x$IPTABLES_SAVE_COUNTER" = "xyes" ] && OPT="-c"

    ret=0
    TMP_FILE=`/bin/mktemp -q /tmp/$IPTABLES.XXXXXX` \
	&& chmod 600 "$TMP_FILE" \
	&& $IPTABLES-save $OPT > $TMP_FILE 2>/dev/null \
	&& size=`stat -c '%s' $TMP_FILE` && [ $size -gt 0 ] \
	|| ret=1
    if [ $ret -eq 0 ]; then
	if [ -e $IPTABLES_DATA ]; then
	    cp -f $IPTABLES_DATA $IPTABLES_DATA.save \
		&& chmod 600 $IPTABLES_DATA.save \
		|| ret=1
	fi
	if [ $ret -eq 0 ]; then
	    cp -f $TMP_FILE $IPTABLES_DATA \
		&& chmod 600 $IPTABLES_DATA \
	        || ret=1
	fi
    fi
    log_end_msg $ret
    rm -f $TMP_FILE
    return $ret
}

status() {
    # Do not print status if lockfile is missing and iptables modules are not 
    # loaded.
    # Check if iptable module is loaded
    if [ ! -f "$VAR_SUBSYS_IPTABLES" ]; then
	log_success_msg "Firewall is stopped."
	return 1
    fi

    # Check if firewall is configured (has tables)
    if [ ! -e "$PROC_IPTABLES_NAMES" ]; then
	log_success_msg "Firewall is not configured. "
	return 1
    fi
    tables=`cat $PROC_IPTABLES_NAMES 2>/dev/null`
    if [ -z "$tables" ]; then
	logsuccess_msg "Firewall is not configured. "
	return 1
    fi

    NUM=
    [ "x$IPTABLES_STATUS_NUMERIC" = "xyes" ] && NUM="-n"

    for table in $tables; do
	echo $"Table: $table"
	$IPTABLES -t $table --list $NUM && echo
    done

    return 0
}

restart() {
    [ "x$IPTABLES_SAVE_ON_RESTART" = "xyes" ] && save
    stop
    start
}

case "$1" in
    start)
	stop
	start
	RETVAL=$?
	;;
    stop)
	[ "x$IPTABLES_SAVE_ON_STOP" = "xyes" ] && save
	stop
	RETVAL=$?
	;;
    restart)
	restart
	RETVAL=$?
	;;
    condrestart)
	[ -e "$VAR_SUBSYS_IPTABLES" ] && restart
	;;
    status)
	status
	RETVAL=$?
	;;
    panic)
	flush_n_delete
	set_policy DROP
	RETVAL=$?
        ;;
    save)
	save
	RETVAL=$?
	;;
    *)
	log_success_msg "Usage: $0 {start|stop|restart|condrestart|status|panic|save}"
	exit 1
	;;
esac

exit $RETVAL
```

EDIT AGAIN: There are also some other errors in there to do with lock files and stuff, if someone could help me work these out then I would appreciate it

---

### Post by eviltwin on 2006-02-03
Ok, so the only thing that I actually have left to change in that file is the parts with echo in them and the lock file, it doesn't exist by default. Should I create it or is it actually in existance somewhere else? Soooo close... help... :(

---

### Post by plumcreek on 2007-04-18
On line 19 change:
```
VAR_SUBSYS_IPTABLES=/var/lock/subsys/$IPTABLES
```to
```
VAR_SUBSYS_IPTABLES=/var/lock/$IPTABLES
```There is no /var/lock/subsys directory on Ubuntu

---

### Post by plumcreek on 2007-04-18
To have the iptables init script run automatically at boot you should run

```
[SIZE=-1]update-rc.d iptables defaults[/SIZE]
```

...instead of manually creating the link in /etc/rc2.d

---

### Post by plumcreek on 2007-04-18
A couple final changes to the script that I would make. :-)

On ubuntu-server boxes, **sh** is really **dash** (at least, it is by default). On RedHat-type boxes,  **sh** is really **bash** by default. This caused errors like:
```
/etc/init.d/iptables: 323: let: not found
```...because dash doesn't know what *let* is.

To fix, I just changed the first line from:
```
#!/bin/sh
```to
```
#!/bin/bash
```...and those errors went away.

Lastly, I commented out line #130:
```
    #echo -n "$i "
```...because it was making the log output less pretty. ;-)

The script works great now. Thanks!

---

### Post by plumcreek on 2007-04-18
Here's my modified version of the script for those that might want to just copy/paste it instead of making the changes I outlined previously.
```
#!/bin/bash
#
# iptables    Start iptables firewall
#
# description:    Starts, stops and saves iptables firewall
#        Based on the Fedora 4 iptables script
#           initial mods by eviltwin
#           further tweaks by plumcreek
#
# This was initially posted to ubuntuforums.org in the following post:
#    http://ubuntuforums.org/showpost.php?p=2474546&postcount=11
#
# config: /etc/network/iptables
# config: /etc/network/iptables-config

# Source function library.
. /lib/lsb/init-functions

IPTABLES=iptables
IPTABLES_DATA=/etc/network/$IPTABLES
IPTABLES_CONFIG=/etc/network/${IPTABLES}-config
IPV=${IPTABLES%tables} # ip for ipv4 | ip6 for ipv6
PROC_IPTABLES_NAMES=/proc/net/${IPV}_tables_names
VAR_SUBSYS_IPTABLES=/var/lock/$IPTABLES

if [ ! -x /sbin/$IPTABLES ]; then
    log_warning_msg "/sbin/$IPTABLES does not exist."
    exit 0
fi

if [ ! -x /sbin/$IPTABLES-save ]; then
    log_warning_msg "/sbin/$IPTABLES-save does not exist."
    exit 0
fi

if [ ! -x /sbin/$IPTABLES-restore ]; then
    log_warning_msg "/sbin/$IPTABLES-restore does not exist."
    exit 0
fi

if lsmod 2>/dev/null | grep -q ipchains ; then
    log_warning_msg "ipchains and $IPTABLES can not be used together."
    exit 0
fi

# Old or new modutils
/sbin/modprobe --version 2>&1 | grep -q module-init-tools \
    && NEW_MODUTILS=1 \
    || NEW_MODUTILS=0

# Default firewall configuration:
IPTABLES_MODULES=""
IPTABLES_MODULES_UNLOAD="yes"
IPTABLES_ON_STOP="no"
IPTABLES_SAVE_ON_RESTART="no"
IPTABLES_SAVE_COUNTER="no"
IPTABLES_STATUS_NUMERIC="yes"

# Load firewall configuration.
[ -f "$IPTABLES_CONFIG" ] && . "$IPTABLES_CONFIG"

rmmod_r() {
    # Unload module with all referring modules.
    # At first all referring modules will be unloaded, then the module itself.
    local mod=$1
    local ret=0
    local ref=

    # Get referring modules.
    # New modutils have another output format.
    [ $NEW_MODUTILS = 1 ] \
    && ref=`lsmod | awk "/^${mod}/ { print \\\$4; }" | tr ',' ' '` \
    || ref=`lsmod | grep ^${mod} | cut -d "[" -s -f 2 | cut -d "]" -s -f 1`

    # recursive call for all referring modules
    for i in $ref; do
    rmmod_r $i
    let ret+=$?;
    done

    # Unload module.
    # The extra test is for 2.6: The module might have autocleaned,
    # after all referring modules are unloaded.
    if grep -q "^${mod}" /proc/modules ; then
    modprobe -r $mod > /dev/null 2>&1
    let ret+=$?;
    fi

    return $ret
}

flush_n_delete() {
    # Flush firewall rules and delete chains.
    [ -e "$PROC_IPTABLES_NAMES" ] || return 1

    # Check if firewall is configured (has tables)
    tables=`cat $PROC_IPTABLES_NAMES 2>/dev/null`
    [ -z "$tables" ] && return 1

    log_begin_msg "Flushing firewall rules: "
    ret=0
    # For all tables
    for i in $tables; do
        # Flush firewall rules.
    $IPTABLES -t $i -F;
    let ret+=$?;

        # Delete firewall chains.
    $IPTABLES -t $i -X;
    let ret+=$?;

    # Set counter to zero.
    $IPTABLES -t $i -Z;
    let ret+=$?;
    done

    log_end_msg $ret
    return $ret
}

set_policy() {
    # Set policy for configured tables.
    policy=$1

    # Check if iptable module is loaded
    [ ! -e "$PROC_IPTABLES_NAMES" ] && return 1

    # Check if firewall is configured (has tables)
    tables=`cat $PROC_IPTABLES_NAMES 2>/dev/null`
    [ -z "$tables" ] && return 1

    log_begin_msg "Setting chains to policy $policy: "
    ret=0
    for i in $tables; do
    #echo -n "$i "
    case "$i" in
        filter)
                $IPTABLES -t filter -P INPUT $policy \
            && $IPTABLES -t filter -P OUTPUT $policy \
            && $IPTABLES -t filter -P FORWARD $policy \
            || let ret+=1
        ;;
        nat)
        $IPTABLES -t nat -P PREROUTING $policy \
            && $IPTABLES -t nat -P POSTROUTING $policy \
            && $IPTABLES -t nat -P OUTPUT $policy \
            || let ret+=1
        ;;
        mangle)
            $IPTABLES -t mangle -P PREROUTING $policy \
            && $IPTABLES -t mangle -P POSTROUTING $policy \
            && $IPTABLES -t mangle -P INPUT $policy \
            && $IPTABLES -t mangle -P OUTPUT $policy \
            && $IPTABLES -t mangle -P FORWARD $policy \
            || let ret+=1
        ;;
        *)
            let ret+=1
        ;;
        esac
    done

    log_end_msg $ret
    return $ret
}

start() {
    # Do not start if there is no config file.
    [ -f "$IPTABLES_DATA" ] || return 1

    log_begin_msg "Applying $IPTABLES firewall rules: "

    OPT=
    [ "x$IPTABLES_SAVE_COUNTER" = "xyes" ] && OPT="-c"

    $IPTABLES-restore $OPT $IPTABLES_DATA
    if [ $? -eq 0 ]; then
    log_end_msg $?
    else
    log_end_msg $?; return 1
    fi
    
    # Load additional modules (helpers)
    if [ -n "$IPTABLES_MODULES" ]; then
    log_begin_msg "Loading additional $IPTABLES modules: "
    ret=0
    for mod in $IPTABLES_MODULES; do
        echo -n "$mod "
        modprobe $mod > /dev/null 2>&1
        let ret+=$?;
    done
    log_end_msg $ret
    fi
    
    touch $VAR_SUBSYS_IPTABLES
    return $ret
}

stop() {
    # Do not stop if iptables module is not loaded.
    [ -e "$PROC_IPTABLES_NAMES" ] || return 1

    flush_n_delete
    set_policy ACCEPT
    
    if [ "x$IPTABLES_MODULES_UNLOAD" = "xyes" ]; then
    log_begin_msg "Unloading $IPTABLES modules: "
    ret=0
    rmmod_r ${IPV}_tables
    let ret+=$?;
    rmmod_r ${IPV}_conntrack
    let ret+=$?;
    log_end_msg $ret
    fi
    
    rm -f $VAR_SUBSYS_IPTABLES
    return $ret
}

save() {
    # Check if iptable module is loaded
    [ ! -e "$PROC_IPTABLES_NAMES" ] && return 1

    # Check if firewall is configured (has tables)
    tables=`cat $PROC_IPTABLES_NAMES 2>/dev/null`
    [ -z "$tables" ] && return 1

    log_begin_msg "Saving firewall rules to $IPTABLES_DATA: "

    OPT=
    [ "x$IPTABLES_SAVE_COUNTER" = "xyes" ] && OPT="-c"

    ret=0
    TMP_FILE=`/bin/mktemp -q /tmp/$IPTABLES.XXXXXX` \
    && chmod 600 "$TMP_FILE" \
    && $IPTABLES-save $OPT > $TMP_FILE 2>/dev/null \
    && size=`stat -c '%s' $TMP_FILE` && [ $size -gt 0 ] \
    || ret=1
    if [ $ret -eq 0 ]; then
    if [ -e $IPTABLES_DATA ]; then
        cp -f $IPTABLES_DATA $IPTABLES_DATA.save \
        && chmod 600 $IPTABLES_DATA.save \
        || ret=1
    fi
    if [ $ret -eq 0 ]; then
        cp -f $TMP_FILE $IPTABLES_DATA \
        && chmod 600 $IPTABLES_DATA \
            || ret=1
    fi
    fi
    log_end_msg $ret
    rm -f $TMP_FILE
    return $ret
}

status() {
    # Do not print status if lockfile is missing and iptables modules are not 
    # loaded.
    # Check if iptable module is loaded
    if [ ! -f "$VAR_SUBSYS_IPTABLES" ]; then
    log_success_msg "Firewall is stopped."
    return 1
    fi

    # Check if firewall is configured (has tables)
    if [ ! -e "$PROC_IPTABLES_NAMES" ]; then
    log_success_msg "Firewall is not configured. "
    return 1
    fi
    tables=`cat $PROC_IPTABLES_NAMES 2>/dev/null`
    if [ -z "$tables" ]; then
    logsuccess_msg "Firewall is not configured. "
    return 1
    fi

    NUM=
    [ "x$IPTABLES_STATUS_NUMERIC" = "xyes" ] && NUM="-n"

    for table in $tables; do
    echo $"Table: $table"
    $IPTABLES -t $table --list $NUM && echo
    done

    return 0
}

restart() {
    [ "x$IPTABLES_SAVE_ON_RESTART" = "xyes" ] && save
    stop
    start
}

case "$1" in
    start)
    stop
    start
    RETVAL=$?
    ;;
    stop)
    [ "x$IPTABLES_SAVE_ON_STOP" = "xyes" ] && save
    stop
    RETVAL=$?
    ;;
    restart)
    restart
    RETVAL=$?
    ;;
    condrestart)
    [ -e "$VAR_SUBSYS_IPTABLES" ] && restart
    ;;
    status)
    status
    RETVAL=$?
    ;;
    panic)
    flush_n_delete
    set_policy DROP
    RETVAL=$?
        ;;
    save)
    save
    RETVAL=$?
    ;;
    *)
    log_success_msg "Usage: $0 {start|stop|restart|condrestart|status|panic|save}"
    exit 1
    ;;
esac

exit $RETVAL

```Copy/Paste the above to /etc/init.d/iptables and then run:

```
sudo chmod 755 /etc/init.d/iptables
sudo update-rc.d iptables defaults

```If you have iptables rules already in place and running, do:
```
sudo /etc/init.d/iptables save
```...before you go any further.

To start iptables do:
```
sudo /etc/init.d/iptables start
```...and iptables will start. :-) (well, it will read in the chains that you saved previously and apply them, but start is a simpler way of referring to it)

To stop iptables do:
```
sudo /etc/init.d/iptables stop
```...and iptables will stop. :-) (well, actually, it just flushes your chains from memory, but let's not nit-pick)

Add new iptables rules using the iptables command (see any iptables how-to for how to do this) and once you are happy with your rules, issue:
```
sudo /etc/init.d/iptables save
```...to save your rules to /etc/network/iptables

Once you have issued a "save" your rules will load auto-magically every reboot. How spiffy is that!

---

