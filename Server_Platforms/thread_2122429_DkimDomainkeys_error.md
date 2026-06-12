---
title: "Dkim/Domainkeys error"
date: 2013-03-05
forum: Server Platforms
---

### Post by mircica3d on 2013-03-05
I installed and configured opendkim for dkim and dk-filter for domainkeys. I created two keys (one for dkim and other for domainkeys).

When insert the txt record for domainkeys in dns, and stop opendkim service, and send mail to yahoo, domainkeys pass (ok) and dkim permerror(no key).
When insert the txt record for domainkeys in dns, and  start opendkim service, and send mail to yahoo, domainkeys pass (ok) and dkim dkim=permerror (bad sig).


Can you help me?

---

