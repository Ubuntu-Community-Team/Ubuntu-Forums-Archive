---
title: "MySQL incorrect key problem."
date: 2012-01-17
forum: Server Platforms
---

### Post by Nailox on 2012-01-17
Hi. On my server When I restart mysqld i get this
```

Checking for corrupt, not cleanly closed and upgrade needing tables..
root@server1:/tmp# ERROR 126 (HY000) at line 1: Incorrect key file for table '/tmp/#sql_69d5_0.MYI'; try to repair it 
```
I tried with mysqlcheck tool - all the tables are ok. How do I fix this error ? I cant even find this table anywhere - its not in /tmp. This error happened after I ran out of disk space. I dont think I need this table sql_69d5_0.MYI So I might as well find it and delete it but I can't find it anywhere.

---

