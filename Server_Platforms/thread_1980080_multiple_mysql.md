---
title: "multiple mysql"
date: 2012-05-14
forum: Server Platforms
---

### Post by jhayes on 2012-05-14
so lets say i have more than one instance of mysql running.
what do i do to check to make sure they are both running?
tried this  : ps  -ef | grep -i sqlroot
but i don't think i9t returned valid info.

---

### Post by anonymouschief on 2012-05-15
> **jhayes said:**
> so lets say i have more than one instance of mysql running.
what do i do to check to make sure they are both running?
tried this  : ps  -ef | grep -i sqlroot
but i don't think i9t returned valid info.

Try:
```
ps -ef | grep mysqld
```

I do not know what the -i does to "grep", but I get the same result whether or not I include it.

Alternatively, install htop then sort the results by "Command" using "F6".

---

### Post by jhayes on 2012-05-16
ok sounds good.
sounds like something starting with ps, with a mysql filter .. basically what i was thinking.

---

