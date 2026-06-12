---
title: "dansguardian logs show user name?"
date: 2007-03-06
forum: Server Platforms
---

### Post by bluesmudge on 2007-03-06
Setup;
6.06 LTS - Running Squid, dansguardian.
Windows 2003 server running active directory which our windows users log into - web access is passed to dansguardian then out through squid.

Quite simply I want the dansguardian logs to record the user name next to the entries.

Any Ideas?

Thanks!

---

### Post by jonathan.lees on 2007-03-06
I have the same setup as you, I have'nt tried this myself yet but you could try setting up squid/dansguardian with NTLM. Here's a link to a howto:

[http://www.opensourcehowto.org/how-to/squid/squid1-ntlm---dansguardian---squid2-cache.html](http://www.opensourcehowto.org/how-to/squid/squid1-ntlm---dansguardian---squid2-cache.html)

---

