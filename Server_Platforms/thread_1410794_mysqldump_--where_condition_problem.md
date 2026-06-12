---
title: "mysqldump --where condition problem"
date: 2010-02-19
forum: Server Platforms
---

### Post by gkapo on 2010-02-19
Hello everyone,

i am trying to dump some rows from a mysql table using mysqldump and --where option but nothing comes up as a result.....

Below you can see the command i am typing

```
mysqldump -umyusername -pmypass mydb mytable --where="topic_id IN (SELECT id FROM topics WHERE catid=1 )" > /home/somefile.sql
```If i run the where condition into a phpmyadmin i get all the results i want, so i guess that there is nothing wrong with my query....

Can --where option in mysqldump get more complicated queries than 'catid=2' that i found in almost every example when i googled the problem?


Any help would be highly appreciated....
Thank you very much for your time

---

