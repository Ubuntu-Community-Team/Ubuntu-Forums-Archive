---
title: "saslauthd: Memory buffer error after a couple of days"
date: 2013-09-24
forum: Server Platforms
---

### Post by kayncz on 2013-09-24
Hello,

I have installed postfix + sasl + cyrus and I have problem that after couple of days authentication doesn't work. In htop is on top of memory usage after this time.

It's public server and it is performed thousands queries from robots. Restart of saslauthd helps me, but I don't want add it to cron :).


Some data:

Ubuntu 12.04
version - saslauthd 2.1.25



Restart in debug mode:
```
/etc/init.d/saslauthd restart 
 * Stopping SASL Authentication Daemon saslauthd
   ...done.
 * Starting SASL Authentication Daemon saslauthd
saslauthd[13867] :main            : num_procs  : 5
saslauthd[13867] :main            : mech_option: NULL
saslauthd[13867] :main            : run_path   : /var/spool/postfix/var/run/saslauthd
saslauthd[13867] :main            : auth_mech  : pam
saslauthd[13867] :cache_alloc_mm  : mmaped shared memory segment on file: /var/spool/postfix/var/run/saslauthd/cache.mmap
saslauthd[13867] :cache_init      : bucket size: 96 bytes
saslauthd[13867] :cache_init      : stats size : 36 bytes
saslauthd[13867] :cache_init      : timeout    : 28800 seconds
saslauthd[13867] :cache_init      : cache table: 985828 total bytes
saslauthd[13867] :cache_init      : cache table: 1711 slots
saslauthd[13867] :cache_init      : cache table: 10266 buckets
saslauthd[13867] :cache_init_lock : flock file opened at /var/spool/postfix/var/run/saslauthd/cache.flock
saslauthd[13867] :ipc_init        : using accept lock file: /var/spool/postfix/var/run/saslauthd/mux.accept
saslauthd[13867] :detach_tty      : master pid is: 0
saslauthd[13867] :ipc_init        : listening on socket: /var/spool/postfix/var/run/saslauthd/mux
saslauthd[13867] :main            : using process model
saslauthd[13867] :have_baby       : forked child: 13868
saslauthd[13867] :have_baby       : forked child: 13869
saslauthd[13867] :have_baby       : forked child: 13870
saslauthd[13867] :have_baby       : forked child: 13871
saslauthd[13867] :get_accept_lock : acquired accept lock
```


log:

```
Sep 24 19:34:37 ******* saslauthd[28974]: DEBUG: auth_pam: pam_authenticate failed: **Memory buffer error**
Sep 24 19:34:37 ******* saslauthd[28974]: do_auth         : auth failure: [user=*****] [service=imap] [realm=] [mech=pam] [reason=PAM auth error]

```


/etc/default/saslauthd

```
START=yes
DESC="SASL Authentication Daemon"
NAME="saslauthd"
MECHANISMS="pam"
MECH_OPTIONS=""
THREADS=5
OPTIONS="-c -m /var/spool/postfix/var/run/saslauthd -r"

```


Can you help me? Thx

Sorry for my English.

---

### Post by DemoniacDeath on 2013-12-11
I have the same problem, my server is set up for my company's internal mail, it doesn't have much of work, but today I've got same problem - I couldn't send email. Just now I've realized that my server was constantly used by some sort of spammers and there is a lot of "Memory buffer error" messages in my auth.log, so I'm suggesting that it has something to do with an intensity of connections, or at least intensity of failed authentications. I'm using pam_mysql for pam authentication, if that has something to do with anything. I would really appreciate some help in this matter, but currently I'm going to try to find the answer myself. If I'll find anything I'll post it here.

---

### Post by kayncz on 2013-12-13
I "solved" it thanks to *fail2ban* and restart *saslauthd* every midnight by *cron.* You can minimize number of threads.

---

