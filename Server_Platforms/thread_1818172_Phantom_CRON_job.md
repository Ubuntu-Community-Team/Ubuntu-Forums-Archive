---
title: "Phantom CRON job"
date: 2011-08-04
forum: Server Platforms
---

### Post by ChrisRChamberlain on 2011-08-04
Hi all

This is simplified code from CRONTAB
```
MAILTO=me@myserver.com
*/5 * * * /var/data/bin/zoneedit.sh

```

...and that runs as expected, checking ip addresses, etc at zoneedit.com.

What is seems to also be running is another CRON job, not included in the CRONTAB, which reports errors in Sent Mail of gmail```
Cron <root@myserver.com> /var/www/zoneedit.sh (failed)
/bin/sh: /var/www/zoneedit.sh: not found
```...every 15 minutes.

The error is correct as the file no longer exists.

Not sure how to locate this other CRON job and remove it?

TIA

---

### Post by skinnyquiver on 2011-08-04
Look in your /etc/cron.* directories
also you could watch lsof to see what files are open
you could try a grep as well, something like
grep "var/www/zoneedit.sh" /etc/cron.* -R

---

### Post by ChrisRChamberlain on 2011-08-04
skinnyquiver

Thanks for your reply.

Unable to locate any file containing the string 'var/www/zoneedit.sh' in  /etc/cron.* folders.

Nor does the grep command return anything.

---

### Post by skinnyquiver on 2011-08-04
try 
watch lsof
and when that triggers what new files get opened

---

### Post by ChrisRChamberlain on 2011-08-05
Any way to output that to a file as the result fills the command window and you cant't scroll to the last entry?

---

### Post by skinnyquiver on 2011-08-11
you could use 
lsof
but you would have to have good timing to time it when the job was running

---

