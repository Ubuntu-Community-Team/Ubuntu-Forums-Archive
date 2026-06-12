---
title: "Logwatch and monitoring mysql syslog entries"
date: 2008-07-02
forum: Server Platforms
---

### Post by mikecrowe on 2008-07-02
Hi folks,

Anybody using logwatch to monitor their logs?  Since mysql dumps in syslog, I'm trying to figure out how to get those entries reported in a different category in the report.

Alternatively, what other recommendations would anybody advise to monitor server logs?

TIA
Mike

---

### Post by windependence on 2008-07-02
You can change the log location in MySQL and have it log to a different place. Make sure the directory exists first. You might want to use someting like /var/log/mysql.log

-Tim

---

