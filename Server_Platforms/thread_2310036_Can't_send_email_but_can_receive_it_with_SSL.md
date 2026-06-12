---
title: "Can't send email but can receive it with SSL"
date: 2016-01-15
forum: Server Platforms
---

### Post by jonah1980 on 2016-01-15
Hi I hope someone can please help. I've set up an Ubuntu Server which is working via the Thunderbird email client to receive emails over port 993 with SSL but I can't send emails.

I want to send via port 465 with SSL and normal password.

Currently I also get this error when I restart postfix:

> postconf: warning: /etc/postfix/master.cf: undefined parameter: permit_sasl_authenticated

Could anybody please help me to get it working?

Thanks very much indeed.

---

### Post by Seb_Boffen on 2016-01-17
My settings in master.cf do not use permit_sasl_authenticated, and I use port 587 for SMTP using TLS
main.cf has permit_sasl_authenticated:
smtpd_recipient_restrictions = reject_unknown_sender_domain reject_unknown_recipient_domain reject_unauth_pipelining permit_mynetworks permit_sasl_authenticated reject_unauth_destination
smtpd_relay_restrictions = reject_unknown_sender_domain reject_unknown_recipient_domain reject_unauth_pipelining permit_mynetworks permit_sasl_authenticated reject_unauth_destination


