---
title: "Mysql web based data entry frontend"
date: 2011-11-17
forum: Server Platforms
---

### Post by bakegoodz on 2011-11-17
Anybody know of a simple web frontend that a user (not admin) can add data to a configured MySql table? Just going to be used on local network, it wouldn't even need authentication. Though it probably would need authentication to work with MySql which is fine.

---

### Post by bakegoodz on 2011-11-17
Hum . . .This might what I'm looking for
[http://xataface.com](http://xataface.com)

---

### Post by memilanuk on 2011-11-17
Mmmm... interesting link.

I was going to suggest installing a simple LAMP stack, and then phpMyAdmin.  If you give a user rights to a particular database, they can do a fair amount of data entry right there... and depending on what rights you give them, they can be limited to where creating new records is *all* they can do.  Its free and already available in the default repos, so its probably simplest to set up.

---

### Post by SeijiSensei on 2011-11-17
Another alternative, if the people entering data are using Windows and MS Office, is to [create an ODBC connection]("http://dev.mysql.com/doc/refman/5.5/en/connector-odbc-configuration-dsn-windows.html") to your database(s).  Then you can use programs like Excel or Access to communicate with the database directly.

---

### Post by Jonathan L on 2011-11-17
> Anybody know of a simple web frontend that a user (not admin) can add data to a configured MySql table? Just going to be used on local network, it wouldn't even need authentication. Though it probably would need authentication to work with MySql which is fine.

Hi Bakedgoodz

How complex are the things the users are going to input?  There's a whole world of difference between a name-and-address capture and, say, a company-project-team capture with lots of constrained fields.

Thanks for the link to xataface ... looks very interesting.

Kind regards,
Jonathan.

---

### Post by rubylaser on 2011-11-17
Personally, I'd just make a simple Ruby on Rails / Python app, and map it to the MySQL current fields.  ODBC is another great idea, but personally, I'd want a web based app, that I could extend.  That way, in the future, if you chose to, you can always add authentication and authorization for roles if you decided you needed them.  

You could have all of your CRUD actions covered in a matter of minutes (and not require users to authenticate if you didn't want them to).  If you could show use the database schema, making a recommendation would be much easier.

---

### Post by bakegoodz on 2011-11-21
Unfortunatly I'm not smart enough to get xataface working. I'm trying phpMyedit now.

---

### Post by bakegoodz on 2011-12-06
Tried PhpMyedit, not too bad. I had to create a table first, used phpMyadmin. Had to figure out the data types I needed and and the number of columns manually.  Then PhpMyedit made an easy data entry interface to that table. Then I decided that I really needed authentication. Now I'm back to searching again. I found PhpMyAccess, but I can't get it working and it is poorly documented.
 Any ideas of a database web front end that prompts for a login?

---

### Post by SeijiSensei on 2011-12-07
> **bakegoodz said:**
> Any ideas of a database web front end that prompts for a login?

You can just use Apache [basic authentication]("http://httpd.apache.org/docs/2.1/howto/auth.html") to limit access to the directory in which the application is stored.  I'd just use a simple htpasswd file myself.  If you have a network-wide authentication system like OpenLDAP or Active Directory you can authenticate against those instead.

---

### Post by bakegoodz on 2011-12-11
I found a program I like, but it takes some work to get it going.
Dadabik - dadabik.org
 You have to setup an initial table for it and it is missing a user manager interface. I figured out how to change its root password from the default, you have to manually change the md5 hash. I struggling to figure out how to add a user to its own user table. It does have a pretty decent interface for adding data or modifying your tables though.

---

### Post by ZettaGeek on 2011-12-12
> **bakegoodz said:**
> Anybody know of a simple web frontend that a user (not admin) can add data to a configured MySql table? Just going to be used on local network, it wouldn't even need authentication. Though it probably would need authentication to work with MySql which is fine.

I would highly recommend PhpMyAdmin as it works quite nicely for managing a MySQL Database.

[http://www.phpmyadmin.net/home_page/index.php](http://www.phpmyadmin.net/home_page/index.php)

---

### Post by bakegoodz on 2011-12-17
Managing additional users can actually be done in the interface, you just select the user table in Dadabik.
So I've found the answer to my question. Dadabik is pretty good web app for creating user database interfaces. You can set it up for non technical people to do data entry on it too.

---

