---
title: "Postfix and Dovecot issues"
date: 2011-08-26
forum: Server Platforms
---

### Post by asai on 2011-08-26
Hi,
I have som problems with my Postfix/Dovecot installation.
Using Squirrelmail as webmail client.
Logs in fine. Sending mail to an outside address gives this respons in mail.log:
```
Aug 26 06:33:56 server1 postfix/smtp[7144]: connect to mail.unitron.no[77.241.101.37]:25: Connection timed out
Aug 26 06:33:58 server1 postfix/smtp[7144]: 9D83F23493: to=<terje@sig-halvorsen.no>, relay=none, delay=25, delays=2.2/2.1/21/0, dsn=4.4.1, status=deferred (connect to mail.unitron.no[77.241.101.37]:25: Connection timed out)

```

Sending mail from a outside mail client to a mailadress on the server seems to go correct and gives no reply mail with error.
But I cant find any mail i Squirrelmail.
Here is the log on receiving mail:
```
Aug 26 06:40:07 server1 postfix/smtpd[7240]: warning: dict_nis_init: NIS domain name not set - NIS lookups disabled
Aug 26 06:40:09 server1 postfix/smtpd[7240]: connect from smtp01.unitron.no[77.241.101.33]
Aug 26 06:40:11 server1 postfix/smtpd[7240]: setting up TLS connection from smtp01.unitron.no[77.241.101.33]
Aug 26 06:40:11 server1 postfix/smtpd[7240]: Anonymous TLS connection established from smtp01.unitron.no[77.241.101.33]: TLSv1 with cipher AES128-SHA (128/128 bits)
Aug 26 06:40:15 server1 postfix/smtpd[7240]: 5F8002349B: client=smtp01.unitron.no[77.241.101.33]
Aug 26 06:40:15 server1 postfix/cleanup[7249]: 5F8002349B: message-id=<55CC3F138123C24C8B2EE59A8F374B81FBE4B85C0E@exch06.unitron.asp>
Aug 26 06:40:15 server1 postfix/qmgr[26066]: 5F8002349B: from=<terje@sig-halvorsen.no>, size=3406, nrcpt=1 (queue active)
Aug 26 06:40:15 server1 postfix/local[7250]: warning: dict_nis_init: NIS domain name not set - NIS lookups disabled
Aug 26 06:40:15 server1 postfix/smtpd[7240]: disconnect from smtp01.unitron.no[77.241.101.33]
Aug 26 06:40:17 server1 postfix/local[7250]: 5F8002349B: to=<terje@example.com>, relay=local, delay=4.3, delays=2.1/0.03/0/2.1, dsn=2.0.0, status=sent (delivered to command: procmail -a "$EXTENSION")
Aug 26 06:40:17 server1 postfix/qmgr[26066]: 5F8002349B: removed
Aug 26 06:40:24 server1 postfix/qmgr[26066]: 7430223491: from=<terje@example.com>, size=728, nrcpt=1 (queue active)
Aug 26 06:40:24 server1 postfix/qmgr[26066]: 9D83F23493: from=<terje@example.com>, size=716, nrcpt=1 (queue active)

```

Here is some lines from dovecot.conf:
```
auth default {	
  socket listen {
    client {
	  path = /var/spool/postfix/private/auth-client
	  mode = 0660
	  user = postfix
	  group = postfix
    }
  }	
  mechanisms = plain login

```

And my main.cf:
```
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

append_dot_mydomain = no

#alias_maps = hash:/etc/postfix/aliases
virtual_alias_maps = hash:/etc/postfix/virtual
#alias_database = hash:/etc/postfix/aliases
#myorigin = hash:/etc/mailname
mydestination = hash:/etc/postfix/mydomains
relayhost =
mynetworks = 127.0.0.0/8, 10.10.160.0/24
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth-client
smtpd_sasl_local_domain = 
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_sasl_auth_enable = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
inet_interfaces = all
smtpd_tls_auth_only = no
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtp_tls_note_starttls_offer = yes
smtpd_tls_key_file = /etc/ssl/private/server.key
smtpd_tls_cert_file = /etc/ssl/certs/server.crt
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
myhostname = example.com
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
home_mailbox = Maildir/
```

mydomains:
```
server1		OK
localhost	OK
example.com	OK

```

This is probably a very small issue, but I cant find it.
Any help would be apreciated. :)

---

### Post by asai on 2011-08-29
Nope

---

### Post by SeijiSensei on 2011-08-29
Call your Internet provider and check whether they block SMTP port 25.

---

