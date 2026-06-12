---
title: "Apache Set Header on 403 page"
date: 2018-05-07
forum: Server Platforms
---

### Post by gkooistrago on 2018-05-07
We setup apache to set headers, like the **X-Frame-Options**.
But this doesn’t work for the 403 pages, only the **Strict-Transport-Security **works.

The headers are set to the virtual hosts and later also to the global apache config.

The problem is that some security scans show warnings to the customers.
 
Is it possible to set the headers, so 403 pages are also delivering this to the browsers?

---

