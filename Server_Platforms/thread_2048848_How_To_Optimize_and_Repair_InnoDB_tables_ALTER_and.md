---
title: "How To Optimize and Repair InnoDB tables? ALTER and OPTIMIZE table failed"
date: 2012-08-27
forum: Server Platforms
---

### Post by THPubs on 2012-08-27
I just switched my Wordpress databases to InnoDB. When using MyISAM, I used to run Optimize and Repair table. But it InnoDB, it won't work.

I manually ran OPTIMIZE TABLE and the suggested ALTER TABLE but non of them removed the overhead. I ran mysqltuner on my server and it showed that there are 14 fragmented tables (I have a total of 14 tables). Even after running optimize and alter tables, still all the 14 tables are fragmented! How can I properly OPTIMIZE and REPAIR InnoDB tables?

---

