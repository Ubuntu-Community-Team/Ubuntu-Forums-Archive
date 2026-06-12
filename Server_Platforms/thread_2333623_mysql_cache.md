---
title: "mysql cache"
date: 2016-08-11
forum: Server Platforms
---

### Post by Vegan on 2016-08-11
Given I have 768MB of memory for my database, I was wondering if i could use more of it for MySQL

I was thinking 384MB cache would go far to speeding up web sites which would be feed largely from RAM instead of disk?

SET GLOBAL query_cache_size = 40000;

is see in the manual, but is this in byes, kilobytes or megabytes?

I wanted 384MB to use the available VM memory, if this is overkill is 256MB or 192MB better?

---

### Post by SeijiSensei on 2016-08-11
Remember that Linux already uses available memory to cache all disk transactions.  I doubt you'll see a substantial improvement in performance.

My WordPress site (see Blog link below) has essentially instantaneous response.  The other sites I've built from scratch all run on PostgreSQL, and they perform similarly.

---

### Post by Vegan on 2016-08-11
my vm is a pure database

---

