---
title: "Apache update automatically removes PHP5"
date: 2010-10-25
forum: Server Platforms
---

### Post by martinofmoscow on 2010-10-25
On a Ubuntu Server 10.04 VM running at [www.memset.com](www.memset.com) with all-standard applications added thru and managed by APT

This has happened twice now; the first time I has Cron automatically updating my virtual server - I have most definitely disabled this now! However, running apt-get upgrade this morning, the update again included an update to apache2 - first thing it did was display the words 'Removing PHP5' - not something you want to see on a production web server! Sure enough, right after the update, requests for pages result in an Internal Server Error.

Fortunately, an apt-get install php5 followed by a reboot solves the problem, but I'm annoyed this keeps happening. Anyone else have this problem?

Thanks,

Martin.

---

