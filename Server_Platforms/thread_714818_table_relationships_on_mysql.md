---
title: "table relationships on mysql"
date: 2008-03-04
forum: Server Platforms
---

### Post by jmwalloh on 2008-03-04
**Hi , how do you create table relationship in mysql?????**

---

### Post by Uaine on 2008-03-04
Just as a note, this is more of a MySQL question than an Ubuntu question.  You'll definitely get more help on a MySQL forum than you will here.  I'll give you enough info to help you get a start on learning this.

If you are familiar with database design, then your problem is probably that you need to use InnoDB as opposed to MyISAM.  Read more here [http://dev.mysql.com/doc/refman/5.0/en/ansi-diff-foreign-keys.html](http://dev.mysql.com/doc/refman/5.0/en/ansi-diff-foreign-keys.html)

If you are not familiar with database design, the concept to learn is foreign keys.  The way in which you implement the foreign key depends on the cardinality of the relationship (one to one, one to many, many to many). Read more about it here [http://www.functionx.com/sql/Lesson11.htm](http://www.functionx.com/sql/Lesson11.htm)

There's a lot more information out there that you can find with just a little googling.

---

