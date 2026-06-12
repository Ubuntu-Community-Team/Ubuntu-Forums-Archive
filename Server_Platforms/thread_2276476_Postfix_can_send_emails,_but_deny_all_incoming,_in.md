---
title: "Postfix can send emails, but deny all incoming, include local"
date: 2015-05-02
forum: Server Platforms
---

### Post by rhandy2 on 2015-05-02
Hello

I start this new thread, because I have postfix running good, but since yestarday, stop to receive emails.
I try many things, I remove postfix, Install again with minimal options, but I still have always the same error.

master.cf

> #
# Postfix master process configuration file.  For details on the format
# of the file, see the master(5) manual page (command: "man 5 master" or
# on-line: [http://www.postfix.org/master.5.html](http://www.postfix.org/master.5.html)).
#
# Do not forget to execute "postfix reload" after editing this file.
#
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       -       -       -       smtpd
#smtp      inet  n       -       -       -       1       postscreen
#smtpd     pass  -       -       -       -       -       smtpd
#dnsblog   unix  -       -       -       -       0       dnsblog
#tlsproxy  unix  -       -       -       -       0       tlsproxy
#submission inet n       -       -       -       -       smtpd
#  -o syslog_name=postfix/submission
#  -o smtpd_tls_security_level=encrypt
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_reject_unlisted_recipient=no
#  -o smtpd_client_restrictions=$mua_client_restrictions
#  -o smtpd_helo_restrictions=$mua_helo_restrictions
#  -o smtpd_sender_restrictions=$mua_sender_restrictions
#  -o smtpd_recipient_restrictions=
#  -o smtpd_relay_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#smtps     inet  n       -       -       -       -       smtpd
#  -o syslog_name=postfix/smtps
#  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_reject_unlisted_recipient=no
#  -o smtpd_client_restrictions=$mua_client_restrictions
#  -o smtpd_helo_restrictions=$mua_helo_restrictions
#  -o smtpd_sender_restrictions=$mua_sender_restrictions
#  -o smtpd_recipient_restrictions=
#  -o smtpd_relay_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#628       inet  n       -       -       -       -       qmqpd
pickup    unix  n       -       -       60      1       pickup
cleanup   unix  n       -       -       -       0       cleanup
qmgr      unix  n       -       n       300     1       qmgr
#qmgr     unix  n       -       n       300     1       oqmgr
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
relay     unix  -       -       -       -       -       smtp
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
scalemail-backend unix - n n - 2 pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}

main.cf

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
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.
smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = example.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
virtual_alias_maps = hash:/etc/postfix/virtual
sender_dependent_default_transport_maps = hash:/etc/postfix/dependent
myorigin = /etc/mailname
mydestination = example.com, localhost.com localhost
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all




/etc/log/mail.log

> May  2 22:33:04 example.com postfix/pickup[6521]: 9408420024A: uid=0 from=<[EMAIL="example.com@example.com"]example.com@example.com[/EMAIL]>
May  2 22:33:04 example.com postfix/cleanup[8597]: 9408420024A: message-id=<[EMAIL="1430602384.8523@example.com"]1430602384.8523@example.com[/EMAIL]>
May  2 22:33:04 example.com postfix/qmgr[6522]: 9408420024A: from=<[EMAIL="example.com@example.com"]example.com@example.com[/EMAIL]>, size=589, nrcpt=1 (queue active)
May  2 22:33:04 example.com postfix/local[8599]: 9408420024A: to=<[EMAIL="example.com@example.com.tk"]example.com@example.com.tk[/EMAIL]>, relay=local, delay=0.12, delays=0.08/0/0/0.04, dsn=5.3.0, status=bounced (Command died with status 126: "procmail -a "$EXTENSION"". Command output: sh: 1: procmail: Permission denied )
May  2 22:33:04 example.com postfix/cleanup[8597]: A7DFA20024C: message-id=<[EMAIL="20150502213304.A7DFA20024C@example.com.tk"]20150502213304.A7DFA20024C@example.com.tk[/EMAIL]>
May  2 22:33:04 example.com postfix/bounce[8602]: 9408420024A: sender non-delivery notification: A7DFA20024C
May  2 22:33:04 example.com postfix/qmgr[6522]: A7DFA20024C: from=<>, size=2410, nrcpt=1 (queue active)
May  2 22:33:04 example.com postfix/qmgr[6522]: 9408420024A: removed
May  2 22:33:04 example.com postfix/local[8599]: A7DFA20024C: to=<[EMAIL="example.com@example.com.tk"]example.com@example.com.tk[/EMAIL]>, orig_to=<[EMAIL="example.com@example.com"]example.com@example.com[/EMAIL]>, relay=local, delay=0.08, delays=0.04/0/0/0.04, dsn=5.3.0, status=bounced (Command died with status 126: "procmail -a "$EXTENSION"". Command output: sh: 1: procmail: Permission denied )
May  2 22:33:04 example.com postfix/qmgr[6522]: A7DFA20024C: removed

Its driven me crazy!!!!

---

### Post by rhandy2 on 2015-05-04
I have to reinstall Dovecot and Postfix, create conf files again, and is working, But I really don´t know what causes  that error.

---

### Post by SeijiSensei on 2015-05-04
```
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
```
That limits inbound messages to ones being sent by the machine itself via the localhost interface.  To accept mail from other locations, you need a different entry.

You should read [http://www.postfix.org/BASIC_CONFIGURATION_README.html#mydestination](http://www.postfix.org/BASIC_CONFIGURATION_README.html#mydestination) and [http://www.postfix.org/SMTPD_ACCESS_README.html](http://www.postfix.org/SMTPD_ACCESS_README.html).

---

### Post by rhandy2 on 2015-05-04
Thanks for your reply!

I read your recomended  links.

Before I reinstall postfix and dovecot

I have

> mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = /usr/bin/procmail-wrapper -o -a $DOMAIN -d $LOGNAME
smtpd_recipient_restrictions = permit_sasl_authenticated reject_unauth_destination


mailbox_command command is diferrent, and it works Now!




[COLOR=#000000]

[/COLOR]

---

