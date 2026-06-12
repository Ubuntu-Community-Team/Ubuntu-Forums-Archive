---
title: "mysqldump Database Name Issues"
date: 2006-08-22
forum: Server Platforms
---

### Post by charlie. on 2006-08-22
I use mysqldump to backup my database, named "mydb-live". When I try to restore the backup to another database, say "mydb-dev", I get an error along the lines of "Cannot Find `ßßß`.my_table", where "ßßß" is a string of rubbish extended-ascii characters.

I tracked this error down to the presence of the database name in a CREATE VIEW statement. (The view used a user defined function defined in my database, in the dump, that came out as `mydb-live`.`myuserdefinedproc`() ) I know that this was causing the error because removing the "`mydb-live`." part fixed the script and allowed it to restore perfectly.

As a temporary solution, I added this line to my backup bash script:

```
sed -i 's/`mydb-live`.//' backup.sql
```

Is there a better way to do this? Is there a switch that I can pass to mysqldump to prevent it from writing "`mydb-live`." instead of just the UDF name?

Thanks.

---

