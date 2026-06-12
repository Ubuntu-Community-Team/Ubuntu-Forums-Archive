---
title: "Postfix slow to send e-mail"
date: 2011-01-21
forum: Server Platforms
---

### Post by hawk2010 on 2011-01-21
Hi,

I'm on Ubuntu 10.04 and using Postfix 2.7 with Dovecot's SASL. The issue is when sending e-mail it takes a bit of time to send. LIke for it to get connected it takes around 15.20 seconds. How can I reduce this delay so it can be sent faster? 

Regards
Hawk.

---

### Post by SeijiSensei on 2011-01-21
I'd start by checking that the nameservers in /etc/resolv.conf exist and are reachable.  Try running "host [www.google.com](www.google.com) ip.of.a.nameserver" for each of the nameservers in resolv.conf to make sure they're working correctly.  For comparative purposes, use Google's own server at 8.8.8.8 and see how fast that is.

One other test is to pick a domain to which you routinely send mail, then try this:

```

$ host -t mx example.com
example.com mail is handled by 5 mx1.example.com.
example.com mail is handled by 10 mx2.example.com.

$ telnet mx1.example.com 25
[banner appears from remote server]
EHLO my.host.name
[server replies]
MAIL FROM: me@mydomain.com
[server replies]
RCPT TO: you@example.com
[server replies]
DATA
[server replies]
This is a test message.
.
[server confirms receipt of message]
QUIT

```
This is exactly the procedure an SMTP mail transfer agent follows when sending a message.  See if you can discern where the delays are.

(Obviously you need to replace "example.com", "my.host.name" and the "me@" and "you@" addresses with valid entries.)

---

### Post by elico on 2011-01-21
did you check you log file?

it might be some filtering rules..

---

