---
title: "Fail to upgrade serve to 16.04LTS because of &quot;blacklist&quot; ?"
date: 2016-06-05
forum: Server Platforms
---

### Post by pcouderc on 2016-06-05
I am trying to update from 14.04LTS and it stops with following log messages :
```
2016-06-05 06:47:31,609 DEBUG Comparing 3.2.0-36 with 3.13.0-87
2016-06-05 06:47:31,610 DEBUG Comparing 4.4.0-22 with 3.13.0-87
2016-06-05 06:47:31,940 DEBUG blacklist expr '^postgresql-.*[0-9]\.[0-9].*' matches 'postgresql-plperl-9.3'
2016-06-05 06:47:31,940 DEBUG The package 'postgresql-plperl-9.3' is marked for removal but it's in the removal blacklist
2016-06-05 06:47:32,101 ERROR Dist-upgrade failed: 'Le paquet « postgresql-plperl-9.3 » est marqué pour suppression mais il est dans la liste noire des suppressions.'
2016-06-05 06:47:32,102 DEBUG abort called
2016-06-05 06:47:32,103 DEBUG openCache()
2016-06-05 06:47:32,103 DEBUG failed to SystemUnLock() (E:Non verrouillé)
2016-06-05 06:47:36,416 DEBUG /openCache(), new cache size 74378
2016-06-05 06:47:36,417 DEBUG enabling apt cron job
```

What should I do ? What is this blacklist ?

---

### Post by RobGoss on 2016-06-05
Hello welcome to the forum, I'm not sure what this list is but there have been a lot of issues trying to upgrade from **14.04 to 16.04,** I recommend doing a fresh installation and see if that works. If you're trying to upgrade I would not skip versions this maybe why so many people have trouble upgrading

---

### Post by howefield on 2016-06-05
Thread moved to the "*Server Platforms*" forum, probably a better fit.

---

### Post by pcouderc on 2016-06-05
I did remove the offending module : 
postgresql-plperl-9.3

It installs fine.
And now I am lost in migrating to postgresl 9.5

---

