---
title: "how can I verify that my mail server is not an open relay?"
date: 2011-04-16
forum: Server Platforms
---

### Post by MakOwner on 2011-04-16
I'm setting up a mailserver for my domain.
I'm seeing relay rejections in the mail.log, but I'd like to have external validation that nothing bad is exiting the domain before I wind up on blacklists...

---

### Post by SeijiSensei on 2011-04-16
Go to an external machine that has a telnet client and try this:

```

telnet your.mail.server 25
[server replies with banner]
ehlo name.of.host.you.are.connecting.from
[server confirms your hostname]
mail from: joe@gmail.com
[server replies with a 250 OK]
rcpt to: bill@yahoo.com
[server should complain and disconnect]

```

---

### Post by t3r0 on 2011-04-16
> **MakOwner said:**
> I'm setting up a mailserver for my domain.
I'm seeing relay rejections in the mail.log, but I'd like to have external validation that nothing bad is exiting the domain before I wind up on blacklists...

[http://www.spamhelp.org/shopenrelay/](http://www.spamhelp.org/shopenrelay/)

---

### Post by MakOwner on 2011-04-16
> **t3r0 said:**
> [http://www.spamhelp.org/shopenrelay/](http://www.spamhelp.org/shopenrelay/)

So, I got a 

554 5.7.1 <test@yahoo.com>: Relay access denied

Anything else I can or should do to harden the mail service?

---

### Post by SeijiSensei on 2011-04-16
> **MakOwner said:**
> 554 5.7.1 <test@yahoo.com>: Relay access denied

That reply says it all.  You're fine.

---

