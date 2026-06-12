---
title: "mail filter/limit out going mail"
date: 2011-05-18
forum: Server Platforms
---

### Post by kasper22 on 2011-05-18
Hi I've run into a bit of a problem with how I'm trying to setup a mail server on a development machine.  The goal seems simple, only allow mail to be sent if it's going to our domain, or bonus if it can get to a few email addresses we specify.

We have postfix currently (10.04 ubuntu) and I thought this route would work [http://www.postfix.org/RESTRICTION_CLASS_README.html#external](http://www.postfix.org/RESTRICTION_CLASS_README.html#external).  However after implementing if I send an email by sendmail the restrictions get skipped.  If I connect to the smtp server by telnet they work.

Here is my postfix config:
```
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
inet_interfaces = all
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
mydestination = mage-gorilla.gorilla.local, localhost.gorilla.local, , localhost
myhostname = mage-gorilla.gorilla.local
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost =
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = check_sender_access hash:/etc/postfix/restricted_senders, reject_unverified_recipient, reject_unauth_destination
smtpd_restriction_classes = local_only
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes

```

Any ideas on where to go from here?  I'm not married to what I've done so I'm open to any suggestions.  

Thanks
-Bryan

---

### Post by kasper22 on 2011-05-23
Anyone? Could really use some help here.

Thanks

---

