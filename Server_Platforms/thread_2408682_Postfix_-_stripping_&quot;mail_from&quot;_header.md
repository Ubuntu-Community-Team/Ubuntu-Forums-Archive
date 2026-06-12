---
title: "Postfix - stripping &quot;mail from&quot; header"
date: 2018-12-21
forum: Server Platforms
---

### Post by jmonroe6 on 2018-12-21
When sending and receiving emails directly from the server everything works as expected.

When connecting to the server remotely I can still send and receive email. For some reason the "mail from" header is being removed, yet the message still lands in the inbox. Is there a protection mechanism someone can point me to that would make this happen?

main.cf file below.

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


# See [http://www.postfix.org/COMPATIBILITY_README.html](http://www.postfix.org/COMPATIBILITY_README.html) -- default to 2 on
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


smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = fa6d3469418c
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = $myhostname, mamailer, fa6d3469418c, localhost.localdomain, localhost
relayhost = 
mynetworks = all, 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all

---

