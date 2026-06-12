---
title: "How to cut a log file ?"
date: 2008-06-17
forum: Server Platforms
---

### Post by consoko on 2008-06-17
The log file of apache is too large, i can't open it. Now i want devide 
it smaller to open.

And i want limit log file of apache to 50mb, if it exceed 50mb, it create a new file.

Can you help me? Thanks all.

---

### Post by windependence on 2008-06-17
> **consoko said:**
> The log file of apache is too large, i can't open it. Now i want devide 
it smaller to open.

And i want limit log file of apache to 50mb, if it exceed 50mb, it create a new file.

Can you help me? Thanks all.

If you just want to look at the last part of the log you can do:

```
tail /var/log/apache2/error.log 
```

Or if you want to look at a specific number of lines:

```
tail -n 100 /var/log/apache2/error.log 
```

The above statement displays the last 100 lines of the log file.

The logs should be rotating on their own and being zipped into smaller files. If not, you may have other problems.

Just wanted to add, you can check your /etc/logrotate.d/apache2 to see how it is set up. You may want to change the rotate interval to something more frequent.

Also you can try sudo logrotate -f to force a log rotation when it isn't scheduled by cron.

-Tim

---

