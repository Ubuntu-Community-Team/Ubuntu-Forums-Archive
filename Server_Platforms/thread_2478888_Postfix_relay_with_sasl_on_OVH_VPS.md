---
title: "Postfix relay with sasl on OVH VPS"
date: 2022-09-07
forum: Server Platforms
---

### Post by wikawikawika on 2022-09-07
Dear all,

  I want to use Postfix as relay on a OVH server, and nothing works as I would expect (it's my first install of Postfix however)
  On the server, I have a single user called "ubuntu", and the domain is wika.ovh

  From the server, if I do :
```

echo "test" | mail -s "Subject" ubuntu@mailhost.wika.ovh

```
I get in /var/log/mail.log :
```

Sep  7 19:43:46 wika postfix/pickup[2930]: 7B4BF89A0B: uid=1000 from=<ubuntu@wika.ovh>
Sep  7 19:43:46 wika postfix/cleanup[3978]: 7B4BF89A0B: message-id=<20220907194346.7B4BF89A0B@mailhost.wika.ovh>
Sep  7 19:43:46 wika postfix/qmgr[2931]: 7B4BF89A0B: from=<ubuntu@wika.ovh>, size=342, nrcpt=1 (queue active)
Sep  7 19:43:47 wika postfix/smtp[3980]: 7B4BF89A0B: to=<ubuntu@mailhost.wika.ovh>, relay=ssl0.ovh.net[193.70.18.144]:25, delay=0.59, delays=0.02/0.01/0.34/0.22, dsn=2.0.0, status=sent (250 2.0.0 Ok: queued as DDF542E4FDA2A)
Sep  7 19:43:47 wika postfix/qmgr[2931]: 7B4BF89A0B: removed
Sep  7 19:43:47 wika postfix/smtpd[3981]: connect from 3.mo550.mail-out.ovh.net[46.105.60.232]
Sep  7 19:43:47 wika postfix/smtpd[3981]: NOQUEUE: reject: RCPT from 3.mo550.mail-out.ovh.net[46.105.60.232]: 454 4.7.1 <ubuntu@mailhost.wika.ovh>: Relay access denied; from=<ubuntu@wika.ovh> to=<ubuntu@mailhost.wika.ovh> proto=ESMTP helo=<3.mo550.mail-out.ovh.net>
Sep  7 19:43:47 wika postfix/smtpd[3981]: disconnect from 3.mo550.mail-out.ovh.net[46.105.60.232] ehlo=2 starttls=1 mail=1 rcpt=0/1 data=0/1 rset=1 quit=1 commands=6/8

```

So the error is "Relay access denied".

Here is a sum of my configuration file :
```

ubuntu@wika:~$ postconf -n
alias_database = hash:/etc/aliases
alias_maps = hash:/etc/aliases
append_dot_mydomain = no
biff = no
compatibility_level = 3.6
inet_interfaces = all
inet_protocols = all
mailbox_size_limit = 0
mydestination =
mydomain = wika.ovh
myhostname = mailhost.wika.ovh
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
myorigin = wika.ovh
readme_directory = no
recipient_delimiter = +
relayhost = ssl0.ovh.net
smtp_sasl_auth_enable = yes
smtp_sasl_mechanism_filter = login, plain
smtp_sasl_password_maps = hash:/etc/postfix/sasl/passwd
smtp_sasl_security_options = noanonymous
smtp_sasl_tls_security_options = noanonymous
smtp_tls_CApath = /etc/ssl/certs
smtp_tls_note_starttls_offer = yes
smtp_tls_security_level = may
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtp_use_tls = yes
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
smtpd_relay_restrictions = permit_mynetworks permit_sasl_authenticated defer_unauth_destination
smtpd_sasl_auth_enable = yes
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_security_level = may

```

where ssl0.ovh.net seems to be the official OVH smtp servern and  /etc/postfix/sasl/passwd contains :
```
ssl0.ovh.net    [EMAIL="mailer@wika.ovh"]mailer@wika.ovh[/EMAIL]:xxxxxx
```

where [EMAIL="mailer@wika.ovh"]mailer@wika.ovh[/EMAIL] with the pass is a valid mail user for OVH (tested with their Roundcube interface)

The DNS contains the following entries about mail :

[TABLE="class: table table-hover"]
[TR]
[TD="class: text-center"][/TD]
[TD="class: word-break"]                                         wika.ovh.[/TD]
[TD="class: text-center"]0[/TD]
[TD="class: text-center"]MX[/TD]
[TD="class: word-break"]                                         10 mailhost.wika.ovh.[/TD]
[TD="class: text-right"][/TD]
[/TR]
[TR]
[TD="class: text-right"][/TD]
[/TR]
[TR]
[TD="class: text-center"][/TD]
[TD="class: word-break"]                                         wika.ovh.[/TD]
[TD="class: text-center"]0[/TD]
[TD="class: text-center"]A[/TD]
[TD="class: word-break"]                                         51.77.194.141[/TD]
[TD="class: text-right"][/TD]
[/TR]
[TR]
[TD="class: text-right"][/TD]
[/TR]
[TR]
[TD="class: text-center"][/TD]
[TD="class: word-break"]                                         mailhost.wika.ovh.[/TD]
[TD="class: text-center"]0[/TD]
[TD="class: text-center"]A[/TD]
[TD="class: word-break"]                                         51.77.194.141[/TD]
[/TR]
[/TABLE]

So I do not understand. Can someone help ?

Regards,
   Mike

---

