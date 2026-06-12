---
title: "Noob: installing phpmyadmin and MySQL"
date: 2011-04-13
forum: Server Platforms
---

### Post by killerclick on 2011-04-13
ok, I installed Apache, phpmyadmin, PHP and MySQL on a virtual machine by just selecting and installing them. Great!

How do I connect to the MySQL server using phpmyadmin?
It's asking me for a username and password and I was not asked for a root password when I installed MySQL (unlike in Windows). I tried no password, I tried root as a password, I tried

$ mysqladmin -u root -p blah
Enter password: 
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: YES)'

Nothing I've tried is working obviously. Why does this have to be so stupid? Why couldn't MySQL ask me what password I want to use?

---

### Post by rubylaser on 2011-04-13
Resetting the root password is the easiest way to proceed.  Here are directions.
[http://www.howtoforge.com/reset-forgotten-mysql-root-password]("http://www.howtoforge.com/reset-forgotten-mysql-root-password")

---

### Post by killerclick on 2011-04-14
Thanks

---

