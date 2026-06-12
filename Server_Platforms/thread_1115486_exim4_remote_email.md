---
title: "exim4 remote email"
date: 2009-04-03
forum: Server Platforms
---

### Post by yvsong on 2009-04-03
Exim4 running, but supports local email only. Where do I start to enable email to remote domains? Thanks.

---

### Post by brian_p on 2009-04-04
> **yvsong said:**
> Exim4 running, but supports local email only. Where do I start to enable email to remote domains? Thanks.

Make a start with:

```
sudo dpkg-reconfigure exim4-config
```

---

