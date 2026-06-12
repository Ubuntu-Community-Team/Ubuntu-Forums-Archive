---
title: "postfix smtp server don't deliver mails to hotmail"
date: 2011-09-22
forum: Server Platforms
---

### Post by vwg2 on 2011-09-22
Hi all,

I like to send mails from my Ubuntu server. So, I installed Postfix, Dovecot and Squirrelmail.

After this, it's very easy to send and mails by using the Squirrel webmail application. It works great but mails that are send to my hotmail, will never be delivered.

mails to other mailadresses wil work great.

I think i need to fill in the relayhost in /etc/postfix/main.cf but I don't know what. 

Please, who can help me?

Jan Bot

/etc/postfix/main.cf

```
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

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

myhostname = mail.botelec.nl
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = botelec.nl, mail.botelec.nl, localhost.botelec.nl, localhost
#relayhost = 
mynetworks = 127.0.0.0/8,192.168.1.0/24
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
home_mailbox = Maildir/

```

---

### Post by elico on 2011-09-22
show us the logs output of 
/var/log/mail.log

---

### Post by linux2001 on 2011-09-23
add this line

local_recipient_maps =
in main.cf
and restart postfix

---

