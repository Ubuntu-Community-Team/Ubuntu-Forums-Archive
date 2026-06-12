---
title: "MSSQL to MySQL"
date: 2010-12-11
forum: Server Platforms
---

### Post by K7522 on 2010-12-11
Does anyone have a simple to use bash script or some such that will convert MSSQL dump files to MySQL formatted dump files?

Thanks.

---

### Post by amauk on 2010-12-11
I'm not quite sure what a "dump file" is, but phpmyadmin can understand MSSQL's dialect of SQL and import it into a MySQL database

Is this what you're asking?

---

### Post by K7522 on 2010-12-11
It is, however the file is 330mb in size and would be inefficient to use phpmyadmin since the file is already on the server.

---

### Post by SeijiSensei on 2010-12-12
Have you tried reading the file into the command-line mysql client?  

```
mysql -u user -p database < dump-file
```

You might be able to track down any syntactic oddities and fix them manually.  

If you're not committed to MySQL, you might try importing the file into PostgreSQL instead.

Another possibility is to use ODBC to connect to both the MSSQL and MySQL databases and transfer the data with a client like MS Access.

---

### Post by elico on 2010-12-12
i was thinking about thw ODBC thing.
i used it before.
what i did was to install java mysql odbc driver on the MSSQL server and then used the MySQL migration wizard to transfer information from one server to another and it wasnt that efficient for this specific 1.1 GB database.

---

### Post by i_am_lost on 2010-12-12
Not all data-types or encodings export from MSSQL properly.  Install your LAMP stack, and then PHPmyAdmin.  It will handle most detection, but you may have to split your SQL/CSV dump into smaller chunks.   Best of luck, J

---

### Post by elico on 2010-12-13
it's 330 MB file so i wouldn't  count on the small chunks part...
maybe you will need to now what you are doing while copying the information from one server to another but still.. you must know your current database structure !!
you can always first try it using mysql as replication server in the MSsql server.
first you set it as replication server and try to replicate the data.
if it works fine then you are pretty done and the next thing is to make sure that your application supports mysql make sure that you have the right mysql settings and permissions and you are good to go,

---

