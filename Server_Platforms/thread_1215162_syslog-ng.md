---
title: "syslog-ng"
date: 2009-07-16
forum: Server Platforms
---

### Post by druhboruch on 2009-07-16
I would like to replace log daemon with syslog-ng.

Is there any howto available for ubuntu?

I appreciate any links, comments or success / failure stores.

---

### Post by druhboruch on 2009-08-13
Anyone?

---

### Post by alastair on 2009-08-13
> **druhboruch said:**
> Anyone?

If you install syslog-ng it will "just work". It has a configuration that mimics normal syslog, so you will not see any difference.

However, you now have the opportunity to configure syslog-ng and use its extra functionality if desired (e.g. filtering etc.).

The config file is fairly clear and you can add new filters and destination file easily.  For docs, see the home page :

[http://www.balabit.com/dl/html/syslog-ng-admin-guide_en.html/bk01-toc.html](http://www.balabit.com/dl/html/syslog-ng-admin-guide_en.html/bk01-toc.html)

Don't try it all at once - do simple things and learn.

---

