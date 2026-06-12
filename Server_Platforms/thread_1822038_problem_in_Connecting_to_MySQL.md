---
title: "problem in Connecting to MySQL"
date: 2011-08-10
forum: Server Platforms
---

### Post by NabiVakili on 2011-08-10
I installed MySQL and now I have a database on my Ubuntu 10.04 server. I want to connect to this database using C#. I founded a necessary DLL (MySQL.Data.DLL) and I added it to references in my C# project. 

I want to connect to MySQL with this connection string :
```
 server = "192.168.11.5";
       database = "myTestDB";
       uid = "myUserName";
       password = "myPassword";
         
       string connectionString;
       connectionString = "SERVER=" + server + ";" + "DATABASE=" + database + ";" + "UID=" + uid + ";" + "PASSWORD=" + password + ";charset=utf8;";
```

but I got the following error when connecting to server:
"Unable to connect to any of the specified MySQL hosts"

What should I do? Is there any needed configuration on Ubuntu server?

---

### Post by Bachstelze on 2011-08-10
The error message is not very helpful... Can you connect to the server using the CLI mysql client?

```
mysql -h 192.168.11.5 -u username -p
```

---

### Post by NabiVakili on 2011-08-10
I tried and I got this error :
ERROR 2003 (HY000): Can't connect to MySQL server on '192.168.11.5' (10061)

---

### Post by Bachstelze on 2011-08-10
By default, MySQL listens only on localhost. Have you changed that?

---

### Post by NabiVakili on 2011-08-10
I changed binding address from 127.0.0.1 to 192.168.11.5 in /etc/mysql/my.cnf 
It solved the problem!
Thank you.

---

