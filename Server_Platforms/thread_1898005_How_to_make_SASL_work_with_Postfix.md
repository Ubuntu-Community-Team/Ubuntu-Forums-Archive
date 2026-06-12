---
title: "How to make SASL work with Postfix*?"
date: 2011-12-20
forum: Server Platforms
---

### Post by loup-vaillant on 2011-12-20
This is quite maddening. No matter how many tutorials I read, I can't get it to work.

I currently have postfix installed on my server. It works: I can receive e-mail just fine (I subscribed here with that server). But, SASL is completely blocked. On the bright side, my server is not an open relay. But I can't get it to send e-mail for me. I can connect, but I cannot authenticate.

Of course, I am root on my server. Additionally, I am the sole user of my mail server (only one account, on my personal domain).

My question is, could anyone point me to a simple, step by step explanation for how to add a username / password to SASL authentication with postfix? If possible, I'd like to avoid complications such as the saslauthd daemon, dovecot, or whatever. If Postfix can do it alone, I'd rather have it do it alone.

In case I made any obvious mistake, here is my /etc/postfix/main.cf (for instance, I think the "smtp_sasl_password_maps" parameter is probably useless, as my server doesn't authenticate to anyone.)

```

# See /usr/share/postfix/main.cf.dist for a commented, more complete version

smtpd_banner = $myhostname ESMTP $mail_name
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

delay_warning_time                  = 4h
unknown_local_recipient_reject_code = 450
maxima_queue_lifetime               = 7d
minimal_backoff_time                = 1000s
maximal_backoff_time                = 8000s
smtp_helo_timeout                   = 60s
smtpd_recipient_limit               = 32
smtpd_soft_error_limit              = 3
smtpt_hard_error_limit              = 12

smtpd_recipient_restrictions = permit_sasl_authenticated,
                               reject_unauth_pipelining,
                               permit_mynetworks,
                               reject_non_fqdn_recipient,
                               reject_unknown_recipient_domain,
                               reject_unauth_destination,
                               permit

smtpd_helo_required = yes
smtpd_delay_reject = yes
disable_vrfy_command = yes

readme_directory = no

#SASL
smtpd_sasl_auth_enable      = yes
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain     =
smtp_sasl_password_maps     = hash:/etc/postfix/sasl/passwd.db

# TLS parameters
smtpd_tls_cert_file              = /etc/ssl/certs/smtp.crt
smtpd_tls_key_file               = /etc/ssl/private/server.key
smtpd_use_tls                    = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database  = btree:${data_directory}/smtp_scache

mydomain         = loup-vaillant.fr
myhostname       = smtp.$mydomain
myorigin         = $mydomain
mydestination    = localhost.$mydomain www.$mydomain imap.$mydomain smtp.$mydomain localhost $mydomain
mynetworks_style = host

relay_domains =
relay_host    =

notyfy_classes = resource, software, bounce

alias_maps     = hash:/etc/aliases
alias_database = hash:/etc/aliases

mailbox_size_limit = 0
recipient_delimiter = +

home_mailbox = Maildir/

```Thanks.

---

### Post by druhboruch on 2011-12-20
The simplest way to configure postfix is to install mail-stack-delivery package.
It will do all the hard work for you.

---

### Post by loup-vaillant on 2011-12-20
Done. But it didn't help yet.

Now it's not an authentication problem.  Before even that (but after the TLS handsake, apparently), my SMTP connection times out!

So, checking /var/log/mail.log…

```

Dec 21 00:04:00 (none) postfix/smtpd[10697]: connect from car13-1-78-234-9-75.fbx.proxad.net[78.234.9.75]
Dec 21 00:04:00 (none) postfix/smtpd[10697]: SSL_accept error from car13-1-78-234-9-75.fbx.proxad.net[78.234.9.75]: 0
Dec 21 00:04:00 (none) postfix/smtpd[10697]: warning: TLS library problem: 10697:error:14094418:SSL routines:SSL3_READ_BYTES:tlsv1 alert unknown ca:s3_pkt.c:1102:SSL alert number 48:
Dec 21 00:04:00 (none) postfix/smtpd[10697]: lost connection after STARTTLS from car13-1-78-234-9-75.fbx.proxad.net[78.234.9.75]
Dec 21 00:04:00 (none) postfix/smtpd[10697]: disconnect from car13-1-78-234-9-75.fbx.proxad.net[78.234.9.75]
Dec 21 00:04:19 (none) postfix/smtpd[10697]: connect from car13-1-78-234-9-75.fbx.proxad.net[78.234.9.75]
Dec 21 00:04:20 (none) postfix/smtpd[10697]: warning: SASL: Connect to private/dovecot-auth failed: No such file or directory
Dec 21 00:04:20 (none) postfix/smtpd[10697]: fatal: no SASL authentication mechanisms
Dec 21 00:04:21 (none) postfix/master[10681]: warning: process /usr/lib/postfix/smtpd pid 10697 exit status 1

```

Ouch. Something to do with some file missing from the chroot jail?
Hmm, let's copy (well, hard link + chmod/chgrp to postfix, actually) that dovecot-auth file to /var/spool/postfix/private/ then.
Still fail: here's the log:

```
Dec 21 00:19:13 (none) postfix/smtpd[11067]: connect from car13-1-78-234-9-75.fbx.proxad.net[78.234.9.75]
Dec 21 00:19:13 (none) postfix/smtpd[11067]: warning: SASL: Connect to private/dovecot-auth failed: Connection refused
Dec 21 00:19:13 (none) postfix/smtpd[11067]: fatal: no SASL authentication mechanisms
Dec 21 00:19:14 (none) postfix/master[11058]: warning: process /usr/lib/postfix/smtpd pid 11067 exit status 1

```

Apparently, that wasn't the right file. But I must say that I didn't know what I was doing anyway. Do you know of a way to fix this ?

---

### Post by loup-vaillant on 2011-12-21
OK, solved for me.

Copy-pasting *warning: SASL: Connect to private/dovecot-auth failed:* into a search engine yielded [this page]("http://htyp.org/Connect_to_private/dovecot-auth_failed"), then [this one]("http://www.linuxmail.info/postfix-smtp-auth-dovecot-sasl/"). Basically, the file missing that postfix was looking for was a pipe, that dovecot was supposed to provide. But, as you could see, dovecot didn't provide it. It has to be configured first, and the relevant section of the configuration file is described on my second link.


Now let's breathe.

(EDIT : mail-stack-delivery *was* a life saver. Thanks)

---

