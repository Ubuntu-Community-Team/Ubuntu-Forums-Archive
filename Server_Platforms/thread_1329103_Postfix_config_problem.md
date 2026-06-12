---
title: "Postfix config problem"
date: 2009-11-17
forum: Server Platforms
---

### Post by fisfia on 2009-11-17
Hi,

I have a problem with configuring postfix. Would like pf to limit the amout of mail that a client can send in for example one hour. 

Thought maybe this would be a good idea:

```
smtpd_client_message_rate_limit=
```

But what happens then is that smtpserver sends maximum amount for that time unit then WAITS until it's ok to send again. 

All the mail are finally send, just they get queued until it's done. That is not what I want. 

I would like to have the possibility to warn the client and then reject further mail. Not delay to queue. 

Is it possible? Should I instead use another parameter which is more sufficent for this task? 

Would be very greatful for any help, thanks!

---

### Post by wyldfury on 2009-11-17
I don't think postfix is capable (and I suspect for good reasons) of that sort of quota enforcement.

I use Policyd ([http://www.policyd.org/tiki-index.php](http://www.policyd.org/tiki-index.php)) for the sort of quota enforcement you're talking about.
Using it in a production environment with approx. 60K users so it's pretty robust and also easy to set up.

Guy

---

### Post by fisfia on 2009-11-17
How do you mean "For good reasons"? 
Was it stupid question?

---

### Post by wyldfury on 2009-11-17
It wasn't a stupid question. I meant there was probably be a good reason why postfix itself doesn't do that level of quota enforcement.

---

### Post by fisfia on 2009-11-17
Ok :D

I pulled myself together and asked on the postfix mailinglist. I'll let you know if they have some news!

Thanks for your tip. I've looked in to policyd a little bit but I would prefer if it's possible to do within Postfix.

---

