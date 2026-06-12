---
title: "fengoffice/apache2 problem"
date: 2010-04-12
forum: Server Platforms
---

### Post by mushr00m on 2010-04-12
I'm at a loss.

I haven't had to maintain a server for a few years, and I've got a potentially simple problem that I can't seem to find a solution for.  Or wrap my brain around.

Problem:

I use a dynamic IP service domain name to externally access various components of our community server.  Jabber, collaboration software (fengoffice) and intranet, etc.

The router I've got seems to be routing everything correctly but something is redirecting my external domain to an internal LAN hostname when I try and connect to fengoffice(formerly opengoo)

ie, when pointing my browser at (not real urls):

```
ourcommunity.dynamicip.com
```

shows me the the default apache2 page, while pointing at:
```

ourcommunity.dynamicip.com/fengoffice/
```

eventually resolves to: localhostname.local/fengoffice/

I'm pretty sure it's a fengoffice setup problem.  but I thought I'd cross post into my favourite distro forum as well :)

Any suggestions?

---

### Post by mushr00m on 2010-04-12
meh, internal conf setting in fengoffice fixed the problem.  I wish I knew another way of doing it than reinstalling and repopulating the db tables with a backup.

c'est la vie.

---

