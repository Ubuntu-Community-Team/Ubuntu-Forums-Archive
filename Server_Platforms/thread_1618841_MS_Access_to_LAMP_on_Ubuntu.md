---
title: "MS Access to LAMP on Ubuntu"
date: 2010-11-11
forum: Server Platforms
---

### Post by astabeno on 2010-11-11
I am planning on migrating an existing Access database which contains one mdb file of only data, and on other that our employees have of access applications that work as a front end.  As you can imagine we have lots of corruption problems.

My plan is to convert the back-end to MySQL on an Ubuntu virtual machine.  Then point the access app to the back-end MySQL database.  Later start writing PHP applications to take the place of the access applications.

I have done some research on tools such as DBForms and DBTools that could help this process.  I would love to here from anyone with experience in this.  We are an American English training center in Jordan and have Arabic script in our data.

---

### Post by Ryan Dwyer on 2010-11-11
I would do it in a one step procedure instead of making Access read a remote datasource.

Export your data as CSV, import to MySQL, build a web app to manage it, then do another export/import and get everyone to switch.

---

### Post by Vegan on 2010-11-11
Because MySQL is configured to localhost by default, you need to change that to make it visible as a network server.

Then you have to find an ODBC driver for Windows for the resource and then you can use the server live.

This is all well documented, visit the MySQL.org site and see what is needed.

---

### Post by SeijiSensei on 2010-11-11
^This is by far the easiest method since you can link to the MySQL tables directly and use them as if they were local to your Access application.

> **Vegan said:**
> Because MySQL is configured to localhost by default, you need to change that to make it visible as a network server.

Change bind_address in /etc/my.cnf to either point to the external IP address, or to 0.0.0.0 if you want MySQL to listen on all interfaces.

> Then you have to find an ODBC driver for Windows for the resource and then you can use the server live.

[http://dev.mysql.com/downloads/connector/odbc/5.1.html](http://dev.mysql.com/downloads/connector/odbc/5.1.html)

You'll install the driver from the Windows Control Panel under Administrative Settings.  Then you can create an instance that points to your MySQL server and database then use the Access ODBC Databases options under External Data to use that connection and link to the tables you need.

---

### Post by astabeno on 2010-11-21
Thanks for the replies.  I have a test database created for my data with a test Access front end pointed to it.  The only problem I have had is two of my tables did not move do to the following error:

```
AUTO_INCREMENT, `Check Number` INTEGER, `TransactionDate` DATETIME, `Vendor` VARCHAR(255), `Vendor (A)` VARCHAR(255), `WithdrawalAmount` DECIMAL(19,4), `DepositAmount` DECIMAL(19,4), `Description` VARCHAR(255), `Description (A)` VARCHAR(255), `Category- English` VARCHAR(50), `Category- Arabic` VARCHAR(50), `Account` VARCHAR(50), `Receipt Number` INTEGER NOT NULL) ENGINE=myisam DEFAULT CHARSET=utf8
- Error: -2147467259 (80004005) [MySQL][ODBC 5.1 Driver][mysqld-5.1.49-1ubuntu8.1]Incorrect table definition; there can be only one auto column and it must be defined as a key
- 0 records moved
```

Two tables are giving this error.  They both have one field with a primary key Auto Increment.  I don't think there are two unless I am missing something.

---

### Post by koenn on 2010-11-21
it looks like you have a syntax error there;
afaik the 'autoincrement' part should be of the form
```

column_name datatype NOT NULL AUTO_INCREMENT,
PRIMARY KEY (column_name)

``` 
you seem to have only "AUTO_INCREMENT" and you're not defining that column as a key. 

*datatype* should be some from of INTEGER, btw.


You seem to be doing some kind of automatic Move operation - maybe you can do it by hand, i.e. create the table first, then insert the data.


[http://dev.mysql.com/doc/refman/5.0/en/example-auto-increment.html](http://dev.mysql.com/doc/refman/5.0/en/example-auto-increment.html)

---

### Post by astabeno on 2010-11-21
Looks like the top line of my SQL statement wasn't in the code box.  Here's the code for our registration database and the error.

```
- Creating 'Registration' failed
- SQL: CREATE TABLE `Registration` ( `RegID` INTEGER NOT NULL
AUTO_INCREMENT, `StudentID` INTEGER NOT NULL, `Date Registered`
DATETIME DEFAULT '=Date()', `Discount Granted` DECIMAL(19,4),
`Discount Reason` VARCHAR(100), `Class` INTEGER, `Test1`
DECIMAL(19,4), `Test2` DECIMAL(19,4), `Test3` DECIMAL(19,4),
`FinalTest` DECIMAL(19,4), `Practical1` DECIMAL(19,4),
`Practical2` DECIMAL(19,4), `Practical3` DECIMAL(19,4),
`FinalPractica` DECIMAL(19,4), `Absences` INTEGER, `Media Costs`
DECIMAL(19,4), `CompCov` TINYINT(1) DEFAULT 0, `Notes`
VARCHAR(50), `First English Class` TINYINT(1) DEFAULT 0, `First
Class` TINYINT(1) DEFAULT 0, `TimeStamp` DATETIME, `Book`
TINYINT(1) DEFAULT 0, `Terb_Reg` TINYINT(1) DEFAULT 0)
ENGINE=myisam DEFAULT CHARSET=utf8
- Error: -2147467259 (80004005) [MySQL][ODBC 5.1 Driver][mysqld-
5.1.49-1ubuntu8.1]Incorrect table definition; there can be only
one auto column and it must be defined as a key
- 0 records moved
```

I can't tell what field is throwing the error.  I assume its the primary key:
```
`RegID` INTEGER NOT NULL AUTO_INCREMENT
```

That is the only AUTO_INCREMENT Variable I have in this table.  I converted several other tables with the same datatype and it worked fine.

---

### Post by SeijiSensei on 2010-11-21
Try

```
`RegID` INTEGER NOT NULL AUTO_INCREMENT PRIMARY KEY
```

I don't see a primary key defined in the table declaration you posted.

---

### Post by koenn on 2010-11-21
what SeijiSensei said.
the auto_increment column apparently is not set as Primary Key.
you can probably just add that to the sql, 
or set a primary key in the ms access table first, if that statement is generated code based on the ms access table.

---

### Post by astabeno on 2010-11-22
I see.  I am using a program called Bullzip Access to MySQL.  It worked for all the other tables in the database except these.  I might need to try another method to do the migration because this doesn't let me edit the SQL statements.  It gets info from Access and and bases its query off that.

---

### Post by koenn on 2010-11-22
well then, set a primary key in the ms access table first, on the auto-incrementing column, and see if your bullzip includes it in the sql statement.

If not, learn 2 look at the sql in access "make table" queries and run it against mysql

---

### Post by astabeno on 2010-11-22
The PK is set in Access.  One time I ran the program it set the PK correctly the other times it has not.

---

### Post by koenn on 2010-11-22
can you tell if there's a difference between the cases where it works and those where itr doesn't ?

the data type of the PK or so ?

---

### Post by SeijiSensei on 2010-11-22
You could just manually create the table in MySQL using the mysql command-line program, then run an Append query in Access with the existing table as the source, and the table you just created as the target.  I suspect if you just take the code you posted above, with "PRIMARY KEY" added like I suggested, you could run it in the mysql client and create the table structure.

Sometimes the best solution is to do these things manually and not rely on third-party programs.

---

