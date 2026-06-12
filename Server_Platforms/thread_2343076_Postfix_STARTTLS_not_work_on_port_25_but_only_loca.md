---
title: "Postfix STARTTLS not work on port 25 but only localhost"
date: 2016-11-12
forum: Server Platforms
---

### Post by falco88 on 2016-11-12
Hi all!!

I have a VPS that i'm using as a email server with Postfix, Dovecot, Clamav and Spamassassins. I'm trying to enable TLS using Let's encrypt, and it works, but i have an issue becouse STARTTLS won't start on port 25, but works on localhost.

If i try to connect with telnet from my laptop, i receive this:

```
telnet smtp.mydomain.com 25
Trying XXX.XXX.XXX.XXX...
Connected to smtp.mydomain.com.
Escape character is '^]'.
220 smtp.mydomain.com ESMTP Postfix
ehlo x
250-smtp.mydomain.com
250-VRFY
250-ETRN
250-AUTH PLAIN LOGIN CRAM-MD5 DIGEST-MD5
250-AUTH=PLAIN LOGIN CRAM-MD5 DIGEST-MD5
250-ENHANCEDSTATUSCODES
250 8BITMIME

```

So anonymus user can send email on the my local domain:

```

telnet smtp.mydomain.com 25
Trying XXX.XXX.XXX.XXX...
Connected to smtp.mydomain.com.
Escape character is '^]'.
220 smtp.mydomain.com ESMTP Postfix
ehlo x
250-smtp.mydomain.com
250-VRFY
250-ETRN
250-AUTH PLAIN LOGIN CRAM-MD5 DIGEST-MD5
250-AUTH=PLAIN LOGIN CRAM-MD5 DIGEST-MD5
250-ENHANCEDSTATUSCODES
250 8BITMIME
mail from:<myemail@gmail.com>
250 2.1.0 Ok
rcpt to:<address@mydomain.com>
250 2.1.5 Ok
data
354 End data with <CR><LF>.<CR><LF>
subject: test
Hello


.
250 2.0.0 Ok: queued as 09F91150BDF

```

This issue don't happen on port 587 because STARTTLS is enabled :

```
telnet smtp.mydomain.com 587
Trying XXX.XXX.XXX.XXX...
Connected to smtp.mydomain.com.
Escape character is '^]'.
220 smtp.mydomain.com ESMTP Postfix
ehlo x
250-smtp.mydomain.com

250-PIPELINING
250-SIZE 52428800
250-VRFY
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
STARTTLS
220 2.0.0 Ready to start TLS
mail from:<myemail@gmail.com>
Connection closed by foreign host.

```

but if i try to connect from the VPS to telnet, magically STARTTLS is enabled:


```
telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 smtp.mydomain.com ESMTP Postfix
ehlo x
250-smtp.mydomain.com
250-PIPELINING
250-SIZE 52428800
250-VRFY
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
STARTTLS
220 2.0.0 Ready to start TLS
mail from:<myemail@gmail.com>
Connection closed by foreign host.

```


This is my postfix conf main.cf file:

