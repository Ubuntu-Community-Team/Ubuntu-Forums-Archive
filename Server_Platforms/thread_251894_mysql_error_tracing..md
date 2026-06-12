---
title: "mysql error tracing."
date: 2006-09-06
forum: Server Platforms
---

### Post by dmizer on 2006-09-06
i need to know how to trace down the cause of an error i'm getting from mysql.

i'm using a modified php script, and i'm not real whippy with it yet.  i'm sure i've made an error, but i have no idea where.

the error is as follows:
MySQL error number 1136: Column count doesn't match value count at row 1

could be something as simple as missed punctuation, but i really have no idea what part of the script to concentrate on.

what's more, i have identical installations on two different servers.  i get the error on one installation, but not on the other :-k 

really, i just need some troubleshooting tips ... please help.

---

### Post by kidders on 2006-09-06
Are you certain everything's identical in both places? It sounds to me as though you've missed a punctuation mark! What's the SQL code?

---

### Post by dmizer on 2006-09-06
i copied the entire folder from one machine to the other.  it must have lost something in the transfer though because i was able to fix the problem by deleting the db and reinstalling the program from scratch.

since there was no data in the db, i decided that it was faster for me to simply reinstall than to try to spend more time tracing down punctuation errors or the like.

my modifications took a little time to reimpliment, but everything seems to be okay now.

---

### Post by kidders on 2006-09-06
Ah. Copying directory structures is not a recommended way of carting databases around ... a far better solution is to mysqldump them.

---

### Post by dmizer on 2006-09-06
does a mysqldump include all the php scripting?  i mean, i didn't transfer anything from the sql database itself.  just the php and css files.  then when i just changed the db access commands in the configure.php file, and i was up and running again.  i've done it this way several times.  is there another more appropriate way to move the php stuff around?

---

### Post by kidders on 2006-09-06
No sorry... doing that is fine :) You seemed to refer to deleting and re-creating your DB in one of your last posts. I must've misunderstood.

All the best!

---

