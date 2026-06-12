---
title: "dig error"
date: 2010-01-25
forum: Server Platforms
---

### Post by mkubu on 2010-01-25
There is like one month since dig fails running after some upgrade.

Platform: Ubuntu-Server 6.06.1 _Dapper Drake_ - Release amd64

Error: ```
dig: error while loading shared libraries: libdns.so.21: cannot open shared object file: No such file or directory
```Please advice... Thank you!

---

### Post by terazen on 2010-01-25
Does this help?

[http://www.linux.com/archive/feature/114007](http://www.linux.com/archive/feature/114007)

---

### Post by StickyStyle on 2010-02-08
Just had the same issue on a 6.06 box also, checking the system for libdns.so.21 and was gone with no apparent replacement.  

Turns out I didn't have 
```
 deb http://security.ubuntu.com/ubuntu dapper-security main 
``` in my /etc/apt/sources.list and some recent upgrade replaced libdns.so.21 with libdns.so.23 which was in the security.ubuntu.com/ubuntu dapper-security repo but not in us.archive.ubuntu.com/ubuntu dapper-security.

Adding deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main to my sources, doing an update, then an upgrade resolved the issue.

---

