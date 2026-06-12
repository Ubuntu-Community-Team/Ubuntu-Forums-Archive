---
title: "How To set up multiple virtual hosts"
date: 2008-08-14
forum: Server Platforms
---

### Post by Jordanwb on 2008-08-14
How would I go about adding additional virtual hosts each with their own set of MySQL databases so that one vhost cannot see another's? I have the default host whose document root is /var/www and I want to move it to /var/www/site_1 and I think I know how to do that without bricking apache.

---

### Post by RealPSL on 2008-08-16
Here is a good article about setting up [multiple virtual hosts]("http://articles.slicehost.com/2008/4/29/ubuntu-hardy-apache-virtual-hosts-1")

As for the database connections that is going to reside in your code. If php your code would connect to the appropriate mysql database.

---

### Post by Jordanwb on 2008-08-16
> **RealPSL said:**
> If php your code would connect to the appropriate mysql database.

For example: One of my dad's websites is on a shared server. Although there's only one installation on Mysql, there are multiple instances. One instance for each website. That way each website's Mysql databases are independent and separate from the others.

That link didn't go into Mysql but it's still useful.

---

### Post by mbeach on 2008-08-17
MySQL is the database manager, which has the ability to handle several databases (or schemas).  Quite typically a hosting provider will allow you to have a number of databases or just one.  Each customer gets a database user and database all of their own, with that user being granted the appropriate privileges to that one database.  As the customer you are typically given the hostname (localhost or other), your database user name, password, and your database name.  Using PHP, python or whatever language you are dealing with, you'll be using those user credentials to connect to that one database.

A side note - when the hosting provider allows you to have only one database, normally you'll see an option in things like drupal, joomla and others to have a table prefix name.  This is so that those tables names associated with that application will not clash with other applications - both applications can have a table names "posts" in the same database because one will be "jml_posts" and the other can be "drup_posts".  In this situation, its still all the same user and database.

You can think of MySQL really only running one 'instance' but it has the capability of handling server databases.  That said, I'm sure you can run multiple instances of MySQL in separate memory spaces etc, but I don't think that's what you are talking about.

So, once you have the virtual hosts setup, MySQL is a separate issue.  It sounds like you want to create a mysql user and database for each virtual host.  That information is then passed along to the owner of the virtual host you created and they can use it in their scripts to connect to the database server, and more specifically to their particular database/schema.

If you are going to be doing a lot of this, you'll probably want to create a script which creates the apache conf file in sites-available, create the mysql user, create the mysql database, grant the appropriate privileges etc.  If I was doing it, I'll also probably have each customer as a separate user on the machine.

does that help?  am I way off topic?

---

### Post by mbeach on 2008-08-17
I was looking for the link which reviews all this, but having some trouble - good reading though at: 
[http://dev.mysql.com/doc/refman/5.0/en/user-names.html](http://dev.mysql.com/doc/refman/5.0/en/user-names.html)
[http://dev.mysql.com/doc/refman/5.0/en/user-resources.html](http://dev.mysql.com/doc/refman/5.0/en/user-resources.html)

---

