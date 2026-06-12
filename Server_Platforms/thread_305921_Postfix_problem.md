---
title: "Postfix problem"
date: 2006-11-24
forum: Server Platforms
---

### Post by random_mike on 2006-11-24
I have a mailserver up and running using Postfix.
I just want to use my server to send mail nothing else.

I followed this guide to add SMTP-Auth with TLS:

[https://help.ubuntu.com/6.10/ubuntu/serverguide/C/email-services.html](https://help.ubuntu.com/6.10/ubuntu/serverguide/C/email-services.html)

I can't send mail with server, i get this in /var/log/mail.log

Nov 24 11:34:46 EXAMPLE postfix/smtpd[8591]: connect from unknown[192.168.x.x]
Nov 24 11:34:46 EXAMPLE postfix/smtpd[8591]: setting up TLS connection from unknown[192.168.x.x]
Nov 24 11:34:46 EXAMPLE postfix/smtpd[8591]: TLS connection established from unknown[192.168.x.x]: TLSv1 with cipher RC4-MD5 (128/128 bits)
Nov 24 11:34:50 EXAMPLE postfix/smtpd[8591]: warning: SASL authentication failure: cannot connect to saslauthd server: No such file or directory
Nov 24 11:34:50 EXAMPLE postfix/smtpd[8591]: warning: unknown[192.168.x.x]: SASL LOGIN authentication failed
Nov 24 11:34:54 EXAMPLE postfix/smtpd[8591]: disconnect from unknown[192.168.x.x]

Don't know what to do next.](*,)

---

### Post by random_mike on 2006-11-25
It works now.

I did a fresh install. Ubuntu Server 6.10.
Before I ran 6.06 LTS.

---

