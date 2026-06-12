---
title: "DRBD won't start, can't find module"
date: 2013-01-24
forum: Server Platforms
---

### Post by tubaguy50035 on 2013-01-24
I'm trying to set up DRBD on my Linode using this guide: [http://library.linode.com/linux-ha/highly-available-file-database-server-ubuntu-10.04](http://library.linode.com/linux-ha/highly-available-file-database-server-ubuntu-10.04)

Everything has worked out well, right up until I want to start DRBD.  It says it "Can not load the drbd module."  

Some Googl'ing has told me that it may be because of my kernel
```
uname -a
Linux tek-lin-f02.company.com 3.5.0-22-generic #34-Ubuntu SMP Tue Jan 8 21:47:00 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

I'm at a loss of what to do here.  I'm not overly familiar with kernel stuff.  Anybody have things for me to try?

---

