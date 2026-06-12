---
title: "multiple instances of ssh server"
date: 2010-05-30
forum: Server Platforms
---

### Post by slyyls on 2010-05-30
Hello,

I want to run 2 instances of ssh, one on the standard port, another on a higher port that will be used occasionally with password authentication instead of ssh keys.

These are the steps I have done up to now.
- copy /etc/ssh to /etc/ssh2
  - modify /etc/ssh2/sshd_config
- copy /etc/default/ssh to /etc/default/ssh2
  - modify /etc/default/ssh2 and add "-f /etc/ssh2/sshd_config" to options
- symlink /usr/sbin/sshd2 to /usr/sbin/ssh
- copy /etc/init.d/ssh to /etc/init.d/ssh2
  - modify /etc/init.d/ssh2

here is my /etc/init.d/ssh2

```
#! /bin/sh

### BEGIN INIT INFO
# Provides:		sshd2
# Required-Start:	$remote_fs $syslog
# Required-Stop:	$remote_fs $syslog
# Default-Start:	2 3 4 5
# Default-Stop:		
# Short-Description:	OpenBSD Secure Shell server
### END INIT INFO

set -e

# /etc/init.d/ssh: start and stop the OpenBSD "secure shell(tm)" daemon

test -x /usr/sbin/sshd2 || exit 0
( /usr/sbin/sshd2 -\? 2>&1 | grep -q OpenSSH ) 2>/dev/null || exit 0

umask 022

export SSHD_OOM_ADJUST=-17
if test -f /etc/default/ssh2; then
    . /etc/default/ssh2
fi

# Are we in a virtual environment that doesn't support modifying
# /proc/self/oom_adj?
if grep -q 'envID:.*[1-9]' /proc/self/status; then
    unset SSHD_OOM_ADJUST
fi

. /lib/lsb/init-functions

if [ -n "$2" ]; then
    SSHD_OPTS="$SSHD_OPTS $2"
fi

# Are we running from init?
run_by_init() {
    ([ "$previous" ] && [ "$runlevel" ]) || [ "$runlevel" = S ]
}

check_for_no_start() {
    # forget it if we're trying to start, and /etc/ssh/sshd2_not_to_be_run exists
    if [ -e /etc/ssh2/sshd2_not_to_be_run ]; then 
	if [ "$1" = log_end_msg ]; then
	    log_end_msg 0
	fi
	if ! run_by_init; then
	    log_action_msg "OpenBSD Secure Shell server not in use (/etc/ssh2/sshd2_not_to_be_run)"
	fi
	exit 0
    fi
}

check_dev_null() {
    if [ ! -c /dev/null ]; then
	if [ "$1" = log_end_msg ]; then
	    log_end_msg 1 || true
	fi
	if ! run_by_init; then
	    log_action_msg "/dev/null is not a character device!"
	fi
	exit 1
    fi
}

check_privsep_dir() {
    # Create the PrivSep empty dir if necessary
    if [ ! -d /var/run/sshd2 ]; then
	mkdir /var/run/sshd2
	chmod 0755 /var/run/sshd2
    fi
}

check_config() {
    if [ ! -e /etc/ssh2/sshd2_not_to_be_run ]; then
	/usr/sbin/sshd2 $SSHD_OPTS -t || exit 1
    fi
}

export PATH="${PATH:+$PATH:}/usr/sbin:/sbin"

case "$1" in
  start)
	check_privsep_dir
	check_for_no_start
	check_dev_null
	log_daemon_msg "Starting OpenBSD Secure Shell server" "sshd2"
	echo "$SSHD_OPTS"
	if start-stop-daemon --start --quiet --oknodo --pidfile /var/run/sshd2.pid --exec /usr/sbin/sshd2 -- $SSHD_OPTS; then
	    log_end_msg 0
	else
	    log_end_msg 1
	fi
	;;
  stop)
	log_daemon_msg "Stopping OpenBSD Secure Shell server" "sshd2"
	if start-stop-daemon --stop --quiet --oknodo --pidfile /var/run/sshd2.pid; then
	    log_end_msg 0
	else
	    log_end_msg 1
	fi
	;;

  reload|force-reload)
	check_for_no_start
	check_config
	log_daemon_msg "Reloading OpenBSD Secure Shell server's configuration" "sshd2"
	if start-stop-daemon --stop --signal 1 --quiet --oknodo --pidfile /var/run/sshd2.pid --exec /usr/sbin/sshd2; then
	    log_end_msg 0
	else
	    log_end_msg 1
	fi
	;;

  restart)
	check_privsep_dir
	check_config
	log_daemon_msg "Restarting OpenBSD Secure Shell server" "sshd2"
	start-stop-daemon --stop --quiet --oknodo --retry 30 --pidfile /var/run/sshd2.pid
	check_for_no_start log_end_msg
	check_dev_null log_end_msg
	if start-stop-daemon --start --quiet --oknodo --pidfile /var/run/sshd2.pid --exec /usr/sbin/sshd2 -- $SSHD_OPTS; then
	    log_end_msg 0
	else
	    log_end_msg 1
	fi
	;;

  try-restart)
	check_privsep_dir
	check_config
	log_daemon_msg "Restarting OpenBSD Secure Shell server" "sshd2"
	set +e
	start-stop-daemon --stop --quiet --retry 30 --pidfile /var/run/sshd2.pid
	RET="$?"
	set -e
	case $RET in
	    0)
		# old daemon stopped
		check_for_no_start log_end_msg
		check_dev_null log_end_msg
		if start-stop-daemon --start --quiet --oknodo --pidfile /var/run/sshd2.pid --exec /usr/sbin/sshd2 -- $SSHD_OPTS; then
		    log_end_msg 0
		else
		    log_end_msg 1
		fi
		;;
	    1)
		# daemon not running
		log_progress_msg "(not running)"
		log_end_msg 0
		;;
	    *)
		# failed to stop
		log_progress_msg "(failed to stop)"
		log_end_msg 1
		;;
	esac
	;;

  status)
	status_of_proc -p /var/run/sshd2.pid /usr/sbin/sshd2 sshd2 && exit 0 || exit $?
	;;

  *)
	log_action_msg "Usage: /etc/init.d/ssh2 {start|stop|reload|force-reload|restart|try-restart|status}"
	exit 1
esac

exit 0

```

