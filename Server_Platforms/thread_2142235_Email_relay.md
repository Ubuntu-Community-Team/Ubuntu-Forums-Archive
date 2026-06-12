---
title: "Email relay"
date: 2013-05-05
forum: Server Platforms
---

### Post by spyros71 on 2013-05-05
I am running a site on an external web server with a static IP address and domain name (xxxxx.gr). On this server I have the possibility of setting up email accounts. The server does have POP and IMAP capabilities.

I have also set up a computer to act as a home server. 
I have installed Ubuntu 12.10 sevrer with a non static public IP (and I must say everything is working fine).

Now the question is if it is possible to set up the  home server as a mail server but use the wwwww.gr domain and email accounts for traficing the emails for my local users.
So the idea is that I store and handle emails locally using email accounts of the form [email]user@xxxxxx.gr[/email].

I did some reading on my own and I come up with the term email relay. But Is it possible to relay emails for all users?

Can some one point me to a step by step how-to?

Thank you in advance for the help,
Spyros

---

### Post by lisati on 2013-05-05
*Thread moved to **Server Platforms**.*

An email relay accepts email and passes it on to another server. This might not be what you need for incoming mail, but certainly can be done for outgoing mail. 

If you're using Postfix as your MTA, you can tell it to forward all outgoing email via another server. One option is the [relayhost](http://www.postfix.org/postconf.5.html#relayhost) option in its main.cf file.

---

### Post by SeijiSensei on 2013-05-05
Yes, I do exactly this, though I use sendmail.  Mail for two of my domains is forwarded to my home server for local delivery, while mail for other domains is placed in mailboxes on the server itself.

In sendmail, I use a "[mailertable]("http://www.sendmail.com/sm/open_source/docs/m4/mailertables.html")" to route mail to different locations depending on the domain name.  I presume Postfix has a similar facility, but my knowlege of that program is rudimentary at best.  The mailertable has a pretty easy syntax:
```

example.com         relay:[mail.example.com]
domain.name         relay:[10.10.10.10]

```

That routes mail for "example.com" to mail.example.com for further processing and delivery.  Mail for "domain.name" is sent to a server identified solely by its IP address.  The square brackets around the addresses are mandatory; see the linked document for details.

---

