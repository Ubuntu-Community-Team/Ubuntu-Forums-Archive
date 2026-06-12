---
title: "How to configure sendmail for Bugzilla"
date: 2011-01-03
forum: Server Platforms
---

### Post by mattyh88 on 2011-01-03
I just installed Bugzilla3. I asked my mate to register to it. He filled in his email, but Bugzilla never sent him an email (the validate email one). 

So I suppose my MTA isn't configured correctly. I've searched quite a bit for a nice tutorial, but I couldn't find any (that isn't to complicated). 

Any help is appreciated ^^

---

### Post by woodman231 on 2011-01-03
I would start by installing a Postfix service on to your server.

[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

Thanks,
Sean W.

---

### Post by HermanAB on 2011-01-03
Howdy,

Alternatively you can use a relay only MTA like nullmailer.

---

### Post by mattyh88 on 2011-01-04
> **woodman231 said:**
> I would start by installing a Postfix service on to your server.

[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

Thanks,
Sean W.

Is postfix supported by Bugzilla? As I can only choose between SendMail and SMTP in the configuration parameters of Bugzilla.

---

### Post by MechaMechanism on 2011-01-04
> **mattyh88 said:**
> Is postfix supported by Bugzilla? As I can only choose between SendMail and SMTP in the configuration parameters of Bugzilla.
Choose Sendmail and it should pick up Postfix automatically.  Sendmail is a generic term nowadays for MTA.  Sendmail merely sends mail to port 25 and whatever is listening on port 25 picks it up and sends the mail on it's way.

---

### Post by HermanAB on 2011-01-05
Howdy,

Postfix, Citadel, Qmail and others include a little program called sendmail, to provide a generic 'sendmail' interface and keep other applications happy.

---

