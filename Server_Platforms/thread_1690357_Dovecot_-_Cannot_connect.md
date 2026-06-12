---
title: "Dovecot - Cannot connect"
date: 2011-02-18
forum: Server Platforms
---

### Post by Celauran on 2011-02-18
I've had Dovecot up and running for months now without any problems whatsoever.  Came in this morning and suddenly I can't connect to it.  Thunderbird hangs with "Checking mail server capabilities..." and Windows Mail spits out the following error:

```
Cannot establish TLS with IMAP server 10.0.0.2:143, SSL_connect error 336142597

Configuration:
   Account: Blah
   Server: foo
   User name: whatever
   Protocol: IMAP
   Port: 143
   Secure(SSL): 0
   Code: 800cccd9

```

Thing is, I'm not using TLS/SSL and have changed exactly nothing since the server was set up.  I've tried having the mail clients use SSL/TLS in response to the above error, but that changed nothing.  Any ideas?

---

### Post by rudelgurke on 2011-02-18
Sorry if my mind reading is a bit bad these days, still do you looked at /var/log/mail.log what Dovecot logs when a client tries to log in and - if there's nothing useful - please posting the output of "dovecot -n" ?

Thank you

---

