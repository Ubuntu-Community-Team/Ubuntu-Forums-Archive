---
title: "/security/limits.conf not working"
date: 2010-06-22
forum: Server Platforms
---

### Post by Moptop650 on 2010-06-22
Hey all,
I'm trying to limit the max memory per process to 50mb. It is my understanding that putting:

```
* hard rss 51200
```

In limits.conf would do this? However, it does not seem to apply. And I have tried rebooting.

Is this the proper way? Or is there something else to do?

Note: My server is running as an OpenVZ VPS.

---

