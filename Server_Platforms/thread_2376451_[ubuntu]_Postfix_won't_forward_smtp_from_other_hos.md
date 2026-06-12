---
title: "[ubuntu] Postfix won't forward smtp from other host"
date: 2017-11-02
forum: Server Platforms
---

### Post by bonaventure on 2017-11-02
Hi, my Postfix server on Ubuntu Server won't forward smtp requests from my AlertMail ILO management console, however there is no problem to send email from Ubuntu terminal using mail -s command. I spend few days browsing documentation of Postfix but no luck. Here is my Postfix config:

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

# See http://www.postfix.org/COMPATIBILITY_README.html -- default to 2 on
# fresh installs.
compatibility_level = 2

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_un$
myhostname = captains.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = $myhostname localhost.$mydomain localhost $mydomain
relayhost =
mynetworks = 192.168.1.20/24 "my server ILO ip address", 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all
```

Here is my server configuration:
[ATTACH=CONFIG]277382[/ATTACH]

I have to mention that recently I had smtp server on Windows 2012 and this server feature work with no problem. Thanks for any help.

---

### Post by darkod on 2017-11-02
I'm not sure if there is any difference between 192.168.1.20/24 and simply 192.168.1.20 in mynetworks. When it is single IP I would use only the IP without the /24. Or if you prefer using it, use the subnet notation properly which is 192.168.1.0/24.

Try something like that and restart postfix.

Also, check the /var/log/mail.log on the ubuntu server, it would have a reason for refusing to relay the message usually.

---

### Post by bonaventure on 2017-11-03
Thanks for help, mail.log gives me the answer :) it turned up that I had accidentially deleted domain name from ILO dedicated interface (not the AlertMail) and the domain wasn't recognised by postfix. Again, thank you

---

### Post by darkod on 2017-11-03
Glad it helped. You can mark the thread as solved in Thread Tools above the first post. :)

---

