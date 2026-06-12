---
title: "trying to create a cron on ubuntu server 14.04"
date: 2014-06-25
forum: Server Platforms
---

### Post by tinatequila on 2014-06-25
I've been trying to create a cron that doesn't seem to be working. i'm running Ubuntu server 14.04. for testing i've set my cron to run every minute.

it's a php script that i'm trying to run as a cron, and it runs fine via the command line. for test purposes and to make sure i'm not blocked by permissions, i've created the cron as 'sudo crontab -e' (i'm the root user anyway, and i do everything as root from the directory… /var/www/html/)

i've searched high and low, been reading loads (much that seems confusing, or pretty straight forward) and can't figure out why it's not working. I've given a couple of my examples. the output of the script is just a simple creation of a table in mysql (this is how i'm checking if it's working). besides creating the cron (shown in the examples below), is there anywhere else i'm meant to do something to get it working, like a specific config file located somewhere?

if anyone can help, is it possible that you could give me exact step by step instructions on creating the cron, so i don't miss anything?

example 1

```

* * * * * /var/www/html/test/index.php

```

example 2

```

SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
MAILTO=me@myemail.com

* * * * * /var/www/html/test/index.php

```

---

### Post by tinatequila on 2014-06-25
just got it working. this is the correct code,

* * * * * php /var/www/html/test/index.php

was able to figure it out after reading this post... [http://askubuntu.com/questions/430509/cannot-run-cron-job-for-a-php-script/430664#430664](http://askubuntu.com/questions/430509/cannot-run-cron-job-for-a-php-script/430664#430664)

---

