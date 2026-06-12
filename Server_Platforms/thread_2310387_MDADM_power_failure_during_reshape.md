---
title: "MDADM power failure during reshape"
date: 2016-01-18
forum: Server Platforms
---

### Post by Okeur on 2016-01-18
Hi everyone,

To sum up I was doing a reshape from raid 5 to raid 6 with mdadm and of course since it's a sensitive task, I had a power failure during the reshape.
I started again the reshape process thanks to the backup-file but now the reshape speed is stuck to 0 ko/s.

Any idea how to get out of this hell ? ...

Ok, so I found that /sys/bloc/md0/md/sync_max was not set to the max of my array.
If you encounter the same problem, do the following :

```
echo max > /sys/bloc/md0/md/sync_max
```

Source : [https://www.kernel.org/doc/Documentation/md.txt](https://www.kernel.org/doc/Documentation/md.txt)

Thank you all !

---

