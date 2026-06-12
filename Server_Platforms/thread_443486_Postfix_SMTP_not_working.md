---
title: "Postfix SMTP not working"
date: 2007-05-14
forum: Server Platforms
---

### Post by Naatan on 2007-05-14
Hi, I have configured postfix on my ubuntu server but I can't seem to use postfix to send mail.

I have configured the SMTP server in thunderbird and now when I send an e-mail it says connecting, then connected and then just stays like that just to time out a bit later.

When I telnet to the mail server and send a mail there it does seem to arrive.

My main.cf looks like this:

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

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/ssl/smtpd.crt
smtpd_tls_key_file = /etc/postfix/ssl/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = mail.naatan.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mail.naatan.com, naatan.com, localhost.localdomain, localhost
relayhost =
#mynetworks_style = subnet
mynetworks = 127.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
home_mailbox = Maildir/
mailbox_command =
inet_protocols = ipv4
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_CAfile = /etc/postfix/ssl/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
```

I have no idea what could be causing this timeout, when I left from work it returned only I was getting a relay error, well at least I can work with that, but now it just gives a timeout.

Does anyone know what's wrong?

---

### Post by MJN on 2007-05-14
Try running **tail -f /var/log/mail.log** whilst your Thunderbird client connects and see at what stage it sits hanging. Better still add **-v** to the end of the **smtp .... smtpd** line in **/etc/postfix/master.cf**, restart Postfix and then do the above... prepare for plenty more logging action! (hence remove the -v afterwards).

Mathew

---

