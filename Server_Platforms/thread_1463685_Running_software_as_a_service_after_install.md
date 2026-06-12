---
title: "Running software as a service after install"
date: 2010-04-27
forum: Server Platforms
---

### Post by divided on 2010-04-27
Hi all, still a linux noob here.  I downloaded openssh and did a ./configure and a make install.  How can I run openssh as a service?  When I try /etc/init.d/ssh restart it doesn't work.  It's installed in /etc/openssh.

Any help would be appreciated and thanks in advance!

---

### Post by HermanAB on 2010-04-27
The SSH daemon is actually called 'sshd'.  The client program is called 'ssh'.

---

### Post by divided on 2010-04-27
> **HermanAB said:**
> The SSH daemon is actually called 'sshd'.  The client program is called 'ssh'.

Thanks for the reply.  When I do /etc/init.d/ssh or sshd restart, I get "No such file or directory."

---

### Post by VernieR on 2010-04-27
Is there any reason why you want to compile and install openssh from source?

It's easier to install it from the repositories:

```
sudo apt-get install openssh-server
```

---

### Post by divided on 2010-04-27
> **VernieR said:**
> Is there any reason why you want to compile and install openssh from source?

It's easier to install it from the repositories:

```
sudo apt-get install openssh-server
```

When I install from the repositories, it installs version 5.1.  I need to install version 5.4 (or above).  I've tried to update the version from the repositories, but it says the 5.1 is the most current version.

---

### Post by VernieR on 2010-04-27
> **divided said:**
> When I install from the repositories, it installs version 5.1.  I need to install version 5.4 (or above).  I've tried to update the version from the repositories, but it says the 5.1 is the most current version.

Ok, that makes sense :P

Lets see, I'm not very experienced with this.

Apparently installing that way doesn't create the start stop script. You'll have to create one yourself.

this is the default /etc/init.d/ssh script on my 9.10 server. I guess that could work, you may have to change some loctions because some files are in other places.

```
#! /bin/sh

### BEGIN INIT INFO
# Provides:		sshd
# Required-Start:	$remote_fs $syslog
# Required-Stop:	$remote_fs $syslog
# Default-Start:	2 3 4 5
# Default-Stop:		1
# Short-Description:	OpenBSD Secure Shell server
### END INIT INFO

set -e

# /etc/init.d/ssh: start and stop the OpenBSD "secure shell(tm)" daemon

test -x /usr/sbin/sshd || exit 0
( /usr/sbin/sshd -\? 2>&1 | grep -q OpenSSH ) 2>/dev/null || exit 0

export SSHD_OOM_ADJUST=-17
if test -f /etc/default/ssh; then
    . /etc/default/ssh
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
    # forget it if we're trying to start, and /etc/ssh/sshd_not_to_be_run exists
    if [ -e /etc/ssh/sshd_not_to_be_run ]; then 
	if [ "$1" = log_end_msg ]; then
	    log_end_msg 0
	fi
	if ! run_by_init; then
	    log_action_msg "OpenBSD Secure Shell server not in use (/etc/ssh/sshd_not_to_be_run)"
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
    if [ ! -d /var/run/sshd ]; then
	mkdir /var/run/sshd
	chmod 0755 /var/run/sshd
    fi
}

check_config() {
    if [ ! -e /etc/ssh/sshd_not_to_be_run ]; then
	/usr/sbin/sshd -t || exit 1
    fi
}

export PATH="${PATH:+$PATH:}/usr/sbin:/sbin"

case "$1" in
  start)
	check_privsep_dir
	check_for_no_start
	check_dev_null
	log_daemon_msg "Starting OpenBSD Secure Shell server" "sshd"
	if start-stop-daemon --start --quiet --oknodo --pidfile /var/run/sshd.pid --exec /usr/sbin/sshd -- $SSHD_OPTS; then
	    log_end_msg 0
	else
	    log_end_msg 1
	fi
	;;
  stop)
	log_daemon_msg "Stopping OpenBSD Secure Shell server" "sshd"
	if start-stop-daemon --stop --quiet --oknodo --pidfile /var/run/sshd.pid; then
	    log_end_msg 0
	else
	    log_end_msg 1
	fi
	;;

  reload|force-reload)
	check_for_no_start
	check_config
	log_daemon_msg "Reloading OpenBSD Secure Shell server's configuration" "sshd"
	if start-stop-daemon --stop --signal 1 --quiet --oknodo --pidfile /var/run/sshd.pid --exec /usr/sbin/sshd; then
	    log_end_msg 0
	else
	    log_end_msg 1
	fi
	;;

  restart)
	check_privsep_dir
	check_config
	log_daemon_msg "Restarting OpenBSD Secure Shell server" "sshd"
	start-stop-daemon --stop --quiet --oknodo --retry 30 --pidfile /var/run/sshd.pid
	check_for_no_start log_end_msg
	check_dev_null log_end_msg
	if start-stop-daemon --start --quiet --oknodo --pidfile /var/run/sshd.pid --exec /usr/sbin/sshd -- $SSHD_OPTS; then
	    log_end_msg 0
	else
	    log_end_msg 1
	fi
	;;

  try-restart)
	check_privsep_dir
	check_config
	log_daemon_msg "Restarting OpenBSD Secure Shell server" "sshd"
	set +e
	start-stop-daemon --stop --quiet --retry 30 --pidfile /var/run/sshd.pid
	RET="$?"
	set -e
	case $RET in
	    0)
		# old daemon stopped
		check_for_no_start log_end_msg
		check_dev_null log_end_msg
		if start-stop-daemon --start --quiet --oknodo --pidfile /var/run/sshd.pid --exec /usr/sbin/sshd -- $SSHD_OPTS; then
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
	status_of_proc -p /var/run/sshd.pid /usr/sbin/sshd sshd && exit 0 || exit $?
	;;

  *)
	log_action_msg "Usage: /etc/init.d/ssh {start|stop|reload|force-reload|restart|try-restart|status}"
	exit 1
esac

exit 0

```

