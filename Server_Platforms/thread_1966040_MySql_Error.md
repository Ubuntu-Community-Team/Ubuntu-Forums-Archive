---
title: "MySql Error"
date: 2012-04-26
forum: Server Platforms
---

### Post by Chriskras on 2012-04-26
Dear friends,

This is my first post here and hope that many more may follow. 

Now I'm stuck with a problem. I'm running Ubuntu 12.04 LTS containing MySQL database. This database would like to be able to configure. 

I type so to log in: mysql-u root-p, then I get an error: ERROR 1045 (28000): Access denied for user 'root' @ 'localhost' (using password: YES) 

The nice thing is that I certainly know that the password is correct. What is the solution for this problem? I do not have ROOT privileges.

---

### Post by SeijiSensei on 2012-04-26
Did you create the root account?  Read this: [http://dev.mysql.com/doc/refman/5.5/en/unix-postinstallation.html](http://dev.mysql.com/doc/refman/5.5/en/unix-postinstallation.html)

I really dislike account management on MySQL.  If you're not yet committed to MySQL, I suggest you give PostgreSQL a spin as well.  You can install it with "sudo apt-get install postgresql" and try it out by following the instructions for Karmic and later releases in section 3.3 of [https://help.ubuntu.com/community/PostgreSQL](https://help.ubuntu.com/community/PostgreSQL).

---

