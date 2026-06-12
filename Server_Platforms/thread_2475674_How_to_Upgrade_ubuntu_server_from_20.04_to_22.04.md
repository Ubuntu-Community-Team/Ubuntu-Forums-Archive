---
title: "How to Upgrade ubuntu server from 20.04 to 22.04?"
date: 2022-06-04
forum: Server Platforms
---

### Post by deepakdeshp on 2022-06-04
I have tried to upgrade from server version 20.04 to 22.04 but it is downloading the impish repositories. How do I upgrade from 20.04 to 22.04?

---

### Post by deadflowr on 2022-06-04
The upgrade channel for 20.04 to 22.04 is not officially open yet,
so in order to force it you need to add the -d option to the do-release-upgrade command like
```
do-release-upgrade -d
```

The channel will officially be opened in August, when the first point release comes for 22.04.

---

