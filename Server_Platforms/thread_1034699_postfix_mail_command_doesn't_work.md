---
title: "postfix mail command doesn't work"
date: 2009-01-08
forum: Server Platforms
---

### Post by DrIdiot on 2009-01-08
Hi,

When sending e-mail using netcat localhost 25, I am able to send e-mail from my server to an external e-mail account.

However, when using the mail command (in mailx), the email can only be sent locally.  If the .forward file is set up for a user, the e-mail is forwarded (not received locally) but does not show up for the inbox in the (external) account it was supposed to be forwarded to.l

Does anyone know why this problem is occurring>

Thanks

---

### Post by DrIdiot on 2009-01-09
I resolved it.

its because when i used netcat i specified a from address (soemthing@localhost) which whent sent through the external SMTP server came out as something@smtpserver

but i didnt specify a from in the mail command so the message got rejected (my server does not have a domain address)

---

