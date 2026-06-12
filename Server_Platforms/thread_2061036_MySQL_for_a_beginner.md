---
title: "MySQL for a beginner"
date: 2012-09-21
forum: Server Platforms
---

### Post by mike acker on 2012-09-21
ok, so I got MySQL installed and I can manipulate it from terminal :(

I need a good GUI client for it. i tried MySQL Navigator and MySQL Client. I think "clinet" is for command line; I couldn't get "navigator" to onnect to the Test Database (using local host) 

any pointer to a good getting started paper will be appreciated !!

---

### Post by josephmills on 2012-09-21
phpmyadmin
[http://www.phpmyadmin.net/home_page/index.php](http://www.phpmyadmin.net/home_page/index.php)

---

### Post by Cheesemill on 2012-09-21
How about [mysql-workbench]("apt://mysql-workbench").

---

### Post by clay7 on 2012-09-21
Here's my preferences:

mysql-workbench for your local setup

phpMyAdmin for web-based

---

### Post by mike acker on 2012-09-21
ok,  2 votes for MySQL Workbench!!

I have that installed and I think I can get around... I did a lot of work with McKesson STAR/Vista earlier..... this seems familiar

now..... what is the best way to enter data ??    create a form ?    run an import ??   I didn't find a default data entry form; perhaps that's a bit inelegant ?

---

### Post by LHammonds on 2012-09-21
Are you talking about end-users entering data a little at a time or are you talking about doing a pre-populate mass upload?

If mass upload, that is typically done using an import file.

Other than that, it is really up to you.  There are a thousand and one ways to get data entered into a database.

> **clay7 said:**
> Here's my preferences:

mysql-workbench for your local setup

phpMyAdmin for web-based
+1

LHammonds

---

### Post by Cheesemill on 2012-09-21
Have you created your database and tables first?

You need a table to put your data into.

Try Googling 'mysql beginners tutorial' if you're not sure what you're doing.

---

### Post by mike acker on 2012-09-22
> **Cheesemill said:**
> Have you created your database and tables first?

You need a table to put your data into.

Try Googling 'mysql beginners tutorial' if you're not sure what you're doing.

yep!! It's just a matter of learning the MySQL/WorkBench: I found the means by which I can edit the data in a given row :D

figured out how to set up Foreign keys:D

it appears WorkBench is the right tool:D thanks for the help!!

how do i mark this question "solved" ?  I'll just give it a gold star
:KS
notes
I'm running a feasibility study for a local theatre which is going to change ticketing systems. they will need to save their history data for events, patrons, and sales. should be be a pretty simple job -- but it will need to be simple.  once the DB is defined and the tables imported they should be able to run queries with Crystal, or Access -- even LibreOffice DB.   -can you run a query from Excel? I know it works fine on an exported answer set.

---

### Post by Wim Sturkenboom on 2012-09-22
> 
how do i mark this question "solved" ?

Using thread tools just above the first post on this page.

---

