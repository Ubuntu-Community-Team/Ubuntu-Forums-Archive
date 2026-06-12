---
title: "Have I set ulimit / file descriptor limit correctly"
date: 2012-10-31
forum: Server Platforms
---

### Post by _Dan on 2012-10-31
Hello,

I have an upstart service, which in the config file I specify the file descriptor limit as:

```
limit nofile 64000 64000
```

Thus, cat /proc/pid/limits correctly gives:
```
Max open files 64000 64000 files
```

However, when logged in as root, the output of "ulimit -Hn" is 4096.

My question, then, is which takes precedence? Have I correctly increased my daemon's file descriptor limit to 64000? Or will the 4096 hard limit shown by the ulimit command take precedence and override this?

---

