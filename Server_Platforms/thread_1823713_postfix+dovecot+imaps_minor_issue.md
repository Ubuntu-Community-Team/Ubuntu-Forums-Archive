---
title: "postfix+dovecot+imaps minor issue"
date: 2011-08-12
forum: Server Platforms
---

### Post by kylegio on 2011-08-12
pretty simple problem, just can't get it to work

i am running postfix, dovecot

in dovecot the only acceptable protocol is imaps

sending emails works 100%
recieving emails is where the trouble crops up. lets say i have a user (lets call them "user") and my domain is "example.com"

i send an email to [email]user@example.com[/email]

user now logs in using imap/ssl and checks their email, they never get the email.

i think there is a miscommunication between where the emails are being saved and where they are being checked.

dovecot.conf has the following settings

```
protocols = imaps
mail_location = maildir:~/Maildir
ssl_cert_file = /etc/ssl/certs/dovecot.pem
ssl_key_file = /etc/ssl/private/dovecot.key
```

postfix/main.cf has teh following settings
```
smtpd_banner = $myhostname ESMTP $mail_name
biff = no
append_dot_mydomain = no
readme_directory = no
# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
myhostname = ********
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = *******, localhost
relayhost =
mynetworks =
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
home_mailbox = Maildir/
mynetworks_style = host
```

interesting part: if i log in via ssh, then issue the "mail" command i get the following
```
"/var/mail/user": 25 messages 12 unread

```'
the emails listed are the ones im expecting, but they are still in /var/mail/user?! 


any help apprciated, thanks!

---

### Post by kylegio on 2011-08-12
some more information that might be useful:
```
$sudo postconf | grep -E "spool|home"
forward_path = $home/.forward${recipient_delimiter}${extension}, $home/.forward
home_mailbox = Maildir/
mail_spool_directory = /var/mail
queue_directory = /var/spool/postfix
require_home_directory = no

```

---

