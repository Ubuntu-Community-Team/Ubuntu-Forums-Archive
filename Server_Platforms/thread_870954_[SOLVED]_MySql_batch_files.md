---
title: "[SOLVED] MySql batch files"
date: 2008-07-26
forum: Server Platforms
---

### Post by Pengwyn44 on 2008-07-26
MySql batch files
I have read the appropriate section of the MySql manual but the instructions are not clear as to how a batch file containing a script for running a series of commands can be made.
Please could someone give an example of how a batch script should be written and saved and in what format?
Also an example of how to invoke the script?
Most computer manuals seem to suffer from the same problem as far as newbies are concerned. They give a synopsis, a description and options but no examples!
Pengwyn44

---

### Post by joebeasley on 2008-07-26
Put the mysql commands into a text file.  You can then use the source command from within mysql.  

You can also call the script from the command line using 'mysql -u user -p  <textfile'.

---

### Post by Pengwyn44 on 2008-07-28
Thanks for your response but it does not help. I have tried to get Mysql Administrator to run a sequence of commands but it will only run one at a time. Then I tried to get it to run a script which I saved as 'script.sql' but it won't. The script contains the following code "SELECT TITLE FROM `p`.`NameAddress` WHERE ID = '9';" (If this had worked I was going to try more than one command).
Then I tried the command line as you suggest but my problem with that is I substituted 'root' for your word 'user' but not sure if that is what you meant. (Mysql Administrator won't let root create another user!).
Your suggested line doesn't refer to the database name.
The instruction in the manual says "shell> mysql db_name"; this when entered gives an error message "Access denied...................."
If I enter 'mysql' I get a welcome message, then if I enter:-
mysql> \. /var/lib/mysql/script.sql
I get this message "ERROR 1142 (42000): SELECT command denied to user ''@'localhost' for table 'NameAddress'".
This shows that the command finds the script (which is owned by me) but refuses to run it.
I hope that this clarifies my problem and that you can point me in the right direction and thanks for taking the time. Pengwyn44

---

