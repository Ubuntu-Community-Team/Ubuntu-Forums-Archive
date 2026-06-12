---
title: "Email Server Security Concerns"
date: 2011-10-04
forum: Server Platforms
---

### Post by Stickiler on 2011-10-04
I've recently been messing around with setting up an email server on a VPS I rent, and I was having trouble with Postfix automatically rejecting emails from external sources. By that I mean, I sent a test email from my hotmail account to one of the accounts I had on the server, and the mail.log kept saying that it was deferring the email, and to try again later. So I kept messing around, and I ended up getting it working, however, I'm worried that I may have inadvertently opened up a security hole while trying to get the server working.


My main.cf is posted below, and the main issue I could see would be the smtpd_recipient_restrictions line, however I couldn't work out any other way to make it work.

Any help would be appreciated.



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
smtpd_tls_cert_file = /etc/ssl/certs/ssl-mail.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-mail.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = olympusgaming.org

alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mailbox_command = /usr/lib/dovecot/deliver -c /etc/dovecot/conf.d/01-mail-stack-delivery.conf -n -m "${EXTENSION}"
mailbox_size_limit = 0
recipient_delimiter = +
home_mailbox = Maildir/
smtpd_sasl_auth_enable = yes
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/dovecot-auth
smtpd_sasl_authenticated_header = yes
smtpd_sasl_local_domain = $myhostname
broken_sasl_auth_clients = yes
smtp_use_tls = yes
smtpd_tls_received_header = yes
smtpd_tls_mandatory_protocols = SSLv3, TLSv1
smtpd_tls_mandatory_ciphers = medium
smtpd_tls_auth_only = yes
tls_random_source = dev:/dev/urandom
best_mx_transport = local
smtpd_recipient_restrictions = permit_mynetworks permit_sasl_authenticated permit reject

```

---

### Post by hawk2010 on 2011-10-04
Looks like from the configuration you have not define mynetworks parameter which means anyone can send mail through your server.

define the mynetworks parameter 

Since its differed then it may be a DNS issues. your MX record of the domain should point to your VPS mail server


> **Stickiler said:**
> I've recently been messing around with setting up an email server on a VPS I rent, and I was having trouble with Postfix automatically rejecting emails from external sources. By that I mean, I sent a test email from my hotmail account to one of the accounts I had on the server, and the mail.log kept saying that it was deferring the email, and to try again later. So I kept messing around, and I ended up getting it working, however, I'm worried that I may have inadvertently opened up a security hole while trying to get the server working.


My main.cf is posted below, and the main issue I could see would be the smtpd_recipient_restrictions line, however I couldn't work out any other way to make it work.

Any help would be appreciated.



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
smtpd_tls_cert_file = /etc/ssl/certs/ssl-mail.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-mail.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = olympusgaming.org

alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mailbox_command = /usr/lib/dovecot/deliver -c /etc/dovecot/conf.d/01-mail-stack-delivery.conf -n -m "${EXTENSION}"
mailbox_size_limit = 0
recipient_delimiter = +
home_mailbox = Maildir/
smtpd_sasl_auth_enable = yes
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/dovecot-auth
smtpd_sasl_authenticated_header = yes
smtpd_sasl_local_domain = $myhostname
broken_sasl_auth_clients = yes
smtp_use_tls = yes
smtpd_tls_received_header = yes
smtpd_tls_mandatory_protocols = SSLv3, TLSv1
smtpd_tls_mandatory_ciphers = medium
smtpd_tls_auth_only = yes
tls_random_source = dev:/dev/urandom
best_mx_transport = local
smtpd_recipient_restrictions = permit_mynetworks permit_sasl_authenticated permit reject

```

---

### Post by Stickiler on 2011-10-04
> **hawk2010 said:**
> Looks like from the configuration you have not define mynetworks parameter which means anyone can send mail through your server.

define the mynetworks parameter 

Since its differed then it may be a DNS issues. your MX record of the domain should point to your VPS mail server


The MX record of the domain is pointing at my mail server.

and if I define the mynetworks parameter, won't that limit me to a set ip range? I need to retain the ability to connect from any ip address, as I'm checking my emails from uni, work, home and my second house. Most of which are on dynamic ip's anyway.

---

### Post by hawk2010 on 2011-10-04
Actually that won't limit you . You can configure sasl-authentication for that. then you can connect from any where

---

### Post by Stickiler on 2011-10-04
> **hawk2010 said:**
> Actually that won't limit you . You can configure sasl-authentication for that. then you can connect from any where

oh, really? how best would I go about this?

I've been working on it for about a week now, and I'm nearly out of hair to pull out.

---

### Post by hawk2010 on 2011-10-04
Checkout this tutorial
[http://workaround.org/ispmail/squeeze](http://workaround.org/ispmail/squeeze)

---

### Post by Stickiler on 2011-10-05
> **hawk2010 said:**
> Checkout this tutorial
[http://workaround.org/ispmail/squeeze](http://workaround.org/ispmail/squeeze)

Excellent! Thank you very much. I realised what I was missing, and got it all working :D


Turns out I already had sasl authentication setup, due probably to the dovecot-postfix package. So all I needed to do was change this line:

```
smtpd_recipient_restrictions = permit_mynetworks permit_sasl_authenticated permit reject
```

to

```
smtpd_recipient_restrictions = permit_mynetworks permit_sasl_authenticated reject_unauth_destination
```


And it all worked perfectly. Thanks for all your help.

---

