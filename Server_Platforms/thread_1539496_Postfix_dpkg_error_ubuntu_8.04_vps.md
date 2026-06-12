---
title: "Postfix dpkg error ubuntu 8.04 vps"
date: 2010-07-26
forum: Server Platforms
---

### Post by barrydirk on 2010-07-26
Hi all need some help here. I am setting up a ubuntu 8.04 vps via ssh and have run into some problems with postfix instalation. This is the second time I have done this exact instalation on the same IP but since they recreated my vps I get the folowing output.

root@31376:~# apt-get install postfix libsasl2-2 sasl2-bin libsasl2-modules procmail
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libldap-2.4-2
Suggested packages:
  libsasl2-modules-gssapi-mit libsasl2-modules-gssapi-heimdal libsasl2-modules-ldap libsasl2-modules-otp
  libsasl2-modules-sql mail-reader postfix-cdb postfix-ldap postfix-mysql postfix-pcre postfix-pgsql resolvconf
The following NEW packages will be installed:
  libldap-2.4-2 libsasl2-2 libsasl2-modules postfix procmail sasl2-bin
0 upgraded, 6 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B/1888kB of archives.
After this operation, 4555kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
Selecting previously deselected package libsasl2-modules.
(Reading database ... 14676 files and directories currently installed.)
Unpacking libsasl2-modules (from .../libsasl2-modules_2.1.22.dfsg1-18ubuntu2.1_i386.deb) ...
Selecting previously deselected package libsasl2-2.
Unpacking libsasl2-2 (from .../libsasl2-2_2.1.22.dfsg1-18ubuntu2.1_i386.deb) ...
Selecting previously deselected package libldap-2.4-2.
Unpacking libldap-2.4-2 (from .../libldap-2.4-2_2.4.9-0ubuntu0.8.04.3_i386.deb) ...
Selecting previously deselected package postfix.
Unpacking postfix (from .../postfix_2.5.1-2ubuntu1.2_i386.deb) ...
Selecting previously deselected package procmail.
Unpacking procmail (from .../procmail_3.22-16ubuntu3_i386.deb) ...
Selecting previously deselected package sasl2-bin.
Unpacking sasl2-bin (from .../sasl2-bin_2.1.22.dfsg1-18ubuntu2.1_i386.deb) ...
Setting up procmail (3.22-16ubuntu3) ...
Setting up libsasl2-modules (2.1.22.dfsg1-18ubuntu2.1) ...
Setting up libsasl2-2 (2.1.22.dfsg1-18ubuntu2.1) ...

Setting up libldap-2.4-2 (2.4.9-0ubuntu0.8.04.3) ...

Setting up postfix (2.5.1-2ubuntu1.2) ...
Adding group `postfix' (GID 111) ...
Done.
Adding system user `postfix' (UID 108) ...
Adding new user `postfix' (UID 108) with group `postfix' ...
Not creating home directory `/var/spool/postfix'.
Creating /etc/postfix/dynamicmaps.cf
Adding tcp map entry to /etc/postfix/dynamicmaps.cf
Adding group `postdrop' (GID 112) ...
Done.
setting myhostname: 31376
setting alias maps
setting alias database
mailname is not a fully qualified domain name.  Not changing /etc/mailname.
setting destinations: 31376, localhost.localdomain, , localhost
setting relayhost: 
setting mynetworks: 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
setting mailbox_command
setting mailbox_size_limit: 0
setting recipient_delimiter: +
setting inet_interfaces: all
WARNING: /etc/aliases exists, but does not have a root alias.

Postfix is now set up with a default configuration.  If you need to make 
changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
newaliases: warning: valid_hostname: numeric hostname: 31376
newaliases: fatal: file /etc/postfix/main.cf: parameter myhostname: bad parameter value: 31376
dpkg: error processing postfix (--configure):
 subprocess post-installation script returned error exit status 75
Setting up sasl2-bin (2.1.22.dfsg1-18ubuntu2.1) ...
 * To enable saslauthd, edit /etc/default/saslauthd and set START=yes

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)

I assume this has something to do with the host name that gets auto assigned to my account but I cant seem to change it and flexisuport.com are about as usefull aas a bucket of wet sand.

my /etc/hosts file looks like this

127.0.0.1 localhost.localdomain localhost
# Auto-generated hostname. Please do not remove this comment.
208.43.137.6 31376.scholfieldtrading.com  

/etc/init.d/hostname.sh start

#! /bin/sh
### BEGIN INIT INFO
# Provides:          hostname
# Required-Start:
# Required-Stop:
# Default-Start:     S
# Default-Stop:
# Short-Description: Set hostname.
# Description:
### END INIT INFO

PATH=/sbin:/bin

. /lib/init/vars.sh
. /lib/lsb/init-functions

do_start () {
        [ -f /etc/hostname ] && HOSTNAME="$(cat /etc/hostname)"

        # Keep current name if /etc/hostname is missing.
        [ -z "$HOSTNAME" ] && HOSTNAME="$(hostname)"

        # And set it to 'localhost' if no setting was found
        [ -z "$HOSTNAME" ] && HOSTNAME=localhost

        [ "$VERBOSE" != no ] && log_action_begin_msg "Setting hostname to '$HOSTNAME'"
        hostname "$HOSTNAME"
        ES=$?
        [ "$VERBOSE" != no ] && log_action_end_msg $ES
}

case "$1" in
  start|"")
        do_start
        ;;
  restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
  stop)
        # No-op
        ;;
  *)
        echo "Usage: hostname.sh [start|stop]" >&2
        exit 3
        ;;
esac

Please help

---

