---
title: "saslauthd startup not using OPTIONS from saslauthd.conf"
date: 2008-06-30
forum: Server Platforms
---

### Post by DantePasquale on 2008-06-30
Hi All,

I used the ISPConfig tutorial for upgrading my ISPConfig server from Ubuntu 7.10 to 8.04 and things went very well. Except for the final steps of setting up Postfix to work with saslauthd. Here's what I found. If I run saslauthd from the command line, explicitly specifying the -m mux path then things work fine, per the tutorial. If I then run /etc/init.d/saslauthd start, it's putting the mux in the default location and Postfix can't find it. It looks to me like the run control startup is not passing the -m flag to start up the service. Here's the log from the startup:

```
++ MECH_OPTIONS=
++ THREADS=5
++ OPTIONS='-c -m /var/spool/postfix/var/run/saslauthd -r'
+ '[' yes '!=' yes ']'
+ '[' xpam = x ']'
+ PARAMS=' -a pam'
[COLOR="Red"]+ START='--start --quiet --pidfile /var/spool/postfix/var/run/saslauthd/saslauthd.pid --startas /usr/sbin/saslauthd --name saslauthd --  -a pam'[/COLOR]
+ case "${1}" in
+ echo -n 'Starting SASL Authentication Daemon: '
Starting SASL Authentication Daemon: ++ dpkg-statoverride --list /var/run/saslauthd
+ dir='root sasl 710 /var/run/saslauthd'
+ test -z 'root sasl 710 /var/run/saslauthd'
+ createdir root sasl 710 /var/run/saslauthd
+ '[' -d /var/run/saslauthd ']'
+ mkdir -p /var/run/saslauthd
+ chown -c -h root:sasl /var/run/saslauthd
changed ownership of `/var/run/saslauthd' to root:sasl
+ chmod -c 710 /var/run/saslauthd
mode of `/var/run/saslauthd' changed to 0710 (rwx--x---)
[COLOR="Red"]+ start-stop-daemon --start --quiet --pidfile /var/spool/postfix/var/run/saslauthd/saslauthd.pid --startas /usr/sbin/saslauthd --name saslauthd -- -a pam[/COLOR]
+ echo saslauthd.
```

Command Line - That Works!
```

root@inferno:/etc/init.d# saslauthd -a pam  -n 5  -V -c -[COLOR="Red"]m /var/spool/postfix/var/run/saslauthd -r -d[/COLOR]
saslauthd[14011] :main            : num_procs  : 5
saslauthd[14011] :main            : mech_option: NULL
saslauthd[14011] :main            : run_path   : /var/spool/postfix/var/run/saslauthd
saslauthd[14011] :main            : auth_mech  : pam
saslauthd[14011] :cache_alloc_mm  : mmaped shared memory segment on file: /var/spool/postfix/var/run/saslauthd/cache.mmap
saslauthd[14011] :cache_init      : bucket size: 96 bytes
saslauthd[14011] :cache_init      : stats size : 36 bytes
saslauthd[14011] :cache_init      : timeout    : 28800 seconds
saslauthd[14011] :cache_init      : cache table: 985828 total bytes
saslauthd[14011] :cache_init      : cache table: 1711 slots
saslauthd[14011] :cache_init      : cache table: 10266 buckets
saslauthd[14011] :cache_init_lock : flock file opened at /var/spool/postfix/var/run/saslauthd/cache.flock
saslauthd[14011] :ipc_init        : using accept lock file: /var/spool/postfix/var/run/saslauthd/mux.accept
saslauthd[14011] :detach_tty      : master pid is: 0
saslauthd[14011] :ipc_init        : listening on socket: /var/spool/postfix/var/run/saslauthd/mux
saslauthd[14011] :main            : using process model
saslauthd[14012] :get_accept_lock : acquired accept lock
saslauthd[14011] :have_baby       : forked child: 14012
saslauthd[14011] :have_baby       : forked child: 14013
saslauthd[14011] :have_baby       : forked child: 14014
saslauthd[14011] :have_baby       : forked child: 14015
saslauthd[14012] :rel_accept_lock : released accept lock
saslauthd[14012] :cache_get_rlock : attempting a read lock on slot: 1473
saslauthd[14012] :cache_lookup    : [login=web8_xxxxxxxx] [service=] [realm=smtp]: not found, update pending
saslauthd[14012] :cache_un_lock   : attempting to release lock on slot: 1473
saslauthd[14013] :get_accept_lock : acquired accept lock
saslauthd[14012] :cache_get_wlock : attempting a write lock on slot: 1473
saslauthd[14012] :cache_commit    : lookup committed
saslauthd[14012] :cache_un_lock   : attempting to release lock on slot: 1473
saslauthd[14012] :do_auth         : auth success: [user=web8_xxxxxxxx] [service=smtp] [realm=] [mech=pam]
saslauthd[14012] :do_request      : response: OK
```


NOTE: No OPTIONS from /etc/default/saslauthd!

Weird, eh? How should one fix this? I really don't want to modify the run control script, but I'm thinking that since this was an upgrade, the proper run control did not get put onto my server.

/etc/default/saslauthd:

```
#
# Settings for saslauthd daemon
# Please read /usr/share/doc/sasl2-bin/README.Debian for details.
#

# Should saslauthd run automatically on startup? (default: no)
START=yes

# Description of this saslauthd instance. Recommended.
# (suggestion: SASL Authentication Daemon)
DESC="SASL Authentication Daemon"

# Short name of this saslauthd instance. Strongly recommended.
# (suggestion: saslauthd)
NAME="saslauthd"

# Which authentication mechanisms should saslauthd use? (default: pam)
#
# Available options in this Debian package:
# getpwent  -- use the getpwent() library function
# kerberos5 -- use Kerberos 5
# pam       -- use PAM
# rimap     -- use a remote IMAP server
# shadow    -- use the local shadow password file
# sasldb    -- use the local sasldb database file
# ldap      -- use LDAP (configuration is in /etc/saslauthd.conf)
#
# Only one option may be used at a time. See the saslauthd man page
# for more information.
#
# Example: MECHANISMS="pam"
MECHANISMS="pam"

# Additional options for this mechanism. (default: none)
# See the saslauthd man page for information about mech-specific options.
MECH_OPTIONS=""

# How many saslauthd processes should we run? (default: 5)
# A value of 0 will fork a new process for each connection.
THREADS=5

# Other options (default: -c -m /var/run/saslauthd)
# Note: You MUST specify the -m option or saslauthd won't run!
#
# See /usr/share/doc/sasl2-bin/README.Debian for Debian-specific information.
# See the saslauthd man page for general information about these options.
#
# Example for postfix users: "-c -m /var/spool/postfix/var/run/saslauthd"
#OPTIONS="-c -m /var/run/saslauthd"
OPTIONS="-[COLOR="Red"]c -m /var/spool/postfix/var/run/saslauthd -r[/COLOR]"
```

---

### Post by DantePasquale on 2008-07-01
Opened bug since I haven't heard back on any resolution:

Bug #244568 in Ubuntu

---

