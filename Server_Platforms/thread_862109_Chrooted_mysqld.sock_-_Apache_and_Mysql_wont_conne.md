---
title: "Chrooted: mysqld.sock - Apache and Mysql wont connect with a soft link"
date: 2008-07-17
forum: Server Platforms
---

### Post by zeepal on 2008-07-17
Hello Guys,

I hope you guys can help me.

This is my first time setting up a Linux server. I have decided to go with Ubuntu (love it).

I have apache installed and mysql and i have chrooted both in separate folders (/chroot/httpd/ and /chroot/mysql/).
I have found different tutorials and howtos on getting the 2 to talk via mysqld.sock and it works if i hard link it (ln /chroot/mysql/var/run/mysqld/mysqld.sock /chroot/httpd/var/run/mysqld/mysqld.sock) but if i soft link it (-s) it cant connect to mysql getting the following error on browse



Warning: mysql_connect() [function.mysql-connect]: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) in /var/www/index.php on line 1
Could not connect to MySQL: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)


would like to note i get that error even if there not linked at all.



Could you please let me know which permissions for which files and folders requires what and if there is anything that needs to be done that i may have not tried or done yet.

I have tried different combos myself and haven't come up with it (probably missing something simple always do).



My server details are below:

OS: Ubuntu 8.04 LTS Server Edition
CPU: Intel Duo 2.2 64bit
Motherboard: ASUS P5KPL-VM
Ram: 2gb (1 stick ddr2 800mhz)
Hard Drive: 500gb (sata 3gbs)

connection via ssh (putty)


MYSQL:

mysql  Ver 14.12 Distrib 5.0.51a, for debian-linux-gnu (x86_64) using readline 5.2

Apache:

Server version: Apache/2.2.8 (Ubuntu)
Server built:   Jun 25 2008 13:54:43



Any help would be very helpful.

---

### Post by PraysToPan on 2008-07-17
> **zeepal said:**
> Hello Guys,


I have apache installed and mysql and i have chrooted both in separate folders (/chroot/httpd/ and /chroot/mysql/).
I have found different tutorials and howtos on getting the 2 to talk via mysqld.sock and it works if i hard link it (ln /chroot/mysql/var/run/mysqld/mysqld.sock /chroot/httpd/var/run/mysqld/mysqld.sock) but if i soft link it (-s) it cant connect to mysql getting the following error on browse





You can't soft link to a file outside of a chroot from inside a chroot.  This would defeat the purpose of the chroot.  By extension, you can't soft link from one chroot environment to another chroot environment.  An attacker could then arbitrarily soft link to any file on the system which wouldn't be good.  Hard links are the best option.  If you can't hard link because they are on different filesystems, you can use mount with the --bind option to mount a directory somewhere else.  Run something like this outside of any chroot:

sudo mount --bind /chroota/dir /chrootb/dir

Of course you have to make sure the mount point is already created in chrootb.

In your /etc/fstab you can add:

/chroota/dir  /chrootb/dir  none  bind  0 0
 
I'm not an expert, so don't count on the security of this.  Chroots aren't necessarily secure anyhow;  they are just a tool in the chain of security.

There is one exception to this rule.  You can soft link to a file inside the chroot from a non chrooted environment.

Jon

---

### Post by zeepal on 2008-07-17
Thanks PraysToPan,

I did remember reading some where that soft or hard links was a security issue.
So soft is the security issue but hard is ok np.

Is it possible you could help me get the hard link to link on starting mysql (/etc/init.d/mysql) or isnt that possible via that script because i did add the ln command in the start section at the end of it and a remove just before it to make sure the old link didnt exist for when the new link is created but the link never seems to happen and i can find an error to help me find out why.

Here is my current /etc/init.d/mysql file the rm and ln are commented since i have left them out for now.

