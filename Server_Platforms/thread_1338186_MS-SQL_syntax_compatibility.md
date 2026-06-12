---
title: "MS-SQL syntax compatibility ?"
date: 2009-11-26
forum: Server Platforms
---

### Post by WitchCraft on 2009-11-26
Is there any tool/plugin that makes MySQL/PostGreSQL syntax compatible with MS-SQL syntax ?

Or any SQL server that runs on Linux that is compatible to MS-SQL server syntax ?

---

### Post by koenn on 2009-11-26
what do you mean ? they both understand sql, which is a standard (barring some extensions)

---

### Post by WitchCraft on 2009-11-26
So much for the theory.

For the real world, just one example out of many:
Have you ever tried a select distinct on just one column when you have several columns?

One line with PostGre/MySQL, 12 lines with MS-SQL...

---

### Post by koenn on 2009-11-26
I suppose I have, and i don't remember anything peculiar about it.
I'll see if I have a a couple of databases lying around... see what it gives.

---

### Post by koenn on 2009-11-26
like this ?

mysql on linux:
```

mysql> select * from tblData01;
+----+---------------+--------+
| id | data1         | data2  |
+----+---------------+--------+
|  1 | Douglas Adams |     42 | 
|  2 | Hot Babe      |     69 | 
|  3 | Spam          |   NULL | 
|  4 | Spam          | 123456 | 
+----+---------------+--------+
4 rows in set (0.00 sec)


mysql> select distinct data1 from tblData01;
+---------------+
| data1         |
+---------------+
| Douglas Adams | 
| Hot Babe      | 
| Spam          | 
+---------------+
3 rows in set (0.03 sec)


```

ms-sql:
see attached screenshot


identical results, imo;

---

### Post by falconindy on 2009-11-26
Both aim to support ANSI SQL. The problem is, ANSI SQL is a very small language, and both MSSQL and mySQL fill in the gaps differently enough, e.g.:

'#' v. 'temp' for defining a temporary table
'top n' v. 'limit n' for limiting query sizes

---

### Post by WitchCraft on 2009-11-27
> **koenn said:**
> like this ?

mysql on linux:
```

mysql> select * from tblData01;
+----+---------------+--------+
| id | data1         | data2  |
+----+---------------+--------+
|  1 | Douglas Adams |     42 | 
|  2 | Hot Babe      |     69 | 
|  3 | Spam          |   NULL | 
|  4 | Spam          | 123456 | 
+----+---------------+--------+
4 rows in set (0.00 sec)


mysql> select distinct data1 from tblData01;
+---------------+
| data1         |
+---------------+
| Douglas Adams | 
| Hot Babe      | 
| Spam          | 
+---------------+
3 rows in set (0.03 sec)


```

ms-sql:
see attached screenshot


identical results, imo;

Yes, but you are querying ONE column.
Try several columns, but the distinct only on one.
Like: select distinct(column1), column2, column3 from tableXY WHERE
With ms-SQL, there's only: select distinct column1, column2, column3 from tableXY WHERE
which is the same as select distinct(column1, column2, column3) from tableXY WHERE
and that's not quite the same.
Of course that makes no difference if you only query one row, unfortunately, iff I had a program that simple and therefore small, I wouldn't search for an automation method... (if you know what I mean)

It's a one liner in both mysql and postgre, but 12 lines on ms-sql to achieve the same (assuming you select appx. 20 columns), including left joins, then I used the result of this to do a select * in where con1 cond2 ... condn


> **falconindy said:**
> Both aim to support ANSI SQL. The problem is, ANSI SQL is a very small language, and both MSSQL and mySQL fill in the gaps differently enough, e.g.:

'#' v. 'temp' for defining a temporary table
'top n' v. 'limit n' for limiting query sizes

Exactly, all the gazillion things of that kind.

And I don't want to rewrite all the SQL queries, so I am looking for perferably some kind of "compatibility module/layer" to postgres.

---

### Post by Vegan on 2009-11-27
What are you trying to achieve, I suggest sticking to the standard so that if a problem arises, you can change databases easily.

The SQL standard is old, and need to be updated.

Nonetheless I stick to it to be safe.

---

### Post by windependence on 2009-11-28
Vegan, you have no idea what you are talking about. Why comment if you don't know?

To the OP, what you are looking for is an ODBC driver. I just successfully had a client connect to my MySQL database from MSSQL using the ODBC driver and we did a push of data from MSSQL to MYSQL. Worked just fine.

More info:

[http://www.postgresql.org/docs/7/static/odbc.htm](http://www.postgresql.org/docs/7/static/odbc.htm)    #Postgres ODBC docs, looks good
[http://msdn.microsoft.com/en-us/library/ms811006.aspx?ppud=4](http://msdn.microsoft.com/en-us/library/ms811006.aspx?ppud=4)    #Article on using ODBC with MSSQL

Hope this helps. 

-Tim

---

### Post by koenn on 2009-11-28
> **WitchCraft said:**
> Yes, but you are querying ONE column.
Try several columns, but the distinct only on one.
Like: select distinct(column1), column2, column3 from tableXY WHERE
With ms-SQL, there's only: select distinct column1, column2, column3 from tableXY WHERE
which is the same as select distinct(column1, column2, column3) from tableXY WHERE
and that's not quite the same.
Of course that makes no difference if you only query one row, unfortunately, iff I had a program that simple and therefore small, I wouldn't search for an automation method... (if you know what I mean)
I'll take your word for it. I was merely trying to get a grasp on what exactly your issue is, and I'm beginning to see now.
I've only ever written small programs that involve only insert, update and select, and occasionaly a select distinct to populate a lookup-list, so that's probably why i didn't see the problem. 

> **WitchCraft said:**
>  ... including left joins, then I used the result of this to do a select * in where con1 cond2 ... condn

this sort of stuff sounds familiar, from a couple of migrations i was involved in. But those were just one-off ad hoc queries to extract data in a shape and form that could be inserted in the new database


> **WitchCraft said:**
> 
And I don't want to rewrite all the SQL queries, so I am looking for perferably some kind of "compatibility module/layer" to postgres.
Could you explain what it is you're trying to do, in context ? 
It sounds to me that you have an application or a set of queries that was written for MS SQL and you want to run them against mysql or postgre ? 
But in that case, do you really want to keep your queries in an MS-SQL syntax ? or is this just a temporary measure ?

---

### Post by WitchCraft on 2009-11-28
> **Vegan said:**
> What are you trying to achieve, I suggest sticking to the standard so that if a problem arises, you can change databases easily.

The SQL standard is old, and need to be updated.

Nonetheless I stick to it to be safe.

You cannot stick to the standard when you need to deliver software that is a bit more complex than an amoeba.

---

### Post by WitchCraft on 2009-12-18
bump.

---

### Post by WitchCraft on 2009-12-28
The answer is nhibernate. Solved.

---

### Post by WitchCraft on 2012-10-27
I revise my answer.
There now is [T-PostGres]("http://tpostgres.org").
That is what I was looking for in the first place, instead of an application level solution.

[http://tpostgres.org/se/tpg_about_us.jsp](http://tpostgres.org/se/tpg_about_us.jsp)

---

