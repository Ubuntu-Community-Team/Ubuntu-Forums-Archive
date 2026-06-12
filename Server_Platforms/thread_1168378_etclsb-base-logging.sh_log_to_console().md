---
title: "/etc/lsb-base-logging.sh log_to_console()"
date: 2009-05-24
forum: Server Platforms
---

### Post by botfish on 2009-05-24
I've running a VPS with Ubuntu 7.10 Gusty. Every time anacron runs a cron job I receive the following error messages:

```

/etc/cron.daily/logrotate:
/etc/lsb-base-logging.sh: line 22: /dev/console: Permission denied
/etc/lsb-base-logging.sh: line 22: /dev/console: Permission denied
/etc/cron.daily/sysklogd:
/etc/lsb-base-logging.sh: line 22: /dev/console: Permission denied
/etc/lsb-base-logging.sh: line 22: /dev/console: Permission denied

```

Line 22 of /etc/lsb-base-logging.sh refers to /dev/console. Being a server it won't have a console (assuming console == monitor?).

What is the purpose of line22? Can I (or should I) replace /dev/console with /dev/null?

Line 22 of /etc/lsb-base-logging.sh
```

loop=y $func "$@" </dev/console >/dev/console 2>&1 || true

```

First 23 lines of /etc/lsb-base-logging.sh:
```

# Default init script logging functions suitable for Ubuntu.
# See /lib/lsb/init-functions for usage help.

log_use_usplash () {
    if [ "${loop:-n}" = y ]; then
        return 1
    fi
    type usplash_write >/dev/null 2>&1
}

log_to_console () {
    [ "${loop:-n}" != y ] || return 0
    [ "${QUIET:-no}" != yes ] || return 0

    # Only output to the console when we're given /dev/null
    stdin=`readlink /proc/self/fd/0`
    [ "${stdin#/dev/null}" != "$stdin" ] || return 0

    func=$1
    shift

    loop=y $func "$@" </dev/console >/dev/console 2>&1 || true
}

```

---

