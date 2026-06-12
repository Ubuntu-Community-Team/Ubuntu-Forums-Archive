---
title: "postfix tls issue: Relay access denied"
date: 2009-06-03
forum: Server Platforms
---

### Post by supremedalek on 2009-06-03
I am testing a mail server (postfix+dovecot with openssl and tls). I test it out by connecting from vogon.local.thespider.com, which is a local machine in thespider.com LAN. I've setup postfix to give me a bit of info on the TLS transaction and tried to send an email using smtp with tls with this mail server:

```
Jun  2 16:12:58 mail postfix/smtpd[22933]: connect from boris.thespider.com[192.168.1.12]
Jun  2 16:12:58 mail postfix/smtpd[22933]: setting up TLS connection from boris.thespider.com[192.168.1.12]
Jun  2 16:12:58 mail postfix/smtpd[22933]: boris.thespider.com[192.168.1.12]: TLS cipher list "ALL:+RC4:@STRENGTH"
Jun  2 16:12:58 mail postfix/smtpd[22933]: SSL_accept:before/accept initialization
Jun  2 16:12:58 mail postfix/smtpd[22933]: SSL_accept:SSLv3 read client hello B
Jun  2 16:12:58 mail postfix/smtpd[22933]: SSL_accept:SSLv3 write server hello A
Jun  2 16:12:58 mail postfix/smtpd[22933]: SSL_accept:SSLv3 write certificate A
Jun  2 16:12:58 mail postfix/smtpd[22933]: SSL_accept:SSLv3 write key exchange A
Jun  2 16:12:58 mail postfix/smtpd[22933]: SSL_accept:SSLv3 write server done A
Jun  2 16:12:58 mail postfix/smtpd[22933]: SSL_accept:SSLv3 flush data
Jun  2 16:12:58 mail postfix/smtpd[22933]: SSL_accept:SSLv3 read client key exchange A
Jun  2 16:12:58 mail postfix/smtpd[22933]: SSL_accept:SSLv3 read finished A
Jun  2 16:12:58 mail postfix/smtpd[22933]: SSL_accept:SSLv3 write session ticket A
Jun  2 16:12:58 mail postfix/smtpd[22933]: SSL_accept:SSLv3 write change cipher spec A
Jun  2 16:12:58 mail postfix/smtpd[22933]: SSL_accept:SSLv3 write finished A
Jun  2 16:12:58 mail postfix/smtpd[22933]: SSL_accept:SSLv3 flush data
Jun  2 16:12:58 mail postfix/smtpd[22933]: Anonymous TLS connection established from boris.thespider.com[192.168.1.12]: TLSv1 with cipher DHE-RSA-AES256-SHA (256/256 bits)
Jun  2 16:12:58 mail postfix/smtpd[22933]: NOQUEUE: reject: RCPT from boris.thespider.com[192.168.1.12]: 554 5.7.1 <raub@kudria.com>: Relay access denied; from=<raub@burp.local.thespider.com.> to=<raub@kudria.com> proto=ESMTP helo=<burp.local.thespider.com>
Jun  2 16:12:58 mail postfix/smtpd[22933]: disconnect from boris.thespider.com[192.168.1.12]

```

Two items that confuse me are the Anonymous TLS connection and the relay access denied messages. Why would it be anonymous tls connection message when I try to to do smtp with tls? Could it be that my machine is making a TLS connection to the mail server's submission port without a client certificate?  

What about the relay access denied? I would think that if I could authenticate (which it might as well be I did not do that yet) I should not have this relay message, right? So, did the authentication phase never took place?

---

### Post by HermanAB on 2009-06-03
Howdy,

I don't have an answer for you, sorry.  I gave up with Postfix years ago since it takes too much time to figure these kind of issues out.  So, if you are doing this as a learning exercise, keep hacking, you will eventually get it to work, but if you want a production system that works without all the hassle, try Citadel - you won't look back and you will save a lot of time and money.

---

