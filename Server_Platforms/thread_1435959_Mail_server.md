---
title: "Mail server"
date: 2010-03-22
forum: Server Platforms
---

### Post by randrija on 2010-03-22
Hi all,
i have just configure my mail server. when I try to access my mail through thunderbird it show me " there is  no mail in this server ", but in command line ( exemple@ns# mail ) i can see all messages.

where is the mistake ? dovecot? postfix?

Regards,
Rija

---

### Post by dudumomo on 2010-03-22
Run postconf -n 
You should have a bit more information.

---

### Post by KB1JWQ on 2010-03-22
Mail retrieval is POP or IMAP; Postfix has nothing to do with this portion.

What does dovecot -n say?

---

