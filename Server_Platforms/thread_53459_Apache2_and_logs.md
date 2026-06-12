---
title: "Apache2 and logs"
date: 2005-07-31
forum: Server Platforms
---

### Post by SychoSly on 2005-07-31
I am running ubuntu and apache, mysql, php, and all that good stuff. I went into my logs directory for apache2 and they were taking up a lot of room on the system so I deleted everything that was in the folder and now apache doesn't produce any logs. 

Do I have to reinstall apache2? If so does that mean I have to uninstall it, and then reinstall it?

Thanks.

---

### Post by heimo on 2005-07-31
To restart Apache2:
 ```
sudo /etc/init.d/apache2 restart

``` 

You should probably just rotate the logs (man logrotate).

---

### Post by LordHunter317 on 2005-07-31
Apache logs shouldn't take up a lot of space unless you're getting lots of hits.

Deleting the active logfile won't cause apache to stop logging: it'll just log to the deleted inode; taking up space until the log is rotated.  Never delete a log file without a number appended to the name unless you know exactly what you're doing.

---

### Post by SychoSly on 2005-08-01
[QUOTE=heimo]To restart Apache2:
 ```
sudo /etc/init.d/apache2 restart

``` 

You should probably just rotate the logs (man logrotate).[/QUOTE]


Restarting Apache fixed it. Thanks.

---

