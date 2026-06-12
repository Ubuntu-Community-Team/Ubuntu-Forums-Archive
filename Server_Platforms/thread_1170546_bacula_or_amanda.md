---
title: "bacula or amanda"
date: 2009-05-26
forum: Server Platforms
---

### Post by b4nsh33 on 2009-05-26
Hi, just want to know experiences of someone who has used both systems, im looking for an easy to mantein backup system, without complicated schedules, etc, just  backup 8-10 win/linux servers, daily (full or incremented) backups, may be weekly too, to local disk in a central server, i dont have a tape.

regards

---

### Post by windependence on 2009-05-26
Neither one of them is going to be easy if you are not an experienced Linux admin. You might do better using tar over ssh in a cron job. BTW, they are both excellent backup tools. I kinda like Amanda better but it's a matter of choice.

-Tim

---

