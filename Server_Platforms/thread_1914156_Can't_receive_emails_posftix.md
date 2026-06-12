---
title: "Can't receive emails posftix"
date: 2012-01-23
forum: Server Platforms
---

### Post by majjj on 2012-01-23
Hi!

I'm trying to set up postfix mailserver called **mail.example.com**. everything's set up and i can send emails as **user@example.com**, but I can't receive them not as **user@mail.example.com** nor **user@example.com**

there shouldn't be anything wrong with the server cause I've tested it when its hostname was example.com (now it's mail.example.com)

posfix main.cf:
>  # See /usr/share/postfix/main.cf.dist for a commented, more complete version

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h
mydomain = **example.com**
myhostname = **mail.example.com**
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = $myhostname, localhost.$mydomain, localhost, $mydomain
relayhost =
mynetworks = 127.0.0.0/8 **0.0.0.0**
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
#Use these on Postfix 2.2.x only
#smtp_use_tls = yes
#smtpd_use_tls = yes
#For Postfix 2.3 or above use:
smtp_tlsmailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
#Use these on Postfix 2.2.x only
#smtp_use_tls = yes
#smtpd_use_tls = yes
#For Postfix 2.3 or above use:
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtp_tls_note_starttls_offer = yes
smtpd_tls_key_file = /etc/apache2/ssl/private.key
smtpd_tls_cert_file = /etc/apache2/ssl/public.crt
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
home_mailbox = Maildir/
message_size_limit = 104857600
inet_protocols = ipv4_security_level = may
smtpd_tls_security_level = may


/etc/mailname
> mail.example.com

Dns records:
> A	**example.com	1.1.1.1**
A	**mail.example.com	2.2.2.2**
10	**mail.example.com	2.2.2.2**	60 min

when I try to send test emails from another service they don't arrive to my server or leave any traces to the logs...

can you please help?

---

### Post by majjj on 2012-01-25
does anyone have a solution for this?

---

### Post by SeijiSensei on 2012-01-25
What are your MX records? I don't know what 
```
10 mail.example.com 2.2.2.2 60 min 
```
is supposed to mean.  An MX record looks like:
```
     IN MX 10 mail.example.com.
```
If you look in /var/log/mail.log, do you see the mail arriving at the server but not being delivered properly, or does the mail never arrive at all?

---

### Post by majjj on 2012-01-25
> **SeijiSensei said:**
> What are your MX records? I don't know what 
```
10 mail.example.com 2.2.2.2 60 min 
```
is supposed to mean.  An MX record looks like:
```
     IN MX 10 mail.example.com.
```
If you look in /var/log/mail.log, do you see the mail arriving at the server but not being delivered properly, or does the mail never arrive at all?

Thank you for your answer!

I just copied the mx record from godaddy dns manager and it's: priority 10, host: **mail.example.com **, points to: **2.2.2.2** and ttl 60 min.

(the domain name and ip aren't of course what i use)

---

### Post by SeijiSensei on 2012-01-25
I knew what it was supposed to mean, but it's not in the correct syntax for a bind zone file.  Take a look at [this](http://www.zytrax.com/books/dns/ch6/mydomain.html) for a start.

Don't rely on GoDaddy; read up on the syntax for bind9.

---

