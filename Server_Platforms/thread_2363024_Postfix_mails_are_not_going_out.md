---
title: "Postfix mails are not going out"
date: 2017-06-05
forum: Server Platforms
---

### Post by info24 on 2017-06-05
Hi,

I've been having some propblems with my postfix configuration and I hop you guys could help me out.

I have my postfix configured to use the google gmail service as a relay. Everytime I send a mail out to any address it keeps returning with "undeliverable". I've also tried to set it up to directly deliver the mails to the destination, but that didn't work either.


I have a few warnings in my log files, I used to have some error but I've managed to get rid of those.

My configuration file (main.cf)
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
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
myhostname = ******.ovh.net
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = ******.ovh.net, localhost.ovh.net, , localhost
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
smtpd_recipient_restrictions = permit_inet_interfaces


relayhost = [smtp.gmail.com]:587
smtp_use_tls = yes
smtp_sasl_auth_enable = yes
smtp_sasl_security_options =
smtp_sasl_password_maps = hash:/etc/postfix/sasl_passwd
smtp_tls_CAfile = /etc/postfix/ssl/postfix.pem
```

Current Mail Queue
```
root@*******:/etc/postfix# mailq
-Queue ID- --Size-- ----Arrival Time---- -Sender/Recipient-------
934E313601FE      470 Mon Jun  5 14:50:57  www-data@*******.ovh.net
            (local data error while talking to smtp.gmail.com[74.125.206.109])
                                         me@*********ot.com

-- 0 Kbytes in 1 Request.
```


My log file:
```
Jun  5 15:19:13 vps******* postfix/qmgr[14108]: 934E313601FE: from=<www-data@*******.ovh.net>, size=470, nrcpt=1 (queue active)
Jun  5 15:19:13 vps******* postfix/smtp[14426]: error: open database /etc/postfix/sasl_passwd.db: Invalid argument
Jun  5 15:19:13 vps******* postfix/smtp[14426]: warning: hash:/etc/postfix/sasl_passwd is unavailable. open database /etc/postfix/sasl_passwd.db: Invalid argument
Jun  5 15:19:13 vps******* postfix/smtp[14426]: warning: hash:/etc/postfix/sasl_passwd lookup error for "smtp.gmail.com"
Jun  5 15:19:13 vps******* postfix/smtp[14426]: warning: 934E313601FE: smtp_sasl_passwd lookup error
Jun  5 15:19:13 vps******* postfix/smtp[14426]: 934E313601FE: local data error while talking to smtp.gmail.com[64.233.166.109]
Jun  5 15:19:13 vps******* postfix/smtp[14426]: warning: hash:/etc/postfix/sasl_passwd is unavailable. open database /etc/postfix/sasl_passwd.db: Invalid argument
Jun  5 15:19:13 vps******* postfix/smtp[14426]: warning: hash:/etc/postfix/sasl_passwd lookup error for "smtp.gmail.com"
Jun  5 15:19:13 vps******* postfix/smtp[14426]: warning: 934E313601FE: smtp_sasl_passwd lookup error
Jun  5 15:19:13 vps******* postfix/smtp[14426]: 934E313601FE: local data error while talking to smtp.gmail.com[2a00:1450:400c:c06::6d]
Jun  5 15:19:13 vps******* postfix/smtp[14426]: warning: hash:/etc/postfix/sasl_passwd is unavailable. open database /etc/postfix/sasl_passwd.db: Invalid argument
Jun  5 15:19:13 vps******* postfix/smtp[14426]: warning: hash:/etc/postfix/sasl_passwd lookup error for "smtp.gmail.com"
Jun  5 15:19:13 vps******* postfix/smtp[14426]: warning: 934E313601FE: smtp_sasl_passwd lookup error
Jun  5 15:19:13 vps******* postfix/smtp[14426]: 934E313601FE: to=<me@*********ot.com>, relay=smtp.gmail.com[64.233.166.108]:587, delay=1696, delays=1696/0.02/0.71/0, dsn=4.3.0, status=deferred (local data error while talking to smtp.gmail.com[64.233.166.108])
```

Contents of sasl_passwd
```
root@vps105385:/etc/postfix# cat sasl_passwd
[smtp.gmail.com]:587    ************@gmail.com:*******************************
```

I also had to create a SSL certificate:
```
root@vps******:/etc/postfix/ssl# ls -l
total 20
-rwxr-xr-x 1 root    root  312 Jun  5 14:47 make_rsa_key.sh
-rw-r--r-- 1 root    root  745 Jun  5 14:42 postfix.crt
-rw-r--r-- 1 root    root  599 Jun  5 14:40 postfix.csr
-rw------- 1 root    root  887 Jun  5 14:38 postfix.key
-rw------- 1 postfix root 1632 Jun  5 14:43 postfix.pem
```


I have no Idea what to do next.    Mails are being sent from a web application. I'm guessing that it never really worked properly.

Thanks for the help.

---

### Post by darkod on 2017-06-05
By default postfix can send email correctly if I'm not mistaken. So sending should work without much changes in the original config. If you want it to send directly I suggest you restore a copy of the original main.cf and try again.

On the other hand, if you insist making it work with gmail, that is little different because gmail has to actually accept the emails sent by your postfix. You need to go carefully through gmail documentation about necessary configuration changes, and also search for tutorials online explaining how to perform the config changes you need.

---

### Post by SeijiSensei on 2017-06-06
If your server is on a residential connection, your ISP may be blocking outbound SMTP traffic.  Run the test I describe here and report back:  [https://ubuntuforums.org/showthread.php?t=2345911&p=13580639&viewfull=1#post13580639](https://ubuntuforums.org/showthread.php?t=2345911&p=13580639&viewfull=1#post13580639)

> Jun  5 15:19:13 vps******* postfix/smtp[14426]: warning: hash:/etc/postfix/sasl_passwd is unavailable. open database /etc/postfix/sasl_passwd.db: Invalid argument

Also, did you create the SASL password database?  Those errors suggest Postfix cannot find sasl_passwd.db.

---

