---
title: "Ubuntu with Squid and Dansguardian"
date: 2008-10-21
forum: Server Platforms
---

### Post by jason2oo2 on 2008-10-21
Hey all,

Just wondering if I can get a quick help out here.

Senario (at work): 

**First Proxy** is an an ubuntu server box, with LAMP, samba, SSH, webmin, squid and dansguardian
**Second Proxy** is an eduPaSS box. (Which i have dansguardian set up to use as its Proxy)

Layout: [ SQUID/Authentication --> Dansguardian] --> [Edupass Proxy]

I have set up a ubuntu box as mentioned above, but have run into a problem.
The squid authenticates the user/s agains Active directory without a problem. and Dansguardian works without a problem.

If i set my lab workstations proxy to the dansguardian port, I can browse the internet perfectly, content filtering and all.
But if i set the proxy settings to the SQUID port (which does the authentication). I can only browse what is in the cache of Dansguardian.

Yes the authentication works.
And i've added a cache_peer line : cache_peer 127.0.0.1 parent 8080 3130 no-query

But there seems to be somewhat of a problem somewhere between squid and dansguardian.

Any ideas on what I can do/try?

I have the following config files with me if anyone wants to have a look. Just let me know.

smb.conf
krb5.conf
squid.conf
dansguardian.conf

Cheers, and thanks in advance

Jason

---

### Post by jason2oo2 on 2009-01-08
Just a bump,

Anyone with any thoughts or tips?

---

