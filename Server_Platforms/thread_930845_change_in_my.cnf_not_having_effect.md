---
title: "change in my.cnf not having effect"
date: 2008-09-26
forum: Server Platforms
---

### Post by nephish on 2008-09-26
hey all,

I am trying to bump the limit for max_heap_table_size from the default of 16777216 to a beefier 52428800. 

i have tried by useing set max_heap_table_size = 52428800
and also tried putting it in my.cnf and restarting MySQL and re-creating the table,
still when i do mysqld --verbose --help, it still shows me the value of 16777216.

How do i change this setting ?
thanks

---

### Post by iLLiCiTgr on 2008-09-26
have you tried changing any other settings on my.cnf to see if mysql actually reads it's conf the same file you are editing?

---

### Post by cariboo on 2008-09-26
Dumb question, but are you restarting mysql after making changes to the configuration file?

```
sudo /etc/init.d/mysql resart
```

Jim

---

### Post by nephish on 2008-09-26
yeah, i am restarting the sql server.
thanks

---

