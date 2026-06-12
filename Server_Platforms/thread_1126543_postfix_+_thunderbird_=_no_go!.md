---
title: "postfix + thunderbird = no go!?"
date: 2009-04-15
forum: Server Platforms
---

### Post by artheus on 2009-04-15
Hi!

I've been trying for a while now.. And I've been searching the net for an answer to my question... but haven't found any..

Well.. I am trying to set up my mailserver (postfix on ubuntu 8.10 server edition) so that it should work sending mails with thunderbird..
But I can't seem to find a way to add useraccounts to postfix, that I can use to login to postfix.. virtual users would be nice..

Well.. I've tried to log in with the username and password of every single user on my server.. even root.. but no go.
(by log in I mean sending mail via Postfix using Thunderbird, and in Thunderbird adding my login username and password..)

Could anyone help me with this?

Using SSL would be nice!! ^^

Cheers!
Artheus

---

### Post by mckenna1977 on 2009-04-15
if you telnet on your server and send an email to a user does it send correctly according to your mail log?

if you login from a pop3 client like thunderbird can you put username and password of user on your server? does this login appear in the mail log?

are there any errors in mail log?

if you create a new user and send from an online account (gmail / yahoo etc) does the server log receive the email?

have you setup user mappings in virtual domains?

your logs should tell you everything /var/log/mail.log

---

### Post by artheus on 2009-04-21
here's the /var/log/mail.log
```

Apr 20 16:02:02 hurricane dovecot: ssl-build-param: SSL parameters regeneration completed
Apr 21 17:33:17 hurricane postfix/master[4691]: terminating on signal 15
Apr 21 17:33:17 hurricane postfix/master[25557]: daemon started -- version 2.5.5, configuration /etc/postfix
Apr 21 17:41:35 hurricane postfix/master[25557]: terminating on signal 15
Apr 21 17:41:36 hurricane postfix/master[25842]: daemon started -- version 2.5.5, configuration /etc/postfix
Apr 21 17:42:04 hurricane postfix/smtpd[25847]: connect from gilbert.local[192.168.1.34]
Apr 21 17:42:13 hurricane postfix/smtpd[25847]: SSL_accept error from gilbert.local[192.168.1.34]: -1
Apr 21 17:42:13 hurricane postfix/smtpd[25847]: lost connection after CONNECT from gilbert.local[192.168.1.34]
Apr 21 17:42:13 hurricane postfix/smtpd[25847]: disconnect from gilbert.local[192.168.1.34]
Apr 21 17:42:45 hurricane postfix/smtpd[25847]: connect from 217-208-2-63-no26.tbcn.telia.com[217.208.2.63]
Apr 21 17:42:54 hurricane postfix/smtpd[25847]: SSL_accept error from 217-208-2-63-no26.tbcn.telia.com[217.208.2.63]: -1
Apr 21 17:42:54 hurricane postfix/smtpd[25847]: lost connection after CONNECT from 217-208-2-63-no26.tbcn.telia.com[217.208.2.63]
Apr 21 17:42:54 hurricane postfix/smtpd[25847]: disconnect from 217-208-2-63-no26.tbcn.telia.com[217.208.2.63]
Apr 21 17:43:35 hurricane postfix/master[25842]: terminating on signal 15
Apr 21 17:43:35 hurricane postfix/master[25945]: daemon started -- version 2.5.5, configuration /etc/postfix
Apr 21 17:43:47 hurricane postfix/smtpd[25950]: connect from 217-208-2-63-no26.tbcn.telia.com[217.208.2.63]
Apr 21 17:43:55 hurricane postfix/smtpd[25950]: SSL_accept error from 217-208-2-63-no26.tbcn.telia.com[217.208.2.63]: -1
Apr 21 17:43:55 hurricane postfix/smtpd[25950]: warning: TLS library problem: 25950:error:140760FC:SSL routines:SSL23_GET_CLIENT_HELLO:unknown protocol:s23_srvr.c:562:
Apr 21 17:43:55 hurricane postfix/smtpd[25950]: lost connection after CONNECT from 217-208-2-63-no26.tbcn.telia.com[217.208.2.63]
Apr 21 17:43:55 hurricane postfix/smtpd[25950]: disconnect from 217-208-2-63-no26.tbcn.telia.com[217.208.2.63]
Apr 21 17:45:32 hurricane postfix/pickup[25946]: 0E75E1204F3: uid=1000 from=<hurricane>
Apr 21 17:45:32 hurricane postfix/cleanup[25957]: 0E75E1204F3: message-id=<20090421154532.0E75E1204F3@theidan.com>
Apr 21 17:45:32 hurricane postfix/qmgr[25947]: 0E75E1204F3: from=<hurricane@myserver>, size=307, nrcpt=1 (queue active)
Apr 21 17:45:33 hurricane postfix/local[25959]: 0E75E1204F3: to=<mail@domain.com>, relay=local, delay=40, delays=39/0.02/0/1, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Apr 21 17:45:33 hurricane postfix/qmgr[25947]: 0E75E1204F3: removed
Apr 21 17:46:40 hurricane postfix/pickup[25946]: 2D15C1204F1: uid=1000 from=<hurricane>
Apr 21 17:46:40 hurricane postfix/cleanup[25957]: 2D15C1204F1: message-id=<20090421154640.2D15C1204F1@theidan.com>
Apr 21 17:46:40 hurricane postfix/qmgr[25947]: 2D15C1204F1: from=<hurricane@myserver>, size=285, nrcpt=1 (queue active)
Apr 21 17:46:40 hurricane postfix/local[25959]: 2D15C1204F1: to=<mail@domain.com>, relay=local, delay=27, delays=27/0/0/0.02, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Apr 21 17:46:40 hurricane postfix/qmgr[25947]: 2D15C1204F1: removed
Apr 21 18:09:45 hurricane postfix/master[25945]: terminating on signal 15
Apr 21 18:09:46 hurricane postfix/master[26388]: daemon started -- version 2.5.5, configuration /etc/postfix
Apr 21 18:10:06 hurricane postfix/smtpd[26472]: connect from 217-208-2-63-no26.tbcn.telia.com[217.208.2.63]
Apr 21 18:10:46 hurricane postfix/master[26388]: terminating on signal 15
Apr 21 18:10:46 hurricane postfix/master[26566]: daemon started -- version 2.5.5, configuration /etc/postfix
Apr 21 18:10:50 hurricane postfix/smtpd[26571]: connect from 217-208-2-63-no26.tbcn.telia.com[217.208.2.63]
Apr 21 18:15:50 hurricane postfix/smtpd[26571]: SSL_accept error from 217-208-2-63-no26.tbcn.telia.com[217.208.2.63]: -1
Apr 21 18:15:50 hurricane postfix/smtpd[26571]: lost connection after CONNECT from 217-208-2-63-no26.tbcn.telia.com[217.208.2.63]
Apr 21 18:15:50 hurricane postfix/smtpd[26571]: disconnect from 217-208-2-63-no26.tbcn.telia.com[217.208.2.63]

```

