---
title: "Cannot receive emails on server"
date: 2013-12-21
forum: Server Platforms
---

### Post by joeborg on 2013-12-21
I've been trying to follow [https://www.digitalocean.com/community/articles/how-to-set-up-a-postfix-e-mail-server-with-dovecot](https://www.digitalocean.com/community/articles/how-to-set-up-a-postfix-e-mail-server-with-dovecot) to be able to send and receive emails on my VS.

I can send emails fine, but when ever one is received, I get the following error.

```
Dec 21 21:12:07 localhost postfix/submission/smtpd[25634]: warning: cannot get RSA private key from file /etc/ssl/private/mail.key: disabling TLS support
Dec 21 21:12:07 localhost postfix/submission/smtpd[25634]: warning: TLS library problem: 25634:error:0B080074:x509 certificate routines:X509_check_private_key:key values mismatch:x509_cmp.c:331:
Dec 21 21:12:07 localhost postfix/submission/smtpd[25634]: connect from mail-qc0-f179.google.com[209.85.216.179]
Dec 21 21:12:07 localhost postfix/cleanup[25638]: 62091E0F44: message-id=<20131221211207.62091E0F44@mail.josephb.org>
Dec 21 21:12:07 localhost postfix/submission/smtpd[25634]: disconnect from mail-qc0-f179.google.com[209.85.216.179]
Dec 21 21:12:07 localhost postfix/qmgr[25620]: 62091E0F44: from=<double-bounce@mail.josephb.org>, size=858, nrcpt=1 (queue active)
Dec 21 21:12:07 localhost postfix/local[25640]: 62091E0F44: to=<root@josephb.org>, orig_to=<postmaster>, relay=local, delay=0.02, delays=0.01/0/0/0.01, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Dec 21 21:12:07 localhost postfix/qmgr[25620]: 62091E0F44: removed
Dec 21 21:12:22 localhost postfix/submission/smtpd[25634]: connect from localhost[127.0.0.1]
Dec 21 21:12:22 localhost postfix/submission/smtpd[25634]: disconnect from localhost[127.0.0.1]

```

The key is there and should be readable
```

-rw-r--r-- 1 root root 1.7K Dec 21 20:56 /etc/ssl/private/mail.key

```

Not sure why they're being removed.  I'm expecting to be able to type `mail` and see the email.

---

### Post by TheFu on 2013-12-21
A shot in the dark, but your ISP may be filtering inbound port 25 connections. Residential ISPs do this and some hosting providers do as well so you get to pay for their email services.  I would check that first.  So .... can you telnet to the server port 25 from across the internet and see a connection?

---

### Post by joeborg on 2013-12-21
Hi Fu,
Don't think that's the problem as I can send mail via 25 fine, it's just receiving.  Tried telnet as well, which was fine.

Thanks for the suggestion though.

---

### Post by TheFu on 2013-12-21
> **joeborg said:**
> Hi Fu,
Don't think that's the problem as I can send mail via 25 fine, it's just receiving.  Tried telnet as well, which was fine.

Thanks for the suggestion though.

My apologies. It appears that inbound email is getting to your box, but having TLS issues. Have you tried disabling the TLS stuff and getting plaintext email to work first, then you can go back and add TLS later.  I'll check my mail server settings ... well, I'm less strict on SSLv3 and need to consider that setting next year. Planning an upgrade here.

**postconf -n** output would be a help.  Do the certs look _reasonable?_ (I'm certain you know this, but never post a private cert anywhere).

Perhaps it is a gmail specific issue?  They do things differently there sometimes. Same issue with a different sender domain?

BTW, is the cert a localhost-creation or did you get a real-commercial cert?

BTW, I scanned those DO instructions - they seem pretty good, though I've never used them for anything. An alternative how-to site is [http://www.howtoforge.com/](http://www.howtoforge.com/), BTW. Complete how-tos are a good resource. I'm adding DO to my resource list. Thanks.

---

### Post by joeborg on 2013-12-30
Thanks for the reply.  Here is my config:
```
root@alpha:~# postconf -n
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
inet_interfaces = all
inet_protocols = all
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
mydestination = mail.josephb.org, josephb.org, localhost, localhost.localdomain, localhost
myhostname = mail.josephb.org
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost =
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_tls_cert_file = /etc/ssl/certs/mailcert.pem
smtpd_tls_key_file = /etc/ssl/private/mail.key
smtpd_tls_protocols = !SSLv2, !SSLv3
smtpd_tls_security_level = may
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes

```

All looks ok to me and the (the .pem and .key are where they should be).

I've generate them myself, as described in the guide.

---

### Post by joeborg on 2013-12-30
They seem to be sitting in /var/mail/nobody
```

From double-bounce@mail.josephb.org  Mon Dec 30 19:46:47 2013
Return-Path: <double-bounce@mail.josephb.org>
X-Original-To: postmaster
Delivered-To: postmaster@josephb.org
Received: by mail.josephb.org (Postfix)
    id 37288E0F4E; Mon, 30 Dec 2013 19:46:47 +0000 (UTC)
Date: Mon, 30 Dec 2013 19:46:47 +0000 (UTC)
From: MAILER-DAEMON@mail.josephb.org (Mail Delivery System)
To: postmaster@josephb.org (Postmaster)
Subject: Postfix SMTP server: errors from mail-qe0-f42.google.com[209.85.128.42]
Message-Id: <20131230194647.37288E0F4E@mail.josephb.org>


Transcript of session follows.


 Out: 220 mail.josephb.org ESMTP Postfix (Ubuntu)
 In:  EHLO mail-qe0-f42.google.com
 Out: 250-mail.josephb.org
 Out: 250-PIPELINING
 Out: 250-SIZE 10240000
 Out: 250-VRFY
 Out: 250-ETRN
 Out: 250-STARTTLS
 Out: 250-ENHANCEDSTATUSCODES
 Out: 250-8BITMIME
 Out: 250 DSN
 In:  STARTTLS
 Out: 454 4.7.0 TLS not available due to local problem
 In:  QUIT
 Out: 221 2.0.0 Bye




For other details, see the local mail logfile

```

---

### Post by CharlesA on 2013-12-30
Well the first error seems to point to having the cert's key file password protected. Did you remove the passphrase?

The other error might be due to it being a self signed cert, but I don't think that is the problem.

---

### Post by joeborg on 2013-12-31
I think so, I just left the field blank.

---

