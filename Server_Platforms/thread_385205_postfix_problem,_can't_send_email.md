---
title: "postfix problem, can't send email"
date: 2007-03-15
forum: Server Platforms
---

### Post by blueblue on 2007-03-15
Hi!
I have installed a server mail with postfix on Ubuntu 6.06. I can send email to local email adress, but I can't send email to external email.

This is the message in /var/log/mail.log
postfix/qmgr[8024]: warning: connect to transport smtp: Connection refused

This is the querys that postfix does, from /var/log/mysql.log

mail@localhost on maildb
SELECT destination FROM aliases WHERE mail='domainofemail' and enabled = 1
mail@localhost on maildb
SELECT domain FROM domains WHERE domain='domainofemail' and enabled = 1

I use mysql to store users, aliases and domains.

This is my configuration files:

FILE: /etc/postfix/main.cf

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no
append_dot_mydomain	= no
delay_warning_time = 4h

smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

maximal_queue_lifetime = 1d
unknown_local_recipient_reject_code = 450

minimal_backoff_time = 1000s
maximal_backoff_time = 8000s
smtp_helo_timeout = 60s

smtpd_soft_error_limit = 3
smtpd_hard_error_limit = 12

smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname,reject_invalid_hostname,permit

smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, eject_unauth_pipelining, permit

smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_non_fqdn_recipient, reject_unauth_destination, check_policy_service inet:127.0.0.1:60000, permit

smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit

smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain =

myhostname = mydomain.xx
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = $myhostname
mydestination =
relayhost =
mynetworks = 127.0.0.0/8
mynetworks_style = host
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
proxy_interfaces = my_router_external_ip

#alias_maps = hash:/etc/postfix/aliases
#alias_database = hash:/etc/postfix/aliases
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf
virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf
virtual_minimum_uid = 104
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf

FILE: /etc/postfix/master.cf

# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
smtp   inet  n         -          n          -           -       smtpd
virtual unix  -          n         n          -           -       virtual

Thanks a lot!

---

### Post by Mr. C. on 2007-03-15
Please show "postconf -n output", and your entire master.cf.

MrC

---

### Post by ckennow on 2008-02-16
well i'm not the original poster but i have the same problem.


```
root@miller:/etc/postfix# postconf -n
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
home_mailbox = Maildir/
inet_interfaces = all
inet_protocols = all
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
mydestination = /etc/postfix/local-host-names
myhostname = mail.stephenmillers.net
mynetworks = 127.0.0.0/8
myorigin = /etc/mailname
recipient_delimiter = +
relayhost = smtp-server.new.rr.com
smtp_tls_note_starttls_offer = yes
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain =
smtpd_sasl_security_options = noanonymous
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_auth_only = no
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtpd_tls_session_cache_timeout = 3600s
smtpd_use_tls = yes
tls_random_source = dev:/dev/urandom
```

```
#
# Postfix master process configuration file.  For details on the format
# of the file, see the master(5) manual page (command: "man 5 master").
#
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       -       -       -       smtpd
#submission inet n       -       -       -       -       smtpd
#  -o smtpd_enforce_tls=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#smtps     inet  n       -       -       -       -       smtpd
#  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
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
  flags=F user=ftn argv=/usr/lib/ifmail/ifmail -r $nexthop ($recipient)
bsmtp     unix  -       n       n       -       -       pipe
  flags=Fq. user=bsmtp argv=/usr/lib/bsmtp/bsmtp -t$nexthop -f$sender $recipient
scalemail-backend unix  -       n       n       -       2       pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}
```

---

### Post by Mr. C. on 2008-02-16
Assuming your log entry was the same as the OP's:

```
postfix/qmgr[8024]: warning: connect to transport smtp: Connection refused
```

Had you recently changed this line in master.cf?  

```
smtp      unix  -       -       -       -       -       smtp
```

What is shown here is correct, but the symptoms indicate it was different than this previously (the private entry would have been an 'n').

If so, restart postfix.

MrC

---

### Post by DDuong on 2008-02-17
There is one entry that "might" need to be changed to test things out.

In my main.cf file, I have this for the follow field:

> mydestination = localhost.$mydomain, localhost

After trying this, please restart postfix and try again.

---

