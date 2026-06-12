---
title: "Server issues"
date: 2009-03-05
forum: Server Platforms
---

### Post by lmcadory on 2009-03-05
I am installing a gforge server. But I am having some issues with it. The gforge server is currently installed in our lab.  In the lab, we setup a DNS record that points to the server name (servername.domain.com).  When I test within the lab with [https://servername.domain.com](https://servername.domain.com), everthing works great.  I don't want to use the servername as the website name for other users to access.  When we setup another DNS record that point to the site, that is when it does not load properly. (gforge.domain.com).  When I put my mouse over the links on the page when using [https://gforge.domain.com](https://gforge.domain.com), the links appear as [https://servername.domain.com/somelink](https://servername.domain.com/somelink), and not [https://gforge.domain.com/somelink](https://gforge.domain.com/somelink).  My network admin does not think this is a DNS issue since he has several other sites on different servers that are working fine.  He thinks there is something hardcoded in the site and is forcing it to use the servername, but he also admits he doesn't know linux very well.  Does this help clarify the issue?

 

Thanks

Lamar

---

### Post by matey3 on 2009-03-06
who is providing the security certificate for your site?

---

### Post by wirelessmonkey on 2009-03-06
This sounds like an Apache configuration issue to me.... Do you have name-based vhosts enabled?

---

### Post by lmcadory on 2009-03-09
I'm not sure. I'm very new to this. Where would I go to find that out?

---

