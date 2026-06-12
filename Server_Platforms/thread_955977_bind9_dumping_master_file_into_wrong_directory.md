---
title: "bind9 dumping master file into wrong directory"
date: 2008-10-22
forum: Server Platforms
---

### Post by vertigo23 on 2008-10-22
I'm getting lots of errors like this in /var/log/daemon.log
```
named[7462]: dumping master file: /etc/bind/tmp-j5GSim3vHX: open: permission denied
```

I've already made sure that /etc/bind/named.conf.options has specified /var/cache/bind as the directory (the default), so I don't understand why named is still trying to write this to /etc/bind.

Any help?

---

