---
title: "postfix config host..acme.com, host.acme.com correct?"
date: 2008-07-03
forum: Server Platforms
---

### Post by jeffk on 2008-07-03
I just installed postfix on Ubuntu 8.04 Hardy Server. During the config step, the terminal characters were somewhat garbled, and I'm asking here to see if the output below is a typo on my part.

I meant to change the transitional hostname 'host2' to 'host', since that's what I'll use after cutover from the current mailserver. I used "Internet Site" as the config option.
```
$ grep ichem /etc/postfix/*
main.cf:myhostname = mail2.acme.com
main.cf:mydestination = mail2..acme.com, mail2.acme.com, localhost.acme.com, localhost
```
I suspect based on that output that I mistyped the hostname as "mail2..acme.com". I couldn't see very well with the garbled term visuals.

Or is the "mail2.." a valid configuration that serves some purpose for postfix to resolve the hostname in various email scenarios?

Thanks.

---

### Post by MJN on 2008-07-03
It's a typo. Remove it, and in fact you ought to add in acme.com itself - this is the most important value for the mydestination directive (it tells Postfix what domains to accept mail for).

Mathew

---

