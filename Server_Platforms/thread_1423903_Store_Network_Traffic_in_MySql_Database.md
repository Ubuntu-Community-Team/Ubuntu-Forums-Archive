---
title: "Store Network Traffic in MySql Database ???"
date: 2010-03-07
forum: Server Platforms
---

### Post by sanketdangi on 2010-03-07
Hey All,
I am working on a project on Green Computing.

I want to know that how can i store network traffic in MySql Database. What i want to do is identify no of client requests hitting a server throughout the day...I have to store no. of request hitting a server in every 15 mins and insert that into database so that i can obtain a network traffic pattern.

I searched for a tool but cudn't find any that satisfy my requirements..

Plz suggest sumthing !!!

Regards,
Sanket Dangi

---

### Post by Vegan on 2010-03-07
You will need to create a database account in the mysql console.

```

mysql -u root -p

CREATE DATABASE traffic;

GRANT SELECT, INSERT, UPDATE, DELETE, INDEX, ALTER, CREATE, DROP ON traffic.* TO 'trafficuser'@'localhost' IDENTIFIED BY 'dbpassword';

```


naturally use a password that is more secure

You might want to bone up on administering a database.

Now inside you page, you will need PHP and a install page to create the table and so on, then the database can he updated with each visitor.

If you need more help, I can help you build such a site but its costly.

---

### Post by sanketdangi on 2010-03-08
Hey 
Thanks for Ur Reply !!!

Can u please elaborate what u mean to say ?? I understood abt database creation but not about php and wat page ??

Sanket !!

---

### Post by dragos2 on 2010-03-08
Parse the web server access log and store that data inside the tables.

---

