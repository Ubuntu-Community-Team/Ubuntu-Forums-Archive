---
title: "PG_dump + phppgadmin + apache error"
date: 2012-09-23
forum: Server Platforms
---

### Post by pesha on 2012-09-23
Hi all,

my problem is I cannot export anything through PhPPgAdmin because of following error:

```
Export error: Failed to execute pg_dump (given path in your  conf/config.inc.php : /usr/lib/postgresql/8.4/bin/pg_dump). Please, fix  this path in your configuration and relog.
```I'm sure the path is right (there was different one originally, I changed the path to actual location of the file), if I copy & paste the path to command line, it's working properly.

There's nothing in log of Postgresql and following line in log of Apache:

```
sh: 1: /pg_dump: not found
```I'm using Postgresql 8.4.11, Apache 2 and PhPPgAdmin 5.0.4.

I have no idea why is it not working so any help would be appreciated!

---

