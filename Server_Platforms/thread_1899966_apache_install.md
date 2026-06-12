---
title: "apache install"
date: 2011-12-24
forum: Server Platforms
---

### Post by vernonh76 on 2011-12-24
I have a developer who wants me to install apache1, not apache2 along with mysql and php.  I don't see a way to install apache1 on Ubuntu, LTS.  Is there a way, what am I missing?  He states he has heard he will have issues with apache2, so I am trying to install apache1.  Thanks.

---

### Post by Lars Noodén on 2011-12-25
Version 1.3 of Apache is [deprecated](http://httpd.apache.org/docs/1.3/).  It's not supported by either Apache or Ubuntu so you won't find it in the repositories.  The OpenBSD project has been maintaining a [version of 1.3 for OpenBSD](http://www.openbsd.org/cgi-bin/cvsweb/src/usr.sbin/httpd/) and has made considerable improvements to it.  So if you really, truly need Apache 1.3, that's where to get it from.

However, it will be far easier for you to maintain Apache2 since that is what is in the repositories.  Can you tell us a bit about the 'issues' he thinks he might have with Apache2?  They might be unfounded or else have easy work-arounds.

---

### Post by vernonh76 on 2011-12-25
Thanks for the info.  I will check with him and see what the issues are.

---