When I do a "sudo /etc/init.d/ssh2 start", it starts the process, but the pid file does not get created, therefore a "sudo /etc/init.d/ssh2 stop" does not kill the process.

Does anyone have any idea what is missing?

Thanks

---

### Post by slyyls on 2010-05-30
Apparently all I had to do was add this line to /etc/ssh2/sshd_config

```
PidFile /var/run/sshd2.pid
```

Now it works.

---

### Post by nixahn on 2012-07-05
I thank the author for what turned into a howto for me; doing this in later versions required minor changes, mostly because of the migration to /etc/init/ instead of /etc/init.d; here is my instructions file (for self reference) that is a small adaptation of the original post:

1_ ```

sudo cp -r /etc/ssh /etc/ssh2
sudo vi etc/ssh2/sshd_config

```
	a_ Port ...
	b_ PidFile /var/run/ssh2.pid
2_ This step is probably obsolete: ```

sudo cp /etc/default/ssh /etc/default/ssh2
sudo vi /etc/default/ssh2

```
	a_ add "-f /etc/ssh2/sshd_config" to options
3_ ```

sudo cp /etc/init/ssh.conf /etc/init/ssh2.conf
sudo vi /etc/init/ssh2.conf

```
	a_ change all ssh for ssh2
	b_ also add "-f /etc/ssh2/sshd_config" to the exec after; this is probably the correct one now instead of in /etc/default
4_ ```
sudo ln -s /usr/sbin/sshd /usr/sbin/sshd2
```
5_ ```

sudo cp /etc/init.d/ssh /etc/init.d/ssh2
sudo vi /etc/init.d/ssh2

```
	a_ replace all sshd for sshd2, ssh for ssh2, etc;
6_ ```
sudo service ssh2 start
```

