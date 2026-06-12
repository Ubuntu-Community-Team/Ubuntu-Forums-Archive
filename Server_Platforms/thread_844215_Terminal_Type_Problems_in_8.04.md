---
title: "Terminal Type Problems in 8.04"
date: 2008-06-29
forum: Server Platforms
---

### Post by Bender NZ on 2008-06-29
Hi there,

We are starting to deploy 8.04 to replace our existing 6.06 VMware Guests and are running into problems with the terminal in 8.04 with some cron jobs.  In the cron log we are getting tons of:

No entry for terminal type "unknown";
using dumb terminal settings.
No entry for terminal type "unknown";
using dumb terminal settings.
No entry for terminal type "unknown";
using dumb terminal settings.
No entry for terminal type "unknown";
using dumb terminal settings.
No entry for terminal type "unknown";
using dumb terminal settings.
No entry for terminal type "unknown";
using dumb terminal settings.

I'm not sure what's causing it and Google is turning up very few hits on this.  Our crons appear to run fine, they are just producing a lot of this output so naturally it's driving me crazy with all the email.

Does anyone know how to fix this?

Thanks,

-Scott

---

### Post by mrpeenut24 on 2008-06-29
Does it specify which cronjob is producing the output?  Could you copy/paste the contents of the cronjob?

---

### Post by Bender NZ on 2008-06-29
Sorry, yes that would probably help:

sudo su - actionstep -c /home/actionstep/cron/backup_databases.php && sudo su - asbackup -c /home/actionstep/cron/offsite_wrapper.php

Basically the cron runs a php script to do a bunch of database dumps as well as taring up some files with the db dumps, and then runs a separate script that scp's them to our secondary site and marks them as backed up.

---

