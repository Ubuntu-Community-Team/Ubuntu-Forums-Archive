---
title: "Constant nfsd CPU usage since upgrading to 19.10"
date: 2019-11-06
forum: Server Platforms
---

### Post by xWEkxhW on 2019-11-06
Since upgrading my home servers to 19.10 I've noticed nfsd is generally using a constant amount of CPU even when no activity present. I've seen this as high as 55% over the past few weeks.

Rebooting the server usually fixes it but only for a day or two.

Example this evening:

```
  PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
 1122 root      20   0       0      0      0 S  11.0   0.0 320:34.18 nfsd
 1121 root      20   0       0      0      0 S   3.3   0.0  95:41.04 nfsd
```

Any help would be appreciated

Thanks

---

