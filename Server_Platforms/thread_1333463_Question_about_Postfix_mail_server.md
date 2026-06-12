---
title: "Question about Postfix mail server"
date: 2009-11-21
forum: Server Platforms
---

### Post by onehitxzibit on 2009-11-21
Is it possible to create a mail server on a free domain like for e.g. example.no-ip.org and which ports do I need to forward?

---

### Post by dalitso on 2009-11-21
Yes it is possible. However, you need to relay your emails through a known smtp server e.g your ISP's smtp server. This is because mail servers reject emails from dynamic hosted domains such as example.no-ip.org.
You do not need to forward any ports to send and receive mail on your mail server unless you need to access your pop3/imap and smtp server from outside your LAN. In such a case ports 110 (pop3), or 143 (imap) and 25(smtp) will have to be forwarded.

---

