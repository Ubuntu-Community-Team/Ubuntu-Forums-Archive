---
title: "[SOLVED] Package management for source installs"
date: 2008-08-23
forum: Server Platforms
---

### Post by promodus on 2008-08-23
Hello,

There is the odd occasion where there is no package available in the repository, or there is no .deb made. 

In this example I want to use winexe, it is a psexec version for Linux to get a dos prompt from a windows box. Pretty handy.

What I'm after is having apt manage the removal of this software after I've installed it. So if I go:
```
apt-get remove winexe
``` 
It's uninstalled and done for, nothing to worry about.

winexe
[http://eol.ovh.org/winexe/]("http://eol.ovh.org/winexe/")

Coincidentally, I do get an error on make. Any help there would also be appreciated. Thanks.

---

### Post by windependence on 2008-08-23
[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

HTH

-Tim

---

### Post by promodus on 2008-08-24
Thanks, I'll post another thread for the compile issues.

---

