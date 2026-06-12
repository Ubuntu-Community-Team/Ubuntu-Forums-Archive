---
title: "squid configuration"
date: 2008-08-27
forum: Server Platforms
---

### Post by skvishnuk on 2008-08-27
hi everybody,
     i am using squid 2 in my proxy server . i block a websit by word (for eg: job). i want to allow a website for eg timesjobs.com. 

acl allowed_sites_names dstdomain [www.timesjob.com/*](www.timesjob.com/*)
http_access allow allowed_sites_names

acl BlockSites dstdom_regex -i jobs job
http_access deny BlockSites

---

