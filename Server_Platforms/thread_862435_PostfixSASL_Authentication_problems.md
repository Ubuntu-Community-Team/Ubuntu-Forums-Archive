---
title: "Postfix/SASL Authentication problems"
date: 2008-07-17
forum: Server Platforms
---

### Post by LPomfrey on 2008-07-17
I've set up a mail server with virtual users and domains according to [http://www.flurdy.com/docs/postfix](http://www.flurdy.com/docs/postfix) (and tried the SASL authentication part of the tutorial at [http://www.howtoforge.com/virtual-users-and-domains-with-postfix-ubuntu-7.10-p3](http://www.howtoforge.com/virtual-users-and-domains-with-postfix-ubuntu-7.10-p3) ) but I'm still having trouble logging in to send mail. Receiving mail is working just fine, however.

Here are my config files:

/etc/postfix/main.cf
```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
delay_warning_time = 4h

# will it be a permanent error or temporary
unknown_local_recipient_reject_code = 450

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/ssl/postfix.cert
smtpd_tls_key_file = /etc/postfix/ssl/postfix.key
smtpd_use_tls = yes
smtp_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
smtpd_tls_loglevel = 1
#smtpd_tls_received_header = yes
#tls_random_source = dev:/dev/urandom

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

mydomain = lukepomfrey.org
myhostname = mail.lukepomfrey.org
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = mail.lukepomfrey.org
mydestination =
relayhost = mail.lukepomfrey.org:25
#relayhost = smtp.virgin.net
relay_domains = lukepomfrey.org, northfleeteaglesfc.org
#relay_transport = relay
mynetworks =
#mynetworks = 127.0.0.0/8
mynetworks_style = all
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
masquerade_domains = mail.lukepomfrey.org,mail.northfleeteaglesfc.org


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

# Requirements for the HELO statement
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit

# Requirements for the sender details
smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit

# Requirements for the connecting server
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org, permit

# Requirement for the recipient address
smtpd_recipient_restrictions = permit_sasl_authenticated, reject_unauth_pipelining, permit_mynetworks, reject_non_fqdn_recipient, reject_unauth_destination, check_rel$

# Requirement for data restrictions
#smtpd_data_restrictions = reject_unauth_pipelining

# require proper helo at connections
smtpd_helo_required = yes

# waste spammers time before rejecting them
smtpd_delay_reject = yes
disable_vrfy_command = yes

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

content_filter = smtp-amavis:[127.0.0.1]:10024
smtp-amavis_destination_concurrency_limit = 2
#receive_override_options = no_address_mappings


# SASL SUPPORT FOR CLIENTS
#
# The following options set parameters needed by Postfix to enable
# Cyrus-SASL support for authentication of mail clients.
#

smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain =
broken_sasl_auth_clients = yes
smtpd_tls_auth_only = no
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
smtp_sasl_password_maps = mysql:/etc/postfix/sasl_auth

```

/etc/postfix/master.cf
```
#
# Postfix master process configuration file.  For details on the format
# of the file, see the master(5) manual page (command: "man 5 master").
#
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       n       -       -       smtpd
   -o cleanup_service_name=pre-cleanup
submission inet n       -       n       -       -       smtpd
  -o smtpd_enforce_tls=yes
  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
smtps     inet  n       -       n       -       -       smtpd
  -o smtpd_tls_wrappermode=yes
  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#628      inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       n       60      1       pickup
   -o content_filter=
   -o receive_override_options=no_header_body_checks
cleanup   unix  n       -       n       -       0       cleanup
   -o mime_header_checks=
   -o nested_header_checks=
   -o body_checks=
   -o header_checks=
qmgr      fifo  n       -       n       300     1       qmgr
#qmgr     fifo  n       -       -       300     1       oqmgr
tlsmgr    unix  -       -       n       1000?   1       tlsmgr
rewrite   unix  -       -       n       -       -       trivial-rewrite
bounce    unix  -       -       n       -       0       bounce
defer     unix  -       -       n       -       0       bounce
trace     unix  -       -       n       -       0       bounce
verify    unix  -       -       n       -       1       verify
flush     unix  n       -       n       1000?   0       flush
proxymap  unix  -       -       n       -       -       proxymap
smtp      unix  -       -       n       -       -       smtp
# When relaying mail as backup MX, disable fallback_relay to avoid MX loops
relay     unix  -       -       n       -       -       smtp
        -o smtp_fallback_relay=
#       -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
showq     unix  n       -       n       -       -       showq
error     unix  -       -       n       -       -       error
retry     unix  -       -       n       -       -       error
discard   unix  -       -       n       -       -       discard
local     unix  -       n       n       -       -       local
virtual   unix  -       n       n       -       -       virtual
lmtp      unix  -       -       n       -       -       lmtp
anvil     unix  -       -       n       -       1       anvil
scache    unix  -       -       n       -       1       scache
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
smtp-amavis     unix    -       n       -       -       2       smtp
    -o smtp_data_done_timeout=1200
    -o smtp_send_xforward_command=yes
    -o disable_dns_lookups=yes
    -o max_use=20
127.0.0.1:10025 inet    n       n       -       -       -       smtpd
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
pre-cleanup unix       n       n       -       -       0       cleanup
   -o virtual_alias_maps=
   -o canonical_maps=
   -o sender_canonical_maps=
   -o recipient_canonical_maps=
   -o masquerade_domains=

```

