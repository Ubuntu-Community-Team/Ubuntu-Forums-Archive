---
title: "Am I losing connection to MySQL server because of my table size?"
date: 2015-05-21
forum: Server Platforms
---

### Post by stupidquestion on 2015-05-21
I'm testing my tables and kept inserting rows until a problem occurred. Phpmyadmin says my largest table currently has about 122 million rows. 

Problem is I'm now getting the following error if I do anything like "select count(id) from tbl" using the mysql prompt:
ERROR 2013 (HY000): Lost connection to MySQL server during query

Trying to browse the table in Phpmyadmin will say "loading" and then say the same thing,  "#2013 - Lost connection to MySQL server during query"

However it works if I ask for "select * from tbl where id = 1".

In my.cnf I've put:
connect_timeout=100
max_allowed_packets=64M

But that didn't help.

I still have free space left.

So is this problem caused by the size of the table, and if so how can I fix this?

---

### Post by SeijiSensei on 2015-05-22
How well indexed is the table?  With that many rows having well-designed indexes is critical.  Is the id field designated as the primary key?

Open a terminal window and run "top", then in another window run the query. You should see mysqld pop up to the top of the process list.  How long does it sit there?  I'm guessing the query is timing out.  

Selecting the record with id=1 is probably trivial, because it's at the top of the table.  How long does it take to select the row with id=100000000?  Are you going to be running an actual database in production with that many rows?

You might try installing PostgreSQL as well and seeing if it performs better.

---

### Post by stupidquestion on 2015-05-22
> **SeijiSensei said:**
> How well indexed is the table?  With that many rows having well-designed indexes is critical.  Is the id field designated as the primary key?

Open a terminal window and run "top", then in another window run the query. You should see mysqld pop up to the top of the process list.  How long does it sit there?  I'm guessing the query is timing out.  

Selecting the record with id=1 is probably trivial, because it's at the top of the table.  How long does it take to select the row with id=100000000?  Are you going to be running an actual database in production with that many rows?

You might try installing PostgreSQL as well and seeing if it performs better.

The table had indexes on some combinations of columns needed for some queries I was using, but id wasn't one of them (it's part of some combinations though; uniqueness depends on id and a couple other columns in the table). If I try to create an index on id now, it loses connection. 

I see mysqld as the top process for about 14 seconds for the select query, and then it timed out. 

Selecting id=n takes about the same time regardless of n's size. 

I don't think I'd be running that many rows initially but over time it's hard to say. It would not be practical for me to run a server with queries that typically take a very long time to execute though.

I tried to delete all rows greater than some id but it lost connection too after a couple minutes. If I try to delete a small range only then it works. But if I used a larger range I get a new error message:
#1205 - Lock wait timeout exceeded; try restarting transaction 

I haven't tried PostgreSQL before. How do you think it compares to MySQL?

---

### Post by SeijiSensei on 2015-05-24
I've used PostgreSQL since the mid-1990s.  At the time, MySQL was not open-source, so I could not install it on machines I sold to clients.  I only use MySQL when a particular application needs it like WordPress.  Since my experience with MySQL is pretty limited, I recommend looking at some of the comparisons in the articles listed here: [https://www.google.com/search?q=mysql+vs+postgresql](https://www.google.com/search?q=mysql+vs+postgresql)

---

