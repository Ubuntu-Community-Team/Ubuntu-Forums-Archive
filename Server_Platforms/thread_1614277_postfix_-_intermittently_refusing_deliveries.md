---
title: "postfix - intermittently refusing deliveries"
date: 2010-11-05
forum: Server Platforms
---

### Post by sdedgar on 2010-11-05
I have an install on Ubuntu Server 10.04.1 LTS running Postfix straight from the standard repository. Server up to date with all updates. I have Postfix configured so that all messages received for unrecognised users are forwarded to my own mailbox. Most of the time this works just fine, but it seems that when certain servers try and deliver email to me the mail gets rejected as recipient unknown. What I really don't understand about this is that if I send email from a different server to the exact same address, it gets through.

Below is the mail.info log showing me sending email to myself from two different servers. The first transaction here is from my employers email server

```
Nov  5 11:26:40 myServer postfix/smtpd[27259]: connect from mailserver1.employer.com[123.123.123.123]
Nov  5 11:26:40 myServer postfix/smtpd[27259]: setting up TLS connection from mailserver1.employer.com[123.123.123.123]
Nov  5 11:26:40 myServer postfix/smtpd[27259]: Anonymous TLS connection established from mailserver1.employer.com[123.123.123.123]: TLSv1 with cipher RC4-SHA (128/128 bits)
Nov  5 11:26:40 myServer postfix/smtpd[27259]: 7A9D922FAE: client=mailserver1.employer.com[123.123.123.123]
Nov  5 11:26:40 myServer postfix/cleanup[27263]: 7A9D922FAE: message-id=<0D2FF0ADB3FC394D9CA136A9D2F295C70284A0C9@XXXXXXXXXXXXXX.employer.com>
Nov  5 11:26:40 myServer postfix/qmgr[27202]: 7A9D922FAE: from=<prvs=918055c3c=sdedgar@employer.com>, size=4572, nrcpt=1 (queue active)
Nov  5 11:26:41 myServer postfix/pickup[27203]: 0A9DD22FB3: uid=5001 from=<prvs=918055c3c=sdedgar@employer.com>
Nov  5 11:26:41 myServer postfix/pipe[27264]: 7A9D922FAE: to=<sdedgar@myserver.com>, orig_to=<myAlias@myServer.com>, relay=spamassassin, delay=0.57, delays=0.11/0/0/0.46, dsn=2.0.0, status=sent (delivered via spamassassin service)
Nov  5 11:26:41 myServer postfix/cleanup[27263]: 0A9DD22FB3: message-id=<0D2FF0ADB3FC394D9CA136A9D2F295C70284A0C9@XXXXXXXXX.employer.com>
Nov  5 11:26:41 myServer postfix/qmgr[27202]: 7A9D922FAE: removed
Nov  5 11:26:41 myServer postfix/qmgr[27202]: 0A9DD22FB3: from=<prvs=918055c3c=sdedgar@employer.com>, size=4895, nrcpt=1 (queue active)
Nov  5 11:26:41 myServer postfix/local[27269]: 0A9DD22FB3: to=<sdedgar@myserver.com>, relay=local, delay=0.03, delays=0.01/0.01/0/0, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Nov  5 11:26:41 myServer postfix/qmgr[27202]: 0A9DD22FB3: removed
Nov  5 11:26:45 myServer postfix/smtpd[27259]: disconnect from mailserver1.employer.com[123.123.123.123]

```

This next section is an email from a websites registration page. Recipient address is exactly the same as in the section above

```

Nov  5 11:27:35 myServer postfix/smtpd[27259]: warning: 155.155.155.155: address not listed for hostname 155.155.155.155.ip.websites-provider.com
Nov  5 11:27:35 myServer postfix/smtpd[27259]: connect from unknown[155.155.155.155]
Nov  5 11:27:35 myServer postfix/smtpd[27259]: setting up TLS connection from unknown[155.155.155.155]
Nov  5 11:27:35 myServer postfix/smtpd[27259]: Anonymous TLS connection established from unknown[155.155.155.155]: TLSv1 with cipher DHE-RSA-AES256-SHA (256/256 bits)
Nov  5 11:27:36 myServer postfix/smtpd[27259]: NOQUEUE: reject: RCPT from unknown[155.155.155.155]: 550 5.1.1 <myAlias@myserver.com>: Recipient address rejected: User unknown in local recipient table; from=<noreply@website.com> to=<alias@myserver.com> proto=ESMTP helo=<mailserver.website-provider.com>
Nov  5 11:27:37 myServer postfix/smtpd[27259]: disconnect from unknown[155.155.155.155]

```


Config follows

Main.cf
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
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = myServer.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = myServer.com
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
home_mailbox = Maildir/
mailbox_command = procmail -a "$EXTENSION"
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
virtual_alias_maps = hash:/etc/postfix/virtual
#local_recipient_maps =
luser_relay = steven
header_checks = regexp:/etc/postfix/header-checks
message_size_limit = 20480000

```

Master.cf
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
#  -o smtpd_tls_security_level=encrypt
#  -o smtpd_sasl_auth_enable=yes
#  -o smtpd_client_restrictions=permit_sasl_authenticated,reject
#  -o milter_macro_daemon_name=ORIGINATING
#smtps     inet  n       -       -       -       -       smtpd
#  -o smtpd_tls_wrappermode=yes
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

spamassassin unix -     n       n       -       -       pipe
        user=spamd argv=/usr/bin/spamc -f -e    
        /usr/sbin/sendmail -oi -f ${sender} ${recipient}

```

/etc/virtual 
```

@myserver.com

```

I do have header-checks in place to reject email addresses that only get spam, but they all give a distinctive error, which I can see in the logs when it is triggered, and this is not the case here.

Any pointers to where the problem might be appreciated, I've been digging and googling, but no joy.

---

### Post by sdedgar on 2010-11-08
Figured it out, although I've noted that I actually censored the very information in the logs above that pointed to the cause.

It seems that some mail servers change the rcpt to: field to be like [email]user@server1.myServer.com[/email], whereas others leave it as [email]user@myServer.com[/email]. Email sent to the latter worked fine, sent to the former it didn't. I think the reason some mail servers do this is that my MX record points to server1.myServer.com, rather than the IP address or myServer.com.

Fix was simple enough, just add a virtualmapping '@server.myServer.com [email]sdedgar@myServer.com[/email]'. Alternatively I could have changed my MX entry.

---

