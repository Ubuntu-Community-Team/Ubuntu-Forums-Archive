---
title: "Enabling sqlite3 with PHP?"
date: 2009-05-13
forum: Server Platforms
---

### Post by Newbie123 on 2009-05-13
I've been unable to get PHP to recognize sqlite3 on my system.

I believe i have all of the packages installed, and the following .so files are on my system:

/usr/lib/php5/20060613+lfs/pdo_sqlite.so
/usr/lib/php5/20060613+lfs/sqlite.so

However, when I run phpinfo(), it outputs:

PDO drivers 	sqlite, sqlite2 

Does anyone have any ideas....

Thanks

---

### Post by wojox on 2009-05-13
Check your error logs. Do you have the sqlite3.so file installed ?

---

### Post by Vegan on 2009-05-13
phpBB works best with the standard LAMP stack which includes MySQL (the M part).

I use phpBB and sqllite is not one the favorites.

---

### Post by Newbie123 on 2009-05-14
It looks like i have 

/usr/lib/libsqlite3.so.0
/usr/lib/libsqlite3.so.0.8.6
/usr/lib/python2.5/lib-dynload/_sqlite3.so

I also have the php-sqlite package installed... Some other posts referred to a php-sqlite3 package, but it doesn't seem to exist anymore...


Which log file should i look at? I am running php under apache2, but the log file seems to just have generic http requests/errors.

Thanks

---

### Post by Newbie123 on 2009-05-14
Hmm...

Ok, after spending several hours, I've just decided to use mysql, and it requires a little more setup, but overall everything appears to be working....

Apparently there are some problems with sqlite3 and php5. At one point, i got it installed through 'pecl install pdo', but it didn't work due to some binary version incompatibilities.

---

### Post by wojox on 2009-05-14
newb ,
when you log on  hit /. then the enter key.
then type cd /var/log/apache2 then enter key.
type ls ( for list ) then enter key.
you should see an error.log file.
type more error.log then enter key.
if apache2 can't find something this should tell you.
I don't run python so I hope this helps.
I do run mysqlite with php5 apache2 and mysql, which works well.
Good luck -wojox

---

