---
title: "Need help understanding postfix"
date: 2012-07-14
forum: Server Platforms
---

### Post by kfcSmitty on 2012-07-14
Hi guys,

I've been running a virtual server through godaddy for about 2 years, but now I'm moving onto a dedicated server. 

One thing I want to set up is email forwarding and I've been told postfix is the way to go.

I've got postfix set up and it is able to forward to the domains and aliases I set up, but it is completely unsecured. After Googling, everyone said to use sasl, but I set that up and now when I run "ehlo localhost" I get the following list:

```

250-<my actual server>
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250-STARTTLS
250-AUTH PLAIN LOGIN
250-AUTH=PLAIN LOGIN
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN

```

But I am still able to telnet into port 25 from any machine and send an email unauthenticated.

So I guess my question is: is it even possible to lock that down so it requires a username and password, or is it always left open? I went back to my godaddy VPS to check its settings (it had postfix running as well, but it was set up by godaddy) but that server is also completely unprotected.

Any information/advice is welcome.

Thanks,

Smitty

---

### Post by SeijiSensei on 2012-07-15
MTAs like Postfix and sendmail are generally designed to be open to the world as you'd expect for software that accepts, relays, and delivers mail from potentially anywhere.

You can impose various restrictions with rules.  I recommend starting by reading this:
[http://www.postfix.org/SMTPD_ACCESS_README.html](http://www.postfix.org/SMTPD_ACCESS_README.html)

If you're only forwarding for a set of known domains, then make sure Postfix is configured only to accept inbound messages for addresses in those domains.  The worst security problem for a mail server is becoming an "open relay" where spammers can push mail through your server with arbitrary From and To addresses.  At a minimum, limit the To list to the domains you need to service.

---

