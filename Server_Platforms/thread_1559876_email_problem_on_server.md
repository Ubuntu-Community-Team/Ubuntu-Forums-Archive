---
title: "email problem on server"
date: 2010-08-24
forum: Server Platforms
---

### Post by ianmorris1960 on 2010-08-24
Hi,

I am a little inexperienced so be gentle with me!

I have an ubuntu server providing email/web proxy/ftp for our business, and since a recent upgrade there are problems with email.

The OS is 8.04.1, I am using postfix as MTA, the server name is 'server2' user names are in a simple form e.g. mine is 'ian'

When I send an email from my client PC there is no problem, a fully formed email address is sent e.g. ian [ at} peakpress.co.uk and the email is delivered, however when the server creates the email, e.g. webmin backup, it only send the email to ian@server2 the email then sits in the postfix queue.

The server cannot be named peakpress.co.uk as this already exists, and I collect mail from it using fetchmail.

This problem only arose after an upgrade, but I have no way of going back to the state where it was working ;(

This becomes an issue in two situations, firstly when a user sets an out of office in usermin and asks for ,ail to be delivered to thier own mailbox - it ends up lost in the postfix Q, and secondly system generated emails land in the postfix q.

Any suggestions

---

### Post by paulisdead on 2010-08-24
what do you see in /var/log/mail.log when this happens?  Also, what are the reasons in mailq for it not being delivered?

---

### Post by ianmorris1960 on 2010-08-24
Hi, thanks for the reply,

The service is working normally for example if I send an email to [email]fred@bbc.co.uk[/email], then it appears in postfix Q and then dissapears - normal behavior.

However if the system 'generates' an email such as the 'deliver to my box' in usermin, or root executes a cron job, and it needs to send an email, then this is sent to an address such as 'ian@server2'.

Each time a message gets stuck in postfix, it has just the username@server_name e.g. ian@server2

it as if postfix? does not know how to deliver to a local mailbox, or does not recognise server2 as the local (i.e. me) server.

I have not looked in the log, as I think the posfix q has the answer!

Is there a way to tell 'the system' what is local, and not to be fussy just deliver it, or better a way to tell it what the default domain is for local users - without changing the server name?

thanks Ian

---

### Post by ianmorris1960 on 2010-08-24
just caused the system to put such a message into the postfix Q,

ran a cron job - it starts and stops HAVP (web proxy) and this currently is winging about clamav being out of date, so root sends an email to root to tell it!

These emails were arriving in the root user mail box, but now just hang in pF Q.

Ian

---

### Post by Bachstelze on 2010-08-24
You need 

```
myorigin = peakpress.co.uk
```

In your main.cf.

[http://www.postfix.org/postconf.5.html#myorigin](http://www.postfix.org/postconf.5.html#myorigin)

Though normally you would set that in mydomain, and give your server a hostname like mail.peakpress.co.uk.

---

### Post by ianmorris1960 on 2010-08-24
Bonjour & salut,

Problem sorted!

thank you

Ian

---

