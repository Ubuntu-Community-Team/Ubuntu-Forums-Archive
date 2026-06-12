---
title: "FLEXlm init script"
date: 2011-08-01
forum: Server Platforms
---

### Post by Turmoyl on 2011-08-01
I designed it to work as an umbrella daemon which covers one or many vendor license daemons in one swoop. You put all your licenses in one directory, then put all their corresponding executables in the same directory with the FLEXlm executables, and it runs as a single daemon process. I find this to be more efficient than running one daemon per vendor executable.

I added a feature I've always wanted to tie into a FLEXlm init script: reload. It employes the 'lmreread' ability of 'lmutil' for all your licenses. This gives you the ability to easily replace license files in-line, without having to restart the umbrella daemon.

Copy the code below to a new file (e.g. /etc/init.d/flexlm), change the variables at the top to fit your environment, make it executable (e.g. chmod +x /etc/init.d/flexlm), and symlink it to your desired runlevel to make it autorun at boot time (e.g. ln -s /etc/init.d/flexlm /etc/rc2.d/S99flexlm).

```
#!/bin/sh

# FLEXlm init script
# Designed to work as an umbrella daemon for multiple vendor licenses
#
# Created by Brian Morris (bmorris {at}  cyberarmor zDOTz net), 08/08/2011
#
# Change the variables below to fit your environment

FLEXLM_BASEDIR=/usr/local/flexlm
FLEXLM_LICENSEDIR=$FLEXLM_BASEDIR/licenses/
FLEXLM_BINDIR=$FLEXLM_BASEDIR/x86_64linux
FLEXLM_BIN=$FLEXLM_BINDIR/lmgrd
FLEXLM_UTIL=$FLEXLM_BINDIR/lmutil
FLEXLM_LOGDIR=/var/log/flexlm

########## DO NOT CHANGE ANYTHING BELOW THIS LINE ##########

# Check for the existence of the FLEXLM daemon
test -x $FLEXLM_BIN || { echo "$FLEXLM_BIN is not installed"; 
	if [ "$1" = "stop" ]; then exit 0;
	else exit 5; fi; }

# Check for the existence of the FLEXLM utility
test -x $FLEXLM_UTIL || { echo "$FLEXLM_UTIL is not installed";
        if [ "$1" = "stop" ]; then exit 0;
        else exit 5; fi; }

# Check license files for read access
FLEXLM_LICENSE=`find $FLEXLM_LICENSEDIR -name "*.license.dat"`
for file in $FLEXLM_LICENSE
do
    test -r $file || { echo "$file not readable. Please correct its permissions.";
	if [ "$1" = "stop" ]; then exit 0;
	else exit 6; fi; }
done


start () {
        echo -n "\n"
        for file in $FLEXLM_LICENSE
        do
                SERVICE=`basename $file | awk -F. '{print $1}'`
                echo "Starting $SERVICE license server"
                $FLEXLM_BIN -c $file -L $FLEXLM_LOGDIR/$SERVICE.flexlm.log
        done
        echo -n "\n"
}

stop () {
        for file in $FLEXLM_LICENSE
        do
                SERVICE=`basename $file | awk -F. '{print $1}'`
                echo "\nStopping $SERVICE license server"
                $FLEXLM_UTIL lmdown -all -c $file
		echo -n "\n"
        done
        echo -n "\nWaiting for all license ports to close..."
        # The CST license daemon takes around 50 seconds to spin down,
	# so I set this at 60 seconds.
        for i in `seq 1 60`;
        do
                sleep 1
                echo -n "."
        done
        echo "\n"
}

reload () {
	for file in $FLEXLM_LICENSE
	do
		SERVICE=`basename $file | awk -F. '{print $1}'`
		echo "\nRereading $SERVICE"
		$FLEXLM_UTIL lmreread -c $file
		echo -n "\n"
	done
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

	reload)
		reload
	;;

	*)
	echo "\nUsage: /etc/init.d/flexlm {start|stop|restart|reload}\n"
	;;

esac
```

---

