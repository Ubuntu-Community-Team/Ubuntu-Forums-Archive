---
title: "Recommendations for SQL Query Builders for Linux Platform"
date: 2014-07-24
forum: Ubuntu, Linux and OS Chat
---

### Post by zoomiest2 on 2014-07-24
I have a LAMP-based MySQL database that I rely on, for my business. I currently use a VM to run windows, so I can use MS Access for the querying/reporting functions it has, to query, report, etc. on my ATS, through MySQL Connector ODBC connection.

Are there any good suggestions for another Linux-based SQL query builder replacement for MS Access? 

[LIST]
[*]I looked into LibreOffice Base a few years ago, and it never had an "update query" equivalent (need that to clean up data).
[*]I have installed MySQL Workbench, but I have yet to be able to get it to connect to my database (???!!!!)
[*]My hand-coding of SQL is weak, but I am not opposed to learning it. A GUI would be nice, but I am comfortable rolling up my sleeves.
[/LIST]

Any recommendations from the community would be fantastic.

/Zoomiest

---

### Post by oldfred on 2014-07-25
While I have installed MySQL, I have mostly been using SQLite.
But I learned my SQL from MS Access by converting the queries to show the sql and then copying sql into forms to execute them directly.

I had this in my notes but not used any of them.
 Alt to phpmyadmin
[http://www.adminer.org/en/phpmyadmin/](http://www.adminer.org/en/phpmyadmin/)
[http://squirrel-sql.sourceforge.net/index.php?page=screenshots](http://squirrel-sql.sourceforge.net/index.php?page=screenshots)

---

### Post by SeijiSensei on 2014-07-25
I vote for getting down and dirty and learning some SQL.  Viewing how your Access queries convert to SQL is a good start.

---

### Post by QIII on 2014-07-25
Using Access for reports is a good idea, since it is very easy to design very smart looking reports.

But do all the stored procedures, views and supporting user-defined functions on the real relational database side.  Access is inefficient and just does *not *perform the actual SQL stuff well -- and the 2GB size limitation is a killer.  

Access tends to collect chaff, and if you don't frequently compact you can hit that 2GB limit at the worst possible moment and corrupt the file.  Even if you do compact, Access will spontaneously become corrupted for no apparent reason at all -- so you need to back up frequently.

Access also allows you to develop really bad habits like having spaces in query and column names, using keywords as column names, etc.

Use a real database on the back end and use Access only for the reports.  If you need some special functionality, you can create some VBA functions to deal with that.  (VBA - shudder!  Another place to learn really bad habits!)

If you need to do some heavy lifting massaging or analysing data, you might need to write some middleware.  But it doesn't sound like you are looking at that.

But I have to say again ...  Access is really good for designing reports and I don't think there is an open source solution similar to it that can even come close.  Some may think this heresy, but I recommend using Windows and Access for your reporting.

---

### Post by zoomiest2 on 2014-07-25
Thank you oldfred - sounds like the path I will be on.
Thank you, SijiSensei. I still have my original SQL book, to dust off.
[COLOR=#000000][FONT=undefined]Thank you, QIII. LOL! At least I wasn't missing too much (MS Access for reporting) - I had better go compact that db. I haven't done the for some time. Thanks for the reminder, and also validation. [/FONT][/COLOR]

---

