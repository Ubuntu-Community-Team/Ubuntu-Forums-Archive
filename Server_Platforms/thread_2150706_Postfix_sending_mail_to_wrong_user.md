---
title: "Postfix sending mail to wrong user"
date: 2013-06-01
forum: Server Platforms
---

### Post by Hwest on 2013-06-01
Hi all,
Im working on installing and configuring a Postfix/Dovecot mail server and have run into a bump, whenever I send an email to [EMAIL="sales@3mhosts.com"]sales@3mhosts.com[/EMAIL], it send thats mail to [EMAIL="sales.3mhosts@jhcenterprises.net"]sales.3mhosts@jhcenterprises.net[/EMAIL]
To make my situation a little clearer, my hostname is server1.jhcenterprises.net, Im then hosting several sites including 3mhosts.com and jhcenterprises.net.

The following are some config and log files.
Main.cf:
```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version
virtual_alias_maps = hash:/etc/postfix/virtual
smtpd_recipient_restrictions = permit_sasl_authenticated


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


myhostname = server1.jhcenterprises.net
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = hash:/etc/postfix/mydomains
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command =
mailbox_size_limit = 0
recipient_delimiter = +
myorigin = /etc/mailname
inet_protocols = all
home_mailbox = Maildir/
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
#smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
```

mail.log:

```
Jun  2 12:44:48 server1 postfix/smtpd[12666]: connect from mail-ie0-f178.google.com[209.85.223.178]Jun  2 12:44:48 server1 postfix/smtpd[12666]: Anonymous TLS connection established from mail-ie0-f178.google.com[209.85.223.178]: TLSv1 with cipher ECDHE-RSA-RC4-SHA (128/128 bits)
Jun  2 12:44:48 server1 postfix/smtpd[12666]: 898F7712A68: client=mail-ie0-f178.google.com[209.85.223.178]
Jun  2 12:44:48 server1 postfix/cleanup[12671]: 898F7712A68: message-id=<CAAY5ta8O74R6tOUQMW3cz=fdSiKQzSVxYgW=zv0i0Fhkmi55Ew@mail.gmail.com>
Jun  2 12:44:48 server1 postfix/qmgr[12664]: 898F7712A68: from=<spam.hamish@gmail.com>, size=3287, nrcpt=1 (queue active)
Jun  2 12:44:48 server1 postfix/smtp[12672]: 898F7712A68: to=<sales.3mhosts@jhcenterprises.net>, orig_to=<sales@3mhosts.com>, relay=none, delay=0.27, delays=0.26/0.01/0/0, dsn=5.4.6, status=bounced (mail for jhcenterprises.net loops back to myself)
Jun  2 12:44:48 server1 postfix/cleanup[12671]: C71A5712A6D: message-id=<20130602031448.C71A5712A6D@server1.jhcenterprises.net>
Jun  2 12:44:48 server1 postfix/smtpd[12666]: disconnect from mail-ie0-f178.google.com[209.85.223.178]
Jun  2 12:44:48 server1 postfix/qmgr[12664]: C71A5712A6D: from=<>, size=5282, nrcpt=1 (queue active)
Jun  2 12:44:48 server1 postfix/bounce[12673]: 898F7712A68: sender non-delivery notification: C71A5712A6D
Jun  2 12:44:48 server1 postfix/qmgr[12664]: 898F7712A68: removed
Jun  2 12:44:56 server1 postfix/smtp[12672]: connect to gmail-smtp-in.l.google.com[2607:f8b0:400e:c01::1b]:25: Connection timed out
Jun  2 12:44:56 server1 postfix/smtp[12672]: C71A5712A6D: to=<spam.hamish@gmail.com>, relay=gmail-smtp-in.l.google.com[173.194.79.26]:25, delay=8.1, delays=0.05/0/7.6/0.4, dsn=2.0.0, status=sent (250 2.0.0 OK 1370142896 qs1si36891479pbc.346 - gsmtp)
Jun  2 12:44:56 server1 postfix/qmgr[12664]: C71A5712A6D: removed
```

Any insight will be greatly appreciated,
Thanks

---

### Post by lisati on 2013-06-01
One clue is in the message "mail for jhcenterprises.net loops back to myself."

This means that Postfix found a DNS record for jhcenterprises.net which points to your server, but isn't configured to accept mail for it. You might want to check the format for the "[mydestination]("http://www.postfix.org/postconf.5.html#mydestination")" paramter of postfix, which usually has a list of domains in the main.cf file, not in a separate file.

---

### Post by Hwest on 2013-06-02
> **lisati said:**
> One clue is in the message "mail for jhcenterprises.net loops back to myself."

This means that Postfix found a DNS record for jhcenterprises.net which points to your server, but isn't configured to accept mail for it. You might want to check the format for the "[mydestination]("http://www.postfix.org/postconf.5.html#mydestination")" paramter of postfix, which usually has a list of domains in the main.cf file, not in a separate file.

Thanks for the quick reply.

I edited my main.cf as you suggested with the mydestination looking like this now:
```
mydestination = localhost, jhcenterprises, 3mhosts, kurrupt, mail.3mhosts, 3mhosts.com, mail.3mhosts.com, server1.jhcenterprises.net

```
I sent another test email and got the same error.

---

### Post by lisati on 2013-06-02
If you want your server to accept mail for jhcenterprises.net you'll need to include that in *mydesetination*.

---

### Post by Hwest on 2013-06-02
Whoa, This is for me:
[IMG]http://i.stack.imgur.com/jiFfM.jpg[/IMG]

Cant believe I missed that, Thanks :)

---

