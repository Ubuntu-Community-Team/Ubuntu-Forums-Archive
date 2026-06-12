---
title: "bind9 attempting  ipv6 on ipv4 network"
date: 2010-10-29
forum: Server Platforms
---

### Post by DrJohn999 on 2010-10-29
After upgrading from 9.10 to 10.04, a hundred or so of (for example) ```
 error (network unreachable) resolving '14.42.117.203.in-addr.arpa/PTR/IN': 2001:500:13::c7d4:35#53: 1 Time(s)
``` messages appear in syslog each day. Each URL has from 2 - 6 attempts at various ipv6 addresses. My question is why is bind9 trying to resolve ipv6 addresses? I have done nothing to enable or disable ipv6 and thought that if not explicitly enabled I would not have to be concerned with it.

It's only a small niggle, but I'm curious to know what's going on.

---

### Post by r00tintheb0x on 2010-10-29
This might help:

[http://ubuntu-tutorials.com/2009/03/21/configure-bind-9-for-ipv4-or-ipv6-only/](http://ubuntu-tutorials.com/2009/03/21/configure-bind-9-for-ipv4-or-ipv6-only/)

Iff not, I think you're going to have to recompile...

vi /etc/default/bind9
OPTIONS="-4 -u bind"
//-4 = to use ipv4 only.

I know I had to on Debian.

---

### Post by zorglubx on 2012-10-08
Just wanted to thank you for solving my problem as well :p

---

### Post by overdrank on 2012-10-08
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

