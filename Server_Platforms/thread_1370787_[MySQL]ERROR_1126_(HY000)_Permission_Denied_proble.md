---
title: "[MySQL]ERROR 1126 (HY000) Permission Denied problem"
date: 2010-01-02
forum: Server Platforms
---

### Post by shedh on 2010-01-02
Hi,

On the ubuntu 9.10 server edition I have been trying to add the Maatkit plugin for MySQL, prior to 9.10 I haven't had a problem as such, This is the MySQL query that I am trying to run:

```
CREATE FUNCTION fnv_64 RETURNS INTEGER SONAME 'fnv_udf.so';

```

This is the error I keep getting:

```
ERROR 1126 (HY000): Can't open shared library 'fnv_udf.so' (errno: 22 /usr/lib/mysql/plugin/fnv_udf.so: failed to map segment from shared object: Permission denied)
```

The folders mysql & plugin, did not exist so i created them also i have changed the permission on the "mysql" & "plugin" folders and also the fnv_udf.so file to mysql:mysql

Any help given to this problem I am getting will be greatly appreciated in advance

Shedh

---

### Post by Vegan on 2010-01-02
Looks like the plug-in did not go so well.

I use it straight up without problem. The to make it work, I fed MySQL to PHP and my web site where it earns its keep.

What function does the plug-in provide?

---

### Post by shedh on 2010-01-02
I am trying to use the udf to create the function fnv64(), i used this on a Ubuntu 8.04 LTS Server on which it worked.

---

### Post by Vegan on 2010-01-02
Sounds like a dependency is broken.

---

### Post by shedh on 2010-01-03
What action would I need to take to fix the broken

---

### Post by johndunne on 2010-01-03
Anyone got any ideas on what's causing this error? I'm seeing to too when I try to add a new UDF to mysql (levenshtein distance to be precise). The process I follow for compiling and installing the udf worked perfectly on jaunty but since upgrading to karmic I'm unable to install this udf - nothing tricky. I've got the correct mysql sources (for the server running) for compiling against and all permissions are correct, so I'm at a loss! 

Anyone got any background info on this error? Thanks.

---

### Post by chinacode on 2010-01-26
:

---

### Post by chinacode on 2010-01-26
:popcorn:

---

### Post by grana on 2010-02-26
Try with [this solution]("http://forums.mysql.com/read.php?117,298997,300655#msg-300655")

---

### Post by busicode on 2011-08-29
u can see this bug,maybe it's helpful!

---

