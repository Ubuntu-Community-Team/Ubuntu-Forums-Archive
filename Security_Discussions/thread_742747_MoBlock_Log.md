---
title: "MoBlock Log"
date: 2008-04-02
forum: Security Discussions
---

### Post by sekinto on 2008-04-02
For some reason whenever I run MoBlock with the MoBloquer GUI it blocks the site gaiaonline.com, however it doesn't "say" it is blocking anything, so I can't unblock it.

---

### Post by jre on 2008-04-02
mobloquer only shows connections that were blocked after mobloquer was started.
So first start mobloquer and then try to access your website.

You may have a look directly at /var/log/moblock.log to see what was blocked.
You can whitelist the IPs directly in /etc/default/moblock.

---

