---
title: "cron question concerning webalizer commands"
date: 2007-03-26
forum: Server Platforms
---

### Post by huggy77 on 2007-03-26
i would like to run the command:
 webalizer -c  aerialphotosofnjWebalizer.conf

but for that script to work correctly it has to be run from a specific direcory:
/www/sites/foo.net/logs
 because that dir contains bot the script and the logs...

would this be terribly hard to add to the crontab??????

i have uber basic cron skills - all help is appreciated...

---

### Post by Mr. C. on 2007-03-27
From a Terminal window, write the code below to a file, let's call it updatewebalizer.sh :

```
#!/bin/bash

cd /www/sites/foo.net/logs
/fullpathto/webalizer -c aerialphotosofnjWebalizer.conf 2>&1 > /dev/null

```

Now change its permissions and ownership:
```
chmod a+rx updatewebalizer.sh
sudo chown root:root updatewebalizer.sh

```

Now decide how often you want the script to run.  If daily, place it in /etc/cron.daily.  If hourly, place it in cron.hourly, if monthly place it in /etc/cron.monthly.  For example, 

```
sudo mv updatewebalizer.sh /etc/cron.daily
```

to run it daily.

If you want different time periods, let us know what your requirements are.

MrC

---

