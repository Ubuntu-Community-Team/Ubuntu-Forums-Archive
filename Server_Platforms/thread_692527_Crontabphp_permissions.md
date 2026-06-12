---
title: "Crontab/php permissions?"
date: 2008-02-09
forum: Server Platforms
---

### Post by Ramthebuffs on 2008-02-09
I've just setup a home standalone server.  Previously I had a box with desktop and lamp installed and used nautilus to leave the www permissions wide open.

As of now I can run a php script by calling it through firefox on a different machine, but my cronjob isn't working.  I tried to set it under my user and as root and still nada.  Do I need to have permissions changed on the script, on cron, both?  I have php5-cli installed, here is what I have in cron just in case I've done something stupid */1 * * * * php /var/www/path to script.

Any help would be greatly appreciated.

---

### Post by faulkes on 2008-02-09
Specify the full path to php "/usr/bin/php /var/www/path/to/script" or try using wget instead (which would be exactly as if you had called the file from a browser).

faulkes

---

### Post by Ramthebuffs on 2008-02-09
Thanks, I don't know why I didn't think of wget.

---

