---
title: "PostgreSQL Upgrade"
date: 2005-09-09
forum: Server Platforms
---

### Post by amerigo5 on 2005-09-09
I upgraded my system from Hoary to Breezy PR.  Currently, I still have PostgreSQL 7.4 installed.  How should I upgrade it to PostgreSQL 8.0?  Should I simply use Synaptic and install PostgreSQL 8.0 (8.0.3-14)?

I currently have databases in PostgreSQL and don't to re-create them. 

Thanks.

---

### Post by LordHunter317 on 2005-09-09
You'll have to recreate them as moving from 7.4 to 8.0 isn't binary compatible.  The procedure is roughly:[list=1][*]Dump the databases out of 7.4[*]Stop the DB server[*]Install the 8.0 packages. [*]Restore the databases from the dump[/list]  Don't forget to save a copy of your 7.4 pg_hba.conf and your user account information if necessary before running.

Also, the 7.4 dumps may not be perfect and may need manual massaging to load.  pg_dump before 8.0 isn't perfect.

---

### Post by amerigo5 on 2005-09-11
That works. Thanks!!!

---

### Post by LordHunter317 on 2005-09-11
Also, if you have any issues with the migration in terms of compatibilty, you can install 7.5 alongside 8.0, which may be more compatible.  It does AFAIK, also require a dump/restore procedure, but if there's some behavior you're reliant on that 8.0 doesn't work with, it's worth looking into.

---

### Post by derrick1985 on 2007-02-02
How were you able to restore your dump? I have a postgresql DB for sql-ledger I need restored.

---

