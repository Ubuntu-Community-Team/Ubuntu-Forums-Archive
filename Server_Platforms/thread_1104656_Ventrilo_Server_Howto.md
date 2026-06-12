---
title: "Ventrilo Server Howto"
date: 2009-03-23
forum: Server Platforms
---

### Post by faldore on 2009-03-23
I wanted to set up Ventrilo server to always run on my Ubuntu machine.  There was no good walkthrough for this.  Here is my procedure.  If you know how to make it better, please comment! :)  I am a novice.

Download ventrilo_srv-<version>-Linux-i386.tar.gz from [www.ventrilo.com](www.ventrilo.com) to your home directory

Open command line

```
cd
tar -zxvf ventrilo_srv-<version>-Linux-i386.tar.gz
sudo mv ventsrv /usr/sbin
gksudo gedit --new-document /etc/init.d/ventrilo

```

Paste the following into gedit:

```
#!/bin/sh

do_start() {
	echo -n "Starting Ventrilo server..."
	
	if [ ! -e /usr/sbin/ventsrv/ventrilo_srv.pid ]
	then		
		start-stop-daemon --start --oknodo --pidfile /usr/sbin/ventsrv/ventrilo_srv.pid --exec /usr/sbin/ventsrv/ventrilo_srv -- -f/usr/sbin/ventsrv/ventrilo_srv -d
		echo "done."
	else
		echo "already running!"
		exit
	fi
}

do_stop() {
	echo -n "Stopping Ventrilo server..."
	
	if [ -e /usr/sbin/ventsrv/ventrilo_srv.pid ]
	then
		start-stop-daemon --stop --oknodo --quiet --pidfile /usr/sbin/ventsrv/ventrilo_srv.pid --exec /usr/sbin/ventsrv/ventrilo_srv
		echo "done."
	else
		echo "not running!"
		exit
	fi	
}

case "$1" in
start)
	do_start
	;;

stop)
	do_stop
	;;

restart|reload|force-reload)
	do_stop
	sleep 10
	do_start
	;;
	
*)
	echo "Usage: $0 start|stop|restart|reload|force-reload"
	exit 1
	;;
	
esac

```

Save and exit 

Add to defaults:

```
sudo chmod 755 /etc/init.d/ventrilo
sudo update-rc.d ventrilo defaults
sudo /etc/init.d/ventrilo start
```

Of course, you will also need to set up your Ubuntu machine to a static IP, and use your router to forward port 3784 to your Ubuntu machine, and of course give your friends the IP address that the router says it has with the WAN, or better yet use DynDNS.org.

I'm sure I have lots of things that could be better, but this gets the job done.  Please feel free to suggest improvements.

