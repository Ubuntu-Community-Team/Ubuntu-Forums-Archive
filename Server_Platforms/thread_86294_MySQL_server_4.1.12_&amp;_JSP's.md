---
title: "MySQL server 4.1.12 &amp; JSP's"
date: 2005-11-04
forum: Server Platforms
---

### Post by NaughtyusMaximus on 2005-11-04
I recently upgraded the version of MySQL on my server from 4.0.x to 4.1.12, and am having problems running prepared statements. The following java code worked before, but now returns an error:

```
String sql = "INSERT INTO personalInfo("
+ "sinno,"
+ "lname,"
+ "fname,"
+ "mname,"
+ "email,"
+ "mstatus,"
+ "yrs,"
+ "mths,"
+ "days,"
+ "title)"
+ "VALUES(?,?,?,?,?,?,?,?,?,?)";
PreparedStatement pstmt = con.prepareStatement(sql);

pstmt.setString(1, sin);
pstmt.setString(2, lname);
pstmt.setString(3, fname);
pstmt.setString(4, mname);
pstmt.setString(5, email);
pstmt.setString(6, mstatus);
pstmt.setString(7, yrs);
pstmt.setString(8, mths);
pstmt.setString(9, days);
pstmt.setString(10, title);
pstmt.executeUpdate();
```

The error is:
"java.sql.SQLException: Incorrect arguments to mysql_stmt_execute"

Help!

---

### Post by LordHunter317 on 2005-11-04
You likely needto update your JDBC driver.

---

### Post by NaughtyusMaximus on 2005-11-05
Okay, I'll try that.  The mysqlconnector I'm using is the same version as the one that is working on a different computer using MySQL 4.1.14 though, so I had assumed that this wouldn't be the problem:???:

---

### Post by NaughtyusMaximus on 2005-11-05
That didn't work :(

The strange thing is that I know that prepared statements would execute fine a week ago, and after more reflection it wasn't the MySQL update that created the problem.  I downgraded to the older version again with no change.

Of course I can't think of whats changed since then (very little if anything), but definetly tomcat and java aren't any of the things that might have been modified.

I can't for the life of me think of why regular SQL statements would execute perfectly, but prepared statements wouldn't.

---

### Post by mindhaq on 2005-11-14
I can confirm this bug regarding PreparedStatements. And I have no solution yet. In another thread, one suggests manually upgrading to the latest mysql version, but I already have enough packages I need to keep up-to-date manually :(

---

### Post by NaughtyusMaximus on 2005-11-14
The strange thing is that it seems to be only with jdbc and INSERT prepared statements.  SELECT works fine.

---

### Post by mindhaq on 2005-11-18
This bug is also discussed on the MySQL.com forums as well:

[forums.mysql.com]("http://forums.mysql.com/read.php?39,49989,49989#msg-49989")

According to those posts, this seems to be a Debian/Ubuntu-only issue. I wonder how we could point the package maintainers to this information?

Until then here is a workaround for the this; you need to set the mysql-connection property "UseServerPreparedStmts" to false. According to the  [MySQL-Documentation]("http://dev.mysql.com/doc/refman/4.1/en/cj-configuration-properties.html") you set such properties in one of those ways:
> 
[LIST][*]Using the set*() methods on MySQL implementations of java.sql.DataSource (which is the preferred method when using implementations of java.sql.DataSource): 

com.mysql.jdbc.jdbc2.optional.MysqlDataSource 
com.mysql.jdbc.jdbc2.optional.MysqlConnectionPoolDataSource 


[*]As a key/value pair in the java.util.Properties instance passed to DriverManager.getConnection() or Driver.connect() 


[*]As a JDBC URL parameter in the URL given to java.sql.DriverManager.getConnection(), java.sql.Driver.connect() or the MySQL implementations of javax.sql.DataSource's setURL() method.[/LIST]


With my setup, using Tomcat 5.5, the last method does not work, but that seems to be another, rather unrelated problem. Because of that, I changed my code so that I generate my Connections without JNDI, and changed the property via the setUseServerPreparedStmts() method. After that, my statements worked again flawlessly. 
I never tried the second option.

All I can add at the moment, is that I also had problems using "normal" statements with nothing but a simple select all. There wasn't an error, but the results where simply empty, although they shouldn't be.

---

### Post by NaughtyusMaximus on 2005-11-18
Thank you very much for finding this hack!

---

### Post by kcypers on 2006-05-21
Because some of the nerds in my classroom absolutely wanted the shared MySQL server to be upgraded, we got stuck with this bug too and all other students could change their code. ](*,) It took us a week of discussions to solve the problem, but this hack works well. Adding the URL parameter, as discussed in mindhaq's post, works fine over here. My connection URL becomes:

```
jdbc:mysql://localhost/database?user=username&password=pw&useServerPrepStmts=false
```

Thanks, mindhaq!

---

### Post by adamkane on 2006-05-21
If MySQL is working, don't upgrade.

---

### Post by englert.james on 2007-01-18
Thanks for the excellent solution!!

---

