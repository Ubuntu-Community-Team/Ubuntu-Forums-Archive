---
title: "mysql backup assistance"
date: 2007-03-07
forum: Server Platforms
---

### Post by tocleora on 2007-03-07
I'd like to know what other people in corporate environments are doing in regards to backing up their data in mysql.  I had a server crash Monday that caused me to get some corrupted tables and lose some data, and I want to make sure I prevent this as much as possible in the future.  TIA...

---

### Post by conjur3r on 2007-03-08
Export the data into a set of SQL statements which you can then use on any other MySQL database to reconstruct the schema and data.  Something like the following:

# mysqldump --opt --all-databases

Play around with that, you can pipe to a file with compression, etc.

I basically run this daily and store a copy locally and offsite.  Whenever I need to use it, I've only lost at most a days worth of work.  Obviously, you can have the command ran multiple times daily.  Up to your backup plans.

---

### Post by tocleora on 2007-03-08
Do you know why an export done from mysqldump on MySQL4 would not work imported in MySQL 5?  I'm getting errors when trying to import, I can't remember the exact error but it refers to a "''" on line 2097, and when I look at line 2097 it looks like the rest of the file, I don't see anything wrong, plus I can import it back into MySQL 4 without a problem.  Thoughts?

---

### Post by conjur3r on 2007-03-09
Take a look at the docs [http://dev.mysql.com/doc/refman/5.0/en/upgrade.html](http://dev.mysql.com/doc/refman/5.0/en/upgrade.html)

Personally, I do not restore onto a different major/minor version.  If I have to restore to another version, I would have already done the mysql upgrade beforehand and tested appropriately.

There will almost always be slight changes in schema support.  How else could they improve a database system?

---

