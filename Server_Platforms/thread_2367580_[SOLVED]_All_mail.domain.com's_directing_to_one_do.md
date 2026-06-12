---
title: "[SOLVED] All mail.domain.com's directing to one domain"
date: 2017-08-01
forum: Server Platforms
---

### Post by astarmathsandphysics on 2017-08-01
I have several websites on my server with hostname server.astarmathsandphysics.com
All versions of mail.domain.com are redirecting to astarmathsandphysics.com, and I am using https so am getting certificate conflict issues, and backlinks I do not want.
I would like to redirect [https://mail.domain.com/string-of-crap](https://mail.domain.com/string-of-crap) to [https://domain.com](https://domain.com).
I have tried using htaccess and the apache site config file
How cam I do this?

---

### Post by slickymaster on 2017-08-01
*Thread moved to **Server Platforms**.*

---

### Post by astarmathsandphysics on 2017-08-02
What I will do is this and will post if it works.
Create subdomain mail.domain.com for each domain
At the moment I am using postix/dovecot with a self signed ssl certificate. I will get a certificate from lets encrypt to replace it, and refer all subdomaINS to this certificate in their apache configuration files.

---

### Post by astarmathsandphysics on 2017-08-18
That worked.

---

