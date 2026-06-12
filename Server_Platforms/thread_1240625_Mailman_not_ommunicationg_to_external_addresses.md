---
title: "Mailman not ommunicationg to external addresses"
date: 2009-08-14
forum: Server Platforms
---

### Post by Stuart1745 on 2009-08-14
Im trying to set up a mailman server on 9.04 I followd the ubuntu guide for setting it up ho ever when I try and invite external addresses( my gmail for example ) I get connection timed out errors, and when I try to send an email to the [email]subscibe@list.com[/email] address I get an undeliverable error.

/var/log/mail.log
```
Aug 14 21:13:24 Pearcerobotics postfix/smtp[23513]: connect to ig3net57.richardson.k12.tx.us[165.199.8.87]:25: Connection timed out
Aug 14 21:13:24 Pearcerobotics postfix/smtp[23515]: connect to sbcmx5.prodigy.net[207.115.21.24]:25: Connection timed out
Aug 14 21:13:29 Pearcerobotics postfix/smtp[23516]: connect to gmail-smtp-in.l.google.com[209.85.211.98]:25: Connection timed out
Aug 14 21:13:54 Pearcerobotics postfix/smtp[23513]: connect to inet57.richardson.k12.tx.us[165.199.8.57]:25: Connection timed out
Aug 14 21:13:54 Pearcerobotics postfix/smtp[23515]: connect to sbcmx8.prodigy.net[207.115.36.22]:25: Connection timed out

``` 

here is the postfix config
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
#submission inet n       -       -       -       -       smtpd
#  -o smtpd_tls_security_level=encrypt
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#smtps     inet  n       -       -       -       -       smtpd
#  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#628      inet  n       -       -       -       -       qmqpd
pickup    fifo  n       -       -       60      1       pickup
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
scalemail-backend unix	-	n	n	-	2	pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
#mailman
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}
#spamassassin
spamassassin unix -     n       n       -       -       pipe
        user=spamd argv=/usr/bin/spamc -f -e    
        /usr/sbin/sendmail -oi -f ${sender} ${recipient}

# make sure it's all on one line or
# start the consecutive lines with a whitespace
# like I did here
smtp-amavis     unix    -       -       -       -       2       smtp
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

postfix main.cf
```
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
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.pearcerobotics.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = pearcerobotics.com, pearcerobotics.com, robertrampy.com, officeretreat.com, aliensrus.com
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_protocols = all
smtpd_sasl_local_domain = 
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated permit_mynetworks reject_unauth_destination
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
smtp_use_tls = yes
virtual_maps = hash:/etc/postfix/virtusertable
home_mailbox = Maildir/
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/dovecot-auth
smtpd_sasl_authenticated_header = yes
smtpd_sender_restrictions = reject_unknown_sender_domain
smtpd_tls_mandatory_protocols = SSLv3, TLSv1
smtpd_tls_mandatory_ciphers = medium, high
mailbox_command = 
relayhost = 
inet_interfaces = all
relay_domains = lists.pearcerobotics.com
transport_maps = hash:/etc/postfix/transport
mailman_destination_recipient_limit = 1

content_filter=smtp-amavis:[127.0.0.1]:10024
```

/etc/postfix/transport
```
lists.pearcerobotics.com	mailman
```



again thanks for all the help ( and thank you to every one who has helped me up to this point)

---

### Post by Stuart1745 on 2009-08-14
/etc/aliases
```
# See man 5 aliases for format
postmaster:    root
# Added by installer for initial user
root:	stuart
clamav: root
mentors:              "|/var/lib/mailman/mail/mailman post mentors"
mentors-admin:        "|/var/lib/mailman/mail/mailman admin mentors"
mentors-bounces:      "|/var/lib/mailman/mail/mailman bounces mentors"
mentors-confirm:      "|/var/lib/mailman/mail/mailman confirm mentors"
mentors-join:         "|/var/lib/mailman/mail/mailman join mentors"
mentors-leave:        "|/var/lib/mailman/mail/mailman leave mentors"
mentors-owner:        "|/var/lib/mailman/mail/mailman owner mentors"
mentors-request:      "|/var/lib/mailman/mail/mailman request mentors"
mentors-subscribe:    "|/var/lib/mailman/mail/mailman subscribe mentors"
mentors-unsubscribe:  "|/var/lib/mailman/mail/mailman unsubscribe mentors"

#test list
test:              "|/var/lib/mailman/mail/mailman post test"
test-admin:        "|/var/lib/mailman/mail/mailman admin test"
test-bounces:      "|/var/lib/mailman/mail/mailman bounces test"
test-confirm:      "|/var/lib/mailman/mail/mailman confirm test"
test-join:         "|/var/lib/mailman/mail/mailman join test"
test-leave:        "|/var/lib/mailman/mail/mailman leave test"
test-owner:        "|/var/lib/mailman/mail/mailman owner test"
test-request:      "|/var/lib/mailman/mail/mailman request test"
test-subscribe:    "|/var/lib/mailman/mail/mailman subscribe test"
test-unsubscribe:  "|/var/lib/mailman/mail/mailman unsubscribe test"



```

---

### Post by Stuart1745 on 2009-08-15
Well I was looking more in to the problem today and it looks like any email coming from a NON user on the system( ie any vitual user) is getting rejected.

---

### Post by Stuart1745 on 2009-08-18
Still having problems with any non User accoutn sending email ( joomal word press and mailman). I double checked that port 25 is not being blocked and it is not, still cannot figure out what is going on here.

---

