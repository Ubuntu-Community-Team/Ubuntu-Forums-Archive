---
title: "smbd randomly using 100% CPU"
date: 2011-08-03
forum: Server Platforms
---

### Post by tsigo on 2011-08-03
In the last week or so, smbd has begun utilizing 100% of my server's CPU, even when not being used actively, and it does so constantly until I restart the service. If I don't restart the service file transfers stall or go extremely slowly.

Any ideas how I can begin tracking down the cause?

```
$ smbd --version
Version 3.5.4
```

---

