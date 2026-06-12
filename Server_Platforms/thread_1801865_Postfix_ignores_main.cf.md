---
title: "Postfix ignores main.cf"
date: 2011-07-11
forum: Server Platforms
---

### Post by ginge6000 on 2011-07-11
Hi,

I seem to be having an issue with Postfix as it seems to ignore the settings for myorigin & masquerade_domains in main.cf.  Now I may not have helped myself by naming my internal domain and external domain differently but I thought that was the whole point of the myorigin setting?

So, my server (11.04, clean install) has a hostname of server.localdomain and I want to send mail from external.net.  I can receive mail fine but when I go to send it I get an undeliverable message as it trys to send from [email]admin@server.locald[/email]omain rather than [email]admin@external.net[/email].  Here is my main.cf (with real domain names substituted) - it just seems to be ignored and the info from /etc/hostname used instead....

```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydomain = external.net
myorigin = $mydomain
mydestination = external.net, server.localdomain, localhost.localdomain, localhost
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
swap_bangpath = no
masquerade_domains = external.net
myhostname = server.localdomain
```

---

