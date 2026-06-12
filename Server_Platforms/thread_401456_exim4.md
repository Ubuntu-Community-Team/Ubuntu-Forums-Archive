---
title: "exim4"
date: 2007-04-04
forum: Server Platforms
---

### Post by noone123 on 2007-04-04
hi,again. I searched this forum for some mail servers that could be easily to setup and ready for work. I just need a simple mail server that could send me a mail from web server. I can't understand, whats wrong every time? maybe someone can tell me an easy way to set this mail server up(i alredy tried the official Doc) the problem is simple! Doesn't send mail.

By the way, how does mail work? it chooses a username which is in my ubuntu and takes one of my domains? like [email]noone@mydomain.com[/email] ?

---

### Post by MrHorus on 2007-04-05
> **noone123 said:**
> the problem is simple! Doesn't send mail.


Your problem might be simple but your explanation isn't much use.

In which was does it "not send mail"?

Does it get the email from your client and then do nothing with it?
Will it reject all connections?
Do you get any error messages?

Have you set it up properly?

From my own setup I was running BIND and hosting my own domain, so I added my own domain as a local host during setup and really that was all that was nescesarry. After the initial install I was able to ammend the config files to add TLS and authenticated relaying.
Admittadly I did install on Debian but since Ubuntu is largely built on Debian there shouldn't be that much difference.

Sorry to be a bit harsh but without the nescesarry information it's understandably hard to know what your specific problem is.

---

### Post by MrHorus on 2007-04-05
> **noone123 said:**
> 
By the way, how does mail work? it chooses a username which is in my ubuntu and takes one of my domains? like [email]noone@mydomain.com[/email] ?

It might do, depending on your setup.

Generally if you were sending mail to an address in mydomain.com then your mail gateway (SMTP server) would find that domain's MX (Mail eXchanger) record and this is what points to the mail server.

Your mailserver would then connect to the domain's mailserver (the MX record) and this would then work out what to do with the email i.e. is it a local delivery, is it being relayed elsewhere and so on.

I run local mail delivery so anything sent to <login name>@mydomain.com will be delivered into the relevant local mailbox on my server.

---

