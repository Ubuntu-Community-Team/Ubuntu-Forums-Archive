---
title: "Postfix with sasl not working on usernames containing @"
date: 2008-01-03
forum: Server Platforms
---

### Post by bss on 2008-01-03
I have troubles with my mailserver's sasl auth. It works fine on regular usernames (test, root, user) but not on the ones containing @ (user@domain, [email]info@example.com[/email], ect.)

I am using webmin/virtualmin for webserver hosting and I have usernames for mail accouts in form user@domain, as mentiond before :s.

Here is my main.cf from postifx:
```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (mojBox.com // mailhosting)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

# TLS parameters
smtpd_use_tls = yes
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = bss-mail-server
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
#mydestination = bss-mail-server, localhost.localdomain, , localhost
mynetworks = 127.0.0.0/8

mailbox_size_limit = 0
recipient_delimiter = +
virtual_alias_maps = hash:/etc/postfix/virtual_domains_mapping

#mailbox_command =
mailbox_command = procmail -a "$EXTENSION"
home_mailbox = Maildir/


smtpd_sasl_auth_enable = yes

#smtpd_sasl_local_domain = $myhostname
broken_sasl_auth_clients = yes

smtpd_recipient_restrictions = permit_sasl_authenticated permit_mynetworks permit_inet_interfaces reject_unauth_destination

#mynetworks_style = host
mynetworks_style = subnet

```

Is there trouble in "@" character in username??

---

