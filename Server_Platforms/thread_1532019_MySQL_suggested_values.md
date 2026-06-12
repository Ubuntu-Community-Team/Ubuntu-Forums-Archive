---
title: "MySQL suggested values"
date: 2010-07-15
forum: Server Platforms
---

### Post by LepeKaname on 2010-07-15
Ok, this is not an Ubuntu topic but as it is related to Ubuntu Server, here I go...

I have a db server with 8GB RAM and I would like to give MySQL (InnoDB) as much as memory it may require to cache most of the requests. Which values would you recommend (I would like to reserve 2GB for anything else)? 

```

group_concat_max_len = 
max_allowed_packet = 
max_heap_table_size = 
max_connections = 
table_cache = 
query_cache_limit = 
query_cache_size = 
thread_cache = 
thread_stack =
thread_concurrency = 
key_buffer = 
sort_buffer_size = 
read_buffer_size = 
join_buffer_size = 
net_read_timeout = 
net_write_timeout = 
open_files_limit = 
```

Maybe just pointing out which of these settings are the most important to increase.

Thx.

---

### Post by richardjh on 2010-07-19
This is one of those "it depends" questions.

If you just want a good configuration that will mostly work without having to read up on mysql optimisation, and you have mysql installed you can find template configuration files in /usr/share/mysql/

You can start with my-innodb-heavy-4G.cnf. Just copy it to /etc/my.cnf and restart mysqld.

If you want to get a better idea of what setting you require specifically for your database, then run mysqltuner. It is available in the repos or from [http://mysqltuner.pl](http://mysqltuner.pl)

It is a perl script that you can run as a normal user by doing

```
perl mysqltuner.pl
```

You will of course need to enter the mysql administrators username and password to get results.

It will highlight any areas that need changing.

I would suggest you run this periodically for a reasonable amount of time. For example daily for three months. This will ensure you allow for the peak activity.

---

### Post by LepeKaname on 2010-07-19
I will use the my-innodb-heavy-4G.cnf as a base config and I will change some of the values I feel it may better fit my setup. 
I didn't know about the "mysql" tuner script, which I think it would be very very helpful. 

Thank you Richard! I'm glad I posted this question.

---

### Post by richardjh on 2010-07-20
No worries. I like getting the thanks so I am glad I posted the answer too. 

:)

---

