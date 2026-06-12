---
title: "Postfix problem"
date: 2011-05-23
forum: Server Platforms
---

### Post by chmurson on 2011-05-23
Hello i followed the tutorial from site: [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

and when I send mail using:

```
printf "Subject: blah" | sendmail -f support@MY_DOMAIN SOME_ADDRESS@gmail.com
```

got following error written into logs:

```
May 23 15:00:32 ubuntu postfix/pickup[12797]: 18E89102C6: uid=0 from=<support@MY_DOMAIN>
May 23 15:00:32 ubuntu postfix/cleanup[12806]: 18E89102C6: message-id=<20110523140032.18E89102C6@MY_DOMAIN>
May 23 15:00:32 ubuntu postfix/qmgr[12641]: 18E89102C6: from=<support@MY_DOMAIN>, size=301, nrcpt=1 (queue active)
May 23 15:00:32 ubuntu postfix/smtp[12809]: connect to gmail-smtp-in.l.google.com[209.85.143.27]:25: Connection refused
May 23 15:00:32 ubuntu postfix/smtp[12809]: connect to alt1.gmail-smtp-in.l.google.com[74.125.79.27]:25: Connection refused
May 23 15:00:32 ubuntu postfix/smtp[12809]: connect to alt2.gmail-smtp-in.l.google.com[74.125.53.27]:25: Connection refused
May 23 15:00:32 ubuntu postfix/smtp[12809]: connect to alt3.gmail-smtp-in.l.google.com[209.85.225.27]:25: Connection refused
May 23 15:00:32 ubuntu postfix/smtp[12809]: connect to alt4.gmail-smtp-in.l.google.com[74.125.159.27]:25: Connection refused
May 23 15:00:32 ubuntu postfix/smtp[12809]: 18E89102C6: to=<SOME_ADDRESS@gmail.com>, relay=none, delay=0.06, delays=0.04/0.01/0.01/0, dsn=4.4.1, status=deferred (connect to alt4.gmail-smtp-in.l.google.com[74.125.159.27]:25: Connection refused)
```

I'm able to connect via telnet:

```
telnet MY_DOMAIN 25
Trying IP_OF_MY_DOMAIN...
Connected to MY_DOMAIN.
Escape character is '^]'.
220 MY_DOMAIN ESMTP Postfix (Ubuntu)
ehlo MY_DOMAIN
250-MY_DOMAIN
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH LOGIN PLAIN
250-AUTH=LOGIN PLAIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
MAIL FROM:SOME_ADDRESS@gmail.com
250 2.1.0 Ok
RCPT TO:SOME_ADDRESS@gmail.com
554 5.7.1 <SOME_ADDRESS@gmail.com>: Relay access denied

```

In both examples i'm not able to send an email. I appreciate any ideas how i can resolve that problem.

heres snapshot of my config /etc/postfix/main.cf

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

myhostname = MY_DOMAIN
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = MY_DOMAIN, localhost, localhost.localdomain, localhost
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

inet_protocols = all
home_mailbox = Maildir/
mailbox_command =
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtp_tls_security_level = may
smtpd_tls_security_level = may
smtpd_tls_auth_only = no
smtp_tls_note_starttls_offer = yes
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
```

where MY_DOMAIN is valid hostname with MX record.

---

