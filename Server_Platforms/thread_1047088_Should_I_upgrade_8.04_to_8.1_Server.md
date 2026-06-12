---
title: "Should I upgrade 8.04 to 8.1 Server?"
date: 2009-01-22
forum: Server Platforms
---

### Post by sierraloewe on 2009-01-22
Hi community,

I've run into a known bug regarding openLDAP and TLS in 8.04 server.  It seems I have three options:

[LIST=1]
[*]Recompile openLDAP to use openSSL instead of GnuTLS
[*]Install a newer version of openLDAP
[*]Upgrade to 8.1
[/LIST]

I'm at the very beginning of building a server which I expect to deploy for a long time- so I naturally want to stay with an LTS version if possible.  Upgrading seems to be the easiest way out.

What would you do and why?

--Brandon

---

### Post by bobsta63 on 2009-01-22
Hi Brandon,

Sounds a tricky one to me mate, I personally would definetly stay with the LTS version (especially as you say you will be using it for a long period), I'd personally upgrade my version of OpenLDAP instead of recompiling with OpenSSL... Just my personal opinion.

I just think that upgrading OpenLDAP would be must quicker than recompiling OpenLDAP with OpenSSL... Might be wrong however, just the way I'd do it... :)


Good luck with whatever you decide to do :)
Bobby

---

