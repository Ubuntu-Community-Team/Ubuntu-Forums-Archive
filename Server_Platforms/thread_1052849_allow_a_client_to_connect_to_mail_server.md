---
title: "allow a client to connect to mail server"
date: 2009-01-28
forum: Server Platforms
---

### Post by genset on 2009-01-28
hi guys
i have configured a ubuntu server as a proxy for one of our branches, one probleme that im having is i cant get the clients to connect to a mail server on the outside. what are the rules that needs to be added?

---

### Post by HermanAB on 2009-01-28
You need to handle all the mail ports and those depend on what you use:
SMTP, IMAP and POP are the usual suspects, but you may also need all the SSL versions of the same.

The port numbers are in /etc/services

Cheers,

Herman

---

