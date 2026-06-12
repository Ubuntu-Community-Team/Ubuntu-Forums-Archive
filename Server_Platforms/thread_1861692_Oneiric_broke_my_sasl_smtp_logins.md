---
title: "Oneiric broke my sasl smtp logins"
date: 2011-10-15
forum: Server Platforms
---

### Post by emunson on 2011-10-15
I just updated my mail server and now I cannot send mail.  This was working under natty.  For server setup I followed this guide to the letter: [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

I have re-enabled all the logging on the system and when I attempt to adjust the outgoing settings on my phone (because it complains about them) I see this in the auth.log on the server
```
Oct 15 22:08:38 server postfix/smtpd[4930]: sql auxprop plugin using mysql engine
```

So I moved over to try and test login by hand
```
EHLO client.domain.com
250-server.localdomain
250-PIPELINING
250-SIZE 10240000
250-ETRN
250-AUTH PLAIN LOGIN CRAM-MD5 DIGEST-MD5
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
AUTH PLAIN SomeLongEncryptedString
535 5.7.8 Error: authentication failed: no mechanism available  
```
But the entry doesn't show in the auth.log for this.  Also, I have enabled mysql logging and nothing ever shows there about a login attempt (it would normally select the users credentials to verify.

Any help or suggestions would be greatly appreciated, I need outgoing mail back.

---

### Post by lisati on 2011-10-16
Closed at [request]("http://ubuntuforums.org/showpost.php?p=11350349&postcount=3") of OP

---

