---
title: "Dovecot managesieve missing?"
date: 2010-09-09
forum: Server Platforms
---

### Post by blink0 on 2010-09-09
Hello everyone,

I am trying to get our dovecot server to work with managesieve so that the users can add/edit servers via Horde. Before anything else, I copied the server's configuration to my local machine (Ubuntu 9.04 Jaunty, dovecot 1:1.1.11-0ubuntu4.1) and manage to get everything working. Unfortuantely, that is not the case when I tried to mimic the changed config items to the server itself (Ubuntu 8.04.1 hardy, dovecot 1:1.0.10-1ubuntu5.2), where I got a "Unknown protocol managesieve" error...

I did some investigating (with "dpkg --listfiles") and realized that while my local ubuntu Jaunty's dovecot-common includes several managesieve files, the same isn't true for the server ubuntu hardy's dovecot-common....

So my question is, is there any (simples) way to install managesive on a ubuntu hardy?

I also accept suggestions on how to do it without managesieve (and with smth hardy does support, while we're at it ;-)

Thanks in advance!

Cheers,
Daniel

---

### Post by blink0 on 2010-09-13
I ended up using pysieved and everything is running smoothly now.

Thanks anyway.

---