my ssh2 script
```

### BEGIN INIT INFO
# Provides:		sshd2
# Required-Start:	$remote_fs $syslog
# Required-Stop:	$remote_fs $syslog
# Default-Start:	2 3 4 5
# Default-Stop:		
# Short-Description:	OpenBSD Secure Shell server
### END INIT INFO

set -e

# /etc/init.d/ssh2: start and stop the OpenBSD "secure shell(tm)" daemon

test -x /usr/sbin/sshd2 || exit 0
( /usr/sbin/sshd2 -\? 2>&1 | grep -q OpenSSH ) 2>/dev/null || exit 0

chrooted() {
    # borrowed from udev's postinst
    # and then borrowed from initramfs-tools's preinst
    if [ "$(stat -c %d/%i /)" = "$(stat -Lc %d/%i /proc/1/root 2>/dev/null)" ]; then
	# the devicenumber/inode pair of / is the same as that of
	# /sbin/init's root, so we're *not* in a chroot and hence
	# return false.
	return 1
    fi
    return 0
}

# The init.d script is only for chroots
if [ -e /etc/init/ssh2.conf ] && ! chrooted; then
    exec /lib/init/upstart-job ssh "$@"
fi

umask 022

if test -f /etc/default/ssh2; then
    . /etc/default/ssh2
fi

. /lib/lsb/init-functions

if [ -n "$2" ]; then
    SSHD_OPTS="$SSHD_OPTS $2"
fi

# Are we running from init?
run_by_init() {
    ([ "$previous" ] && [ "$runlevel" ]) || [ "$runlevel" = S ]
}

check_for_no_start() {
    # forget it if we're trying to start, and /etc/ssh2/sshd2_not_to_be_run exists
    if [ -e /etc/ssh2/sshd2_not_to_be_run ]; then 
	if [ "$1" = log_end_msg ]; then
	    log_end_msg 0
	fi
	if ! run_by_init; then
	    log_action_msg "OpenBSD Secure Shell server not in use (/etc/ssh2/sshd2_not_to_be_run)"
	fi
	exit 0
    fi
}

check_dev_null() {
    if [ ! -c /dev/null ]; then
	if [ "$1" = log_end_msg ]; then
	    log_end_msg 1 || true
	fi
	if ! run_by_init; then
	    log_action_msg "/dev/null is not a character device!"
	fi
	exit 1
    fi
}

check_privsep_dir() {
    # Create the PrivSep empty dir if necessary
    if [ ! -d /var/run/sshd2 ]; then
	mkdir /var/run/sshd2
	chmod 0755 /var/run/sshd2
    fi
}

check_config() {
    if [ ! -e /etc/ssh2/sshd2_not_to_be_run ]; then
	/usr/sbin/sshd2 $SSHD_OPTS -t || exit 1
    fi
}

export PATH="${PATH:+$PATH:}/usr/sbin:/sbin"

case "$1" in
  start)
	check_privsep_dir
	check_for_no_start
	check_dev_null
	log_daemon_msg "Starting OpenBSD Secure Shell server" "sshd2"
	if start-stop-daemon --start --quiet --oknodo --pidfile /var/run/sshd2.pid --exec /usr/sbin/sshd2 -- $SSHD_OPTS; then
	    log_end_msg 0
	else
	    log_end_msg 1
	fi
	;;
  stop)
	log_daemon_msg "Stopping OpenBSD Secure Shell server" "sshd2"
	if start-stop-daemon --stop --quiet --oknodo --pidfile /var/run/sshd2.pid; then
	    log_end_msg 0
	else
	    log_end_msg 1
	fi
	;;

  reload|force-reload)
	check_for_no_start
	check_config
	log_daemon_msg "Reloading OpenBSD Secure Shell server's configuration" "sshd2"
	if start-stop-daemon --stop --signal 1 --quiet --oknodo --pidfile /var/run/sshd2.pid --exec /usr/sbin/sshd2; then
	    log_end_msg 0
	else
	    log_end_msg 1
	fi
	;;

  restart)
	check_privsep_dir
	check_config
	log_daemon_msg "Restarting OpenBSD Secure Shell server" "sshd2"
	start-stop-daemon --stop --quiet --oknodo --retry 30 --pidfile /var/run/sshd2.pid
	check_for_no_start log_end_msg
	check_dev_null log_end_msg
	if start-stop-daemon --start --quiet --oknodo --pidfile /var/run/sshd2.pid --exec /usr/sbin/sshd2 -- $SSHD_OPTS; then
	    log_end_msg 0
	else
	    log_end_msg 1
	fi
	;;

  try-restart)
	check_privsep_dir
	check_config
	log_daemon_msg "Restarting OpenBSD Secure Shell server" "sshd2"
	set +e
	start-stop-daemon --stop --quiet --retry 30 --pidfile /var/run/sshd2.pid
	RET="$?"
	set -e
	case $RET in
	    0)
		# old daemon stopped
		check_for_no_start log_end_msg
		check_dev_null log_end_msg
		if start-stop-daemon --start --quiet --oknodo --pidfile /var/run/sshd2.pid --exec /usr/sbin/sshd2 -- $SSHD_OPTS; then
		    log_end_msg 0
		else
		    log_end_msg 1
		fi
		;;
	    1)
		# daemon not running
		log_progress_msg "(not running)"
		log_end_msg 0
		;;
	    *)
		# failed to stop
		log_progress_msg "(failed to stop)"
		log_end_msg 1
		;;
	esac
	;;

  status)
	status_of_proc -p /var/run/sshd2.pid /usr/sbin/sshd2 sshd2 && exit 0 || exit $?
	;;

  *)
	log_action_msg "Usage: /etc/init.d/ssh2 {start|stop|reload|force-reload|restart|try-restart|status}"
	exit 1
esac

exit 0

```

---

### Post by Shockburner on 2012-09-04
Thanks guys. I had the same problem, and this solved all my issues.

---

