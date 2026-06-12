---
title: "odd issue with nginx on ubuntu 20.04"
date: 2021-01-12
forum: Server Platforms
---

### Post by espressobeanmachine on 2021-01-12
I am having an odd issue starting with the use Ubuntu 20.04 and NGiNX 1.18 that comes from NGiNX's repo. So a bit of background,

I am running Ubuntu 20.04 on baremetal that is running LXD, within LXD containers I am running Ubuntu 20.04 and NGiNX 1.18 that was installed from NGiNX's own repo. When I set the commands "nginx -s reload" I get the following error message:

```
nginx: [error] open() "/var/run/nginx.pid" failed (2: No such file or directory)
```

Anyone else getting this issue?

---

