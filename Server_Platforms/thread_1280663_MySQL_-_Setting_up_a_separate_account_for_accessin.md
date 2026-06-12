---
title: "MySQL - Setting up a separate account for accessing the database?"
date: 2009-10-02
forum: Server Platforms
---

### Post by johnnydopefish on 2009-10-02
Hello,

I'm reading through [this guide here]("http://dev.mysql.com/tech-resources/articles/ddws/5.html") and am doing my best to reconcile Red Hat instructions with the way it works on Ubuntu.

I ignored their compile-from-scratch approach in favor of installing from repo but this bit has me confused:

> While you can run the server as the root user, or even as yourself (if, for example, you installed the server in your own home directory), the best idea is to set up a special user on the system that can do nothing but run the MySQL server. This will remove any possibility of someone using the MySQL server as a way to break into the rest of your system.

I see that a mysql:mysql user and group were created during the installation of MySQL through tasksel.  Permissions for this user and group were set on /var/lib/mysql.  

Was this step already completed for me then, or do I still need to create a separate unprivileged user account to access the database?

Thanks

---

### Post by BQAggie2006 on 2009-10-02
Yes, this was already done for you, though this user was not created to access the databases hosted by MySQL, it is a system account created to run the MySQL server. 

During the installation of MySQL from the repositories, you should have set up the MySQL root password (different from the system root). This is the account that you will be using to administer your databases. If you don't feel comfortable using the root account to administer your databases, then you'll need to create another MySQL account (not system account).

Instead of trying to reconcile Red Hat instructions, check out the Ubuntu Server Guide documentation: [https://help.ubuntu.com/9.04/serverguide/C/mysql.html](https://help.ubuntu.com/9.04/serverguide/C/mysql.html)

---

### Post by johnnydopefish on 2009-10-08
Thanks for the reply.  Sorry I did not express my appreciation sooner.

For archival's sake, [here are the instructions for setting up new user accounts]("http://dev.mysql.com/doc/refman/5.1/en/adding-users.html").  The tutorial I linked to earlier is horribly outdated and the setup instructions only pertain to Red Hat-- everything is done automatically in Ubuntu.

No folder permissions need to be changed; just add the user and (I'm assuming) grant them SELECT privileges only.

Here is a [much better tutorial]("http://www.w3schools.com/php/default.asp") (w3schools) for working with PHP and MySQL than the one I was working with, for anybody interested.

---

