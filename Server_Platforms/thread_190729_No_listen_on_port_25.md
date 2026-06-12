---
title: "No listen on port 25"
date: 2006-06-06
forum: Server Platforms
---

### Post by jrohde on 2006-06-06
Hi,

I'm trying to setup a mail server using Postfix. When I execute:

**sudo /etc/init.d/postfix start**

I get an [Ok], but there is no luck with this command:

**telnet localhost 25**

and netstat shows that nothing is listening on port 25.

I have installed Postfix using apt-get.

Any ideas?

Jakob

---

### Post by ape on 2006-06-06
take a look in /var/log/mail.log (or /var/log/mail.err) to see if there are any issues with the postfix processes.

Also verify that the postfix processes are indeed running.

---

