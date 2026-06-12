---
title: "mySQL Error 1046 No Database Selected"
date: 2008-09-11
forum: Server Platforms
---

### Post by kmeth187 on 2008-09-11
Im new to linux and mySQL in installed mySQL on ubuntu and when I went to the terminal and started mySQL I tried to create a talbe. For example if I type the following: 

CREATE TABLE books (
title_id INT NOT NULL AUTO_INCREMENT,
title VARCHAR (150),
pages INT,
PRIMARY KEY (title_id));

I get the following back:

ERROR 1046 (3D000): No database selected

---

### Post by cariboo on 2008-09-11
You need to create a database before you can create a table. In the mysql console type:

```
create database <databasename>;
```

then

```
use <databasename>;
```

Where <databasename> is the name of your database.

Jim

---

