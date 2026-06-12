---
title: "how to back up myqul data base?"
date: 2009-09-14
forum: Server Platforms
---

### Post by rhythmiccycle on 2009-09-14
I am hosting a site from my pc.
I have LAMP and phpmyadmin installed.

is there a quick and easy to save and load databases and/or their tables.

The only thing i can think of is to copy the displayed data base and using code to rebuild it piece by piece. I am hoping someone knows a faster way.

(also, i run mysql code from php pages, how do i run mysql code directly w/o php)

---

### Post by scragar on 2009-09-14
```
mysqldump [options] db_name
```
In other words:
```
mysqldump -h **host** -u **username** -qQ -r **outputFile** **DATABASE_NAME**
```This will output a huge file containing everything in the database to outputFile using the quick method(-q) which means it won't wait to output data(Normally it buffers, which for large tables is a waste of ram and annoying). It will also backtick table and field names incase any of them are MySQL key words(Which are a good idea to avoid, but it's still worth adding backtick support, just in case).

---

