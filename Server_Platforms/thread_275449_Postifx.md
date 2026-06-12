---
title: "Postifx"
date: 2006-10-11
forum: Server Platforms
---

### Post by Compact on 2006-10-11
I've got a webserver which also send mail from php using postfix. The server has example.net as its name. Example.net has also a separate email server. The problem is when server tries to send e-mails to example.net, which is its name, it send it to itself. I want webserver to send emails to the real email server which is not the webserver. The emails that the webserver sends has also appear to come from example.net.

---

### Post by foxylad on 2006-10-11
There is a setting in postfix that tells it what domains to consider "local", and another to tell it what domain sent mail should be sent from. I think adding (or changing) the following in /etc/postfix/main.cf should do the trick:
```
myorigin = example.com
mydestination = localhost

```
If for some reason you want to deliver an email to this machine, just address it to greg@localhost.

Cheers!
Greg.

---

