---
title: "deploy multiple services on one machine?"
date: 2016-04-24
forum: Ubuntu Cloud and Juju
---

### Post by hoangweb on 2016-04-24
i want to deploy multiple wordpress sites in one machine for my customers? it;s possible. for example: i will deploy 3 WP sites to machine 0 (192.168.205.10). So i wondering, what URLs for my wp 3 sites? i'm new to juju & i dont find any tutorial show how to do that. i think juju integrate DNS automation solution, such as i figure out environments.yaml like this:
```

host3:
  type: manual
  bootstrap-host: mysite.dev
  bootstrap-user: root
  default-series: trusty

```
mysite.dev point to 192.168.205.10
it's possible allow to add subdomain. e.g:
wp1.mysite.dev
wp2.mysite.dev
wp3.mysite.dev

Thank very much!

---

