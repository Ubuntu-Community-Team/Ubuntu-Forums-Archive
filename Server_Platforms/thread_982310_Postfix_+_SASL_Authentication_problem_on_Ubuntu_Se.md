---
title: "Postfix + SASL Authentication problem on Ubuntu Server 8.04"
date: 2008-11-14
forum: Server Platforms
---

### Post by beusekom on 2008-11-14
Hi,

I am trying to configure an e-mail server (for the first time) based on Ubuntu server 8.04 and Postfix and run into a small problem. 

At the moment receiving e-mail and fetching it using POP3 is working, I also successfully configured Postfixadmin. However I run into problems when sending e-mail from a remote client through the (SMTP) server.

I see in the logs that connecting works but that the SASL Authentication doesn't work. The exact error shows:```
Nov 14 12:53:58 mail postfix/smtpd[17161]: connect from unknown[192.168.1.20]
Nov 14 12:54:00 mail postfix/smtpd[17161]: warning: unknown[192.168.1.20]: SASL LOGIN authentication failed: authentication failure
Nov 14 12:54:00 mail postfix/smtpd[17161]: lost connection after AUTH from unknown[192.168.1.20]
Nov 14 12:54:00 mail postfix/smtpd[17161]: disconnect from unknown[192.168.1.20]
```
When I manually run the saslauthd daemon I get the following error:```
root@mail:~# saslauthd -a pam  -n 5  -V -c -m /var/spool/postfix/var/run/saslauthd -r -d
saslauthd[17187] :main            : num_procs  : 5
saslauthd[17187] :main            : mech_option: NULL
saslauthd[17187] :main            : run_path   : /var/spool/postfix/var/run/saslauthd
saslauthd[17187] :main            : auth_mech  : pam
saslauthd[17187] :cache_alloc_mm  : mmaped shared memory segment on file: /var/spool/postfix/var/run/saslauthd/cache.mmap
saslauthd[17187] :cache_init      : bucket size: 92 bytes
saslauthd[17187] :cache_init      : stats size : 36 bytes
saslauthd[17187] :cache_init      : timeout    : 28800 seconds
saslauthd[17187] :cache_init      : cache table: 944764 total bytes
saslauthd[17187] :cache_init      : cache table: 1711 slots
saslauthd[17187] :cache_init      : cache table: 10266 buckets
saslauthd[17187] :cache_init_lock : flock file opened at /var/spool/postfix/var/run/saslauthd/cache.flock
saslauthd[17187] :ipc_init        : using accept lock file: /var/spool/postfix/var/run/saslauthd/mux.accept
saslauthd[17187] :detach_tty      : master pid is: 0
saslauthd[17187] :ipc_init        : listening on socket: /var/spool/postfix/var/run/saslauthd/mux
saslauthd[17187] :main            : using process model
saslauthd[17188] :get_accept_lock : acquired accept lock
saslauthd[17187] :have_baby       : forked child: 17188
saslauthd[17187] :have_baby       : forked child: 17189
saslauthd[17187] :have_baby       : forked child: 17190
saslauthd[17187] :have_baby       : forked child: 17191
saslauthd[17188] :rel_accept_lock : released accept lock
saslauthd[17188] :cache_get_rlock : attempting a read lock on slot: 469
saslauthd[17188] :cache_lookup    : [login=mvanbeusekom@themobilebrand.com] [service=themobilebrand.com] [realm=smtp]: not found, update pending
saslauthd[17188] :cache_un_lock   : attempting to release lock on slot: 469
saslauthd[17189] :get_accept_lock : acquired accept lock
saslauthd[17188] :do_auth         : auth failure: [user=mvanbeusekom@themobilebrand.com] [service=smtp] [realm=themobilebrand.com] [mech=pam] [reason=PAM auth error]

```

Can anyone help me out, I am completely lost. Below is more information on my configuration:

/etc/postfix/mail.cf:```
root@mail:~# cat /etc/postfix/main.cf
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mail, localhost.localdomain, localhost
relayhost =
mynetworks = 127.0.0.0/8 192.168.1.0/24 [::ffff:127.0.0.0]/104 [::1]/128
#mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
notify_classes = resource, software, protocol
home_mailbox = Maildir/

# All virtual mailboxes live somewhere here ..
virtual_mailbox_base = /var/mail/vmail

# The (virtual) domains we accept mail for
virtual_mailbox_domains = mysql:/etc/postfix/mysql/mysql-virtual-domains.cf

# Lookup mailbox location, uid and gid based on email address received.
virtual_mailbox_maps = mysql:/etc/postfix/mysql/mysql-virtual-mailbox-maps.cf
virtual_uid_maps = static:101
virtual_gid_maps = static:101

virtual_alias_maps = mysql:/etc/postfix/mysql/mysql-virtual-alias-maps.cf

relay_domains = mysql:/etc/postfix/mysql/mysql-relay-domains.cf
local_transport = virtual
local_recipient_maps = $virtual_mailbox_maps


# Restrictions
smtpd_recipient_restrictions = permit_sasl_authenticated,
        permit_mynetworks,
        reject_non_fqdn_recipient,
        reject_unauth_destination
smtpd_sender_restrictions = permit_mynetworks,
        reject_non_fqdn_sender,
        reject_unknown_sender_domain,
        reject_unauth_pipelining

# Configuration for Postfix SMTP Auth support
smtpd_sasl_local_domain=
smtpd_sasl_authenticated_header = yes
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
```
/etc/postfix/sasl/smtpd.conf:```
root@mail:~# cat /etc/postfix/sasl/smtpd.conf
pwcheck_method: saslauthd
saslauthd_path: /var/run/saslauthd/mux
log_level:      3
mech_list:      PLAIN LOGIN
```
/etc/default/saslauthd:```
root@mail:~# cat /etc/default/saslauthd
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
OPTIONS="-r -c -m /var/spool/postfix/var/run/saslauthd"
```

Many thanks, Maurits

---

### Post by HermanAB on 2008-11-14
In my experience with Postfix and SASL Authentication, the best solution is to say 'Screw It' and install Citadel.  With Citadel, everything 'Just Works' so you can install it and in less than an hour, you can get on with your life and go do something better...

Cheers,

Herman

---

### Post by beusekom on 2008-11-14
Somebody pointed me out on a from option which I set in the /etc/default/saslauthd file. I was using the following options:```
OPTIONS="-r -c -m /var/spool/postfix/var/run/saslauthd"
```The -r option should not be here, after removing it and restart postfix and saslauthd I was able to send my first e-mail.

This is what the man pages say about the -r option (for those who are interrested):```
     -r      Combine the realm with the login (with an '@' sign in between).
             e.g.  login: "foo" realm: "bar" will get passed as login:
             "foo@bar".  Note that the realm will still be passed, which may
             lead to unexpected behavior.
```
Herman thanks for the tip regarding Citadel, I will definately look into it, looks promising.

---

