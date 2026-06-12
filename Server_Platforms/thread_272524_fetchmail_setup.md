---
title: "fetchmail setup"
date: 2006-10-06
forum: Server Platforms
---

### Post by rogier.de.groot on 2006-10-06
I've got this mail server, which handles a number of mail accounts, eg. [email]user1@domain.nl[/email], [email]user2@domain.nl[/email], etc. Mail for domain.nl doesn't go directly to this server, it winds up in a catch-all mailbox provided by my ISP. I can only access this mailbox via POP3.
What I want is to set up fetchmail to act like a deamon, getting mail from this catch-all box and delivering it to the mail server so it can distribute the mail amongst the various users.
I've been trying to do this for the better part of today but no joy. I've no idea why it won't work, it's not like I've never done this before.
One important aspect of this configuration is that fetchmail should ignore DNSsy things like MX records and such, just get the mail and deliver it to the server on IP adres 192.168.1.2 (which is on the same machine, but for reasons I won't go in to I can't use localhost).
Anybody know how to make this work?

---

