---
title: "Postfix: Delay in receiving emails."
date: 2016-01-05
forum: Server Platforms
---

### Post by super1395 on 2016-01-05
I have a Postfix server setup on Ubuntu 15.04. I'm trying to send emails from my server to my GMail account for server notifications. 
I used Webmin to install Postfix, all of the configuration files are default, except for setting a relay host through Comcast.

So here's the problem. I can send and emails out successfully but on average it takes about two minutes to hit my GMail account. I have another server with, from what I can tell, Identical configurations that send emails to my GMail instantly. So I'll send an email out at 7:48pm but it wont be in my GMail inbox until 7:50pm. What could be causing this delay between sending it out and getting to my GMail? 

```
Jan  5 19:48:43 [hostname]postfix/qmgr[338]: 5842B3806CC: from=<#####@[hostname]>, size=797, nrcpt=1 (queue active)
Jan  5 19:48:43 [hostname] postfix/smtp[486]: 5842B3806CC: to=<#####@gmail.com>, relay=smtp.comcast.net[96.114.157.81]:587, delay=0.6, delays=0.07/0.01/0.21/0.31, dsn=2.0.0, status=sent (250 2.0.0 2Soj1s00A3tUXk301SojQk mail accepted for delivery)
Jan  5 19:48:43 [hostname]postfix/qmgr[338]: 5842B3806CC: removed
```

---

### Post by SeijiSensei on 2016-01-06
Looks to me like Comcast is the guilty party.  

> relay=smtp.comcast.net[96.114.157.81]:587, delay=0.6, delays=0.07/0.01/0.21/0.31

Can you connect to gmail on port 587?  I know Comcast blocks port 25.  Try using "telnet gmail-smtp-in.l.google.com 587" from the command prompt and see if you get a reply.

---

### Post by super1395 on 2016-01-06
telnet gmail-smtp-in.l.google.com 587 returned:
```
Trying 74.125.127.26...
Trying 2607:f8b0:4003:c07::1a...
telnet: Unable to connect to remote host: Network is unreachable

```

Whats strange is, I have another Comcast box that uses them as a relay(same credentials and everything), with no delay, but it returned the same error as above.
> [COLOR=#000000]*relay=smtp.comcast.net[96.114.157.81]:587*[/COLOR]

---

