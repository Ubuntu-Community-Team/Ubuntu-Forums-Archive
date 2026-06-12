---
title: "Postfix Help"
date: 2010-08-11
forum: Server Platforms
---

### Post by Superfreek on 2010-08-11
I had postfix running fine before. But have encountered issues lately.

So i sent a test email from gmail to my server and this is the output

Aug 11 22:15:23 elephant postfix/smtpd[15433]: connect from mail-fx0-f50.google.com[209.85.161.50]
Aug 11 22:15:23 elephant postfix/smtpd[15433]: 728FCEACA10: client=mail-fx0-f50.google.com[209.85.161.50]
Aug 11 22:15:23 elephant postfix/cleanup[15438]: 728FCEACA10: message-id=<AANLkTik7Kqe=C3hixFi_iRgCrS=CvkpX+eCjX-5h1Gm5@mail.gmail.com>
Aug 11 22:15:23 elephant postfix/qmgr[15430]: 728FCEACA10: from=<my.email@gmail.com>, size=1872, nrcpt=1 (queue active)
Aug 11 22:15:23 elephant postfix/cleanup[15438]: A3C2DEACA34: message-id=<AANLkTik7Kqe=C3hixFi_iRgCrS=CvkpX+eCjX-5h1Gm5@mail.gmail.com>
Aug 11 22:15:23 elephant postfix/local[15439]: 728FCEACA10: to=<user.domain@elephant.serverffs.com>, orig_to=<user@domain.com>, relay=local, delay=0.3, delays=0.29/0/0/0, dsn=2.0.0, status=sent (forwarded as A3C2DEACA34)
Aug 11 22:15:23 elephant postfix/qmgr[15430]: A3C2DEACA34: from=<my.email@gmail.com>, size=2035, nrcpt=1 (queue active)
Aug 11 22:15:23 elephant postfix/qmgr[15430]: 728FCEACA10: removed
Aug 11 22:15:25 elephant postfix/smtp[15440]: A3C2DEACA34: to=<my.email@gmail.com>, orig_to=<user@domain.com>, relay=gmail-smtp-in.l.google.com[74.125.91.27]:25, delay=1.6, delays=0/0/0.06/1.5, dsn=2.0.0, status=sent (250 2.0.0 OK 1281550525 s11si877254qcp.151)
Aug 11 22:15:25 elephant postfix/qmgr[15430]: A3C2DEACA34: removed

It doesnt show up in the users inbox

here is my postconf -n

alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
broken_sasl_auth_clients = yes
config_directory = /etc/postfix
home_mailbox = Maildir/
mailbox_command = /usr/bin/procmail-wrapper -o -a $DOMAIN -d $LOGNAME
mailbox_size_limit = 0
message_size_limit = 20480000
mydestination = localhost, mail.domain.com, $mydomain, $myhostname
readme_directory = no
recipient_delimiter = +
sender_bcc_maps = hash:/etc/postfix/bcc
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_recipient_restrictions = permit_mynetworks permit_sasl_authenticated reject_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
swap_bangpath = no
virtual_alias_maps = hash:/etc/postfix/virtual

**note: all real domain names are replaced with 'domain'

Also I am using webmin, and my users cant sign in through webmail.domain.com

they get this output error:

Failed to create /home/domain.com/homes/user/.usermin : Permission denied

all permissions on their user directory are fine.


Can anyone help out?

Or atleast point me in the right direction as where i should post this?

Thanks

---

