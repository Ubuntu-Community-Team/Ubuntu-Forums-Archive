---
title: "LTSP / Second SSH Server / Error:  no response from server, restart"
date: 2013-06-09
forum: Server Platforms
---

### Post by bvargo on 2013-06-09
This morning I had a working LTSP server that was built several weeks ago using one interface and the --arch i386 option of the Quick Start Wiki:  [https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall](https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall)

I wanted to deny password access for standard SSH and only allow public key access so I followed [http://www.nubae.com/hardening-ubuntu-ltsp-server](http://www.nubae.com/hardening-ubuntu-ltsp-server)

I am still able to boot into the LTSP authentication screen but I when I attempt to log in I get "No response from server, restarting."

I did do ```
**sudo ltsp-update-sshkeys**[COLOR=#333333][FONT=Ubuntu] && [/FONT][/COLOR]**sudo ltsp-update-image**&#8203;
``` after changing the port in the /etc/ltsp/ltsp-sshd_config.

```

# Package generated configuration file
# See the sshd_config(5) manpage for details


# What ports, IPs and protocols we listen for
Port 2222
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
ListenAddress 0.0.0.0
#ListenAddress 173.49.27.220
Protocol 2
# HostKeys for protocol version 2
HostKey /etc/ssh/ssh_host_rsa_key
HostKey /etc/ssh/ssh_host_dsa_key
HostKey /etc/ssh/ssh_host_ecdsa_key
#Privilege Separation is turned on for security
UsePrivilegeSeparation yes


# Lifetime and size of ephemeral version 1 server key
KeyRegenerationInterval 3600
ServerKeyBits 768


# Logging
SyslogFacility AUTH
LogLevel INFO


# Authentication:
LoginGraceTime 120
StrictModes yes


#### Changed to no 2013/01/17


PermitRootLogin no


RSAAuthentication yes
PubkeyAuthentication yes
#AuthorizedKeysFile    %h/.ssh/authorized_keys


# Don't read the user's ~/.rhosts and ~/.shosts files
IgnoreRhosts yes
# For this to work you will also need host keys in /etc/ssh_known_hosts
RhostsRSAAuthentication no
# similar for protocol version 2
HostbasedAuthentication no
# Uncomment if you don't trust ~/.ssh/known_hosts for RhostsRSAAuthentication
#IgnoreUserKnownHosts yes


# To enable empty passwords, change to yes (NOT RECOMMENDED)
PermitEmptyPasswords no


# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no


# Change to no to disable tunnelled clear text passwords


#### Changed to no 2013/01/17


PasswordAuthentication yes


# Kerberos options
#KerberosAuthentication no
#KerberosGetAFSToken no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes


# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes


X11Forwarding yes
X11DisplayOffset 10
PrintMotd no
PrintLastLog yes
TCPKeepAlive yes
#UseLogin no


#MaxStartups 10:30:60
#Banner /etc/issue.net


# Allow client to pass locale environment variables
AcceptEnv LANG LC_*


Subsystem sftp /usr/lib/openssh/sftp-server


# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
UsePAM yes
PidFile /var/run/ltsp-sshd.pid

```

Troubleshooting help is appreciated.

I should note that I only see one instance of sshd
```
/etc/ltsp$ sudo ps -A |grep ssh
 1325 ?        00:00:00 sshd
 2925 ?        00:00:00 ssh-agent
```

and there is an init.d script:

```

/etc/init.d$ cat ltsp-ssh
#! /bin/sh


### BEGIN INIT INFO
# Provides:        sshd
# Required-Start:    $remote_fs $syslog
# Required-Stop:    $remote_fs $syslog
# Default-Start:    2 3 4 5
# Default-Stop:        
# Short-Description:    OpenBSD Secure Shell server
### END INIT INFO


set -e


# /etc/init.d/ssh: start and stop the OpenBSD "secure shell(tm)" daemon


test -x /usr/sbin/sshd || exit 0
( /usr/sbin/sshd -\? 2>&1 | grep -q OpenSSH ) 2>/dev/null || exit 0


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
if [ -e /etc/init/ssh.conf ] && ! chrooted; then
    exec /lib/init/upstart-job ssh "$@"
fi


umask 022


if test -f /etc/default/ssh; then
    . /etc/default/ssh
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
        log_end_msg 0 || true
    fi
    if ! run_by_init; then
        log_action_msg "OpenBSD Secure Shell server not in use (/etc/ssh/sshd_not_to_be_run)" || true
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
        log_action_msg "/dev/null is not a character device!" || true
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
    /usr/sbin/sshd $SSHD_OPTS -t || exit 1
    fi
}


export PATH="${PATH:+$PATH:}/usr/sbin:/sbin"


case "$1" in
  start)
    check_privsep_dir
    check_for_no_start
    check_dev_null
    log_daemon_msg "Starting OpenBSD Secure Shell server" "sshd" || true
    if start-stop-daemon --start --quiet --oknodo --pidfile /var/run/sshd.pid --exec /usr/sbin/sshd -- $SSHD_OPTS; then
        log_end_msg 0 || true
    else
        log_end_msg 1 || true
    fi
    ;;
  stop)
    log_daemon_msg "Stopping OpenBSD Secure Shell server" "sshd" || true
    if start-stop-daemon --stop --quiet --oknodo --pidfile /var/run/sshd.pid; then
        log_end_msg 0 || true
    else
        log_end_msg 1 || true
    fi
    ;;


  reload|force-reload)
    check_for_no_start
    check_config
    log_daemon_msg "Reloading OpenBSD Secure Shell server's configuration" "sshd" || true
    if start-stop-daemon --stop --signal 1 --quiet --oknodo --pidfile /var/run/sshd.pid --exec /usr/sbin/sshd; then
        log_end_msg 0 || true
    else
        log_end_msg 1 || true
    fi
    ;;


  restart)
    check_privsep_dir
    check_config
    log_daemon_msg "Restarting OpenBSD Secure Shell server" "sshd" || true
    start-stop-daemon --stop --quiet --oknodo --retry 30 --pidfile /var/run/sshd.pid
    check_for_no_start log_end_msg
    check_dev_null log_end_msg
    if start-stop-daemon --start --quiet --oknodo --pidfile /var/run/sshd.pid --exec /usr/sbin/sshd -- $SSHD_OPTS; then
        log_end_msg 0 || true
    else
        log_end_msg 1 || true
    fi
    ;;


  try-restart)
    check_privsep_dir
    check_config
    log_daemon_msg "Restarting OpenBSD Secure Shell server" "sshd" || true
    RET=0
    start-stop-daemon --stop --quiet --retry 30 --pidfile /var/run/sshd.pid || RET="$?"
    case $RET in
        0)
        # old daemon stopped
        check_for_no_start log_end_msg
        check_dev_null log_end_msg
        if start-stop-daemon --start --quiet --oknodo --pidfile /var/run/sshd.pid --exec /usr/sbin/sshd -- $SSHD_OPTS; then
            log_end_msg 0 || true
        else
            log_end_msg 1 || true
        fi
        ;;
        1)
        # daemon not running
        log_progress_msg "(not running)" || true
        log_end_msg 0 || true
        ;;
        *)
        # failed to stop
        log_progress_msg "(failed to stop)" || true
        log_end_msg 1 || true
        ;;
    esac
    ;;


  status)
    status_of_proc -p /var/run/sshd.pid /usr/sbin/sshd sshd && exit 0 || exit $?
    ;;


  *)
    log_action_msg "Usage: /etc/init.d/ssh {start|stop|reload|force-reload|restart|try-restart|status}" || true
    exit 1
esac


exit 0
/etc/init.d$ cat ltsp-ssh
#! /bin/sh


### BEGIN INIT INFO
# Provides:        sshd
# Required-Start:    $remote_fs $syslog
# Required-Stop:    $remote_fs $syslog
# Default-Start:    2 3 4 5
# Default-Stop:        
# Short-Description:    OpenBSD Secure Shell server
### END INIT INFO


set -e


# /etc/init.d/ssh: start and stop the OpenBSD "secure shell(tm)" daemon


test -x /usr/sbin/sshd || exit 0
( /usr/sbin/sshd -\? 2>&1 | grep -q OpenSSH ) 2>/dev/null || exit 0


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
if [ -e /etc/init/ssh.conf ] && ! chrooted; then
    exec /lib/init/upstart-job ssh "$@"
fi


umask 022


if test -f /etc/default/ssh; then
    . /etc/default/ssh
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
        log_end_msg 0 || true
    fi
    if ! run_by_init; then
        log_action_msg "OpenBSD Secure Shell server not in use (/etc/ssh/sshd_not_to_be_run)" || true
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
        log_action_msg "/dev/null is not a character device!" || true
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
    /usr/sbin/sshd $SSHD_OPTS -t || exit 1
    fi
}


export PATH="${PATH:+$PATH:}/usr/sbin:/sbin"


case "$1" in
  start)
    check_privsep_dir
    check_for_no_start
    check_dev_null
    log_daemon_msg "Starting OpenBSD Secure Shell server" "sshd" || true
    if start-stop-daemon --start --quiet --oknodo --pidfile /var/run/sshd.pid --exec /usr/sbin/sshd -- $SSHD_OPTS; then
        log_end_msg 0 || true
    else
        log_end_msg 1 || true
    fi
    ;;
  stop)
    log_daemon_msg "Stopping OpenBSD Secure Shell server" "sshd" || true
    if start-stop-daemon --stop --quiet --oknodo --pidfile /var/run/sshd.pid; then
        log_end_msg 0 || true
    else
        log_end_msg 1 || true
    fi
    ;;


  reload|force-reload)
    check_for_no_start
    check_config
    log_daemon_msg "Reloading OpenBSD Secure Shell server's configuration" "sshd" || true
    if start-stop-daemon --stop --signal 1 --quiet --oknodo --pidfile /var/run/sshd.pid --exec /usr/sbin/sshd; then
        log_end_msg 0 || true
    else
        log_end_msg 1 || true
    fi
    ;;


  restart)
    check_privsep_dir
    check_config
    log_daemon_msg "Restarting OpenBSD Secure Shell server" "sshd" || true
    start-stop-daemon --stop --quiet --oknodo --retry 30 --pidfile /var/run/sshd.pid
    check_for_no_start log_end_msg
    check_dev_null log_end_msg
    if start-stop-daemon --start --quiet --oknodo --pidfile /var/run/sshd.pid --exec /usr/sbin/sshd -- $SSHD_OPTS; then
        log_end_msg 0 || true
    else
        log_end_msg 1 || true
    fi
    ;;


  try-restart)
    check_privsep_dir
    check_config
    log_daemon_msg "Restarting OpenBSD Secure Shell server" "sshd" || true
    RET=0
    start-stop-daemon --stop --quiet --retry 30 --pidfile /var/run/sshd.pid || RET="$?"
    case $RET in
        0)
        # old daemon stopped
        check_for_no_start log_end_msg
        check_dev_null log_end_msg
        if start-stop-daemon --start --quiet --oknodo --pidfile /var/run/sshd.pid --exec /usr/sbin/sshd -- $SSHD_OPTS; then
            log_end_msg 0 || true
        else
            log_end_msg 1 || true
        fi
        ;;
        1)
        # daemon not running
        log_progress_msg "(not running)" || true
        log_end_msg 0 || true
        ;;
        *)
        # failed to stop
        log_progress_msg "(failed to stop)" || true
        log_end_msg 1 || true
        ;;
    esac
    ;;


  status)
    status_of_proc -p /var/run/sshd.pid /usr/sbin/sshd sshd && exit 0 || exit $?
    ;;


  *)
    log_action_msg "Usage: /etc/init.d/ssh {start|stop|reload|force-reload|restart|try-restart|status}" || true
    exit 1
esac


exit 0

```

however, and I don't know if this matters or should work, but

```
:/etc/init.d$ sudo start ltsp_sshd
start: Unknown job: ltsp_sshd

```

---

