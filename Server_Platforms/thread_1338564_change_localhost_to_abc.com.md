---
title: "change localhost to abc.com"
date: 2009-11-26
forum: Server Platforms
---

### Post by shaifymehtadnn on 2009-11-26
hii....

i m using apache2 in linux...

i want to chage localhost to my desired name...like abc.com

reply urgent...

---

### Post by scorp123 on 2009-11-26
Please consider reading some TCP/IP tutorials. Your own server is ALWAYS "localhost" from its own perspective. And the domain "abc.com" is already taken. Regardless of this: That's a DNS setting. Your client computer has to be able to resolve your server's IP address to that human-readable address.

e.g. 199.181.132.250 => [www.abc.com](www.abc.com)

Yes, that's the real IP of the real "www.abc.com" web site. So a DNS server has to translate the IP address into a human-readable name.

So you'd need your own DNS server that would make sure your web server resolves itself according to whatever you want it to resolve to.

This has not so much to do with the Apache web server software itself. You'd have to configure the correct web site settings in an additional step.

Please use these resources and read, read, read ...

[www.wikipedia.org](www.wikipedia.org)
[www.google.com](www.google.com)
[www.apache.org](www.apache.org)

- TCP/IP networking
- DNS
- Apache configuration
- Apache web site hosting

---

