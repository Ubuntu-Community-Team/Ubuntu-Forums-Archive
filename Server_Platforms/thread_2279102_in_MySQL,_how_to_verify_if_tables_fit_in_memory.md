---
title: "in MySQL, how to verify if tables fit in memory?"
date: 2015-05-20
forum: Server Platforms
---

### Post by stupidquestion on 2015-05-20
This is what I've read so far:

SELECT FLOOR(SUM(data_length+index_length)/POWER(1024,2)) InnoDBSizeMB
FROM information_schema.tables WHERE engine='InnoDB';

If this number is smaller than innodb_buffer_pool_size, then it can fit in memory.

I understand that innodb_buffer_pool_size has to be specified my.cnf, which I did.

My quesiton is, how do I verify that the current running size of innodb_buffer_pool_size, to make sure there are no problems?

---

### Post by stupidquestion on 2015-05-21
The answer I found was this:

MySQL 5.0+

SHOW VARIABLES LIKE 'innodb_buffer_pool_size';

MySQL 5.1+

SELECT variable_value FROM information_schema.global_variables
WHERE variable_name = 'innodb_buffer_pool_size';

---

