---
title: "amavis-stats"
date: 2009-05-01
forum: Server Platforms
---

### Post by Dy1anW on 2009-05-01
Not sure if anyone is still using this as it appears to be discontinued(?)

This was how I installed it (as su):

cp /etc/amavis-stats/apache.conf /etc/apache2/sites-available/amavis-stats
a2ensite amavis-stats
/etc/init.d/apache2 reload

Starting up firefox and heading to mydomain.com/amavis-stats I get the daily, weekly, monthly and yearly graphs.  Strangely all it shows are the mails that passed, and nothing on spam or viruses I deliberately sent to myself (though logs show them to be blocked/bounced).  I also get a little message under each graph that reads:

amavis-stats::error :rrdgraph():

Anyone know what went wrong?

---

### Post by gencha on 2010-05-12
Did you ever fix this? I'm having a similar issue, except I don't get the error you are mentioning.

---

