---
title: "Postfix relayhost..."
date: 2005-12-05
forum: Server Platforms
---

### Post by oberon on 2005-12-05
I need to setup post to relay SMTP traffic to my ISPs smtp server since they block mail from my server to other Verizon users. This wouldn't be a problem except they are responsible and require authentication for their smtp server. Is there a way to give the credentials to the RELAYHOST setting?

ie:
```

RELAYHOST = outgoing.verizon.net user:pass

```

Thanks for your help,

oberon

---

### Post by LordHunter317 on 2005-12-05
You have to setup SASL.  I'd link a tutorial but I don't know any good ones.

---

### Post by cocophone on 2005-12-05
Here is a couple of links that I used.  One is how to use Mandrake, but the principles still would apply.

[http://www.dyndns.com/support/kb/archives/mail_servers_and_mailhop_outbound.html](http://www.dyndns.com/support/kb/archives/mail_servers_and_mailhop_outbound.html)

[http://www.dcs.napier.ac.uk/~peter/linux/postfix.html](http://www.dcs.napier.ac.uk/~peter/linux/postfix.html)

---

### Post by oberon on 2005-12-06
Thanks for info and the links!

-oberon

---