Not possible to connect to postfix through telnet either.. And now the relayserver is not working either..

"gilbert.local[192.168.1.34]" is my desktop computer from which I'm trying to telnet.

Here's my Main.cf
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
smtpd_use_tls=no
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = theidan.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = hurricane, localhost.localdomain, localhost
relayhost = smtprelay1.telia.com:25
#smtp_sasl_auth_enable = yes
#smtp_sasl_security_option = noanonymous
#smtp_sasl_password_maps = hash:/etc/postfix/sasl_password
mynetworks = 127.0.0.0/8 192.168.1.0/24
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

#virtual_mailbox_domains = /usr/local/postfix/etc/virtual_domains

```

and here is the Master.cf
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
#smtp      inet  n       -       -       -       -       smtpd
2525	   inet	 n	 -	 n	 -	 -	 smtpd
#submission inet n       -       -       -       -       smtpd
#  -o smtpd_tls_security_level=encrypt
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#smtps     inet  n       -       -       -       -       smtpd
  -o smtpd_tls_wrappermode=yes
  -o smtpd_sasl_auth_enable=yes
  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
  -o milter_macro_daemon_name=ORIGINATING
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

---

### Post by BkkBonanza on 2009-04-21
I see a bunch of ssl accept errors there. Make sure you have Thunderbird configured for SSL or no SSL to connect to server. It doesn't seem to be getting to authentication stage as it's stopping when one side or the other is expecting SSL.

---

### Post by tubezninja on 2009-04-21
postfix in and of itself doesn't do IMAP or POP3, which is what you need for Thunderbird to work.  In addition to postfix, wihich is a mail server, you'll need to install a mail delivery *agent* that works in tandem with postfix, such as dovecot:

[https://help.ubuntu.com/community/Dovecot](https://help.ubuntu.com/community/Dovecot)

If you're willing to wait a couple of days, Jaunty is supposed to have a prepackaged turnkey mail server using both components that makes deployment easy.

---

