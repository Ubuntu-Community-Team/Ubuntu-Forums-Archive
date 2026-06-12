---
title: "mysql noob needing assistance"
date: 2007-10-25
forum: Server Platforms
---

### Post by sixstorm on 2007-10-25
Hello all.  I'm currently taking a database class in my university and I'm having to use Microsoft SQL Server 2K in order to do some SQL projects, mostly making queries and making tables.  I've just bought a new laptop and am using Gutsy x64 (Gutsy is very nice!).  I've been looking on here and Google for some noob assistance but I can't find anything.  I just want to know, how in the heck do I start MySQL?  Is it command-line or is it GUI?  

I went into terminal and typed "sudo mysql -u root", as instructed in a howto elsewhere, but it says "Access Denied for user 'root@localhost'  PASSWORD:NO"  Any idea here guys?  All I need to do is remote into my university's SQL server and work from there.  Is MySQL for me or do I need to use another program?

---

### Post by kebes on 2007-10-25
> Any idea here guys?  All I need to do is remote into my university's SQL server and work from there.  Is MySQL for me or do I need to use another program?

I don't think MySQL is what you want.

MySQL is a database system that runs on Linux. It is a full-fledged database (with associated query browser, etc.) It is different from Microsoft SQL.

It is possible to access a MS SQL server from programming languages on Linux (PHP, Ruby, etc.) using an appropriate binding.

However it sounds like you are actually trying to connect a query browser to Microsoft SQL. As far as I know, there isn't a MS SQL browser for Linux. You can use "wine" to run some Windows applications on Linux (but not all Windows programs will work), so you could try installing the Microsoft SQL Client (Windows version).


Sorry I can't be of more help. You might consider posting a new thread with a title like "Can I access Microsoft SQL Server from Linux?" and see if any experts can help you out (since this isn't really a MySQL question).

---

### Post by paparucino on 2007-10-25
> **sixstorm said:**
> 
I went into terminal and typed "sudo mysql -u root", as instructed in a howto elsewhere, but it says "Access Denied for user 'root@localhost'  PASSWORD:NO"  Any idea here guys?  All I need to do is remote into my university's SQL server and work from there.  Is MySQL for me or do I need to use another program?
This should help you

===========================================================
Mysql (5.0.19 at the time of writing)


In the terminal (as root):

Code:

root[username]#su - mysql
/dev/pts/0: Operation not permitted
mysql[~]$


Now install the database
Code:

mysql_install_db


exit from the prompt

Code:

mysql[~]$ exit
logout
root[username]#


As root (after typing exit you should be root). We are going to make the mysql script executable.

Code:

chmod +x /etc/rc.d/rc.mysqld


Start the mysql server

Code:

root[username]# /etc/rc.d/rc.mysqld start


You should see this:

Code:

root[username]# Starting mysqld daemon with databases from /var/lib/mysql


the terminal will stay like this. You can get a prompt back by typing CTRL-C.
Note: The mysql server will not stop. It is still running.

Now create a root password for mysql:

Code:

mysqladmin -u root password 'new-password'


An example of the root password for mysql:
Code:

root[username]# mysqladmin -u root password ubuntu
================================================


Now if you type

root[username]# mysql

you should get the prompt: mysql>

if you get a password error edit the file /etc/my.cnf and remove the symbol # in front of password the insert the psw you gave via mysqladmin.
Save, exit and retry.

---

### Post by steve.horsley on 2007-10-25
The only way I can think of is to use OpenOffice.org, install a Sun java VM and the MS java driver for MS-SQL and enter the queries into the OOo Base query designer. Very long-winded, but I think it could be done.

---

### Post by sixstorm on 2007-10-25
Thanks for the replies everyone.  Maybe MYSQL isn't what I'm looking for.  I can get MS SQL Server 2K again from the Comp-Sci building but it just takes up a lot of HDD space.  Guess I'll try to look it up in Wine-DB to see if it works.  Thanks again guys!

---

### Post by steve.horsley on 2007-10-26
MS SQL Server 2K?

Are you looking for a client that will connect to the existing MS SQL server (which is what I thought you were looking for), or are you looking to create your own database server? If the latter, MySQL might be the way to go, althougn you should be aware that every database speaks a slightly different dialect of SQL, and what works on MySQL might need tweaking before it works on MS SQL and vice versa.

---

### Post by codmate on 2007-10-26
Unfortunatly for students such as yourself, MySQL and Microsoft SQL Server are quite different. There are no views in MySQL (last time I looked anyway) for instance.

The SQL they take can also be slightly different.
If you're still learning it's best to stick with the MS stuff for now, if that's what you're using in college.

If you have plenty of time to spare - go ahead with MySQL - but do bear in mind that there are significant differences.

```
SELECT fun FROM learning
```  :D

---

