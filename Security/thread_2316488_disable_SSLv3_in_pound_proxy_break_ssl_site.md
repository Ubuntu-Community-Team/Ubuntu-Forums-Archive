---
title: "disable SSLv3 in pound proxy break ssl site"
date: 2016-03-08
forum: Security
---

### Post by rican-linux on 2016-03-08
We are trying to disable SSLv3 on our pound proxy. In the config file we added the following 

Ciphers "HIGH:!SSLv3"

When we restart pound proxy and open  the site in firefox we get alerted that the ssl connection is insecure. When we revert back the error goes away. Has anyone else ran into this before? We are running Ubuntu 14.04

---

