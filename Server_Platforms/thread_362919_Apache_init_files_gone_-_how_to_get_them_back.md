---
title: "Apache init files gone - how to get them back"
date: 2007-02-16
forum: Server Platforms
---

### Post by CptFuzzy on 2007-02-16
Using Ubuntu 6.10 (i'm new to ubuntu, but i've used apache before with RedHat)

While trying to trouble-shoot problems installing apache2, i deleted /etc/init.d/apache* in the hopes that reinstalling (using aptitude) would reconfigure apache2 and also install the missing init file.  It did not - how can i force the reinstall of apache2 to fully reconfigure and install all files like /etc/init.d/apach2 ?

after removing apache 1.3, I've tried :

aptitude reinstall apache2
 dpkg-reconfigure apache2
 dpkg --force-configure apache2 (error)
dpkg --unpack /var/cache/apt/archives/apache2_2.0.55-4ubuntu4_i386.deb 

nothing seems to work... any ideas?

---

### Post by captfats on 2007-02-21
Ok I've done the same thing and going mad trying to get it back? Does anyone have an answer???

---

### Post by Brazen on 2007-02-21
```
sudo apt-get -y --purge remove apache2 && sudo apt-get -y install apache2
```

---

### Post by CptFuzzy on 2007-02-21
Thanks... but still nothing

sudo apt-get -y --purge remove apache2 && sudo apt-get -y install apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  apache2
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  apache2*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 81.9kB disk space will be freed.
(Reading database ... 251933 files and directories currently installed.)
Removing apache2 ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  apache2
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/36.0kB of archives.
After unpacking 81.9kB of additional disk space will be used.
Selecting previously deselected package apache2.
(Reading database ... 251933 files and directories currently installed.)
Unpacking apache2 (from .../apache2_2.0.55-4ubuntu4_i386.deb) ...
Setting up apache2 (2.0.55-4ubuntu4) ...

l /etc/init.d/apache*
ls: /etc/init.d/apache*: No such file or directory

---

### Post by Brazen on 2007-02-21
That's surprising.  I've seen that fix missing or bad config files, I figured it would work the same for init.d scripts.  Well you can use this info to recreate the file...

ls -l /etc/init.d/apache2:```
-rwxr-xr-x 1 root root 4705 2006-07-26 13:01 /etc/init.d/apache2
```

nano /etc/init.d/apache2:```
#!/bin/bash -e
#
# apache2		This init.d script is used to start apache2.
#			It basically just calls apache2ctl.

ENV="env -i LANG=C PATH=/usr/local/bin:/usr/bin:/bin"

#edit /etc/default/apache2 to change this.
NO_START=0

set -e
if [ -x /usr/sbin/apache2 ] ; then
	HAVE_APACHE2=1
else
	exit 0
fi

. /lib/lsb/init-functions

test -f /etc/default/rcS && . /etc/default/rcS
test -f /etc/default/apache2 && . /etc/default/apache2
if [ "$NO_START" != "0" -a "$1" != "stop" ]; then 
        [ "$VERBOSE" != "no" ] && log_warning_msg "Not starting apache2 - edit /etc/default/apache2 and change NO_START to be 0.";
        exit 0;
fi

APACHE2="$ENV /usr/sbin/apache2"
APACHE2CTL="$ENV /usr/sbin/apache2ctl"

apache_stop() {
	PID=""
	PIDFILE=""
	AP_CONF=/etc/apache2/apache2.conf

	# apache2 allows more than PidFile entry in the config but only the
	# last found in the config is used; we attempt to follow includes
	# here, but only first-level includes are supported, not nested ones

	for i in $AP_CONF `awk '$1 ~ /^\s*[Ii]nclude$/ && $2 ~ /^\// {print $2}' $AP_CONF`; do
		PIDFILE=`grep -i ^PidFile $i | tail -n 1 | awk '{print $2}'`
		if [ -e "$PIDFILE" ]; then
			PID=`cat $PIDFILE`
		fi
	done
	
	errors=`$APACHE2 -t 2>&1`
	if [ $? = 0 ]; then
		# if the config is ok than we just stop normaly

		if [ -n "$PID" ]
		then
			$APACHE2CTL stop

			CNT=0
			while [ 1 ]
			do
				CNT=$(expr $CNT + 1)
		
				[ ! -d /proc/$PID ] && break

				if [ $CNT -gt 60 ]
				then
					if [ "$VERBOSE" != "no" ]; then
						echo " ... failed!"
						echo "Apache2 failed to honor the stop command, please investigate the situation by hand."
					fi
					return 1
				fi

				sleep 1
			done
		else
			if [ "$VERBOSE" != "no" ]; then
				echo -n " ... no pidfile found! not running?"
			fi
		fi

	else
		[ "$VERBOSE" != "no" ] && echo "$errors"

		# if we are here something is broken and we need to try
		# to exit as nice and clean as possible

		# if pidof is null for some reasons the script exits automagically
		# classified as good/unknown feature
		PIDS=`pidof apache2` || true

		REALPID=0
		# if there is a pid we need to verify that belongs to apache2
		# for real
		for i in $PIDS; do
			if [ "$i" = "$PID" ]; then
				# in this case the pid stored in the
				# pidfile matches one of the pidof apache
				# so a simple kill will make it
				REALPID=1
			fi
		done

		if [ $REALPID = 1 ]; then
			# in this case everything is nice and dandy
			# and we kill apache2
			kill $PID
		else
			# this is the worst situation... just kill all of them
			#for i in $PIDS; do
			#	kill $i
			#done
			# Except, we can't do that, because it's very, very bad
			if [ "$PIDS" ] && [ "$VERBOSE" != "no" ]; then
                                echo " ... failed!"
			        echo "You may still have some apache2 processes running.  There are"
 			        echo "processes named 'apache2' which do not match your pid file,"
			        echo "and in the name of safety, we've left them alone.  Please review"
			        echo "the situation by hand."
                        fi
                        return 1
		fi
	fi
}

# Stupid hack to keep lintian happy. (Warrk! Stupidhack!).
case $1 in
	start)
		[ -f /etc/apache2/httpd.conf ] || touch /etc/apache2/httpd.conf
		# ssl_scache shouldn't be here if we're just starting up.
		[ -f /var/run/apache2/ssl_scache ] && rm -f /var/run/apache2/*ssl_scache*
		# /var/run and /var/lock could be on a tmpfs
		[ ! -d /var/run/apache2 ] && mkdir /var/run/apache2
		[ ! -d /var/lock/apache2 ] && mkdir /var/lock/apache2
		# Make sure /var/lock/apache2 has the correct permissions
		chown www-data /var/lock/apache2

		log_begin_msg "Starting apache 2.0 web server..."
		if $APACHE2CTL startssl; then
                        log_end_msg 0
                else
                        log_end_msg 1
                fi
	;;
	stop)
		log_begin_msg "Stopping apache 2.0 web server..."
		if apache_stop; then
                        log_end_msg 0
                else
                        log_end_msg 1
                fi
	;;
	reload)
		log_begin_msg "Reloading apache 2.0 configuration..."
		if $APACHE2CTL graceful $2 ; then
                        log_end_msg 0
                else
                        log_end_msg 1
                fi
	;;
	restart | force-reload)
		log_begin_msg "Forcing reload of apache 2.0 web server..."
		if ! apache_stop; then
                        log_end_msg 1
                fi
		if $APACHE2CTL startssl; then
                        log_end_msg 0
                else
                        log_end_msg 1
                fi
	;;
	status)
		exit 4
	;;
	*)
		echo "Usage: /etc/init.d/apache2 start|stop|restart|reload|force-reload" >&2
		exit 2
	;;
esac
```

