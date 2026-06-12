---
title: "Vulnerabilities in in PHP&lt;5.2.4"
date: 2007-11-06
forum: Server Platforms
---

### Post by toniturn on 2007-11-06
Nessus tells me that my server (Edgy) has security holes due to vulnerabilities in PHP, and suggests upgrading to version 5.2.4.
Am I at risk? If so, what's the suggested procedure?
Many thanks
Toni

---

### Post by Tomek on 2007-11-08
Normally the ubuntu security team backports the security patches, so you should be on the safe side.

You can take a look at the source package:
[https://launchpad.net/ubuntu/+source/php5/](https://launchpad.net/ubuntu/+source/php5/)

Or at the changelog:
[http://changelogs.ubuntu.com/changelogs/pool/main/p/php5/php5_5.2.3-1ubuntu6/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/p/php5/php5_5.2.3-1ubuntu6/changelog)

---

