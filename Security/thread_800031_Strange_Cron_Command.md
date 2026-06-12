---
title: "Strange Cron Command"
date: 2008-05-19
forum: Security
---

### Post by wh33t on 2008-05-19
Can anyone tell me what this might do?

```
[ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm
```

It's in my cron commands and set to execute as root.

---

### Post by cdenley on 2008-05-19
Basically, if /var/lib/php5 exsits, and any files in that directory were created recently, it runs the files. I'm not sure what purpose it has. That cron script seems to be installed by the php5-common package.

---

### Post by wh33t on 2008-05-19
Hrm. Does that really need to run as root? I guess it might if it's the PHP binaries.

---

### Post by cdenley on 2008-05-19
Sorry, it doesn't run the file if it's new, it deletes the file if it's old. Garbage collection, cleaning old sessions.

[http://oscarm.org/news/detail/666-debian_php5_and_session_garbage_collection](http://oscarm.org/news/detail/666-debian_php5_and_session_garbage_collection)
```

man test
man find
man xargs

```

---

### Post by wh33t on 2008-05-19
Thank you.

---