---

### Post by CptFuzzy on 2007-02-21
thanks again.. but I think my problems are bigger that the init files... isn't there supposed to be more then this in the apache deb file?

# dpkg-deb --contents /var/cache/apt/archives/apache2_2.0.55-4ubuntu4_i386.deb 
drwxr-xr-x root/root         0 2006-09-27 12:54 ./
drwxr-xr-x root/root         0 2006-09-27 12:54 ./usr/
drwxr-xr-x root/root         0 2006-09-27 12:54 ./usr/share/
drwxr-xr-x root/root         0 2006-09-27 12:54 ./usr/share/doc/
drwxr-xr-x root/root         0 2006-09-27 12:55 ./usr/share/doc/apache2/
-rw-r--r-- root/root     31769 2006-09-27 12:41 ./usr/share/doc/apache2/copyright
-rw-r--r-- root/root     24184 2006-09-27 12:41 ./usr/share/doc/apache2/changelog.Debian.gz
#

---

### Post by etcpool on 2007-02-21
if  you have your configuration files , back them up, purge the package then reinstall it and restore your configuration..


hope this helps

---

### Post by Brazen on 2007-02-22
> **CptFuzzy said:**
> thanks again.. but I think my problems are bigger that the init files... isn't there supposed to be more then this in the apache deb file?

# dpkg-deb --contents /var/cache/apt/archives/apache2_2.0.55-4ubuntu4_i386.deb 
drwxr-xr-x root/root         0 2006-09-27 12:54 ./
drwxr-xr-x root/root         0 2006-09-27 12:54 ./usr/
drwxr-xr-x root/root         0 2006-09-27 12:54 ./usr/share/
drwxr-xr-x root/root         0 2006-09-27 12:54 ./usr/share/doc/
drwxr-xr-x root/root         0 2006-09-27 12:55 ./usr/share/doc/apache2/
-rw-r--r-- root/root     31769 2006-09-27 12:41 ./usr/share/doc/apache2/copyright
-rw-r--r-- root/root     24184 2006-09-27 12:41 ./usr/share/doc/apache2/changelog.Debian.gz
#

you might try running:```
sudo apt-get clean
``` and then re-run the command I posted above.  You might also check your /etc/apt/sources.list and make sure it is a valid configuration.

---

### Post by Brazen on 2007-02-22
You know, I think you might be installing the wrong package.  You might try installing "apache2-common" and see what that does.

I'm not really sure because I've always installed php on my Apache servers, so the command I use is:```
sudo apt-get -y install php5-gd php5-mysql
```and that grabs all the dependencies for Apache2 and PHP.

---

