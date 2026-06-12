---
title: "Apache 2 and user permissions"
date: 2007-03-02
forum: Server Platforms
---

### Post by godsyn on 2007-03-02
**_NOTICE : _**This post's topic should be changed, as it is no longer about user permissions. It has evolved into a general hodge-podge of my issues getting apache2 to work properly. My latest issue can be found starting at [post #5]("http://www.ubuntuforums.org/showthread.php?t=374690#post2242204").
----- Begin original post ------

I've recently installed a lamp server, and am having issues serving any documents. Any request to any file on the server via http results in a 403.
I assume that I need to chown -r the dir the htdocs reside in, and apache is pointing to, but would like to give apache its own user/group (default www-data?) for security reasons.

Step 1 : creating a new user/group from a shell
Step 2 : chown - R (user) : (group) <directory>
Step 3 : restart apache and PREY the 403s are gone.

I can handle step 3, and am pretty sure about step 2, but I'm absolutely clueless if this will solve my issue (I'm just guessing).

ANY insight to would be greatly appreciated.

httpd 403 ](*,) 

(i've been working on this for 6 hours now)



Server : ubuntu edgy 6.10
behind a router w/80 forwarded to it
setup to accept connections from *
user / group in apache2.conf = www-data (default)
apache is setup as a service, and has been reset.
having to ssh from remote.

(turned out to be user incompetence, and after chmodding/chowning the served files, all is well in this regard.)

---

### Post by Mr. C. on 2007-03-02
Apache needs read access to files, and read/examine access for the entire directory tree down to the leaf nodes (html pages, etc.).  If you want to serve a page

It is wise to have a user/group dedicated to apache.

Verify that apache is actually running with that user/group you setup.

MrC

---

### Post by gaten on 2007-03-03
Like the poster above said, Apache needs only read permission on files and rx permission on directories. All of the documents my website serves are like so:

```
-rwxr-xr-x 1 root root  9687 2007-02-27 17:06 contact.html
-rwxr-xr-x 1 root root 11016 2006-12-19 15:15 contactus.html
-rwxr-xr-x 1 root root  2827 2007-02-26 16:35 ie.css
drwxr-xr-x 2 root root  4096 2007-02-14 23:15 images
-rwxr-xr-x 1 root root  4323 2007-02-27 17:10 index.html
-rwxr-xr-x 1 root root  4599 2007-02-17 15:17 index.html.bak
-rwxr-xr-x 1 root root  3270 2007-02-26 18:23 main.css
drwxr-xr-x 3 root root  4096 2007-02-26 17:00 pics

```As you can see, the webserver doesnt even own the file (increased security) and can only read from them, so that isn't your problem. Post you sites conf (the one located in /etc/apache2/site-enabled/) and we'll go from there. Also, read up on that config at apache's website.

---

### Post by godsyn on 2007-03-03
working...

---

### Post by godsyn on 2007-03-03
new issue : service isn't starting. I have to ssh in and sudo apache2 -k start to start my server.

---

### Post by Mr. C. on 2007-03-03
Typically when you add the package via Synaptic or other, you will get init scripts in /etc/init.d, and symlinks will be created in /etc/rcN.d, where N is the run level for which the service starts or stops.

Check to see if you have the init script in /etc/init.d/ or in rc*.d:

 find /etc/init.d /etc/rc*.d -name "*apache*" -ls

and see what you get back.  If the script exists, just not configured for startup, you can use update-rc.d:

update-rc.d apache2 start 90 2 3 4 5 . stop 10 0 1 6 .

These describe the runlevels and priority for starting/stopping the service at change of runlevels (and hence boot or shutdown).

MrC

---

### Post by godsyn on 2007-03-04
```
10912734    8 -rwxr-xr-x   1 root     root         4705 Sep 27 12:54 /etc/init.d/apache2
10912747    0 lrwxrwxrwx   1 root     root           17 Mar  2 14:47 /etc/rc0.d/K91apache2 -> ../init.d/apache2
10912748    0 lrwxrwxrwx   1 root     root           17 Mar  2 14:47 /etc/rc1.d/K91apache2 -> ../init.d/apache2
10912750    0 lrwxrwxrwx   1 root     root           17 Mar  2 14:47 /etc/rc2.d/S91apache2 -> ../init.d/apache2
10912751    0 lrwxrwxrwx   1 root     root           17 Mar  2 14:47 /etc/rc3.d/S91apache2 -> ../init.d/apache2
10912752    0 lrwxrwxrwx   1 root     root           17 Mar  2 14:47 /etc/rc4.d/S91apache2 -> ../init.d/apache2
10912753    0 lrwxrwxrwx   1 root     root           17 Mar  2 14:47 /etc/rc5.d/S91apache2 -> ../init.d/apache2
10912749    0 lrwxrwxrwx   1 root     root           17 Mar  2 14:47 /etc/rc6.d/K91apache2 -> ../init.d/apache2
```
are the results... whats that mean?

---

### Post by Mr. C. on 2007-03-04
Scripts are run in numeric order as run levels change.  The S prefix means start, the K prefix means kill.

Read week 4 Notes:

[http://cis68c1.mikecappella.com/calendar.php](http://cis68c1.mikecappella.com/calendar.php)

MrC

---

### Post by godsyn on 2007-03-04
Ok, so how can I use this data to figure out why Apache isn't running at boot?

---

### Post by Mr. C. on 2007-03-04
Hopefullly you learned how the script and links work.  Now you can test them out manually to see if there's some error.

Stop apache with :

  /etc/rc3.d/S91apache2 stop

This runs the apache2 script and shuts down apache.  If this fails, you've determine where the problem is and need to examine the results.

Start it up again with 

  /etc/rc3.d/S91apache2 start

If this starts apache, you know the script is working, and the links are correctly installed to cause launch when the system changes run levels.  If this works, and apache is still not starting, there is some other problem.  You will have to examine your logs for what is failing.  If the scripts work manually, they will work when the system comes up.

MrC

---

### Post by godsyn on 2007-03-04
/etc/rc3.d/S91apache2 start
echo's no text, places me back @ the prompt, and noting is found in file /var/log/apache2/error.log pertaining to me attempting to stop / start the service.

The last line in error.log is > [Sun Mar 04 23:15:50 2007] [notice] caught SIGTERM, shutting downfrom where I stopped the service via apache2 -k stop prior to apptempting the above lines. Any insight is greatly appreciated, and thank you all very much for the previous help. Started apache2 again with apache2 -k start.. as that is having to suffice, for now.

---

### Post by Mr. C. on 2007-03-04
I'm happy to help.

Your output from the scripts should be:

 * Stopping apache 2.0 web server...
   ...done.

and 

 * Starting apache 2.0 web server...
   ...done.

Your /var/log/apache2/error.log would look like:

[Sun Mar 04 20:34:38 2007] [notice] caught SIGTERM, shutting down
[Sun Mar 04 20:35:14 2007] [notice] Apache/2.0.55 (Ubuntu) configured -- resuming normal operations


Therefore, we can now conclude your startup script itself is not functional.  Please post /etc/init.d/apache2 here, and I'll look it over.

MrC

---

### Post by godsyn on 2007-03-05
```
remote@synserv:/$ sudo apache2 -k stop
Password:
remote@synserv:/$ /etc/rc3.d/S91apache2 stop
 * Stopping apache 2.0 web server...                                                                                   [ ok ]
remote@synserv:/$ /etc/rc3.d/S91apache2 start
remote@synserv:/$ sudo /etc/rc3.d/S91apache2 start
remote@synserv:/$ please?
-bash: please?: command not found
remote@synserv:/$ /etc/rc3.d/S91apache2 stop
 * Stopping apache 2.0 web server...                                                                                   [ ok ]
remote@synserv:/$ /etc/rc3.d/S91apache2 stop
 * Stopping apache 2.0 web server...                                                                                   [ ok ]
```
odd... I can stop it many times?
nothing in my /var/log/apache2/error.log

---

### Post by godsyn on 2007-03-05
apache2
```
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

### Post by Mr. C. on 2007-03-05
Be sure /etc/default/apache2  contains:

NO_START=0

If not, change it to 0.  Then try the startup script.

If that doesn't solve the problem, edit  /etc/default/rcS and set:

set VERBOSE=yes

and retry the startup script.  You can change it back later when the init script works.

Report back any output.

( and to your question about stopping multiiple times, no it cannot be.  The kill script just outputs OK if there are no important errors)

MrC

---

### Post by godsyn on 2007-03-06
it was 1. set to 0
received 
```
remote@synserv:/etc/default$ /etc/rc3.d/S91apache2 start
mkdir: cannot create directory `/var/run/apache2': Permission denied
```
when attemping to run. VERBOSE=yes is the other file.
sooo...
```
remote@synserv:/var/run$ sudo mkdir apache2
remote@synserv:/var/run$ /etc/rc3.d/S91apache2 start
chown: changing ownership of `/var/lock/apache2': Operation not permitted
```
/cry
(update)
```
sudo chown -R www-data:www-data /var/lock/apache2
```
All is well, again. Thank you all so much!

---

### Post by Mr. C. on 2007-03-06
> it was 1. set to 0

This was the problem; changing to 0 was the solution.

Unless you've changed your prompt, $ indicates to me you are not root when you try starting apache:

remote@synserv:/etc/default$ /etc/rc3.d/S91apache2 start

You need to be root or use sudo:

$ sudo /etc/rc3.d/S91apache2 start

You will be able to stop crying after that... 

MrC

---

