---
title: "Small php admin interface?"
date: 2007-07-24
forum: Server Platforms
---

### Post by aNt1X on 2007-07-24
Hi all.

I'd like to have a small php interface to manage basic server settings: basically network configuration, startup services, and so on.

Is there any ready php app?

Thank you,

aNt1X

---

### Post by elst on 2007-07-24
[Webmin]("http://www.webmin.com/") is the most popular Web-based admin tool, and it allows you to define users and groups within the application, so you could create a user that only has access to networking settings if you wanted. Webmin is written in Perl (which is part of the base Ubuntu install), and uses it's own Web server, so you don't need Apache or similar.

I would not recommend deploying Webmin on a public server, but it can be a huge help for LAN servers with less experienced support staff.

---

