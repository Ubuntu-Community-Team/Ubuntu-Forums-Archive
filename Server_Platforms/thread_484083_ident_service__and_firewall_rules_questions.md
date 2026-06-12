---
title: "ident service ? and firewall rules questions"
date: 2007-06-25
forum: Server Platforms
---

### Post by lilliz on 2007-06-25
Hi I'm setting up a ubuntu server 6.06 1 for clan web and irc. web moved niceley (I had some help from the guys that hosted the old server) and I am about to apply for a quakenet trust, they do require the ident service running which leads me to my question, how do I install or enable this ? I've tried to find it thru apt-get but theres no such package it can find.

The server only have terminal thru SSH as a configureable interface.

And while im at it, theres been plenty of attempts to log on to the server thru ssh, is there some easy script that could block an ip after xx numbers of unknown users/failed attempts automatically for a couple of hours (will probably keep most bots at bay? )

Thanks In advance.

---

### Post by Mr. C. on 2007-06-25
There are several ident HowTo's here in the forums.  Search for identd.

Some firewalls provide an ident server - check yoru router/firewall.

Don't bother trying to block the SSH scripts - just move your SSH server to another port (say, 221).

MrC

---

### Post by lilliz on 2007-06-25
the ident issue is probably solved, I'll know tomorrow :)

 Well, the server is not behind a firewall and will never be either, the problem with changing the port is that I'm going to be less able to connect to it from various locations  when working, it's easier to ask for port 22 to be opened by a network admin than port 221 or any other for that matter and explaining why etc.

is it that difficult to make a rule that adds an offending IP with more than 10 failed login attempts from same ip ?

Regards LilliZ

---

### Post by Mr. C. on 2007-06-25
Do a search for fail2ban.

MrC

---