```
~$ postconf -n
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/postfix/virtual
broken_sasl_auth_clients = yes
command_directory = /usr/sbin
config_directory = /etc/postfix
content_filter = smtp-amavis:[127.0.0.1]:10024
daemon_directory = /usr/lib/postfix
debug_peer_level = 2
debugger_command = PATH=/bin:/usr/bin:/usr/local/bin:/usr/X11R6/bin xxgdb $daemon_directory/$process_name $process_id & sleep 5
delay_warning_time = 4
disable_vrfy_command = no
dovecot_destination_recipient_limit = 1
html_directory = no
inet_interfaces = all
inet_protocols = all
mail_owner = postfix
mailbox_command = /usr/lib/dovecot/deliver
mailbox_size_limit = 0
mailbox_transport = dovecot
mailq_path = /usr/bin/mailq.postfix
manpage_directory = /usr/share/man
message_size_limit = 52428800
milter_default_action = accept
milter_protocol = 2
mydomain = mydomain.com
myhostname = smtp.mydomain.com
mynetworks = 127.0.0.0/8
myorigin = /etc/mailname
newaliases_path = /usr/bin/newaliases.postfix
queue_directory = /var/spool/postfix
readme_directory = /usr/share/doc/postfix-2.2.2/README_FILES
recipient_delimiter = +
relay_domains = proxy:mysql:/etc/zpanel/configs/postfix/mysql-relay_domains_maps.cf
relayhost =
sample_directory = /usr/share/doc/postfix-2.2.2/samples
sendmail_path = /usr/sbin/sendmail.postfix
setgid_group = postdrop
smtp_tls_note_starttls_offer = yes
smtp_use_tls = yes
smtpd_client_restrictions = permit_mynetworks, permit
smtpd_data_restrictions = reject_unauth_pipelining
smtpd_helo_required = yes
smtpd_helo_restrictions =
smtpd_recipient_restrictions = reject_sender_login_mismatch,permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination,reject_unknown_sender_domain
smtpd_relay_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = #$myhostname
smtpd_sasl_path = private/auth
smtpd_sasl_security_options = noanonymous
smtpd_sasl_type = dovecot
smtpd_sender_login_maps = proxy:mysql:/etc/zpanel/configs/postfix/mysql-virtual_sender_login_maps
smtpd_sender_restrictions = reject_sender_login_mismatch, reject_unknown_sender_domain, reject_unlisted_sender, reject_unauthenticated_sender_login_mismatch, permit_sasl_authenticated, permit_mynetworks, reject_unverified_sender
smtpd_tls_CAfile = /etc/letsencrypt/live/mydomain.com/fullchain.pem
smtpd_tls_auth_only = yes
smtpd_tls_cert_file = /etc/letsencrypt/live/mydomain.com/cert.pem
smtpd_tls_key_file = /etc/letsencrypt/live/mydomain.com/privkey.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
soft_bounce = yes
tls_random_source = dev:/dev/urandom
unknown_local_recipient_reject_code = 550
virtual_alias_maps = proxy:mysql:/etc/zpanel/configs/postfix/mysql-virtual_alias_maps.cf, regexp:/etc/zpanel/configs/postfix/virtual_regexp, hash:/etc/postfix/virtual
virtual_gid_maps = static:5000
virtual_mailbox_base = /var/zpanel/vmail
virtual_mailbox_domains = proxy:mysql:/etc/zpanel/configs/postfix/mysql-virtual_domains_maps.cf
virtual_mailbox_maps = proxy:mysql:/etc/zpanel/configs/postfix/mysql-virtual_mailbox_maps.cf
virtual_minimum_uid = 150
virtual_transport = dovecot
virtual_uid_maps = static:5000

```
and this is master.cf