```


#!/bin/bash
#
### BEGIN INIT INFO
# Provides:          mysql
# Required-Start:    $remote_fs $syslog mysql-ndb
# Required-Stop:     $remote_fs $syslog mysql-ndb
# Should-Start:      $network $named $time
# Should-Stop:       $network $named $time
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start and stop the mysql database server daemon
# Description:       Controls the main MySQL database server daemon "mysqld"
#                    and its wrapper script "mysqld_safe".
### END INIT INFO
#
set -e
set -u
${DEBIAN_SCRIPT_DEBUG:+ set -v -x}

test -x /usr/sbin/mysqld || exit 0

. /lib/lsb/init-functions
. /etc/default/mysql-chroot

SELF=$(cd $(dirname $0); pwd -P)/$(basename $0)
CONF=/etc/mysql/my.cnf
MYADMIN="/usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf"

# priority can be overriden and "-s" adds output to stderr
ERR_LOGGER="logger -p daemon.err -t /etc/init.d/mysql -i"

# Safeguard (relative paths, core dumps..)
cd /
umask 077

# mysqladmin likes to read /root/.my.cnf. This is usually not what I want
# as many admins e.g. only store a password without a username there and
# so break my scripts.
export HOME=/etc/mysql/

## Fetch a particular option from mysql's invocation.
#
# Usage: void mysqld_get_param option
mysqld_get_param() {
        /usr/sbin/mysqld --print-defaults \
                | tr " " "\n" \
                | grep -- "--$1" \
                | tail -n 1 \
                | cut -d= -f2
}

## Do some sanity checks before even trying to start mysqld.
sanity_checks() {
  # check for config file
  if [ ! -r /etc/mysql/my.cnf ]; then
    log_warning_msg "$0: WARNING: /etc/mysql/my.cnf cannot be read. See README.Debian.gz"
    echo                "WARNING: /etc/mysql/my.cnf cannot be read. See README.Debian.gz" | $ERR_LOGGER
  fi

  # check for diskspace shortage
  datadir=`mysqld_get_param datadir`
  if LC_ALL=C BLOCKSIZE= df --portability $CHROOT_DIR$datadir/. | tail -n 1 | awk '{ exit ($4>4096) }'; then
    log_failure_msg "$0: ERROR: The partition with $datadir is too full!"
    echo                "ERROR: The partition with $datadir is too full!" | $ERR_LOGGER
    exit 1
  fi
}

## Checks if there is a server running and if so if it is accessible.
#
# check_alive insists on a pingable server
# check_dead also fails if there is a lost mysqld in the process list
#
# Usage: boolean mysqld_status [check_alive|check_dead] [warn|nowarn]
mysqld_status () {
    ping_output=`$MYADMIN ping 2>&1`; ping_alive=$(( ! $? ))

    ps_alive=0
    pidfile=`mysqld_get_param pid-file`
    if [ -f "$pidfile" ] && ps `cat $pidfile` >/dev/null 2>&1; then ps_alive=1; fi

    if [ "$1" = "check_alive"  -a  $ping_alive = 1 ] ||
       [ "$1" = "check_dead"   -a  $ping_alive = 0  -a  $ps_alive = 0 ]; then
        return 0 # EXIT_SUCCESS
    else
        if [ "$2" = "warn" ]; then
            echo -e "$ps_alive processes alive and '$MYADMIN ping' resulted in\n$ping_output\n" | $ERR_LOGGER -p daemon.debug
        fi
        return 1 # EXIT_FAILURE
    fi
}

#
# main()
#

case "${1:-''}" in
  'start')
        sanity_checks;
        # Start daemon
        log_daemon_msg "Starting MySQL database server" "mysqld"
        if mysqld_status check_alive nowarn; then
           log_progress_msg "already running"
           log_end_msg 0
        else
        setup_chroot
            /usr/bin/mysqld_safe > /dev/null 2>&1 &
            # 6s was reported in #352070 to be too few when using ndbcluster
            for i in 1 2 3 4 5 6 7 8 9 10 11 12 13 14; do
                sleep 1
                if mysqld_status check_alive nowarn ; then break; fi
                log_progress_msg "."
            done
            if mysqld_status check_alive warn; then
                log_end_msg 0
  ln -sf $CHROOT_DIR/var/run/mysqld/mysqld.pid \
                 /var/run/mysqld
                # Now start mysqlcheck or whatever the admin wants.
               output=$(/etc/mysql/debian-start)
                [ -n "$output" ] && log_action_msg "$output"
            else
                log_end_msg 1
                log_failure_msg "Please take a look at the syslog"
            fi
        fi
#rm /chroot/httpd/var/run/mysqld/mysqld.sock
#ln /chroot/mysql/var/run/mysqld/mysqld.sock /chroot/httpd/var/run/mysqld/mysqld.sock
        # Some warnings
        if $MYADMIN variables | egrep -q have_bdb.*YES; then
            echo "BerkeleyDB is obsolete, see /usr/share/doc/mysql-server-5.0/README.Debian.gz" | $ERR_LOGGER -p daemon.info
        fi
        if [ -f /etc/mysql/debian-log-rotate.conf ]; then
            echo "/etc/mysql/debian-log-rotate.conf is obsolete, see /usr/share/doc/mysql-server-5.0/NEWS.Debian.gz" | $ERR_LOGGER -p daemon.info
        fi
        ;;

  'stop')
        # * As a passwordless mysqladmin (e.g. via ~/.my.cnf) must be possible
        # at least for cron, we can rely on it here, too. (although we have
        # to specify it explicit as e.g. sudo environments points to the normal
        # users home and not /root)
        log_daemon_msg "Stopping MySQL database server" "mysqld"
        if ! mysqld_status check_dead nowarn; then
          set +e
          shutdown_out=`$MYADMIN shutdown 2>&1`; r=$?
          set -e
          if [ "$r" -ne 0 ]; then
            log_end_msg 1
            [ "$VERBOSE" != "no" ] && log_failure_msg "Error: $shutdown_out"
            log_daemon_msg "Killing MySQL database server by signal" "mysqld"
            killall -15 mysqld
            server_down=
            for i in 1 2 3 4 5 6 7 8 9 10; do
              sleep 1
              if mysqld_status check_dead nowarn; then server_down=1; break; fi
            done
          if test -z "$server_down"; then killall -9 mysqld; fi
          fi
        fi
#rm /chroot/httpd/var/run/mysqld/mysqld.sock
        if ! mysqld_status check_dead warn; then
          log_end_msg 1
          log_failure_msg "Please stop MySQL manually and read /usr/share/doc/mysql-server-5.0/README.Debian.gz!"
          exit -1
        else
          log_end_msg 0
        fi
        ;;

  'restart')
        set +e; $SELF stop; set -e
        $SELF start
        ;;

  'reload'|'force-reload')
        log_daemon_msg "Reloading MySQL database server" "mysqld"
        $MYADMIN reload
        log_end_msg 0
        ;;

  'status')
        if mysqld_status check_alive nowarn; then
          log_action_msg "$($MYADMIN version)"
        else
          log_action_msg "MySQL is stopped."
          exit 3
        fi
        ;;

  *)
        echo "Usage: $SELF start|stop|restart|reload|force-reload|status"
        exit 1
        ;;
esac


```

Thanks for your help again PraysToPan.

---

### Post by zeepal on 2008-07-18
NVM i fixed it that was my bad i didnt know that when a /etc/init.d/* runs it stops once an error comes up (eg the .sock link didnt exist)

Sorry to waste your time guys but thanks again PraysToPan!

I have one last question if i have a soft link that goes from /var/run/apache2.pid (link) to /chroot/httpd/var/run/apache2.pid (real) is this a security issue? or because its outside the chroot pointing into it its ok?

---

### Post by promodus on 2008-07-20
Why chroot?

[http://kerneltrap.org/Linux/Abusing_chroot](http://kerneltrap.org/Linux/Abusing_chroot)

> When it was suggested that chroot is frequently used as a security tool, Adrian Bunk retorted, "incompetent people implementing security solutions are a real problem." Alan added, "chroot is not and never has been a security tool. People have built things based upon the properties of chroot but extended (BSD jails, Linux vserver) but they are quite different."

---

