---
title: "Missing mysql-query-browser?"
date: 2012-03-04
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by The Cog on 2012-03-04
Has it been renamed, or am I doing something silly? I can't find it in synaptic.

---

### Post by Irihapeti on 2012-03-04
It and mysql-administrator have both been removed from the repositories, possibly because they were official MySQL offerings (that's only my guess).

Unfortunately, I haven't found other programs that do as good a job, other than phpmyadmin. And that requires a webserver, which not everyone wants to run.

---

### Post by effenberg0x0 on 2012-03-05
> **Irihapeti said:**
> It and mysql-administrator have both been removed from the repositories, possibly because they were official MySQL offerings (that's only my guess).

Unfortunately, I haven't found other programs that do as good a job, other than phpmyadmin. And that requires a webserver, which not everyone wants to run.

There's emma in the repos. It had some capabilities, more in the sense of a MySQL client: Running queries, editing tables, looking at some table info and processes, also users (if I remember correctly - not sure). But it was far from a complete product for managing DBs. You might want to have a look at it, maybe it has evolved since the last time I tested it.

Regards,
Effenberg

---

### Post by Irihapeti on 2012-03-05
I tried emma and found it didn't do what I wanted. Ditto with the other offerings in the repos. Mysql-administrator allowed one to do pretty much everything.

Thanks for the suggestion, though.

---

### Post by effenberg0x0 on 2012-03-05
What about mysql-workbench? [http://dev.mysql.com/downloads/workbench/5.2.html](http://dev.mysql.com/downloads/workbench/5.2.html) It has 32 and 64 bit deb downloads that work OK on Ubuntu 12.04.

Regards,
Effenberg

---

### Post by Irihapeti on 2012-03-05
> **effenberg0x0 said:**
> What about mysql-workbench? [http://dev.mysql.com/downloads/workbench/5.2.html](http://dev.mysql.com/downloads/workbench/5.2.html) It has 32 and 64 bit deb downloads that work OK on Ubuntu 12.04.

Regards,
Effenberg

I've downloaded and installed it, and it looks much more promising. Thanks!

---

### Post by Elfy on 2012-03-05
Being curious - especially about things I never use - [http://dev.mysql.com/downloads/gui-tools/5.0.html](http://dev.mysql.com/downloads/gui-tools/5.0.html)

Looks like effenberg hit the nail on the head.

Can't find any reference to mysql-query-browser anywhere though and now mu curiosity is quenched.

---

### Post by Irihapeti on 2012-03-05
It also says on the MySQL site that mysql-query-browser and mysql-admin have been discontinued. mysql-workbench is intended to replace them.

---

### Post by The Cog on 2012-03-06
Hmm. MySQL Workbench seems quite usable. I guess I'll soon be using that instead of query-browser. Workbench doesn't seem to be in the repositories either, but at least it's downloadable.

Thanks for the help.

Edit:
Actually, I think I like workbench.

---