```
#
# Postfix master process configuration file.  For details on the format
# of the file, see the Postfix master(5) manual page.
#
# ***** Unused items removed *****
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       n       -       -       smtpd -v
  -o smtpd_enforce_tls=yes
  -o content_filter=smtp-amavis:127.0.0.1:10024
#  -o content_filter=smtp-amavis:127.0.0.1:10024
  -o smtpd_proxy_filter=127.0.0.1:10025
  -o content_filter=spamassassin
  -o smtpd_tls_auth_only=yes
  -o smtpd_tls_security_level=encrypt
  -o smtpd_sasl_auth_enable=yes
  -o smtpd_sasl_type=dovecot
  -o smtpd_sasl_path=private/auth
  -o smtpd_sasl_security_options=noanonymous
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o smtpd_sender_restrictions=reject_unknown_sender_domain,reject_unlisted_sender,reject_unauthenticated_sender_login_mismatch,permit_sasl_authenticated,reject_unverified_sender,reject_known_sender_login_mism$
#   -o smtpd_sender_restrictions=reject_unauthenticated_sender_login_mismatch
#  -o smtpd_recipient_restrictions=reject_non_fqdn_recipient,reject_unknown_recipient_domain,permit_sasl_authenticated,reject


submission      inet  n     -     n     -     -     smtpd -v
  -o content_filter=smtp-amavis:127.0.0.1:10024
  -o receive_override_options=no_address_mappings
  -o content_filter=spamassassin
  -o smtpd_tls_security_level=encrypt
  -o smtpd_sasl_auth_enable=yes
  -o smtpd_sasl_type=dovecot
  -o smtpd_sasl_path=private/auth
  -o smtpd_sasl_security_options=noanonymous
  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
  -o smtpd_sender_restrictions=reject_sender_login_mismatch
  -o smtpd_recipient_restrictions=reject_non_fqdn_recipient,reject_unknown_recipient_domain,permit_sasl_authenticated,reject


#  -o smtpd_sasl_local_domain=$myhostname
pickup    fifo  n       -       n       60      1       pickup
  -o content_filter=
  -o receive_override_options=no_header_body_checks
cleanup   unix  n       -       n       -       0       cleanup
qmgr      fifo  n       -       n       300     1       qmgr
#qmgr     fifo  n       -       n       300     1       oqmgr
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
        -o fallback_relay=
#       -o smtp_helo_timeout=5 -o smtp_connect_timeout=5
showq     unix  n       -       n       -       -       showq
error     unix  -       -       n       -       -       error
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
# ====================================================================
maildrop  unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail argv=/usr/local/bin/maildrop -d ${recipient}
uucp      unix  -       n       n       -       -       pipe
  flags=Fqhu user=uucp argv=uux -r -n -z -a$sender - $nexthop!rmail ($recipient)
ifmail    unix  -       n       n       -       -       pipe
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=foo argv=/usr/local/sbin/bsmtp -f $sender $nexthop $recipient
#
# spam/virus section
#






smtp-amavis  unix  -    -       y       -       2       smtp -v
  -o smtpd_tls_security_level=none
  -o smtp_data_done_timeout=1200
  -o disable_dns_lookups=yes
  -o smtp_send_xforward_command=yes
  -o max_use=20


127.0.0.1:10026 inet n  -       y       -       -       smtpd -v
  -o content_filter=
  -o smtpd_helo_restrictions=
  -o smtpd_sender_restrictions=
  -o smtpd_recipient_restrictions=permit_mynetworks,reject
  -o mynetworks=127.0.0.0/8
  -o smtpd_error_sleep_time=0
  -o smtpd_soft_error_limit=1001
  -o smtpd_hard_error_limit=1000
  -o receive_override_options=no_header_body_checks
#  -o smtpd_bind_address=127.0.0.1
  -o smtpd_helo_required=no
  -o smtpd_client_restrictions=
  -o smtpd_restriction_classes=
  -o disable_vrfy_command=no
  -o strict_rfc821_envelopes=yes
#
# Dovecot LDA
dovecot   unix  -       n       n       -       -       pipe
  flags=DRhu user=vmail:mail argv=/usr/lib/dovecot/deliver -d ${recipient}
#
# Vacation mail
vacation    unix  -       n       n       -       -       pipe
  flags=Rq user=vacation argv=/var/spool/vacation/vacation.pl -f ${sender} -- ${recipient}
retry     unix  -       -       -       -       -       error
proxywrite unix -       -       n       -       1       proxymap




smtps     inet  n       -       -       -       -       smtpd -v
      -o smtpd_tls_wrappermode=yes
      -o smtpd_sasl_auth_enable=yes
      -o smtpd_reject_unlisted_sender=yes
      -o smtpd_recipient_restrictions=permit_sasl_authenticated,reject
      -o broken_sasl_auth_clients=yes
      -o milter_macro_daemon_name=ORIGINATING
# Dovecot LDA
dovecot unix - n n - - pipe
 flags=DRhu user=vmail:mail argv=/usr/lib/dovecot/deliver -d ${recipient}
#
# Vacation mail
vacation    unix  -       n       n       -       -       pipe
  flags=Rq user=vacation argv=/var/spool/vacation/vacation.pl -f ${sender} -- ${recipient}
retry     unix  -       -       -       -       -       error
proxywrite unix -       -       n       -       1       proxymap




smtps     inet  n       -       -       -       -       smtpd -v
      -o smtpd_tls_wrappermode=yes
      -o smtpd_sasl_auth_enable=yes
      -o smtpd_reject_unlisted_sender=yes
      -o smtpd_recipient_restrictions=permit_sasl_authenticated,reject
      -o broken_sasl_auth_clients=yes
      -o milter_macro_daemon_name=ORIGINATING
# Dovecot LDA
dovecot unix - n n - - pipe
 flags=DRhu user=vmail:mail argv=/usr/lib/dovecot/deliver -d ${recipient}
spamassassin unix -     n       n       -       -       pipe
        user=spamd argv=/usr/bin/spamc -f -e
        /usr/sbin/sendmail -oi -f ${sender} ${recipient}

```

From mail log, i don't receive any error, only this message seems strange:

```
Anonymous TLS connection established from unknown[151.26.151.156]: TLSv1.2 with cipher ECDHE-RSA-AES256-GCM-SHA384 (256/256 bits)

```

Where am I going wrong? This issue has become really frustrating lately.


Any help is really appreciated

---

