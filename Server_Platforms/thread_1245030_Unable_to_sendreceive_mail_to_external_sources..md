---
title: "Unable to send/receive mail to external sources."
date: 2009-08-20
forum: Server Platforms
---

### Post by Honortech on 2009-08-20
Ok let me start off by saying I have searched high and low and read countless posts while still unable to find a solution... Everything is working perfectly within a local means it's just external sources I cannot send or receive from. I'm using postfix-dovecot with MySQL/Virtual mailboxes and I have Comcast for the moment knowing they block port 25. As you can see I've tried both commenting in the submission protocol and adding port 2500 as a work around however it's still not working. I'm also using DynDNS at the moment since I have a dynamic IP. I have MX records setup and pointing to mailserver.honortech.net since I use mail.honortech.net as a redirect to my webmail. Hrmm I that's about all the useful information I can think if you need to know anything else please let me know. I've been working on this one issue about 3 days now and it's literally driving me nuts... Thanks in advance =)

This is my mail.log:
> Aug 20 03:38:51 honortech dovecot: IMAP(test@honortech.net): Disconnected: Logged out bytes=280/2036
Aug 20 03:42:15 honortech postfix/qmgr[9665]: 21A32284B3: from=<test@honortech.net>, size=540, nrcpt=1 (queue active)
Aug 20 03:42:56 honortech postfix/smtp[25343]: connect to mx3.hotmail.com[65.55.37.104]:25: Connection timed out
Aug 20 03:43:26 honortech postfix/smtp[25343]: connect to mx3.hotmail.com[65.55.37.88]:25: Connection timed out
Aug 20 03:43:56 honortech postfix/smtp[25343]: connect to mx2.hotmail.com[65.55.37.104]:25: Connection timed out
Aug 20 03:44:26 honortech postfix/smtp[25343]: connect to mx2.hotmail.com[65.55.92.136]:25: Connection timed out
Aug 20 03:44:56 honortech postfix/smtp[25343]: connect to mx1.hotmail.com[65.55.37.104]:25: Connection timed out
Aug 20 03:44:56 honortech postfix/smtp[25343]: 21A32284B3: to=<RRexA3@hotmail.com>, relay=none, delay=113792, delays=113632/0.02/160/0, dsn=4.4.1, status=deferred (connect to mx1.hotmail.com[65.55.37.104]:25: Connection timed out)
Aug 20 03:52:15 honortech postfix/qmgr[9665]: E11D9284CB: from=<test@honortech.net>, size=522, nrcpt=1 (queue active)
Aug 20 03:52:15 honortech postfix/qmgr[9665]: D345F28484: from=<admin@honortech.net>, size=476, nrcpt=1 (queue active)
Aug 20 03:52:55 honortech postfix/smtp[25562]: connect to mx2.hotmail.com[65.55.37.88]:25: Connection timed out
Aug 20 03:52:55 honortech postfix/smtp[25563]: connect to mx2.hotmail.com[65.55.92.136]:25: Connection timed out
Aug 20 03:53:25 honortech postfix/smtp[25562]: connect to mx4.hotmail.com[65.55.37.72]:25: Connection timed out
Aug 20 03:53:25 honortech postfix/smtp[25563]: connect to mx3.hotmail.com[65.55.92.168]:25: Connection timed out
Aug 20 03:53:55 honortech postfix/smtp[25563]: connect to mx4.hotmail.com[65.55.92.184]:25: Connection timed out
Aug 20 03:53:55 honortech postfix/smtp[25562]: connect to mx3.hotmail.com[65.55.37.88]:25: Connection timed out
Aug 20 03:54:25 honortech postfix/smtp[25563]: connect to mx3.hotmail.com[65.55.37.88]:25: Connection timed out
Aug 20 03:54:25 honortech postfix/smtp[25562]: connect to mx4.hotmail.com[65.55.92.168]:25: Connection timed out
Aug 20 03:54:55 honortech postfix/smtp[25563]: connect to mx3.hotmail.com[65.55.92.152]:25: Connection timed out
Aug 20 03:54:55 honortech postfix/smtp[25562]: connect to mx1.hotmail.com[65.55.37.104]:25: Connection timed out
Aug 20 03:54:55 honortech postfix/smtp[25563]: D345F28484: to=<RRexA3@hotmail.com>, relay=none, delay=117888, delays=117727/0.03/160/0, dsn=4.4.1, status=deferred (connect to mx3.hotmail.com[65.55.92.152]:25: Connection timed out)
Aug 20 03:54:55 honortech postfix/smtp[25562]: E11D9284CB: to=<RRexA3@hotmail.com>, relay=none, delay=36363, delays=36202/0.03/160/0, dsn=4.4.1, status=deferred (connect to mx1.hotmail.com[65.55.37.104]:25: Connection timed out)

This is my master.cf
> #
# Postfix master process configuration file.  For details on the format
# of the file, see the master(5) manual page (command: "man 5 master").
#
# Do not forget to execute "postfix reload" after editing this file.
#
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
2500      inet  n       -       n       -       -       smtpd
submission inet n       -       n       -       -       smtpd
dovecot unix - n n - - pipe flags=DRhu user=vmail:mail argv=/usr/lib/dovecot/deliver -c /etc/dovecot/dovecot-postfix.conf -f ${sender} -d $(recipient)
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
scalemail-backend unix    -    n    n    -    2    pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}


This is my main.cf
> # See /usr/share/postfix/main.cf.dist for a commented, more complete version


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
smtpd_tls_cert_file = /etc/ssl/certs/ssl-mail.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-mail.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mailserver.honortech.net
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
#myorigin = /etc/mailname
#mydestination = localhost
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
#home_mailbox = Maildir/
smtpd_sasl_auth_enable = yes
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/dovecot-auth
smtpd_sasl_authenticated_header = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain = $myhostname
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = reject_unknown_sender_domain, reject_unknown_recipient_domain, reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
smtpd_sender_restrictions = reject_unknown_sender_domain
#mailbox_command = /usr/lib/dovecot/deliver -c /etc/dovecot/dovecot-postfix.conf -n -m "${EXTENSION}"
smtp_use_tls = yes
smtpd_tls_received_header = yes
smtpd_tls_mandatory_protocols = SSLv3, TLSv1
smtpd_tls_mandatory_ciphers = medium, high
smtpd_tls_auth_only = yes
tls_random_source = dev:/dev/urandom
virtual_minimum_uid = 150
virtual_uid_maps = static:150
virtual_gid_maps = static:8
virtual_mailbox_base = /var/vmail
virtual_transport = dovecot
dovecot_destination_recipient_limit = 1

virtual_alias_maps = mysql:/etc/postfix/my_alias_maps.cf
virtual_mailbox_limit = mysql:/etc/postfix/my_mailbox_limits.cf
virtual_mailbox_domains = mysql:/etc/postfix/my_domains_maps.cf
virtual_mailbox_maps = mysql:/etc/postfix/my_mailbox_maps.cf

---

