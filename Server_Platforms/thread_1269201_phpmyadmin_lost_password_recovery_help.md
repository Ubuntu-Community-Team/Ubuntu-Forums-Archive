---
title: "phpmyadmin lost password recovery help"
date: 2009-09-17
forum: Server Platforms
---

### Post by AnLGP on 2009-09-17
hello,

i've done some basic searching and haven't found a thread.

i can go to "http://localhost" and i can see the joomla! install i'm trying to set up but when I get to the "database name" portion to fill out i need to get into phpmyadmin to see the database i have set up.

i went to log in (i thought i made the password relatively easy to remember) but i can't get the right password.

is there a way I can reset it?

thanks!

---

### Post by i.r.id10t on 2009-09-18
[http://www.thegeekstuff.com/2009/07/how-to-reset-forgot-mysql-root-password-on-unix-linux-windows/](http://www.thegeekstuff.com/2009/07/how-to-reset-forgot-mysql-root-password-on-unix-linux-windows/)

---

### Post by AnLGP on 2009-09-18
Add –skip-grant-tables to mysqld_safe Startup Command

---

when i do this step the file is blank.

---

### Post by hessiess on 2009-09-18
[http://dev.mysql.com/doc/refman/5.1/en/resetting-permissions.html#resetting-permissions-unix](http://dev.mysql.com/doc/refman/5.1/en/resetting-permissions.html#resetting-permissions-unix)

---

### Post by AnLGP on 2009-09-18
is there a way to just delete the whole server and start over?

i've got nothing on it and starting over would be so much easier..

---