---

### Post by divided on 2010-04-27
> **VernieR said:**
> Ok, that makes sense :P

Lets see, I'm not very experienced with this.

Apparently installing that way doesn't create the start stop script. You'll have to create one yourself.

this is the default /etc/init.d/ssh script on my 9.10 server. I guess that could work, you may have to change some loctions because some files are in other places.

```
#! /bin/sh

### BEGIN INIT INFO
# Provides:        sshd
# Required-Start:    $remote_fs $syslog
# Required-Stop:    $remote_fs $syslog
# Default-Start:    2 3 4 5
# Default-Stop:        1
# Short-Description:    OpenBSD Secure Shell server
### END INIT INFO

set -e

# /etc/init.d/ssh: start and stop the OpenBSD "secure shell(tm)" daemon

test -x /usr/sbin/sshd || exit 0
( /usr/sbin/sshd -\? 2>&1 | grep -q OpenSSH ) 2>/dev/null || exit 0

export SSHD_OOM_ADJUST=-17
if test -f /etc/default/ssh; then
    . /etc/default/ssh
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
    # forget it if we're trying to start, and /etc/ssh/sshd_not_to_be_run exists
    if [ -e /etc/ssh/sshd_not_to_be_run ]; then 
    if [ "$1" = log_end_msg ]; then
        log_end_msg 0
    fi
    if ! run_by_init; then
        log_action_msg "OpenBSD Secure Shell server not in use (/etc/ssh/sshd_not_to_be_run)"
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
    if [ ! -d /var/run/sshd ]; then
    mkdir /var/run/sshd
    chmod 0755 /var/run/sshd
    fi
}

check_config() {
    if [ ! -e /etc/ssh/sshd_not_to_be_run ]; then
    /usr/sbin/sshd -t || exit 1
    fi
}

export PATH="${PATH:+$PATH:}/usr/sbin:/sbin"

case "$1" in
  start)
    check_privsep_dir
    check_for_no_start
    check_dev_null
    log_daemon_msg "Starting OpenBSD Secure Shell server" "sshd"
    if start-stop-daemon --start --quiet --oknodo --pidfile /var/run/sshd.pid --exec /usr/sbin/sshd -- $SSHD_OPTS; then
        log_end_msg 0
    else
        log_end_msg 1
    fi
    ;;
  stop)
    log_daemon_msg "Stopping OpenBSD Secure Shell server" "sshd"
    if start-stop-daemon --stop --quiet --oknodo --pidfile /var/run/sshd.pid; then
        log_end_msg 0
    else
        log_end_msg 1
    fi
    ;;

  reload|force-reload)
    check_for_no_start
    check_config
    log_daemon_msg "Reloading OpenBSD Secure Shell server's configuration" "sshd"
    if start-stop-daemon --stop --signal 1 --quiet --oknodo --pidfile /var/run/sshd.pid --exec /usr/sbin/sshd; then
        log_end_msg 0
    else
        log_end_msg 1
    fi
    ;;

  restart)
    check_privsep_dir
    check_config
    log_daemon_msg "Restarting OpenBSD Secure Shell server" "sshd"
    start-stop-daemon --stop --quiet --oknodo --retry 30 --pidfile /var/run/sshd.pid
    check_for_no_start log_end_msg
    check_dev_null log_end_msg
    if start-stop-daemon --start --quiet --oknodo --pidfile /var/run/sshd.pid --exec /usr/sbin/sshd -- $SSHD_OPTS; then
        log_end_msg 0
    else
        log_end_msg 1
    fi
    ;;

  try-restart)
    check_privsep_dir
    check_config
    log_daemon_msg "Restarting OpenBSD Secure Shell server" "sshd"
    set +e
    start-stop-daemon --stop --quiet --retry 30 --pidfile /var/run/sshd.pid
    RET="$?"
    set -e
    case $RET in
        0)
        # old daemon stopped
        check_for_no_start log_end_msg
        check_dev_null log_end_msg
        if start-stop-daemon --start --quiet --oknodo --pidfile /var/run/sshd.pid --exec /usr/sbin/sshd -- $SSHD_OPTS; then
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
    status_of_proc -p /var/run/sshd.pid /usr/sbin/sshd sshd && exit 0 || exit $?
    ;;

  *)
    log_action_msg "Usage: /etc/init.d/ssh {start|stop|reload|force-reload|restart|try-restart|status}"
    exit 1
esac

exit 0

```