### Post by xenoson on 2014-10-07
Many sources claim this is a problem in pam modules. Dovecot wiki [http://wiki2.dovecot.org/PasswordDatabase/PAM](http://wiki2.dovecot.org/PasswordDatabase/PAM) says they have a pam_maxrequests for this.
I use postfix and courier and wanted to try courier's authdaemon also for SASL because it seems to work over long periods of time. It was not trivial to get its socket into the postfix changeroot as /run is a tmpfs now. So I post this here because this is the first search hit for memory buffer error with saslauthd.

We set /etc/postfix/sasl/smtpd.conf to use authdaemond
```

pwcheck_method: authdaemond
mech_list: PLAIN LOGIN
authdaemond_path: /var/run/courier/authdaemon/socket

```


and insert this into /etc/courier/authdaemonrc
```

#allow to change a chrooted postfix sasl configuration to use authdaemond socket
#the socket will be created in postfix chroot and the hardcoded /var/run/courier/authdaemon
#will symlink to it.
#activate /etc/init.d/courier-authdaemon-socket
#with
#update-rc.d courier-authdaemon-socket defaults 19 21
#remove it with
#update-rc.d -f courier-authdaemon-socket remove
#or disable by setting no here
putsocketintopostfixchroot="yes"
postfixchroot="/var/spool/postfix"
#
clean_existing_var_run_courier_in_postfix_chroot="yes"
#
#

```

and save this script executable as /etc/init.d/courier-authdaemon-socket
```

#! /bin/sh -e
#
### BEGIN INIT INFO
# Provides:          courier-authdaemon-socket
# Required-Start:    $remote_fs $syslog
# Required-Stop:     $remote_fs $syslog
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
### END INIT INFO

prefix="/usr"
exec_prefix=${prefix}
sysconfdir="/etc/courier"
sbindir="${exec_prefix}/sbin"
daemonscript="${sbindir}/authdaemond"
rundir_courier="/var/run/courier"
rundir="/var/run/courier/authdaemon"

. /lib/lsb/init-functions

#this will import custom variables
#putsocketintopostfixchroot=yes
#postfixchroot="/var/spool/postfix"
#clean_existing_var_run_courier_in_postfix_chroot="yes"
. /etc/courier/authdaemonrc


if [ "${putsocketintopostfixchroot}" != "yes" ]; then
    exit 0
fi


# Check for a leftover init script
if [ ! -x $daemonscript ]; then
    exit 0
fi


# Check for a running authdaemond
if grep -q authdaemond /proc/$(cat ${rundir}/pid 2>/dev/null)/cmdline 2>/dev/null; then
    log_warning_msg "Exiting: detected running authdaemond"
    exit 0
fi

case "$1" in
start)
    # Prepare daemon socket in postfix chroot.
    cd /
    log_daemon_msg "Preparing Courier authentication services" "authdaemond"
    
    if [ ! -d "${postfixchroot}" ]; then
        log_warning_msg "Exiting: configured chroot directory for postfix does not exist: \"${postfixchroot}\""
        exit 0
    fi

    if [ ! -d "${postfixchroot}/var/run" ]; then
        log_warning_msg "Exiting: configured chroot directory for postfix is incomplete: \"${postfixchroot}/var/run\""
        exit 0
    fi

    if [ -d "${postfixchroot}${rundir_courier}" ]; then
        if [ "${clean_existing_var_run_courier_in_postfix_chroot}" = "yes" ]; then
            rm -rf -- "${postfixchroot}${rundir_courier}"
        else
            log_warning_msg "Warning: configured to leave existing: \"${postfixchroot}${rundir_courier}\" untouched."
        fi
    fi

    if [ ! -d "${postfixchroot}${rundir_courier}" ]; then
        mkdir -m 0775 ${postfixchroot}${rundir_courier}
        chown daemon:daemon ${postfixchroot}${rundir_courier}
    fi

    if [ ! -d "${postfixchroot}${rundir}" ]; then
        mkdir -m 0750 ${postfixchroot}${rundir}
        chown daemon:sasl ${postfixchroot}${rundir} #original courier initscript uses group "daemon" postfix is in group sasl
    fi

#this was the job of the original courier-authdaemon initscript and we need to do this here
    if [ ! -d "$rundir_courier" ]; then
        mkdir -m 0775 $rundir_courier
        chown daemon:daemon $rundir_courier
#but if courier-authdaemon was running before it does not remove the $rundir, so make shure we can link it now
    elif [ -d "$rundir" -a ! -h "$rundir" ]; then
        rm -rf -- ${rundir}/
    fi

    if [ ! -d "$rundir" ]; then
        ln -s ${postfixchroot}${rundir}/ ${rundir}
    fi

    log_end_msg 0
    ;;
stop)
    # Delete courier files from postfix chroot.
    cd /
    log_daemon_msg "Cleaning up Courier authentication services" "authdaemond"

    if [ -d "${postfixchroot}${rundir_courier}" ]; then
        if [ "${clean_existing_var_run_courier_in_postfix_chroot}" = "yes" ]; then
            rm -rf -- "${postfixchroot}${rundir_courier}"
        else
            log_warning_msg "Not cleaning up, configured to leave existing: \"${postfixchroot}${rundir_courier}\" untouched."
        fi
    fi

    if [ -h "$rundir" ]; then
        unlink ${rundir}
    fi

    log_end_msg 0
    ;;
restart|force-reload)
    $0 stop
    $0 start
    ;;
*)
    echo "Usage: $0 {start|stop|restart|force-reload}" >&2
    exit 2
    ;;
esac
exit 0

```

and activate it as explained in the comment above with
```
update-rc.d courier-authdaemon-socket defaults 19 21
```
to execute before the courier-authdaemon startscript at system boot.
Dont forget to turn off saslauthd (START=no) in /etc/default/saslauthd afterwards.

Reference: [http://wiki.tolien.co.uk/Postfix_w/o_Maildrop#Courier-Authdaemon](http://wiki.tolien.co.uk/Postfix_w/o_Maildrop#Courier-Authdaemon)

---

