---
title: "HELP! mail transport unavailable-Problem not solvable (for me)"
date: 2014-05-07
forum: Server Platforms
---

### Post by stickybit2 on 2014-05-07
you guys,

got a big problem on a productive system (website, mailserver were heavyly used by about 500 Accounts 24/7)!
The Mailaccounts on my server don't receive any mails! Nor from inside (internal mails), nor from outside... The problem occured 2 days ago - but I didn't change anything! And before these errors, everything worked fine.

I noticed the following errors: 

/var/log/mail.warn: 
```
May  7 20:23:51 xyz-domain postfix/qmgr[2004]: warning: connect to transport private/amavis: No such file or directory
```

/var/log/mail.log:
```
postfix/error[7999]: 799E784C033: to=<fail2ban@blocklist.de>, relay=none, delay=1179, delays=1179/0.33/0/0, dsn=4.3.0, status=deferred (mail transport unavailable)
```

/var/log/dovecot.info:
```
2014-05-07 20:38:11 auth(default): Info: passwd(blablabla@xyz-domain.org,209.85.214.162): lookup
2014-05-07 20:38:11 auth(default): Info: passwd(blablabla@xyz-domain.org,209.85.214.162): unknown user
```


Any ideas why this is happening!?? The errors occured suddenly 2 days ago, not a clue why.. For further research, here are my config files:

[postconf -n]
```
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
content_filter = amavis:127.0.0.1:10024
inet_interfaces = all
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
message_size_limit = 20480000
mydestination = mail.market-team.org, localhost.localdomain, localhost
mydomain = mail.market-team.org
myhostname = market-team.org
mynetworks = 127.0.0.0/8 [::1]/12
readme_directory = no
receive_override_options = no_header_body_checks
recipient_delimiter = +
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Debian/GNU)
smtpd_recipient_restrictions = permit_mynetworks,permit_sasl_authenticated,reject_unauth_destination, check_policy_service inet:127.0.0.1:2501 permit
smtpd_sasl_auth_enable = yes
smtpd_sasl_authenticated_header = yes
smtpd_sasl_local_domain = $myhostname
smtpd_sasl_path = private/auth
smtpd_sasl_security_options = noanonymous
smtpd_sasl_type = dovecot
smtpd_tls_auth_only = no
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
soft_bounce = no
virtual_alias_maps = mysql:/etc/postfix/mysql-virtual-alias-maps.cf,mysql:/etc/postfix/mysql-email2email.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql-virtual-mailbox-domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql-virtual-mailbox-maps.cf
virtual_transport = dovecot

```

[/etc/postfix/main.cf]
```

#myorigin = /etc/mailname
smtpd_sasl_authenticated_header = yes
smtpd_banner = $myhostname ESMTP $mail_name (Debian/GNU)
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

mydomain = mail.xyz.org
myhostname = xyz.org
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = mail.market-team.org, localhost.localdomain, localhost
#relayhost =
mynetworks = 127.0.0.0/8 [::1]/12
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
message_size_limit = 20480000
recipient_delimiter = +
inet_interfaces = all
virtual_mailbox_domains = mysql:/etc/postfix/mysql-virtual-mailbox-domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql-virtual-mailbox-maps.cf
#virtual_mailbox_base = /var/spool/vmail
virtual_alias_maps = mysql:/etc/postfix/mysql-virtual-alias-maps.cf,mysql:/etc/postfix/mysql-email2email.cf
virtual_transport = dovecot
dovecot_destination_recipient_limit = 1
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
smtpd_sasl_auth_enable = yes
smtpd_recipient_restrictions = permit_mynetworks,permit_sasl_authenticated,reject_unauth_destination, check_policy_service inet:127.0.0.1:2501 permit
#smtpd_client_restrictions = reject_rbl_client dnsbl.sorbs.net
#smtpd_helo_restrictions = reject_invalid_helo_hostname, reject_non_fqdn_helo_hostname, reject_unknown_helo_hostname
smtpd_tls_auth_only = no
content_filter = amavis:127.0.0.1:10024
receive_override_options = no_header_body_checks
soft_bounce = no
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = $myhostname
broken_sasl_auth_clients = yes

```

[/etc/postfix/master.cf]
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
        -o content_filter=spamassassin
submission inet n       -       -       -       -       smtpd
  -o smtpd_tls_security_level=encrypt
  -o smtpd_sasl_auth_enable=yes
  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
  -o milter_macro_daemon_name=ORIGINATING
smtps     inet  n       -       -       -       -       smtpd
  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#628       inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       -       60      1       pickup
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
# ====================================================================
#
# Recent Cyrus versions can use the existing "lmtp" master.cf entry.
#
# Specify in cyrus.conf:
#   lmtp    cmd="lmtpd -a" listen="localhost:lmtp" proto=tcp4
#
# Specify in main.cf one or more of the following:
#  mailbox_transport = lmtp:inet:localhost
#  virtual_transport = lmtp:inet:localhost
#
# ====================================================================
#
# Cyrus 2.1.5 (Amos Gouaux)
# Also specify in main.cf: cyrus_destination_recipient_limit=1
#
#cyrus     unix  -       n       n       -       -       pipe
#  user=cyrus argv=/cyrus/bin/deliver -e -r ${sender} -m ${extension} ${user}
#
# ====================================================================
# Old example of delivery via Cyrus.
#
#old-cyrus unix  -       n       n       -       -       pipe
#  flags=R user=cyrus argv=/cyrus/bin/deliver -e -m ${extension} ${user}
#
# ====================================================================
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
dovecot   unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/lib/dovecot/deliver -d ${recipient}
smtp-amavis unix -      -       y       -       2       smtp
    -o smtp_data_done_timeout=1200
#    -o smtp_send_xforward_command=yes
    -o disable_dns_lookups=yes
#    -o max_use=20

127.0.0.1:10025 inet n -       -       -        2       smtpd
   -o content_filter=
#   -o local_recipient_maps=
#   -o relay_recipient_maps=
#   -o smtpd_restriction_classes=
#   -o smtpd_delay_reject=no
   -o smtpd_client_restrictions=permit_mynetworks,reject
   -o smtpd_helo_restrictions=
   -o smtpd_sender_restrictions=
   -o smtpd_recipient_restrictions=permit_mynetworks,reject
#   -o smtpd_data_restrictions=reject_unauth_pipelining
#   -o smptd_end_of_data_restrictions=
   -o mynetworks=127.0.0.0/8
#   -o smtpd_error_sleep_time=0
#   -o smtpd_soft_error_limit=1001
#   -o smtpd_hard_error_limit=1000
#   -o smtpd_client_connection_count_limit=0
#   -o smtpd_client_connection_rate_limit=0
#   -o recieve_override_options=no_header_body_checks,no_unknown_recipients_checks
#   -o local_header_rewrite_clients=

spamassassin unix -     n       n       -       -       pipe
        user=spamd argv=/usr/bin/spamc -f -e
        /usr/sbin/sendmail -oi -f ${sender} ${recipient}

```

So. here we go.. as I said: I changed nothing regarding the configuration-files.. :/ ANY HELP APPRECIATED!

---

