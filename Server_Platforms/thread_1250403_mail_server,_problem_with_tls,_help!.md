---
title: "mail server, problem with tls, help!"
date: 2009-08-26
forum: Server Platforms
---

### Post by lunatiko on 2009-08-26
hi everyone, (specially the gurus)

i follow the flurdy how to setup a mail server, i complete all the steps, but the squirrelmail isn't working fine i guess, when i log on its shows:

[COLOR=#cc0000]**ERROR**[/COLOR]
Error connecting to IMAP server: tls://localhost.
0 : 

Does anyone know what i doing wrong?

Wainting for an answer

Thx!

---

### Post by noway2 on 2009-08-26
I will venture a guess: you are trying to send mail via squirrelmail.

I was getting the same error until I went into the squirrelmail configuration and set the sending to use Sendmail instead of SMTP.

Someone was kind of enough to subsequently explain that Postfix has a sendmail compatibility stub and that is what in essence you are using by doing this.

---

