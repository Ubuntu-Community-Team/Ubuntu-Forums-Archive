---
title: "New to MySQL"
date: 2011-07-06
forum: Server Platforms
---

### Post by headvampyre@hotmail.co.uk on 2011-07-06
Hi, im currently on work experienced with a computing shop, and ive been given a task to intergrate osCommerce with MySQL and to import an Excel file into the database. I've got all the data organised and in the databases, etc, but im now stuck with MySQL.

My issue is that i need to assign an ID to each product, and i have a large amount, so doing it manually is out of the question. 

So, is there anyway to have MySQL add the row number into a column so that can continue importing them?

---

### Post by rubylaser on 2011-07-06
Add and id column to your database, and set it up to auto increment.  MySQL should take care of the rest for you.

---

### Post by SeijiSensei on 2011-07-06
I'm a bit puzzled.  First you say you have the data in the database, but now you want to add an auto-increment field?  You have to set that up in the table definition before the records are entered.  You can either drop the table from the database and recreate it with the auto-increment field, or add the field to the table with an "ALTER TABLE" command.

Now install the [MySQL ODBC connector]("http://dev.mysql.com/downloads/connector/odbc/") in Windows.  If you have a copy of Access around as well, import the spreadsheet into Access, then create an ODBC link to the table in MySQL. You'll then be able to run an Append Query to insert the records into MySQL.  One advantage of this approach is that you can use Access for queries and updates rather than running SQL commands on the Linux box.  It will also be a useful learning experience for you.  It may also make your employer happy to see how well you've integrated Windows and Linux.  He or she may feel more comfortable using a GUI application like Access to manage the data in osCommerce.

---

### Post by rubylaser on 2011-07-06
> **SeijiSensei said:**
> I'm a bit puzzled.  First you say you have the data in the database, but now you want to add an auto-increment field?  You have to set that up in the table definition before the records are entered.  You can either drop the table from the database and recreate it with the auto-increment field, or add the field to the table with an "ALTER TABLE" command.

Now install the [MySQL ODBC connector]("http://dev.mysql.com/downloads/connector/odbc/") in Windows.  If you have a copy of Access around as well, import the spreadsheet into Access, then create an ODBC link to the table in MySQL. You'll then be able to run an Append Query to insert the records into MySQL.  One advantage of this approach is that you can use Access for queries and updates rather than running SQL commands on the Linux box.  It will also be a useful learning experience for you.  It may also make your employer happy to see how well you've integrated Windows and Linux.  He or she may feel more comfortable using a GUI application like Access to manage the data in osCommerce.

That is a pretty crafty solution :)  I'd normally just suggest to use PHPmyadmin, but this is not a bad idea at all in a Windows shop.

---

### Post by headvampyre@hotmail.co.uk on 2011-07-07
Okay, AUTO_INCREMENT worked :) thanks guys :) and for others who are looking to do the same, this is what it would turn out like :)

id|products_model|
1 | MRIPRODUCT1  |
2 | MRIPRODUCT2  |
3 | MRIPRODUCT3  |
4 | MRIPRODUCT4  |

---

