---
title: "Postfix SMTP"
date: 2011-06-09
forum: Server Platforms
---

### Post by Jay89 on 2011-06-09
Hello, I have an email server setup with postfix and dovecot. They are configured to support SSL/TLS authentication. I can connect to my inbox fine and receive email using Thunderbird. However, SMTP times out connecting to the server if I use port 465 for SSL/TLS. I can send mail using port 25 and no authentication on the outgoing server. Would someone be able to help? I am using Ubuntu-server-10.04 LTS.

Thanks.
Below is what was in my /var/log/mail.log

[B]Jun  9 09:08:42 newmail postfix/master[2723]: terminating on signal 15
Jun  9 09:08:42 newmail postfix/master[2854]: daemon started -- version 2.7.0, configuration /etc/postfix
Jun  9 09:08:47 newmail postfix/master[2854]: reload -- version 2.7.0, configuration /etc/postfix
Jun  9 09:08:50 newmail postfix/master[2854]: terminating on signal 15
Jun  9 09:08:50 newmail postfix/master[2986]: daemon started -- version 2.7.0, configuration /etc/postfix[/B]
**Jun  9 09:08:55 newmail postfix/smtpd[2991]: warning: cannot get RSA private key from file /etc/ssl/private/ssl-cert-snakeoil.key: disabling TLS support**
**Jun  9 09:08:55 newmail postfix/smtpd[2991]: warning: TLS library problem: 2991:error:0B080074509 certificate routines:X509_check_private_key:key values mismatch509_cmp.c:406:**
[B]Jun  9 09:08:55 newmail postfix/smtpd[2991]: connect from user.test.net[10.1.1.142]
Jun  9 09:08:57 newmail postfix/smtpd[2991]: lost connection after UNKNOWN from user.test.net[10.1.1.142]
Jun  9 09:08:57 newmail postfix/smtpd[2991]: disconnect from user.test.net[10.1.1.142]
Jun  9 09:09:06 newmail dovecot: imap-login: Login: user=<fakeuser>, method=PLAIN, rip=10.1.1.142, lip=10.1.0.207, TLS
Jun  9 09:09:07 newmail dovecot: imap-login: Login: user=<fakeclient>, method=PLAIN, rip=10.1.1.142, lip=10.1.0.207, TLS
Jun  9 09:09:21 newmail postfix/smtpd[2991]: connect from user.test.net[10.1.1.142]
Jun  9 09:11:15 newmail postfix/smtpd[2991]: lost connection after UNKNOWN from user.test.net[10.1.1.142]
Jun  9 09:11:15 newmail postfix/smtpd[2991]: disconnect from user.test.net[10.1.1.142][/B]

Not sure what any of those mean, especially the one with the .key file since it *is* in that directory.

---

