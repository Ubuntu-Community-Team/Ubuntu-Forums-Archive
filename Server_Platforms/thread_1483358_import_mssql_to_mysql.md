---
title: "import mssql to mysql"
date: 2010-05-14
forum: Server Platforms
---

### Post by jrtboht on 2010-05-14
It took a while but I got my home webserver setup and running with mysql.  Now I want to import a 70MB MSSQL backup file from my hosting company.  I noticed phpMyAdmin can import up to 2MB.  Any suggestions on how to do this for a larger file.  I do have access to the server running SSH so I'm not opposed to using the command line if I need to.

---

### Post by cdenley on 2010-05-14
> **jrtboht said:**
> It took a while but I got my home webserver setup and running with mysql.  Now I want to import a 70MB MSSQL backup file from my hosting company.  I noticed phpMyAdmin can import up to 2MB.  Any suggestions on how to do this for a larger file.  I do have access to the server running SSH so I'm not opposed to using the command line if I need to.

I highly doubt MSSQL backup files will be run by mysql successfully. If it were a mysql backup file:
```

mysql database -u root -p < mybackup.sql

```

---

### Post by jrtboht on 2010-05-14
Well, that didn't give me an error but you were right it didn't work.  I guess I'll have to try to find a program that can convert a mssql backup file to something mysql can import.  I'm up for any suggestions if anyone knows of one.

---

