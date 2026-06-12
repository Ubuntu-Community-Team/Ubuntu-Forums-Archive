---
title: "Problem with mysql/mysql.sock after upgrading to dapper"
date: 2006-06-08
forum: Server Platforms
---

### Post by Xerak on 2006-06-08
Hello,

I have just upgraded to Dapper and although MySQL 5 works fine in command line, I can access the DB using "mysql -u<user> -p" etc, I can't access it through PHP.

I get the error "/etc/mysql.sock" not found. It actually doesnt exist anywhere, and restarting the machine doesnt help creating it. 

Anyone could help me recreating this missing mysql.sock?

---

### Post by bluewave on 2007-10-03
check out this one:
[http://hervalicio.us/blog/2007/07/07/no-such-file-or-directory-tmpmysqlsock/](http://hervalicio.us/blog/2007/07/07/no-such-file-or-directory-tmpmysqlsock/)

or just do this
sudo ln -s /var/run/mysqld/mysqld.sock /tmp/mysql.sock

---

