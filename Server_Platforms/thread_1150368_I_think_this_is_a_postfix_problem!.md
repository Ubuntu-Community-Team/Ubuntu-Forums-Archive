---
title: "I think this is a postfix problem!"
date: 2009-05-06
forum: Server Platforms
---

### Post by nevets_anderson on 2009-05-06
Hi I've been working on building a Lamp based ubuntu server and I've installed bind 9 (which seems to be working ok and giving me a proper domain name MX records etc).

I've also installed Postfix and Dovecot
Dovecot I believe is working correctly using the test mentioned in the server documentation I get

Connected to mail.mydomain_name.com.
Escape character is '^]'.
+OK Dovecot ready.

The Postfix test is how ever giving me this

250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
----------

The documentation recommends it should include 

250-STARTTLS 
250-AUTH LOGIN PLAIN 
250-AUTH=LOGIN PLAIN 
250 8BITMIME 


--------
I can log on and get my mail - but not send, 


Any thoughts about this and what might be going on?

Regards

Nevets
Aka 
Steve

---

### Post by a9k3d on 2009-05-14
It might be your email client. Have you checked postfix port 25 using telnet and a complete conversation?
For example:
```
telnet yourmail.com 25
EHLO your.org
MAIL FROM: you@your.org
RCPT TO: yourself@your.org
DATA&#8232;
Subject: testing&#8232;
this is my test message
.
QUIT

```
Postfix should reply with 200. Otherwise check the error it gives you.

---

