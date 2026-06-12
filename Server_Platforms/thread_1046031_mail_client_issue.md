---
title: "mail client issue"
date: 2009-01-21
forum: Server Platforms
---

### Post by anwoke8204 on 2009-01-21
hi, when I or anyone else tries to connect to my mail server using outlook or any other mail client they get the following error when they try to send a message:

            554 5.7.1 <email address here>: Relay access denied
it is a valid email, I use it every day.  how do we resolve this?
TIA

---

### Post by hyper_ch on 2009-01-21
you're not authorized to use the mail server that you want to use. Very likely you'll need to authenticate yourself first with username/password.

Please post the config of the mailserver.

---

### Post by anwoke8204 on 2009-01-21
not sure why it would say I am not authorized as it is my mail server, lol
here is the main.cf config file:

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
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = srv1.rooksystems.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = srv1.rooksystems.com.rooksystems.com, localhost.rooksystems.com, localhost
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
virtual_alias_maps = hash:/etc/postfix/virtual
sender_bcc_maps = hash:/etc/postfix/bcc
mailbox_command = /usr/bin/procmail-wrapper -o -a $DOMAIN -d $LOGNAME
home_mailbox = Maildir/
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_mynetworks permit_sasl_authenticated reject_unauth_destination

```
here is the master.cf file

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
smtp	inet	n	-	-	-	-	smtpd -o smtpd_sasl_auth_enable=yes
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
mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py
  ${nexthop} ${user}

```

also I am using virtual hosts on the server as well through virtualmin/webmin/usermin to admin the virtual hosts.

TIA

---

### Post by hyper_ch on 2009-01-21
use [noparse]```

```[/noparse] tags to make it more easily readable.

---

### Post by anwoke8204 on 2009-01-21
I have edited my post using the code tags to make it easier to read, sorry

---

### Post by hyper_ch on 2009-01-21
one problem is this:

```

smtpd_recipient_restrictions = permit_mynetworks permit_sasl_authenticated reject_unauth_destination

```

Each one needs to be seperated with a comman... I even make line breaks:
```

smtpd_recipient_restrictions =
        reject_invalid_hostname,
        permit_sasl_authenticated,
        reject_non_fqdn_hostname,
        reject_non_fqdn_sender,
        reject_non_fqdn_recipient,
        reject_unknown_sender_domain,
        reject_unknown_recipient_domain,
        permit_mynetworks,
        reject_unauth_destination,
        check_recipient_access hash:/etc/postfix/recipient_checks,
        check_recipient_access pcre:/etc/postfix/recipient_checks.pcre,
        check_helo_access hash:/etc/postfix/helo_checks,
        check_sender_access hash:/etc/postfix/sender_checks,
        check_client_access hash:/etc/postfix/client_checks,
        check_client_access pcre:/etc/postfix/client_checks.pcre,
        reject_rbl_client zen.spamhaus.org,
        reject_rbl_client dnsbl.sorbs.net,
        reject_rbl_client list.dsbl.org,
        reject_rbl_client dul.dnsbl.sorbs.net,
        reject_rbl_client blackholes.easynet.nl,
        reject_rbl_client cbl.abuseat.org,
        reject_rbl_client proxies.blackholes.wirehub.net,
        reject_rbl_client bl.spamcop.net,
        reject_rbl_client dnsbl.njabl.org,
        check_policy_service inet:127.0.0.1:60000

```

In your case alter this line to this
```

smtpd_recipient_restrictions =
        permit_sasl_authenticated,
        permit_mynetworks,
        reject_unauth_destination,

```

Restart postfix then and try again.

---

### Post by anwoke8204 on 2009-01-21
I have made those changes and am still unable to connect
any other ideas?
TIA

---

### Post by hyper_ch on 2009-01-21
what does mail.log say?

---

### Post by anwoke8204 on 2009-01-21
here is the entries in my mail log for when I have been trying to do the test

