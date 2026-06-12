---
title: "OpenOffice.org-Base JDBC connection to MySQL"
date: 2008-07-31
forum: Server Platforms
---

### Post by pizzipie on 2008-07-31
I am using Ubuntu 8.04.

I have tried to connect to a mysql database with no success. Here is what I did.

1. Connect to existing database => MYSQL .. next
2. Connect using JDBC .. next
3. Name of database => pizzi_db
Server URL => mysql://localhost:3306
Port Number | 3306 | default: 3306
Mysql JDBC driver class => com.mysql.jdbc.Driver
Test class => The JDBC driver was loaded sucessfully ... next
4. User name => rick
Password => required ... next
5. Yes - Register database
Yes - Open the database for editing ... Finish
6. Name => pizzi_db or any other
ODF database ... save
7. Tables => rick
password => rick ... ok

THEN the Problem: Receive following message.

"The connection to data source pizzi_db could not be established. Must specify port after ':' in connection string"

I don't know what they are talking about; what connection string?

Can anyone help to solve this? Would greatly appreciate a solution since I am almost there (I hope).

Rick P

---

### Post by Pengwyn44 on 2008-09-01
I have the same problem as you have, although the error message is not exactly the same as yours. I have been given some help from the forum which it would be worth you having a look at. >> see Pengwyn44.
However I have still not been able to connect!

---

### Post by mbeach on 2008-09-01
is this different from:
[http://www.oooforum.org/forum/viewtopic.phtml?t=39011](http://www.oooforum.org/forum/viewtopic.phtml?t=39011)

or did that not work quite right

server url: localhost

---

### Post by Pengwyn44 on 2008-09-11
Yes, this is a different URL.

---

