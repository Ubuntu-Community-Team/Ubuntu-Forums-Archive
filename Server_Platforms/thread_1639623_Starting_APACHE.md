---
title: "Starting APACHE"
date: 2010-12-06
forum: Server Platforms
---

### Post by ingeva on 2010-12-06
I've defined the APAerror.log as the log file, and this is what it contains after
trying to start Apache:

[Tue Dec 07 04:02:00 2010] [error] (2)No such file or directory: could not open transfer log file /etc/apache2/${APACHE_LOG_DIR}/other_vhosts_access.log.
Unable to open logs

The question is: Where do I define APACHE_LOG_DIR?

Testing Ubuntu 10.10 32-bit server.

(My init scripts work perfectly in 9.10).

---

### Post by James78 on 2010-12-06
You define it in /etc/apache2/envvars

P.S. Make sure the entries in your configuration files that use ${APACHE_LOG_DIR} look like:
```
${APACHE_LOG_DIR}/error.log
```
As an entry like the one that follows would be incorrect.
```
/etc/apache2/${APACHE_LOG_DIR}/error.log
```
Default /etc/apache2/envvars file in apache2 (2.2.16) maverick release
```
# envvars - default environment variables for apache2ctl

# this won't be correct after changing uid
unset HOME

# for supporting multiple apache2 instances
if [ "${APACHE_CONFDIR##/etc/apache2-}" != "${APACHE_CONFDIR}" ] ; then
	SUFFIX="-${APACHE_CONFDIR##/etc/apache2-}"
else
	SUFFIX=
fi

# Since there is no sane way to get the parsed apache2 config in scripts, some
# settings are defined via environment variables and then used in apache2ctl,
# /etc/init.d/apache2, /etc/logrotate.d/apache2, etc.
export APACHE_RUN_USER=www-data
export APACHE_RUN_GROUP=www-data
export APACHE_PID_FILE=/var/run/apache2$SUFFIX.pid
export APACHE_RUN_DIR=/var/run/apache2$SUFFIX
export APACHE_LOCK_DIR=/var/lock/apache2$SUFFIX
# Only /var/log/apache2 is handled by /etc/logrotate.d/apache2.
export APACHE_LOG_DIR=/var/log/apache2$SUFFIX

## The locale used by some modules like mod_dav
export LANG=C
## Uncomment the following line to use the system default locale instead:
#. /etc/default/locale

export LANG

## The command to get the status for 'apache2ctl status'.
## Some packages providing 'www-browser' need '--dump' instead of '-dump'.
#export APACHE_LYNX='www-browser -dump'
```

---

### Post by ingeva on 2010-12-11
> **James78 said:**
> You define it in /etc/apache2/envvars

Thank you!

I actually did write a response to you, but it must have gone to heaven.

Well, here it is, and I now mark the thread as solved.

---

### Post by LordDelta on 2011-08-08
Solved the mystery of where these were defined! :) I suspect apache2ctl runs this file?

---

### Post by kleverbear on 2011-09-21
@James78 your answer was the best thing i ever came across good sir!

My /etc/apache2/envvars file was empty, Im glad you posted your file i was able to fill in mine with your info. Now im good to go.

@ingeva thanks for keeping this thread open.

---

### Post by melc_sokat on 2012-08-14
Working like a charm.
Thank you.

---

