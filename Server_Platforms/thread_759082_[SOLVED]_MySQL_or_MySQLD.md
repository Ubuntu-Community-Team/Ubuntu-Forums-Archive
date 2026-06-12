---
title: "[SOLVED] MySQL or MySQLD?"
date: 2008-04-18
forum: Server Platforms
---

### Post by cleanfacets on 2008-04-18
Current environment:
Dell desktop running Gusty Gibbon, 7.10 installed with server version and LAMP setup from the server package.  I did not install Apache2, MySQL, or PHP separately, I used the LAMP selection during the ubuntu install.

I've used MySQLD on other systems but am having trouble with the ubuntu install.  I have already changed the password for the MySQL.user table so all root user(s) have the same password I selected.

I can type in:   (this one works ok, but is not mysqld)

mysql -u root -p

It then asks me for a password and after typing in the right one, I get the mysql> prompt.  I can SHOW various databases and see information_schema and mysql.

If I type in: (trying the same without the -p option)

mysql -u root

I get:
ERROR 1045 (28000): Access denied for user 'root'@'localhost'  (using password: NO)

If I type in:  (trying mysqld this time, with both -u and -p)

mysqld -u root -p

I get:
[Warning] Ignoring user change to 'root' because the user was set to 'mysql' earler on the command line.
[ERROR] mysqld: unknown option '-p'

If I type in just:  (no user or password switches)

mysqld

I get:

[Warning] Can't create test file /var/lib/mysql/WMSustainability.lower-test
[Warning] Can't create test file /var/lib/mysql/WMSustainability.lower-test
[Warning] One can only use the --user switch if running as root
InnoDB: Operating system error number 13 in a file operation.
InnoDB: The error means mysqld does not have the access rights to the directory.
InnoDB: File name ./ibdata1
InnoDB: File operation call: 'open'
InnoDB: Cannot continue operation.

(Yes, the two warnings at the beginning are the same.)

Do we have a document that explains the correct usage for MySQL and how to correctly log in?
Should I just use mysql and leave off the D reference for use in ubuntu?
Should I be able to log in without specifying the -p option?
What is the issue with mysqld and InnoDB?

Thanks,
cleanfacets

---

### Post by mmichalik on 2008-04-18
mysqld is the daemon process for the MySQL server.

I would just use mysql from the command line with the appropriate -u and -p options specified.

When you set up the mysql server, you set up an admin user in the install, I would use that to get into MySQL until you create additional users.

as far as the root user goes, with Ubuntu, by default you don't have access to it.  It is there and you can set it up for use but the default is to allow the initial admin user sudo access.

If you want to set up the root user so you can log in as it do the following:

sudo passwd root

and give root a password. Afterwards you can become root by running

su from the command line.

Not knowing your experience level with Unix though, I have to say that setting the root users password could allow you to do some pretty awful things to your system if you don't fully understand it.  Also, this won't allow access to MySQL as root until you create the user "root" in the MySQL instance and grant it the appropriate privileges.

---

### Post by cleanfacets on 2008-04-21
Thanks mmichalik,
I am pretty familiar with MySQL but not Unix, since I've spent 4 or 5 years in DOS, then the past 15 years in various Windows OSs.  The only unix work I've completed was in Minix writing an improved print queue, but not much at the user level.

I'll call this closed, but the original reason I wrote this post was several people here have asked about MySQLD and I could not get it to work.

cleanfacets.

---

### Post by roopaprabhun on 2008-05-13
Hello,

Can anyone please tell me what is an instance in Mysql?
And what is the procedure to create an instance.

Thanks.
Roopa.

---

