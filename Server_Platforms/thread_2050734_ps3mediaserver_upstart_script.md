---
title: "ps3mediaserver upstart script"
date: 2012-08-31
forum: Server Platforms
---

### Post by arrrghhh on 2012-08-31
Hello,

I recently upgraded to 12.04 because of ps3mediaserver support.

I'm using [this repo/directions](http://www.ps3mediaserver.org/forum/viewtopic.php?f=3&t=13046&sid=733f126a263f4d38929ec63328aafb0d) for installing and keeping up-to-date on ps3mediaserver.

I had a bit of an issue getting this software upgraded, but I managed - and now when I try to run it from the upstart script it simply says:
```
sudo service ps3mediaserver start
[sudo] password for user:
ps3mediaserver stop/pre-start, process 21515
```

But there is no PID 21515.  How can I debug this?  I'm simply using the script provided with the ps3mediaserver deb/repo linked above - so it shouldn't be anything special - I even purged the application and reinstalled, and it still fails.

I am able to run the software manually using my user and the 'root' user using sudo.  I recall previously I had this software starting under my user, but looking at the new upstart script for ps3mediaserver, I don't see an easy way to change the user that is running the software thru the upstart script.  Here it is, just in case:

```
user@nas:~$ cat /etc/init.d/ps3mediaserver
#!/bin/sh -e
# upstart-job
#
# Symlink target for initscripts that have been converted to Upstart.

set -e

INITSCRIPT="$(basename "$0")"
JOB="${INITSCRIPT%.sh}"

if [ "$JOB" = "upstart-job" ]; then
    if [ -z "$1" ]; then
        echo "Usage: upstart-job JOB COMMAND" 1>&2
        exit 1
    fi

    JOB="$1"
    INITSCRIPT="$1"
    shift
else
    if [ -z "$1" ]; then
        echo "Usage: $0 COMMAND" 1>&2
        exit 1
    fi
fi

COMMAND="$1"
shift


if [ -z "$DPKG_MAINTSCRIPT_PACKAGE" ]; then
        ECHO=echo
else
        ECHO=:
fi

$ECHO "Rather than invoking init scripts through /etc/init.d, use the service(8)"
$ECHO "utility, e.g. service $INITSCRIPT $COMMAND"

# Only check if jobs are disabled if the currently _running_ version of
# Upstart (which may be older than the latest _installed_ version)
# supports such a query.
#
# This check is necessary to handle the scenario when upgrading from a
# release without the 'show-config' command (introduced in
# Upstart for Ubuntu version 0.9.7) since without this check, all
# installed packages with associated Upstart jobs would be considered
# disabled.
#
# Once Upstart can maintain state on re-exec, this change can be
# dropped (since the currently running version of Upstart will always
# match the latest installed version).

UPSTART_VERSION_RUNNING=$(initctl version|awk '{print $3}'|tr -d ')')

if dpkg --compare-versions "$UPSTART_VERSION_RUNNING" ge 0.9.7
then
    initctl show-config -e "$JOB"|grep -q '^  start on' || DISABLED=1
fi

case $COMMAND in
status)
    $ECHO
    $ECHO "Since the script you are attempting to invoke has been converted to an"
    $ECHO "Upstart job, you may also use the $COMMAND(8) utility, e.g. $COMMAND $JOB"
    $COMMAND "$JOB"
    ;;
start|stop)
    $ECHO
    $ECHO "Since the script you are attempting to invoke has been converted to an"
    $ECHO "Upstart job, you may also use the $COMMAND(8) utility, e.g. $COMMAND $JOB"
    if status "$JOB" 2>/dev/null | grep -q ' start/'; then
        RUNNING=1
    fi
    if [ -z "$RUNNING" ] && [ "$COMMAND" = "stop" ]; then
        exit 0
    elif [ -n "$RUNNING" ] && [ "$COMMAND" = "start" ]; then
        exit 0
    elif [ -n "$DISABLED" ] && [ "$COMMAND" = "start" ]; then
        exit 0
    fi
    $COMMAND "$JOB"
    ;;
restart)
    $ECHO
    $ECHO "Since the script you are attempting to invoke has been converted to an"
    $ECHO "Upstart job, you may also use the stop(8) and then start(8) utilities,"
    $ECHO "e.g. stop $JOB ; start $JOB. The restart(8) utility is also available."
    if status "$JOB" 2>/dev/null | grep -q ' start/'; then
        RUNNING=1
    fi
    if [ -n "$RUNNING" ] ; then
        stop "$JOB"
    fi
    # If the job is disabled and is not currently running, the job is
    # not restarted. However, if the job is disabled but has been forced into the
    # running state, we *do* stop and restart it since this is expected behaviour
    # for the admin who forced the start.
    if [ -n "$DISABLED" ] && [ -z "$RUNNING" ]; then
        exit 0
    fi
    start "$JOB"
    ;;
reload|force-reload)
    $ECHO
    $ECHO "Since the script you are attempting to invoke has been converted to an"
    $ECHO "Upstart job, you may also use the reload(8) utility, e.g. reload $JOB"
    reload "$JOB"
    ;;
*)
    $ECHO
    $ECHO "The script you are attempting to invoke has been converted to an Upstart" 1>&2
    $ECHO "job, but $COMMAND is not supported for Upstart jobs." 1>&2
    exit 1
esac
```

So, any ideas on why I can't run this program via the upstart job?  Or how to troubleshoot why the upstart job is failing??

Thanks!!!

---

### Post by arrrghhh on 2012-08-31
Derp.

Was trying to get it to run from the upstart job... wouldn't do it no matter what... forgot to look at /etc/default/ps3mediaserver...

Problem solved!!

---

### Post by rlbond86 on 2012-12-08
For the record, since arrrghhh didn't actually say what he did, you need to open /etc/default/ps3mediaserver and change PMS_START="no" to PMS_START="yes".

---

