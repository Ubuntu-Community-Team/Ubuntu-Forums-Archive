---
title: "SendMail Connection Refused Error"
date: 2013-08-21
forum: Server Platforms
---

### Post by Steven_Woods on 2013-08-21
I upgraded from Ubuntu Server 10.04 to 12.04. Now my php sites are no longer sending mail. When I went in to look at the sendmail mail queue, all of my messages were there.
When I try to force the queue with debugging ([COLOR=#111111][FONT=Consolas]sendmail -v -q)[/FONT][/COLOR], I get the following response.
```
Running /var/spool/mqueue/r7KC82jb030432 (sequence 19 of 19)<user@domain.com>... Deferred: Connection refused by server.domain.local.domain.com.



```(actual names masked for privacy/security)
Our SMTP mail server is server.domain.local. How do I get rid of the .domain.com?

---

### Post by coffeecat on 2013-08-21
Support request, not an Ubuntu, Linux and OS Chat thread.

*Thread moved to **Server Platforms**.*

---

### Post by Steven_Woods on 2013-08-21
Thank you. Sorry about that. First Ubuntu Forums post.

---

### Post by SeijiSensei on 2013-08-21
> **Steven_Woods said:**
> Our SMTP mail server is server.domain.local. How do I get rid of the .domain.com?

Usually that indicates that a name in the DNS server's zone files for domain.com is not properly terminated with a dot.  Suppose you have

```
@    IN   MX   5 server.domain.local
```

Since the fully-qualified domain name does not end with a trailing dot, "server.domain.local.", BIND appends the domain to the host name giving you "server.domain.local.domain.com".

Simply upgrading to 12.04 should not affect any of this, but since DNS resolution changed in 12.04, it might have to do with that.  Make sure you are using static addressing on your server, and include the relevant "[dns-nameservers]("http://askubuntu.com/questions/143819/how-do-i-configure-my-static-dns-in-interfaces")" directive in the stanza for eth0 in /etc/networking/interfaces.

---

### Post by Steven_Woods on 2013-08-21
I am trying this now. I will let you know the results in a few.
Thank you!

---

