---
title: "mail server troubles... again"
date: 2009-12-26
forum: Server Platforms
---

### Post by onehitxzibit on 2009-12-26
I am trying to create my own mail server using the guide provided in the ubuntu server official documentation. 

In the Testing section of the documentation it says that when I do "telnet mail.example.com 25" and "ehlo mail.example.com" (I used my own address in stead of mail.example.com of course :D ) everything should be fine if I see these lines in the list that appears. - 

> 250-STARTTLS
250-AUTH LOGIN PLAIN
250-AUTH=LOGIN PLAIN
250 8BITMIME



The problem is that I don't see 250-AUTH LOGIN PLAIN and 250-AUTH=LOGIN PLAIN. How do I fix that?

---

### Post by noway2 on 2009-12-26
It has to do with the configurations for smtpd_sasl settings and smtpd_recipient restrictions.  There will also be a corresponding section in your pop/imap server (such as Dovecot).

Google the terms: "postfix plain authentication" without the quotes and you will get some good examples explaining the postfix commands that need to be setup.  I thought that the one at postfix.state-of-mind.de was pretty informative.

---

### Post by onehitxzibit on 2009-12-28
Hello noway2, 
I reinstalled everything because I have screwed up the SMTP authentication in my last install and now it works fine. But there's another problem - in the mail.err I get 

> Dec 28 22:08:45 test dovecot: Fatal: pop3-login: Can't load private key file /etc/ssl/private/server.key: error:0B080074:x509 certificate routines:X509_check_private_key:key values mismatch
Dec 28 22:08:45 test dovecot: Temporary failure in creating login processes, slowing down for now
Dec 28 22:08:45 test dovecot: Fatal: pop3-login: Can't load private key file /etc/ssl/private/server.key: error:0B080074:x509 certificate routines:X509_check_private_key:key values mismatch
Dec 28 22:08:45 test dovecot: Fatal: pop3-login: Can't load private key file /etc/ssl/private/server.key: error:0B080074:x509 certificate routines:X509_check_private_key:key values mismatch
Dec 28 22:10:01 test dovecot: last message repeated 3 times
Dec 28 22:11:01 test dovecot: last message repeated 3 times
Dec 28 22:12:01 test dovecot: last message repeated 3 times
Dec 28 22:12:45 test dovecot: Fatal: pop3-login: Can't load private key file /etc/ssl/private/server.key: error:0B080074:x509 certificate routines:X509_check_private_key:key values mismatch
Dec 28 22:12:45 test dovecot: child 1454 (login) returned error 89 (Fatal failure)
Dec 28 22:12:45 test dovecot: Fatal: pop3-login: Can't load private key file /etc/ssl/private/server.key: error:0B080074:x509 certificate routines:X509_check_private_key:key values mismatch
Dec 28 22:14:02 test dovecot: last message repeated 4 times
Dec 28 22:14:45 test dovecot: Fatal: pop3-login: Can't load private key file /etc/ssl/private/server.key: error:0B080074:x509 certificate routines:X509_check_private_key:key values mismatch
Dec 28 22:14:45 test dovecot: child 1462 (login) returned error 89 (Fatal failure)
Dec 28 22:14:45 test dovecot: Fatal: pop3-login: Can't load private key file /etc/ssl/private/server.key: error:0B080074:x509 certificate routines:X509_check_private_key:key values mismatch

I am pretty sure that the keys are fine.

Is it a good idea to create a mail server without SSL?

---

### Post by noway2 on 2009-12-28
Hmmm, not sure what went wrong with the key files.  Try recreating the keys and importing them into postfix / dovecot and see if the error goes away.  Follow the steps in the how to carefully.

Personally, I wouldn't run a public email server without SSL.  Without it, anybody with a tap anywhere along the line can pick off the packets and get the information necessary to authenticate with your server.  This would enable them to both spoof emails as you and potentially turn your system into an open relay.

---

### Post by onehitxzibit on 2009-12-29
Ok, I finally got it up and running. Connected to the server using Thunderbird and tried to send an e-mail. No errors appear and everything seems to be fine except the fact that the mail isn't actually sent. :\

Here's the mail.info log - 
> Dec 29 17:03:56 test postfix/smtp[1287]: connect to gmail-smtp-in.l.google.com[209.85.218.11]:25: Connection timed out
Dec 29 17:04:05 test postfix/smtp[1352]: connect to pmx.abv.bg[194.153.145.27]:25: Connection timed out
Dec 29 17:04:26 test postfix/smtp[1287]: connect to alt1.gmail-smtp-in.l.google.com[209.85.223.14]:25: Connection timed out
Dec 29 17:04:35 test postfix/smtp[1352]: connect to pmx.abv.bg[194.153.145.69]:25: Connection timed out

Looks like it isn't able to connect to the other SMTP servers. Any ideas?

**EDIT: Never mind this post. I've figured it out and now it works perfect! :) Thx for the help mate!**

---

### Post by StrangeWill on 2009-12-29
hah nevermind

---

