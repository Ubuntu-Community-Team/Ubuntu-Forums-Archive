---
title: "PostgreSQL init.d script not working"
date: 2011-06-08
forum: Server Platforms
---

### Post by tentimes on 2011-06-08
Hi,

I have installed PostgreSQL from source (as I need 9.0) in Ununtu 10.04 (with no GUI). It is installed to:

opt/postgresql

I setup the database cluster to opt/postgresql/data - that worked ok, and the user is 'postgres'.

The init.d script supplied is called linux and I did the normal stuff, but the script won't work. It gives the error:

"-bash: /etc/init.d/postgresql: /bin/sh^M: bad interpreter: No such file or directory"

The altered init.d script is as follows:

```


#! /bin/sh

# chkconfig: 2345 98 02
# description: PostgreSQL RDBMS

# This is an example of a start/stop script for SysV-style init, such
# as is used on Linux systems.  You should edit some of the variables
# and maybe the 'echo' commands.
#
# Place this file at /etc/init.d/postgresql (or
# /etc/rc.d/init.d/postgresql) and make symlinks to
#   /etc/rc.d/rc0.d/K02postgresql
#   /etc/rc.d/rc1.d/K02postgresql
#   /etc/rc.d/rc2.d/K02postgresql
#   /etc/rc.d/rc3.d/S98postgresql
#   /etc/rc.d/rc4.d/S98postgresql
#   /etc/rc.d/rc5.d/S98postgresql
# Or, if you have chkconfig, simply:
# chkconfig --add postgresql
#
# Proper init scripts on Linux systems normally require setting lock
# and pid files under /var/run as well as reacting to network
# settings, so you should treat this with care.

# Original author:  Ryan Kirkpatrick <pgsql@rkirkpat.net>

# contrib/start-scripts/linux

## EDIT FROM HERE

# Installation prefix
prefix=/opt/postgresql

# Data directory
PGDATA="/opt/postgresql/data"

# Who to run the postmaster as, usually "postgres".  (NOT "root")
PGUSER=postgres

# Where to keep a log file
PGLOG="$PGDATA/serverlog"

# It's often a good idea to protect the postmaster from being killed by the
# OOM killer (which will tend to preferentially kill the postmaster because
# of the way it accounts for shared memory).  Setting the OOM_ADJ value to
# -17 will disable OOM kill altogether.  If you enable this, you probably want
# to compile PostgreSQL with "-DLINUX_OOM_ADJ=0", so that individual backends
# can still be killed by the OOM killer.
#OOM_ADJ=-17

## STOP EDITING HERE

# The path that is to be used for the script
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

# What to use to start up the postmaster.  (If you want the script to wait
# until the server has started, you could use "pg_ctl start -w" here.
# But without -w, pg_ctl adds no value.)
DAEMON="$prefix/bin/postmaster"

# What to use to shut down the postmaster
PGCTL="$prefix/bin/pg_ctl"

set -e

# Only start if we can find the postmaster.
test -x $DAEMON ||
{
	echo "$DAEMON not found"
	if [ "$1" = "stop" ]
	then exit 0
	else exit 5
	fi
}


# Parse command line parameters.
case $1 in
  start)
	echo -n "Starting PostgreSQL: "
	test x"$OOM_ADJ" != x && echo "$OOM_ADJ" > /proc/self/oom_adj
	su - $PGUSER -c "$DAEMON -D '$PGDATA' &" >>$PGLOG 2>&1
	echo "ok"
	;;
  stop)
	echo -n "Stopping PostgreSQL: "
	su - $PGUSER -c "$PGCTL stop -D '$PGDATA' -s -m fast"
	echo "ok"
	;;
  restart)
	echo -n "Restarting PostgreSQL: "
	su - $PGUSER -c "$PGCTL stop -D '$PGDATA' -s -m fast -w"
	test x"$OOM_ADJ" != x && echo "$OOM_ADJ" > /proc/self/oom_adj
	su - $PGUSER -c "$DAEMON -D '$PGDATA' &" >>$PGLOG 2>&1
	echo "ok"
	;;
  reload)
        echo -n "Reload PostgreSQL: "
        su - $PGUSER -c "$PGCTL reload -D '$PGDATA' -s"
        echo "ok"
        ;;
  status)
	su - $PGUSER -c "$PGCTL status -D '$PGDATA'"
	;;
  *)
	# Print help
	echo "Usage: $0 {start|stop|restart|reload|status}" 1>&2
	exit 1
	;;
esac

exit 0

```

Could anyone help me please? I am totally stumped and have been googleing and reading for hours now. It seems the default linux script supplied does not work with Ubuntu 10.04.

NB: I *need* 9.0 hence installing from source.

I would greatly appreciate any help you can give.

Thanks,

TT

---

### Post by tentimes on 2011-06-08
I checked file permissions by the way - 755, so it should execute.

---

### Post by tentimes on 2011-06-08
Solved!

For some reason, the file was not in Unix format. I opened it using the old 'vi' editor (vi /etc/init.d/postgresql)

then typed

```

:set fileformat=unix [RETURN]
:wq! [RETURN]

```

Now this could be because I am using Putty SSL connection to the server, I copied the file to windows to edit it in wordpad, then sent it back. I don't know why I did that! I work on two screens here with a SFTP window and the putty connection on one screen and my windows stuff on the left.

Anyway, I hope this is useful to someone else!

---

