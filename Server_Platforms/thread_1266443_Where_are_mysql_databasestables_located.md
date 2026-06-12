---
title: "Where are mysql databases/tables located?"
date: 2009-09-14
forum: Server Platforms
---

### Post by hockey97 on 2009-09-14
HI, I made a backup of my system and now reinstalled my system. So I need to put back the configs I saved. 

I saved the whole system before. To make sure I got everything I need.

My question is where would the database tables be located? I want to replace or move the old datatables/databases back into mysql.

any ideas?

---

### Post by DaithiF on 2009-09-14
Hi,
see /var/lib/mysql directory, there will be one subdirectory for each database.

---

### Post by hockey97 on 2009-09-14
thanks I found the backups. I also would like to know where would the users be stored? 

I want use a backup or will need to make a new user for mysql to be the same as before since my php scripts is uses the old user and password of mysql before.

---

### Post by DaithiF on 2009-09-15
user table, in mysql database.

```
use mysql;
select User, Host from user;

```

---