/etc/postfix/sasl/smtpd.conf
```
pwcheck_method: saslauthd
mech_list: plain login
allow_plaintext: true
auxprop_plugin: mysql
sql_hostnames: 127.0.0.1
sql_user: ******
sql_passwd: *******
sql_database: ******
sql_select: select crypt from users where id = '%u' and enabled = '1'

```

/etc/default/saslauthd
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
# Example for postfix users: "-c -m /var/spool/postfix/var/run/saslauthd"
OPTIONS="-c -m /var/spool/postfix/var/run/saslauthd -r"

```

/etc/pam.d/smtp
```
auth    required   pam_mysql.so user=****** passwd=****** host=127.0.0.1 db=****** table=users usercolumn=id passwdcolumn=crypt crypt=1
account sufficient pam_mysql.so user=****** passwd=****** host=127.0.0.1 db=****** table=users usercolumn=id passwdcolumn=crypt crypt=1

```

/etc/courier/authmysqlrc
```
MYSQL_SERVER localhost
MYSQL_USERNAME ******
MYSQL_PASSWORD ******
MYSQL_PORT 0
MYSQL_DATABASE ******
MYSQL_USER_TABLE users
MYSQL_CRYPT_PWFIELD crypt
MYSQL_CLEAR_PWFIELD clear
MYSQL_UID_FIELD 5000
MYSQL_GID_FIELD 5000
MYSQL_LOGIN_FIELD id
MYSQL_HOME_FIELD home
MYSQL_MAILDIR_FIELD maildir
#MYSQL_NAME_FIELD
#MYSQL_QUOTA_FIELD quota

```


TLS appears to be working, but logging in to send e-mail isn't. Thunderbird just asks repeatedly for my password.

Any help would be much appreciated.

Thanks.

---

### Post by LPomfrey on 2008-07-18
Running "saslfinger -c" gives output ending in:
```
There is no /etc/postfix/sasl_auth.cf.db!
```

Where /etc/postfix/sasl_auth.cf contains:
```
user=******
password=******
dbname=******
table=users
select_field=pass_map
where_field=id
hosts=localhost

```
Where the 'pass_map' field contains entries of the form:
```
user@domain.org:password
```

I get the impression that this is what is causing the problem, but I can't find anything that explains what should go in /etc/postfix/sasl_auth.cf.

tail /var/log/mail.log gives:
```
Jul 18 12:47:52 heisenberg postfix/smtpd[6623]: warning: SASL authentication problem: unable to open Berkeley db /etc/sasldb2: Permission denied
Jul 18 12:47:52 heisenberg last message repeated 5 times
Jul 18 12:47:52 heisenberg postfix/smtpd[6623]: warning: host212-183-132-77.uk.access.vodafone.net[212.183.132.77]: SASL LOGIN authentication failed: authentication failure
Jul 18 12:47:53 heisenberg postfix/qmgr[6626]: fatal: qmgr_move: update active/AA6EC236ECD time stamps: Operation not permitted
Jul 18 12:47:54 heisenberg postfix/master[5501]: warning: process /usr/lib/postfix/qmgr pid 6626 exit status 1
Jul 18 12:47:54 heisenberg postfix/master[5501]: warning: /usr/lib/postfix/qmgr: bad command startup -- throttling
Jul 18 12:47:58 heisenberg postfix/smtpd[6623]: disconnect from host212-183-132-77.uk.access.vodafone.net[212.183.132.77]
Jul 18 12:48:54 heisenberg postfix/qmgr[6628]: fatal: qmgr_move: update active/AA6EC236ECD time stamps: Operation not permitted
Jul 18 12:48:55 heisenberg postfix/master[5501]: warning: process /usr/lib/postfix/qmgr pid 6628 exit status 1
Jul 18 12:48:55 heisenberg postfix/master[5501]: warning: /usr/lib/postfix/qmgr: bad command startup -- throttling
```

---