I followed this guide to setup the email server: [https://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu9.04](https://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu9.04) 

Details of my master.cf file:

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
amavis unix - - - - 2 smtp
        -o smtp_data_done_timeout=1200
        -o smtp_send_xforward_command=yes
        -o disable_dns_lookups=yes
        -o max_use=20
        -o smtpd_tls_security_level=none
127.0.0.1:10025 inet n - - - - smtpd
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
        -o smtpd_tls_security_level=none
submission inet n       -       n       -       -       smtpd
#  -o smtpd_tls_security_level=encrypt
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
smtp inet n - n - - smtpd 
#  -o smtpd_tls_wrappermode=yes
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#628       inet  n       -       -       -       -       qmqpd
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
```

---

### Post by jonah1980 on 2016-01-18
Hi thanks here is my main.cf:

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
smtpd_tls_cert_file = /etc/postfix/postfix.cert.pem
smtpd_tls_key_file = /etc/postfix/postfix.key.pem
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

smtpd_recipient_restrictions = permit_mynetworks permit_sasl_authenticated reject_unauth_destination
myhostname = svr.ubuntu.server
alias_maps = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = svr.ubuntu.server, localhost.ubuntu.server, , localhost
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
smtpd_sasl_auth_enable = yes
smtpd_recipient_restrictions = permit_mynetworks permit_sasl_authenticated reject_unauth_destination
virtual_alias_maps = hash:/etc/postfix/virtual
smtpd_tls_mandatory_protocols = SSLv3, TLSv1
smtpd_tls_mandatory_ciphers = high
smtp_sasl_auth_enable = yes

```

and my postfix master.cj:

```
#
# Postfix master process configuration file.  For details on the format
# of the file, see the master(5) manual page (command: "man 5 master" or
# on-line: http://www.postfix.org/master.5.html).
#
# Do not forget to execute "postfix reload" after editing this file.
#
# ==========================================================================
# service type  private unpriv  chroot  wakeup  maxproc command + args
#               (yes)   (yes)   (yes)   (never) (100)
# ==========================================================================
smtp      inet  n       -       -       -       -       smtpd
#smtp      inet  n       -       -       -       1       postscreen
smtpd     pass  -       -       -       -       -       smtpd
#dnsblog   unix  -       -       -       -       0       dnsblog
#tlsproxy  unix  -       -       -       -       0       tlsproxy
submission inet n       -       -       -       -       smtpd
  -o syslog_name=postfix/submission
  -o smtpd_tls_security_level=encrypt
  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_reject_unlisted_recipient=no
  -o smtpd_client_restrictions=$permit_sasl_authenticated,reject
#  -o smtpd_helo_restrictions=$mua_helo_restrictions
#  -o smtpd_sender_restrictions=$mua_sender_restrictions
#  -o smtpd_recipient_restrictions=
  -o smtpd_relay_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
smtps     inet  n       -       -       -       -       smtpd
  -o syslog_name=postfix/smtps
  -o smtpd_tls_wrappermode=yes
  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_reject_unlisted_recipient=no
  -o smtpd_client_restrictions=$permit_sasl_authenticated,reject
#  -o smtpd_helo_restrictions=$mua_helo_restrictions
#  -o smtpd_sender_restrictions=$mua_sender_restrictions
#  -o smtpd_recipient_restrictions=
#  -o smtpd_relay_restrictions=permit_sasl_authenticated,reject
  -o milter_macro_daemon_name=ORIGINATING
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
scalemail-backend unix	-	n	n	-	2	pipe
  flags=R user=scalemail argv=/usr/lib/scalemail/bin/scalemail-store ${nexthop} ${user} ${extension}
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}


```


I can't figure out what is wrong but hopefully someone may be able to spot something? Thanks again for any help.

---

### Post by Seb_Boffen on 2016-01-19
In master.cf change:

#  -o smtpd_tls_security_level=encrypt
     -o smtpd_tls_security_level=none

#  -o smtpd_sasl_auth_enable=yes

     -o smtpd_client_restrictions=permit_mynetworks,reject
#  -o smtpd_client_restrictions=$permit_sasl_authenticated,reject

#  -o smtpd_relay_restrictions=permit_sasl_authenticated,reject
     -o smtpd_relay_restrictions=permit_mynetworks,reject

     -o smtpd_recipient_restrictions=permit_mynetworks,reject

stop start postfix and try to sent email.

---

### Post by jonah1980 on 2016-01-20
Hi thanks Seb_Boffen,

After restarting the service I still can't send mail and Thunderbird just keeps asking me for a password. My var/log/mail.err log shows this:

> Jan 20 15:04:15 svr postfix/smtp[16965]: fatal: specify a password table via the `smtp_sasl_password_maps' configuration parameter

Thanks again for any help.

---

### Post by Seb_Boffen on 2016-01-20
Please compair your installation with the installation in the guide: [[COLOR=#dd4814]https://www.howtoforge.com/virtual-u...ail-ubuntu9.04[/COLOR]]("https://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu9.04") especially the sasl part.

---

### Post by jonah1980 on 2016-01-21
> **Seb_Boffen said:**
> Please compair your installation with the installation in the guide: [[COLOR=#dd4814]https://www.howtoforge.com/virtual-u...ail-ubuntu9.04[/COLOR]]("https://www.howtoforge.com/virtual-users-domains-postfix-courier-mysql-squirrelmail-ubuntu9.04") especially the sasl part.

Hi thanks, unfortunately out of desperation I tried following the guide through except the Squirrelmail part.

Now I can't receive email either. Not sure how to get things back on track if any body could help?

---

### Post by Seb_Boffen on 2016-01-21
ok then its best to start from scratch using this guide, my mail server is running with this guide on 10.04 then upgraded to 12.04 and now 14.04. Has been running with the configuration in the above mentioned guide for 5 years now. 
Its best to purge the apps you have installed so you can start with the configuration files comming with each package.

---

### Post by jonah1980 on 2016-01-21
Hi thanks but the problem is if I purge a load of stuff my server is in use and running CMS software and mysql databases and other things which work well. I don't want to start removing things and breaking them. Email did work before, I just couldn't use a mail client like Thunderbird or my phone app. All I really wanted to do was fix it so I could send mail on a phone or from a client but keep the rest working how it was.

I fear the changes the guide led me through have changed quite a lot of other things. I've now deleted the mysql user and database from the guide and the extra text files but I'm not sure how I can clean things up further...

---

### Post by Seb_Boffen on 2016-01-22
I was referring to the packages related to email, not your sql server or cms software. Also your mailserver needs open ports on your firewall and router before you can access mail via internet.

---

### Post by smtp on 2016-01-23
I think you can revert postfix configuration files main.cf and master.cf back using content you copied here earlier. 
You should first find winch SASL authentication you using.
Following could help for configuring postfix: [http://www.postfix.org/SASL_README.html](http://www.postfix.org/SASL_README.html)
Please be careful, configuring all SASL and Postfix elements in not trivial task.

---

