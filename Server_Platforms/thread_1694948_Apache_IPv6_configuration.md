---
title: "Apache IPv6 configuration"
date: 2011-02-25
forum: Server Platforms
---

### Post by nour_al_imen on 2011-02-25
Hi,

I want to modify apache IPv4 configuration to IPv6 config
On both windows and ubuntu.

Any help please ?

Thanks

---

### Post by lemming465 on 2011-02-25
You want to be on an OS platform with good underlying v6 support, meaning recent, so be using windows 2008, redhat 6, ubuntu 10.04, Mac OS 10.7 (this summer).  Probably Apache 2.2 series, too.

Put any v6 addresses you want Apache listening on in square brackets, e.g. ```
Listen [2001:db8::a00:20ff:fea7:ccea]:80
``` as [described]("http://httpd.apache.org/docs/2.2/bind.html") in the apache documentation.

Those parts - the OS and Apache config - are easy.  The fun starts when you try to get applications to deal with v6 cookies and sessions, and analyze your log files using programs which only think in dotted quad addresses.

---

