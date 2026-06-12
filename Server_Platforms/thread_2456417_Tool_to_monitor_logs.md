---
title: "Tool to monitor logs"
date: 2021-01-11
forum: Server Platforms
---

### Post by fernandoch on 2021-01-11
Hello,

What do you recommend to monitor logs and send alerts in case of problems?

For Apache, Mysql, and some other logs...

Thanks

---

### Post by LHammonds on 2021-01-12
I tend to monitor services to ensure everything is running as it should such as MariaDB responding to queries, web sites replying with an OK response, disk space, RAM/CPU/Swap utilization, zombie process, etc.  I use Nagios to monitor these services with warning and error event thresholds.

LHammonds

---

### Post by fernandoch on 2021-01-13
No simpler way to just grep for errors and send an email in case of a problem?

Any guides for Nagios you could recommend?

---

### Post by LHammonds on 2021-01-13
> **fernandoch said:**
> No simpler way to just grep for errors and send an email in case of a problem?
Well, wouldn't you need to EVERY error message/code in order to know what needs to be emailed or not?  You might grep for "ERROR" but what if one of the messages said "CRITICAL" instead?  You could miss that.

> **fernandoch said:**
> Any guides for Nagios you could recommend?I have a setup guide in my sig but it is for Ubuntu 18.04.  I also did not complete the tutorial 100% since I never quite perfected the Windows client monitoring (I tried to make the old way of installing work and the client really wanted to install via MSI) but 98% of all the steps should still work fine.

LHammonds

---

