---
title: "Problem with intializing MySQL Database."
date: 2016-06-05
forum: Server Platforms
---

### Post by Abdullah_Khalid on 2016-06-05
Hi, I'm using Ubuntu 16.04 and used 
```
sudo apt-get install mysql-server php-mysql
```
to get MySQL server.

Now, I was trying to initialize it by:
```
sudo mysqld --initialize-insecure
```

OR
```
sudo mysqld --initialize
```

It gives me this error:
```
2016-06-05T18:24:48.573038Z 0 [Warning] TIMESTAMP with implicit DEFAULT value is deprecated. Please use --explicit_defaults_for_timestamp server option (see documentation for more details).
2016-06-05T18:24:48.580360Z 0 [ERROR] --initialize specified but the data directory has files in it. Aborting.
2016-06-05T18:24:48.582978Z 0 [ERROR] Aborting


```
How would I be able to fix this? Thank You.

---

### Post by Fire_Chief on 2016-06-07
Installing MySQL Server from the APT repository performs the initialization for you automatically. You should have been prompted during installation to set the MySQL root account password.

---

### Post by raja.genupula on 2016-06-08
Read this 

[http://askubuntu.com/questions/671121/cannot-install-mysql](http://askubuntu.com/questions/671121/cannot-install-mysql)

---

