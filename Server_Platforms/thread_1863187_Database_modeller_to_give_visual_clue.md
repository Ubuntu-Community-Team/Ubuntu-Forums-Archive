---
title: "Database modeller to give visual clue?"
date: 2011-10-17
forum: Server Platforms
---

### Post by QwUo173Hy on 2011-10-17
Can anyone recommend a database modeller that can import my database as exported in SQL and display the connections between all the tables (primary / foreign key relations etc).

I just want to paste in the SQL code of the database as exported from phpMyAdmin without actually connecting to the database.

Many thanks,
Jarlath

---

### Post by rubylaser on 2011-10-17
Didn't you do a mysqldump to create your file?  You can just cat the dumpfile and paste that into PHPmyadmin to accomplish what you're trying to do.

---

### Post by QwUo173Hy on 2011-10-18
> **rubylaser said:**
> Didn't you do a mysqldump to create your file?  You can just cat the dumpfile and paste that into PHPmyadmin to accomplish what you're trying to do.

I should have said that I want to see them graphically. Like this:

[http://www.dmp.cz/rt3d/onsi/diplomka/images/database_model.jpg]("http://www.dmp.cz/rt3d/onsi/diplomka/images/database_model.jpg")

---

### Post by rubylaser on 2011-10-18
Here are a couple [examples]("http://stackoverflow.com/questions/1694118/does-a-free-mysql-relationship-diagram-generator-exist").

---

### Post by QwUo173Hy on 2011-10-19
Thanks rubylaser. I know stackoverflow but I didn't have the right lingo in my search. There are a few results there that will do what I want. 

Thanks again,
Jarlath

---

### Post by rubylaser on 2011-10-19
No problem.  I hope one of those helps you out :)

---

