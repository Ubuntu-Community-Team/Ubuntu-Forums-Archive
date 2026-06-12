---
title: "Millions of CRON lines in auth.log"
date: 2018-02-09
forum: Server Platforms
---

### Post by Robert_Boutin on 2018-02-09
Please help me understand what's happening with my mail server.  My auth.log file is huge because of a CRON process running several times per minute.  I can't locate where I've somehow caused this to happen.  I appreciate any suggestions, attached pic is output that basically repeats to the tune of 3 million lines.

Thanks!

---

### Post by wildmanne39 on 2018-02-09
*Thread moved to **Server Platforms, a more appropriate forum**.*

---

### Post by LHammonds on 2018-02-09
It might be related to the logging level of your mail server.

---

### Post by SeijiSensei on 2018-02-09
The only way you can answer this is by looking at the contents of the various cron files:

/etc/crontab
/etc/cron.d/*
/etc/cron.[hourly|daily|weekly|monthly]/*
/var/spool/cron/root

Whatever is generating this seems to be running once a minute.  That makes it unlikely it's coming from the files in the hourly, daily, etc., directories.  Start with /etc/crontab, /var/spool/cron/root, and the files, if any, in /etc/cron.d/.

---

