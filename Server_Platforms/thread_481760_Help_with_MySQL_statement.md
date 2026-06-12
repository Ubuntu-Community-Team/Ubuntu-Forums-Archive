---
title: "Help with MySQL statement"
date: 2007-06-22
forum: Server Platforms
---

### Post by Ptero-4 on 2007-06-22
Hi. I'm doing my final exam in sw development course and it's a practical one, the exam consists in building a Java app (for DOS with Jcreator for Windoze) that connects to a MySQL DB and lets the user add, modify, delete and look up entries. So far the add, delete and look up functions are done and work, but I just can't find what SQL statement can I use to alter the data on an already existing entry and it's proper sintax. And wanted to know. What statement do I use for modifying entries and what's it's sintax (the name of the table is "comision", and the name of the DB is "ventas")?

---

### Post by chippy99 on 2007-06-22
This isn't really a Ubuntu question and should be asked on an sql forum but I will give you a rough guide anyway ;)

update comision set [name of column] = [some value] where [name of column] = [some value];

I suggest you look at [http://www.w3schools.com/sql/sql_update.asp](http://www.w3schools.com/sql/sql_update.asp) which has an excellent tutorial on all things sql which you could have found very easily by searching for sql in google

---