```

Jan 21 04:58:38 srv1 postfix/smtpd[22706]: connect from 118-169-192-156.dynamic.hinet.net[118.169.192.156]
Jan 21 04:58:39 srv1 postfix/smtpd[22706]: NOQUEUE: reject: RCPT from 118-169-192-156.dynamic.hinet.net[118.169.192.156]: 554 5.7.1 <candy59839@yahoo.com.tw>: Relay access denied; from=<michael78694@MyMainServer.com> to=<candy59839@yahoo.com.tw> proto=SMTP helo=<www.MyMainServer.com>
Jan 21 04:58:39 srv1 postfix/smtpd[22706]: lost connection after RCPT from 118-169-192-156.dynamic.hinet.net[118.169.192.156]
Jan 21 04:58:39 srv1 postfix/smtpd[22706]: disconnect from 118-169-192-156.dynamic.hinet.net[118.169.192.156]
Jan 21 05:00:04 srv1 postfix/cleanup[22964]: 96B541F8158: message-id=<20090121120004.96B541F8158@srv1.rooksystems.com>
Jan 21 05:00:04 srv1 postfix/qmgr[13860]: 96B541F8158: from=<root@srv1.rooksystems.com.rooksystems.com>, size=611, nrcpt=1 (queue active)
Jan 21 05:00:04 srv1 postfix/local[22966]: 96B541F8158: to=<andrew@srv1.rooksystems.com.rooksystems.com>, orig_to=<root>, relay=local, delay=2.7, delays=2.6/0.01/0/0.13, dsn=2.0.0, status=sent (delivered to command: /usr/bin/procmail-wrapper -o -a $DOMAIN -d $LOGNAME)
Jan 21 05:00:04 srv1 postfix/qmgr[13860]: 96B541F8158: removed
Jan 21 05:01:02 srv1 postfix/master[5268]: terminating on signal 15
Jan 21 05:01:03 srv1 postfix/master[23178]: daemon started -- version 2.5.1, configuration /etc/postfix
Jan 21 05:02:43 srv1 dovecot: pop3-login: Disconnected: rip=216.152.208.1, lip=192.168.1.13
Jan 21 05:03:23 srv1 last message repeated 8 times
Jan 21 05:04:25 srv1 last message repeated 2 times
Jan 21 05:04:26 srv1 postfix/smtpd[23298]: connect from unknown[216.152.208.1]
Jan 21 05:04:27 srv1 postfix/smtpd[23298]: NOQUEUE: reject: RCPT from unknown[216.152.208.1]: 554 5.7.1 <astevens@rooksystems.com>: Relay access denied; from=<astevens@rooksystems.com> to=<astevens@rooksystems.com> proto=ESMTP helo=<DellCaseMentor>
Jan 21 05:04:27 srv1 postfix/smtpd[23298]: lost connection after RCPT from unknown[216.152.208.1]
Jan 21 05:04:27 srv1 postfix/smtpd[23298]: disconnect from unknown[216.152.208.1]
Jan 21 05:05:52 srv1 postfix/smtpd[23298]: connect from unknown[216.152.208.1]
Jan 21 05:05:52 srv1 postfix/smtpd[23298]: NOQUEUE: reject: RCPT from unknown[216.152.208.1]: 554 5.7.1 <astevens@rooksystems.com>: Relay access denied; from=<astevens@rooksystems.com> to=<astevens@rooksystems.com> proto=ESMTP helo=<DellCaseMentor>
Jan 21 05:05:52 srv1 postfix/smtpd[23298]: lost connection after RCPT from unknown[216.152.208.1]
Jan 21 05:05:52 srv1 postfix/smtpd[23298]: disconnect from unknown[216.152.208.1]
Jan 21 05:07:13 srv1 dovecot: pop3-login: Disconnected: rip=216.152.208.1, lip=192.168.1.13
Jan 21 05:07:14 srv1 dovecot: pop3-login: Aborted login (0 authentication attempts): rip=216.152.208.1, lip=192.168.1.13
Jan 21 05:07:34 srv1 postfix/smtpd[23408]: connect from unknown[216.152.208.1]
Jan 21 05:07:34 srv1 postfix/smtpd[23408]: lost connection after UNKNOWN from unknown[216.152.208.1]
Jan 21 05:07:34 srv1 postfix/smtpd[23408]: disconnect from unknown[216.152.208.1]
Jan 21 05:07:34 srv1 postfix/smtpd[23408]: connect from unknown[216.152.208.1]
Jan 21 05:07:35 srv1 postfix/smtpd[23408]: lost connection after STARTTLS from unknown[216.152.208.1]
Jan 21 05:07:35 srv1 postfix/smtpd[23408]: disconnect from unknown[216.152.208.1]
Jan 21 05:07:35 srv1 postfix/smtpd[23408]: connect from unknown[216.152.208.1]
Jan 21 05:07:35 srv1 postfix/smtpd[23408]: lost connection after EHLO from unknown[216.152.208.1]
Jan 21 05:07:35 srv1 postfix/smtpd[23408]: disconnect from unknown[216.152.208.1]
Jan 21 05:08:00 srv1 dovecot: pop3-login: Disconnected: rip=216.152.208.1, lip=192.168.1.13
Jan 21 05:08:00 srv1 dovecot: pop3-login: Disconnected: rip=216.152.208.1, lip=192.168.1.13
Jan 21 05:08:21 srv1 postfix/smtpd[23408]: connect from unknown[216.152.208.1]
Jan 21 05:08:21 srv1 postfix/smtpd[23408]: warning: SASL authentication failure: cannot connect to saslauthd server: Permission denied
Jan 21 05:08:21 srv1 postfix/smtpd[23408]: warning: unknown[216.152.208.1]: SASL LOGIN authentication failed: generic failure
Jan 21 05:08:21 srv1 postfix/smtpd[23408]: lost connection after AUTH from unknown[216.152.208.1]
Jan 21 05:08:21 srv1 postfix/smtpd[23408]: disconnect from unknown[216.152.208.1]
Jan 21 05:08:21 srv1 postfix/smtpd[23408]: connect from unknown[216.152.208.1]
Jan 21 05:08:22 srv1 postfix/smtpd[23408]: warning: SASL authentication failure: cannot connect to saslauthd server: Permission denied
Jan 21 05:08:22 srv1 postfix/smtpd[23408]: warning: unknown[216.152.208.1]: SASL LOGIN authentication failed: generic failure
Jan 21 05:08:22 srv1 postfix/smtpd[23408]: lost connection after AUTH from unknown[216.152.208.1]
Jan 21 05:08:22 srv1 postfix/smtpd[23408]: disconnect from unknown[216.152.208.1]
Jan 21 05:11:42 srv1 postfix/anvil[23301]: statistics: max connection rate 5/60s for (smtp:216.152.208.1) at Jan 21 05:08:21
Jan 21 05:11:42 srv1 postfix/anvil[23301]: statistics: max connection count 1 for (smtp:216.152.208.1) at Jan 21 05:04:26
Jan 21 05:11:42 srv1 postfix/anvil[23301]: statistics: max cache size 1 at Jan 21 05:04:26

```

---

### Post by hyper_ch on 2009-01-21
logs indicate your SASL setup isn't right yet.

I'd recommend to proceed according to the perfect howtos on [http://www.howtoforge.com](http://www.howtoforge.com) --> that works for me ;)

---

