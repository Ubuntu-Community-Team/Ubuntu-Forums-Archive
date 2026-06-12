---
title: "Postfix mail system with mysql..."
date: 2009-01-07
forum: Server Platforms
---

### Post by hockey97 on 2009-01-07
HI, I want to setup my postfix e-mail system to use mysql for users and e-mail accounts etc.

I have postfix installed already. I kinda works. I can send e-mail to g-mail and other small e-mail servers but can't with yahoo,aol,msn e-mails.

I would get reject errors form aol,yahoo,msn. They say I need a static-ip and a reverse host name lookup record.

I would like to know what it takes to send e-mail from my server to aol,yahoo,msn e-mail servers without any errors?

Thanks for your time.

---

### Post by HermanAB on 2009-01-07
A mail server must have A, MX and PTR records in the DNS.

Your PTR record is missing.

Cheers,

Herman

---