Also if you want OpenRPG I have a guide for that too.  [http://ubuntuforums.org/showthread.php?p=6947448]("http://ubuntuforums.org/showthread.php?p=6947448")

---

### Post by dauthimaster on 2009-03-24
That was a nice and easy guide.

A couple things though

1. I'm running 8.10 x64 and it didn't like your script and gave me a warning (which isn't a huge deal but I like my code running clean :P), you may want to write it to conform to the skeleton (sample) script in /etc/init.d, here is what it looks like:

```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          skeleton
# Required-Start:    $remote_fs
# Required-Stop:     $remote_fs
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Example initscript
# Description:       This file should be used to construct scripts to be
#                    placed in /etc/init.d.
### END INIT INFO

# Author: Foo Bar <foobar@baz.org>
#
# Please remove the "Author" lines above and replace them
# with your own name if you copy and modify this script.

# Do NOT "set -e"

# PATH should only include /usr/* if it runs after the mountnfs.sh script
PATH=/sbin:/usr/sbin:/bin:/usr/bin
DESC="Description of the service"
NAME=daemonexecutablename
DAEMON=/usr/sbin/$NAME
DAEMON_ARGS="--options args"
PIDFILE=/var/run/$NAME.pid
SCRIPTNAME=/etc/init.d/$NAME

# Exit if the package is not installed
[ -x "$DAEMON" ] || exit 0

# Read configuration variable file if it is present
[ -r /etc/default/$NAME ] && . /etc/default/$NAME

# Load the VERBOSE setting and other rcS variables
. /lib/init/vars.sh

# Define LSB log_* functions.
# Depend on lsb-base (>= 3.0-6) to ensure that this file is present.
. /lib/lsb/init-functions

#
# Function that starts the daemon/service
#
do_start()
{
        # Return
        #   0 if daemon has been started
        #   1 if daemon was already running
        #   2 if daemon could not be started
        start-stop-daemon --start --quiet --pidfile $PIDFILE --exec $DAEMON --test > /dev/null \
                || return 1
        start-stop-daemon --start --quiet --pidfile $PIDFILE --exec $DAEMON -- \
                $DAEMON_ARGS \
                || return 2
        # Add code here, if necessary, that waits for the process to be ready
        # to handle requests from services started subsequently which depend
        # on this one.  As a last resort, sleep for some time.
}

#
# Function that stops the daemon/service
#
do_stop()
{
        # Return
        #   0 if daemon has been stopped
        #   1 if daemon was already stopped
        #   2 if daemon could not be stopped
        #   other if a failure occurred
        start-stop-daemon --stop --quiet --retry=TERM/30/KILL/5 --pidfile $PIDFILE --name $NAME
        RETVAL="$?"
        [ "$RETVAL" = 2 ] && return 2
        # Wait for children to finish too if this is a daemon that forks
        # and if the daemon is only ever run from this initscript.
        # If the above conditions are not satisfied then add some other code
        # that waits for the process to drop all resources that could be
        # needed by services started subsequently.  A last resort is to
        # sleep for some time.
        start-stop-daemon --stop --quiet --oknodo --retry=0/30/KILL/5 --exec $DAEMON
        [ "$?" = 2 ] && return 2
        # Many daemons don't delete their pidfiles when they exit.
        rm -f $PIDFILE
        return "$RETVAL"
}

#
# Function that sends a SIGHUP to the daemon/service
#
do_reload() {
        #
        # If the daemon can reload its configuration without
        # restarting (for example, when it is sent a SIGHUP),
        # then implement that here.
        #
        start-stop-daemon --stop --signal 1 --quiet --pidfile $PIDFILE --name $NAME
        return 0
}

case "$1" in
  start)
        [ "$VERBOSE" != no ] && log_daemon_msg "Starting $DESC" "$NAME"
        do_start
        case "$?" in
                0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
                2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
        esac
        ;;
  stop)
        [ "$VERBOSE" != no ] && log_daemon_msg "Stopping $DESC" "$NAME"
        do_stop
        case "$?" in
                0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
                2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
        esac
        ;;
  #reload|force-reload)
        #
        # If do_reload() is not implemented then leave this commented out
        # and leave 'force-reload' as an alias for 'restart'.
        #
        #log_daemon_msg "Reloading $DESC" "$NAME"
        #do_reload
        #log_end_msg $?
        #;;
  restart|force-reload)
        #
        # If the "reload" option is implemented then remove the
        # 'force-reload' alias
        #
        log_daemon_msg "Restarting $DESC" "$NAME"
        do_stop
        case "$?" in
          0|1)
                do_start
                case "$?" in
                        0) log_end_msg 0 ;;
                        1) log_end_msg 1 ;; # Old process is still running
                        *) log_end_msg 1 ;; # Failed to start
                esac
                ;;
          *)
                # Failed to stop
                log_end_msg 1
                ;;
        esac
        ;;
  *)
        #echo "Usage: $SCRIPTNAME {start|stop|restart|reload|force-reload}" >&2
        echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload}" >&2
        exit 3
        ;;
esac

:
```

Also when using my editor of choice, nano, the file was created with 622 permissions, so I had to change  that manually to include executable, you may want to include that :)

```
sudo chmod 755 /etc/init.d/ventrilo
```

For some added security, it may be smart to do the same as [the teamspeak tut did]("http://ubuntuforums.org/showthread.php?t=236834").


I'm looking into the ventrilo_srv.htm file that is included with the installation for more tips and customization options.

---

### Post by dauthimaster on 2009-03-24
Oh also, this should probably be moved to Tutorials & Tips.

---

### Post by faldore on 2009-03-24
Great feedback!

---

### Post by o0Loco0o on 2009-04-07
You are the friggin' man!

---

### Post by imnotjack on 2013-01-10
hello. im running linux mint 13 64 bit. trying to start a ventrilo server. this guide is so simple comparativly speaking and yet im still gettting errors.here is what i get: 



john@Mint-Beast ~ $ sudo gedit --new-document /etc/init.d/ventrilo
john@Mint-Beast ~ $ sudo chmod 755 /etc/init.d/ventrilo
john@Mint-Beast ~ $ sudo update-rc.d ventrilo defaults
update-rc.d: warning: /etc/init.d/ventrilo missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
 System start/stop links for /etc/init.d/ventrilo already exist.
john@Mint-Beast ~ $ sudo /etc/init.d/ventrilo start
Starting Ventrilo server...start-stop-daemon: unable to start /usr/sbin/ventsrv/ventrilo_srv (No such file or directory)
done.
john@Mint-Beast ~ $ cd /usr/sbin/ventsrv/
john@Mint-Beast /usr/sbin/ventsrv $ ls -1
LICENSE
ventrilo_srv
ventrilo_srv.htm
ventrilo_srv.ini
ventrilo_status
john@Mint-Beast /usr/sbin/ventsrv $ start ventrilo_srv
start: Unknown job: ventrilo_srv
john@Mint-Beast /usr/sbin/ventsrv $ ventrilo_srv
bash: /usr/bin/ventrilo_srv: No such file or directory
john@Mint-Beast /usr/sbin/ventsrv $ ventrilo_srv
bash: /usr/bin/ventrilo_srv: No such file or directory


any help and insight would be appreciated. thanks!

---

### Post by ericje627 on 2013-01-10
There seems to be a problem with the line 

```
john@Mint-Beast /usr/sbin/ventsrv $ ventrilo_srv
bash: /usr/bin/ventrilo_srv: No such file or directory
```

The system is unable to find the path you specified.
Are you sure the filename ventrilo_srv is correct?

When trying to run ventrilo_srv from the directory itself, you need to type ```
./ventrilo_srv
``` to execute it.

Also make sure your permissions are set correctly for the user running the server. Since the ventrilo package is an archive, you may have to set the appropriate permissions yourself (I had the same issue with TeamSpeak 3, except the error was Permission denied).

---

