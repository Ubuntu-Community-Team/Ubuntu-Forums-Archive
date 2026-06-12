---
title: "MySQL List Schema"
date: 2012-10-02
forum: Server Platforms
---

### Post by mike acker on 2012-10-02
this is a pretty basic n00b question, --

in MySQL: how do I list a Schema--

I can get into the MySQL Workbench and alter the table to see its structure and I'm good with that. but for people who need a print copy I should be able to do something sort of like this:

SELECT * from <tables> where schema_name in ("xyz_test.patrons")

I should be able to save this as a view and then set up a LibreOffice report to print from it...

---

### Post by LHammonds on 2012-10-02
Doesn't the workbench tool have [reverse engineer database]("http://www.mysql.com/products/workbench/design/") option?
 1. Open WorkBench
 2. Create connection to MySQL server/database
 3. Create ERR Model from Existing Database
 4. Select all table objects, from the menu, click Arrange, AutoLayout
 5. Share diagram with whoever you want...can export to PDF, PNG or even the .sql file to re-create the database.

Here are a couple other options:

[http://schemaspy.sourceforge.net/](http://schemaspy.sourceforge.net/)

[http://code.google.com/p/database-diagram/](http://code.google.com/p/database-diagram/)

---

### Post by volkswagner on 2012-10-02
I'm not sure if this is what you are after.  

I have always had a hard time with differences in MySql vs MS Sql.  I don't think MySql has the same definition for "SCHEMA".  I think mysql schema = database, where MS Sql database can contain a schema.

Anyway, what do you think of the following?

```

use information_schema;
select DISTINCT TABLE_SCHEMA from TABLES WHERE TABLE_TYPE ="BASE TABLE";
```

I think the first line can be omited if you log into MySql without specifying a database.

You may want to drill down using an identifier for TABLES like xyz_test.

---

