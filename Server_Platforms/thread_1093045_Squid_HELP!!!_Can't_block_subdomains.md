---
title: "Squid HELP!!! Can't block subdomains"
date: 2009-03-11
forum: Server Platforms
---

### Post by YaAqoB on 2009-03-11
Hey all.
I have got Squid all running great & now I want to stop access to porn sites.
I have downloaded a blacklist file with almost 2 million known sites and implemented it ok with an ACL rule.
Now for example if I go to playboy.com it's blocked. If I go to [www.playboy.com](www.playboy.com) it works. I have read that to block both I have to add the domain .playboy.com. My obvious issue is that I don't have the time or patience to add a . to 2 million lines of URLs. All the blacklists I have downloaded are the same, because of this I'm going to assume that there is a easy fix as surely you wouldn't want staff adding www. to a site & getting access.
Please help!!!!
O & I'm running Squid 2.7 Stable.

Thanks in advance.

---

### Post by YaAqoB on 2009-03-11
Well I managed to put together a little script that added a . to the beginning of every line but surely this isn't the answer. How is everyone else out there blocking subdomains?

---