Thanks for this.  I ran this script replacing /usr/sbin/sshd with the install directory, but sftp still doesn't work.  Do I need to replace anything else in the script?

---

### Post by VernieR on 2010-04-27
> **divided said:**
> Thanks for this.  I ran this script replacing /usr/sbin/sshd with the install directory, but sftp still doesn't work.  Do I need to replace anything else in the script?

Hmmm... can't really say without trying myself. Any error messages?

---

### Post by divided on 2010-04-27
> **VernieR said:**
> Hmmm... can't really say without trying myself. Any error messages?

I'm not seeing anything in messages, syslog, or auth.log.

---

### Post by VernieR on 2010-04-27
Is the service running and listening for connections?

```

ps aux | grep sshd
netstat -l | grep ssh

```

---

### Post by divided on 2010-04-27
> **VernieR said:**
> Is the service running and listening for connections?

```

ps aux | grep sshd
netstat -l | grep ssh

```

ps gives two sshd processes:

sshd: me [priv]
sshd: me@pts/0

netstat does not list anything

---

### Post by VernieR on 2010-04-27
I'm afraid I can't help you any further. Someone else maybe?

---

### Post by divided on 2010-04-27
> **VernieR said:**
> I'm afraid I can't help you any further. Someone else maybe?

Thanks for your help with this, I appreciate it!  Anyone else have any ideas?

---

### Post by VernieR on 2010-04-27
Ok just tried on a clean 9.10 server installation in VirtualBox:

```

sudo apt-get install gcc zlib1g-dev
wget ftp://ftp.openbsd.org/pub/OpenBSD/OpenSSH/portable/openssh-5.5p1.tar.gz
tar -xfv openssh-5.5p1.tar.gz
./configure
make
sudo echo "sshd:x:74:74:Privilege-separated SSH:/var/empty/sshd:/sbin/nologin" >> /etc/passwd
sudo make install

```

this installed sshd in /usr/local/sbin/

I took the default start/stop script and replaced /usr/sbin/sshd with /usr/local/sbin/sshd and placed it at /etc/init.d/ssh

```

sudo chmod +x /etc/init.d/ssh
sudo /etc/init.d/ssh start

```

the last command returned:
```

 * Starting OpenBSD Secure Shell server sshd               [ OK ]

```

Looks good so far :D

and finally:

Logging in from outside the VM works too!

Maybe you can find what went wrong at your setup from this.

Note. I might have missed some steps in this description

---

### Post by divided on 2010-04-28
VernieR - that worked!  Thank you so much!

---

### Post by VernieR on 2010-04-28
You're welcome :)

Oh and I forgot to mention to start the service at boot you need to make links to the script:

```

sudo ln -s ../init.d/ssh /etc/rc1.d/K84ssh
sudo ln -s ../init.d/ssh /etc/rc2.d/S16ssh
sudo ln -s ../init.d/ssh /etc/rc3.d/S16ssh
sudo ln -s ../init.d/ssh /etc/rc4.d/S16ssh
sudo ln -s ../init.d/ssh /etc/rc5.d/S16ssh

```

---

