---
title: "Cyrus SASL / Posfix issue...please help"
date: 2008-11-26
forum: Server Platforms
---

### Post by shoeman22 on 2008-11-26
Hello,
I'm trying to setup a home mail server (hardy heron) and have been banging my head on my desk the last couple of days trying to get Cyrus SASL / Postfix / Mysql to get along.

My server is built mostly off of this guide: 
[http://flurdy.com/docs/postfix/index.htm]("http://flurdy.com/docs/postfix/index.htm")

I've gotten everything to work except for SASL authentication of the SMTP connections.  I've got sql logging enabled so I can tail the query log and nothing gets fired when I try to authenticate to send an email with Thunderbird, though courier is able to authenticate against it just fine.  I've tried everything I know how to do and have exhaustively googled the interwebs but nothing has solved the problem

So, without further ado, here are my config files...

/etc/postfix/main.cf
```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
# myorigin = leftshoedevelopment

smtpd_banner = $myhostname ESMTP $mail_name
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

# This is already done in /etc/mailname
#myhostname = larry-server.leftshoedevelopment.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = leftshoedevelopment.com
# mydestination = leftshoedevelopment.com, larry-server.leftshoedevelopment.com, localhost.leftshoedevelopment.com, localhost
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
mynetworks_style = host
local_recipient_maps =
mydestination =

# how long if undelivered before sending warning update to sender
delay_warning_time = 4h
# will it be a permanent error or temporary
unknown_local_recipient_reject_code = 450
# how long to keep message on queue before return as failed.
# some have 3 days, I have 16 days as I am backup server for some people
# whom go on holiday with their server switched off.
maximal_queue_lifetime = 7d
# max and min time in seconds between retries if connection failed
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s
# how long to wait when servers connect before receiving rest of data
smtp_helo_timeout = 60s
# how many address can be used in one message.
# effective stopper to mass spammers, accidental copy in whole address list
# but may restrict intentional mail shots.
smtpd_recipient_limit = 16
# how many error before back off.
smtpd_soft_error_limit = 3
# how many max errors before blocking it.
smtpd_hard_error_limit = 12
# enabled for PostGrey
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unauth_destination, reject_unknown_recipient_domain, reject_unauth_destination, check_policy_service inet:127.0.0.1:60000, permit
# enabled for cyrus sasl
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit

#sasl configuration
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
cyrus_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
#smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain =

# require proper helo at connections
smtpd_helo_required = yes
# waste spammers time before rejecting them
smtpd_delay_reject = yes
disable_vrfy_command = yes

# not sure of the difference of the next two
# but they are needed for local aliasing
alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
# this specifies where the virtual mailbox folders will be located
virtual_mailbox_base = /var/spool/mail/virtual
# this is for the mailbox location for each user
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
# and their user id
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf
# and group id
virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf
# and this is for aliases
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
# and this is for domain lookups
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
# this is how to connect to the domains (all virtual, but the option is there)
# not used yet
# transport_maps = mysql:/etc/postfix/mysql_transport.cf

# amavis content filtering
content_filter = amavis:[127.0.0.1]:10024

# TLS parameters
#smtp_use_tls = no
smtp_tls_security_level = may
#smtpd_use_tls=yes
smtpd_tls_security_level = may
#smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
smtpd_tls_cert_file=/etc/ssl/certs/smtpd.crt
smtpd_tls_key_file=/etc/ssl/private/smtpd.key
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
#smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
#smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
```

/etc/postfix/master.cf
```
#
# Postfix master process configuration file.  For details on the format
# of the file, see the master(5) manual page (command: "man 5 master").
#
# Do not forget to execute "postfix reload" after editing this file.
#
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       -       -       -       smtpd
submission inet n       -       -       -       -       smtpd
        -o smtpd_sasl_auth_enable=yes
# if you do not want to restrict it encryption only, comment out next line
        -o smtpd_tls_auth_only=yes
#       -o smtpd_tls_security_level=encrypt
#       -o header checks=
#       -o body_checks=
        -o smtpd_client_restrictions=permit_sasl_authenticated,reject_unauth_destination,reject
        -o smtpd_sasl_security_options=noanonymous,noplaintext
        -o smtpd_sasl_tls_security_options=noanonymous
#       -o smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
#       -o milter_macro_daemon_name=ORIGINATING
smtps     inet  n       -       -       -       -       smtpd
        -o smtpd_tls_wrappermode=yes
        -o smtpd_sasl_auth_enable=yes
        -o smtpd_tls_auth_only=yes
        -o smtpd_client_restrictions=permit_sasl_authenticated,reject
        -o smtpd_sasl_security_options=noanonymous,noplaintext
        -o smtpd_sasl_tls_security_options=noanonymous
#       -o smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
#       -o milter_macro_daemon_name=ORIGINATING
#628      inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       -       60      1       pickup
        -o content_filter=
        -o receive_override_options=no_header_body_checks
cleanup   unix  n       -       -       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
#qmgr     fifo  n       -       -       300     1       oqmgr
tlsmgr    unix  -       -       -       1000?   1       tlsmgr
rewrite   unix  -       -       -       -       -       trivial-rewrite
bounce    unix  -       -       -       -       0       bounce
defer     unix  -       -       -       -       0       bounce
trace     unix  -       -       -       -       0       bounce
verify    unix  -       -       -       -       1       verify
flush     unix  n       -       -       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
proxywrite unix -       -       n       -       1       proxymap
smtp      unix  -       -       -       -       -       smtp
# When relaying mail as backup MX, disable fallback_relay to avoid MX loops
relay     unix  -       -       -       -       -       smtp
        -o smtp_fallback_relay=



#       -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
showq     unix  n       -       -       -       -       showq
error     unix  -       -       -       -       -       error
retry     unix  -       -       -       -       -       error
discard   unix  -       -       -       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       -       -       -       lmtp
anvil     unix  -       -       -       -       1       anvil
scache    unix  -       -       -       -       1       scache
#
# ====================================================================
# Interfaces to non-Postfix software. Be sure to examine the manual
# pages of the non-Postfix software to find out what options it wants.
#
# Many of the following services use the Postfix pipe(8) delivery
# agent.  See the pipe(8) man page for information about ${recipient}
# and other message envelope options.
# ====================================================================
#
# maildrop. See the Postfix MAILDROP_README file for details.
# Also specify in main.cf: maildrop_destination_recipient_limit=1
#
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/bin/maildrop -d ${recipient}
#
# See the Postfix UUCP_README file for configuration details.
#
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
#
# Other external delivery methods.
#
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix  -       n       n       -       2       pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}
# amavis filtering
amavis    unix  -       -       -       -       2       smtp
        -o smtp_data_done_timeout=1200
        -o smtp_send_xforward_command=yes
        -o disable_dns_lookups=yes
        -o max_use=20
127.0.0.1:10025 inet    n       -       -       -       -       smtpd
        -o content_filter=
        -o local_recipient_maps=
        -o relay_recipient_maps=
        -o smtpd_restriction_classes=
        -o smtpd_delay_reject=no
        -o smtpd_client_restrictions=permit_mynetworks,reject
        -o smtpd_helo_restrictions=
        -o smtpd_sender_restrictions=
        -o smtpd_recipient_restrictions=permit_mynetworks,reject
        -o smtpd_data_restrictions=reject_unauth_pipelining
        -o smtpd_end_of_data_restrictions=
        -o mynetworks=127.0.0.0/8
        -o smtpd_error_sleep_time=0
        -o smtpd_soft_error_limit=1001
        -o smtpd_hard_error_limit=1000
        -o smtpd_client_connection_count_limit=0
        -o smtpd_client_connection_rate_limit=0
        -o receive_override_options=no_header_body_checks,no_unknown_recipient_checks

```

/etc/postfix/sasl/smtpd.conf
```
pwcheck_method: auxprop
mech_list: plain login cram-md5 digest-md5
auxprop_plugin: mysql
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: my_user
sql_passwd: my_pass
sql_database: maildb
sql_select: SELECT clear FROM users WHERE id='%u@%r' AND enabled = 1
```

/etc/default/saslauthd
```
#
# Settings for saslauthd daemon
# Please read /usr/share/doc/sasl2-bin/README.Debian for details.
#

# Should saslauthd run automatically on startup? (default: no)
START=yes

PWDIR="/var/spool/postfix/var/run/saslauthd"
#PWDIR="/var/run/saslauthd"
PARAMS="-m ${PWDIR}"
PIDFILE="${PWDIR}/saslauthd.pid"


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
OPTIONS="-c -m /var/spool/postfix/var/run/saslauthd"
#OPTIONS="-c -m /var/run/saslauthd"
```

Here's what my logs look like when I try to send with thunderbird, TLS and username options
tail -f /var/log/auth.log
```
Nov 25 21:55:55 larry-server postfix/smtpd[20568]: sql auxprop plugin using mysql engine
```

tail -f /var/log/mail.log
```
Nov 25 21:55:55 larry-server postfix/smtpd[20568]: warning: my_ip: hostname host-my-ip.my_host.net verification failed: No address associated with hostname
Nov 25 21:55:55 larry-server postfix/smtpd[20568]: connect from unknown[my_ip]
Nov 25 21:55:55 larry-server postfix/smtpd[20568]: setting up TLS connection from unknown[my_ip]
Nov 25 21:55:55 larry-server postfix/smtpd[20568]: Anonymous TLS connection established from unknown[my_ip]: TLSv1 with cipher DHE-RSA-AES256-SHA (256/256 bits)
Nov 25 21:55:58 larry-server postfix/smtpd[20568]: warning: SASL authentication failure: no secret in database
Nov 25 21:55:58 larry-server postfix/smtpd[20568]: warning: unknown[my_ip]: SASL CRAM-MD5 authentication failed: authentication failure
Nov 25 21:55:58 larry-server postfix/smtpd[20568]: warning: SASL authentication failure: Password verification failed
Nov 25 21:55:58 larry-server postfix/smtpd[20568]: warning: unknown[my_ip]: SASL PLAIN authentication failed: authentication failure
Nov 25 21:55:58 larry-server postfix/smtpd[20568]: warning: unknown[my_ip]: SASL LOGIN authentication failed: authentication failure
Nov 25 21:57:00 larry-server postfix/smtpd[20568]: lost connection after AUTH from unknown[my_ip]
Nov 25 21:57:00 larry-server postfix/smtpd[20568]: disconnect from unknown[my_ip]
```

tail -f /var/log/mysql/mysql.log
```
(vast empty void of nothingness that makes me want to cry)
```

also, I don't know if this helps, but here is what 
aptitude search sasl postfix 
returns
```

p   bld-postfix                                                                                                    - Postfix tools for the Black List Daemon
p   cyrus-sasl2-dbg                                                                                                - Cyrus SASL - debugging symbols
p   cyrus-sasl2-doc                                                                                                - Cyrus SASL - documentation
p   cyrus-sasl2-heimdal-dbg                                                                                        - Debugging symbols for Cyrus SASL
p   dtc-postfix-courier                                                                                            - web control panel for admin and accounting hosting services (more depends)
p   gforge-mta-postfix                                                                                             - collaborative development tool - mail tools (using Postfix)
p   gsasl                                                                                                          - GNU SASL command line utility
i   libauthen-sasl-cyrus-perl                                                                                      - Perl extension for Cyrus SASL library
i A libauthen-sasl-perl                                                                                            - Authen::SASL - SASL Authentication framework
p   libgsasl7                                                                                                      - GNU SASL library
p   libgsasl7-dev                                                                                                  - Development files for the GNU SASL library
p   libsasl2                                                                                                       - Cyrus SASL - authentication abstraction library (transitional package)
i   libsasl2-2                                                                                                     - Cyrus SASL - authentication abstraction library
p   libsasl2-dev                                                                                                   - Cyrus SASL - development files for authentication abstraction library
i   libsasl2-modules                                                                                               - Cyrus SASL - pluggable authentication modules
p   libsasl2-modules-gssapi-heimdal                                                                                - Pluggable Authentication Modules for SASL (GSSAPI)
p   libsasl2-modules-gssapi-mit                                                                                    - Cyrus SASL - pluggable authentication modules (GSSAPI)
p   libsasl2-modules-ldap                                                                                          - Cyrus SASL - pluggable authentication modules (LDAP)
p   libsasl2-modules-otp                                                                                           - Cyrus SASL - pluggable authentication modules (OTP)
i   libsasl2-modules-sql                                                                                           - Cyrus SASL - pluggable authentication modules (SQL)
p   php5-sasl                                                                                                      - Cyrus SASL extension for PHP 5
i   postfix                                                                                                        - High-performance mail transport agent
p   postfix-cdb                                                                                                    - CDB map support for Postfix
p   postfix-dev                                                                                                    - Loadable modules development environment for Postfix
p   postfix-doc                                                                                                    - Documentation for Postfix
p   postfix-gld                                                                                                    - greylisting daemon for postfix, written in C, uses MySQL
p   postfix-ldap                                                                                                   - LDAP map support for Postfix
i   postfix-mysql                                                                                                  - MYSQL map support for Postfix
p   postfix-pcre                                                                                                   - PCRE map support for Postfix
p   postfix-pgsql                                                                                                  - PGSQL map support for Postfix
p   postfix-policyd                                                                                                - anti-spam plugin for Postfix
p   postfix-policyd-spf-perl                                                                                       - pure-Perl Postfix policy daemon for RFC 4408 compliant SPF checking
p   postfix-policyd-spf-python                                                                                     - pure-Python Postfix policy daemon for SPF checking
p   postfix-smtpguard                                                                                              - smtpguard policy service daemon for Postfix
v   postfix-tls                                                                                                    -
i   sasl2-bin                                                                                                      - Cyrus SASL - administration programs for SASL users database

```

---

### Post by shoeman22 on 2008-11-26
I finally figured this out...I had a bad value for the auxprop_plugin variable in /etc/sasl/smtpd.conf.  It should be "sql" rather than "mysql".  

so here is the new source of /etc/sasl/smtpd.conf
```
pwcheck_method: auxprop
log_level: 3
mech_list: plain login cram-md5 digest-md5
auxprop_plugin: sql
sql_engine: mysql
sql_hostnames: 127.0.0.1
sql_user: my_user
sql_passwd: my_pass
sql_database: maildb
sql_select: SELECT clear FROM users WHERE id='%u@%r' AND enabled = 1

```

then restart postfix, /etc/init.d/postfix restart

---

