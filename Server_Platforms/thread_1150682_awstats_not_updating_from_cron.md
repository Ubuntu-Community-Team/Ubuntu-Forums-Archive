---
title: "awstats not updating from cron"
date: 2009-05-06
forum: Server Platforms
---

### Post by bjk03 on 2009-05-06
For about the past week or so awstats will not update from the cron job I setup. If I update it manually the stats are updated. Here is what is supposed to run from cron. ```
0 2 * * * www-data [ -x /usr/lib/cgi-bin/awstats.pl -a -f /etc/awstats/awstats.conf -a -r /var/log/apache2/access.log ] && /usr/lib/cgi-bin/awstats.pl -config=www.fayette.k12.oh.us -update >/dev/null
```

This on Ubuntu 8.10

---

### Post by bjk03 on 2009-05-11
Also the stats will update if I run the following manaually```
/usr/lib/cgi-bin/awstats.pl -update -config=www.fayette.k12.oh.us -configdir=/etc/awstats
```

Anyone got any ideas??

---

### Post by rkelly on 2009-05-19
> **bjk03 said:**
> Also the stats will update if I run the following manaually```
/usr/lib/cgi-bin/awstats.pl -update -config=www.fayette.k12.oh.us -configdir=/etc/awstats
```Anyone got any ideas??

So your config for awstats sits in /etc/awstats/awstats.[www.fayette.k12.oh.us.conf](www.fayette.k12.oh.us.conf) ?

Check /usr/share/doc/awstats/ for some examples on how to setup and run awstats.
My server updates awstats for a number of domains daily from a cron script. I took awstats-update as a starting point.

---

### Post by bjk03 on 2009-05-19
I think it was a permission problem. They run from the cron job when its run as root but not when its run as www-data.

---

