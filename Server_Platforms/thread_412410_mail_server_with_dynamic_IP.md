---
title: "mail server with dynamic IP?"
date: 2007-04-18
forum: Server Platforms
---

### Post by forzagrifo on 2007-04-18
I'm using Ubuntu Dapper as a home server.  I have a PHP app which I would like to send emails with (using php's mail() function).  I would like to receive emails using something like Webmail.  I have installed Postfix on the same server.

I don't have a static IP.  I'm using the service from no-ip.com so my domain is fixed at xxx.no-ip.com even if my IP changes.  

Right now I'm having trouble "connecting the dots".  I do not want to use my ISP's smtp server to relay my emails.  I want to send emails so that the recipient will see the sender is from "xxx.no-ip.com".  Port 25 is not blocked by my ISP.

So my question is, is it possible to send and receive emails without using my ISP's smtp server IF I have a dynamic IP (with my domain fixed by no-ip.com at "xxx.no-ip.com")?  If so, how do I set it up in terms of the postfix configuration?

If the above is not possible, then is it possible to use my ISP's smtp server?

---

### Post by heimo on 2007-04-18
> **forzagrifo said:**
> So my question is, is it possible to send and receive emails without using my ISP's smtp server IF I have a dynamic IP (with my domain fixed by no-ip.com at "xxx.no-ip.com")?

Yes, but not recommended.

> **forzagrifo said:**
> 
 If so, how do I set it up in terms of the postfix configuration?

Just the way you'd setup with fixed ip, but you make sure that your MX records stay up to date all the time. EDIT: (I need more coffee.) Your MX records may stay the same, but you keep the A record of your mail server updated.
[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

> **forzagrifo said:**
> If the above is not possible, then is it possible to use my ISP's smtp server?
To send email? Of course. (search for "relayhost" in the guide linked above)

---

### Post by astrogazer on 2007-04-18
You may use a service such as DynDNS to have your A/MX record resolved to your 
dynamic IP. however you should note that. When your IP changes some mail servers 
might keep trying sending you email in the old IP because that is what they have cached
in their DNS, Although the RFC says that they should keep retrying for five days, some 
misconfigured servers might not try for that long.

If you want to use your ISP's SMTP server for incoming mail then you have to ask them
to do the necessary changes on their configuration.

---

### Post by ohioboy757 on 2007-04-18
You may also get rejected e-mails when trying to sent to some sites.  Many e-mail servers do a reverse DNS lookup to check the validity of the sender.  Your reverse lookup will not correspond to the sending domain name (ISP Controls this) and message will be rejected.

---

### Post by heimo on 2007-04-18
> **ohioboy757 said:**
> Your reverse lookup will not correspond to the sending domain name (ISP Controls this) and message will be rejected.

Or they might even block whole ranges of ip addresses because they're known to be reserved for xDSL / dial-up, or because previous "owner" of the address was a spammer or had an infected machine on it and the address got blacklisted.

---

