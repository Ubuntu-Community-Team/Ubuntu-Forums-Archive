---
title: "creating a daemon"
date: 2007-05-14
forum: Server Platforms
---

### Post by wdhasek on 2007-05-14
Hi, i'm very new to linux and attempting to make a tinyMUSH server. For those of you that don't know, TinyMUSH is a C program that allows you to chat and roleplay. I have the source compiled and it works fine, to start the server to start you have to run a shell script. I've attempted to run the shell script through the start-stop daemon using the skeleton file provided with ubuntu but i'm have no luck whatsoever. Does anyone have any pointers or helpful tips. 'm on the verge of tearing my hair out!

---

### Post by gombadi on 2007-05-14
First tip - Don't tear your hair out - it hurts :) 

Second tip - Can you give us some more info. 

You say you have had no luck what so ever with the skeleton script- What have you changed in it? What happened when you tried it? Error message or something else? Can you give us a link to see the script that starts the tinyMUSH server so we can see what it may be doing.

Have fun.

---

### Post by Pobega on 2007-05-14
```
ln -s /etc/init.d/tinymush /etc/rc2.d/S45mush
```

Of course, this is assuming that the TinyMUSH start script is /etc/init.d/tinymush.

---

### Post by wdhasek on 2007-05-16
i appologize for taking so long to respond, busy lately. The hair is intact thankfully. As for the symbolic link approach,.. tried that, it doesn't seem to do a thing. Heres the daemon script i'm using, 

set -e

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DESC="Tinymush daemon"
NAME=Startmush
DAEMON=/tinymush/game/$NAME
PIDFILE=/tinymush/game/netmush.pid
SCRIPTNAME=/etc/init.d/$NAME

# Gracefully exit if the package has been removed.
test -x $DAEMON || exit 0

# Read config file if it is present.
#if [ -r /etc/default/$NAME ]
#then
#	. /etc/default/$NAME
#fi

#
#	Function that starts the daemon/service.
#
d_start() {
	start-stop-daemon --start --quiet --pidfile $PIDFILE \
		--exec $DAEMON \
		|| echo -n " already running"
}

exit 0
#
#	Function that stops the daemon/service.
#
d_stop() {
	kill 'cat$PIDFILE'
}

#
#	Function that sends a SIGHUP to the daemon/service.
#
d_reload() {
	start-stop-daemon --stop --quiet --pidfile $PIDFILE \
		--name $NAME --signal 1
}

case "$1" in
  start)
	echo -n "Starting $DESC: $NAME"
	d_start
	echo "."
	;;
  stop)
	echo -n "Stopping $DESC: $NAME"
	d_stop
	echo "."
	;;
  #reload)
	#
	#	If the daemon can reload its configuration without
	#	restarting (for example, when it is sent a SIGHUP),
	#	then implement that here.
	#
	#	If the daemon responds to changes in its config file
	#	directly anyway, make this an "exit 0".
	#
	# echo -n "Reloading $DESC configuration..."
	# d_reload
	# echo "done."
  #;;
  restart|force-reload)
	#
	#	If the "reload" option is implemented, move the "force-reload"
	#	option to the "reload" entry above. If not, "force-reload" is
	#	just the same as "restart".
	#
	echo -n "Restarting $DESC: $NAME"
	d_stop
	# One second might not be time enough for a daemon to stop, 
	# if this happens, d_start will fail (and dpkg will break if 
	# the package is being upgraded). Change the timeout if needed
	# be, or change d_stop to have start-stop-daemon use --retry. 
	# Notice that using --retry slows down the shutdown process somewhat.
	sleep 1
	d_start
	echo "."
	;;
  *)
	echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload}" >&2
	exit 3
	;;
esac

exit 0


... as you can see, essentially a verbatim copy of the skeleton file. Tinymush is not a debian package, i'm not sure if that makes a difference to the start-stop daemon though, I hope someone can help.

---

### Post by wdhasek on 2007-05-16
oh i appologize, here is the tinymush website, you can download the files for free, if any of 

[http://tinymush.sourceforge.net/](http://tinymush.sourceforge.net/)

if the daemon won't work, are there any other approaches to make the shell script run automatically when the computer boots?

---

### Post by gombadi on 2007-05-16
The install documentation on the tinyMUSH site says to start the server you cd to the directory and then run ./Startmush
It may require adding a -d /tinymush/game to the start-stop-daemon line to change to the correct directory before running.

Another thing - is it  running the server as root?
Is that what is needed and desired?

start-stop-daemon has the option to change to a user before running the server and it may be a worthwhile option. You will have to make sure it is able to open ports and write to files if you change the user.

Let us know if the change of directory fixes the problem.

---

### Post by Pobega on 2007-05-16
The only way I can thinking of is symbolically linking the script in /etc/rc2.d/, other than that I really don't know. Symbolically linking it DOES work, I've symbolically linked my iptables script and it works like a charm.

---

### Post by gombadi on 2007-05-16
The symbolic link will work when the machine boots up and switches to run-level 2. The system will run the scripts in /etc/rc2.d/S*   For it to work though it will need your script to be called /etc/init.d/tinymush and to boot up the machine.

One other thing I thought of was to run the start-stop-daemon command from the command line yourself like -
start-stop-daemon --start --pidfile /tinymush/game/netmush.pid --exec /tinymush/game/Startmush

Do it from the root directory, where start-stop-daeom normally runs things and also from the /tinymush/game directory to see if it gives any errors.

---

### Post by wdhasek on 2007-05-17
i appologize the symbolic linking does work i only needed to add a short line directing the shell script to the tinymush directory. I'm completely new to linux so i wasn't sure if a daemon was neccessary, but i guess not. thank you for all your help

---

