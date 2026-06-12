---
title: "setup focus/sis"
date: 2007-11-20
forum: Server Platforms
---

### Post by mitchi on 2007-11-20
Please help me on this one, I cant configure my pc to make Focus/SIS run. I've already installed PHP, PostgreSQL, Apache, Htmldocs, the php-pgsql support, I've even reinstalled my O.S. with the thought I messed up the system, but I still cant get it to work.

It returns the ff:

> 
Error: Focus/SIS cannot connect to the Postgres database. Either the database "focus" does not exist, Postgres is not running, it was not started with the -i option, or connections from this host are not allowed in the pg_hba.conf file.

If the database does not exist, create it using phpPGAdmin, PGAdmin III, or by opening a terminal window and following these directions:

   1. Login as the postgres user
      ex) server$ su - postgres
   2. Login to the postgres database server using the template1 database
      ex) server$ psql template1
   3. Create the focus database
      ex) template1=# CREATE DATABASE focus; 


I really don't know what to do with this one. Please help.

BTW, I'm using Focus 2.2.
[**http://www.focus-sis.org/**]("http://www.focus-sis.org/")

---

### Post by brentoboy on 2007-12-02
do you have phppgadmin installed?
[http://hocuspokus.net/2007/11/14/install-phppgadmin-on-ubuntu-710/](http://hocuspokus.net/2007/11/14/install-phppgadmin-on-ubuntu-710/)

you'll want it once you get your database in place.

The following is a rough outline of what needs to be done.  I dont remember the details that well.
---
psql is the name of the command line program that lets you interact with the psql server.

to use it, you need to be "postgres" the ubuntu user who owns the postgres files.   to do that, first, become root, then downgrade to postgres (you cant login as postgres directly for security reasons)

sudo -s
(password)
su - postgres

once you are the postgres user, run psql

create a database named "focus", use the command line.
for details, look here....
[http://www.postgresql.org/docs/8.2/static/app-createdb.html](http://www.postgresql.org/docs/8.2/static/app-createdb.html)
While you are in there, create a "focusexperiments" database too, you want a copy of the database that is made to be experimented on.

once you create the db, run the "install.sql" file found in the root of your focus install tree. using the postgres command line again.

you can login to the website:
[http://focushost/phppgadmin](http://focushost/phppgadmin)
(where focushost is the server's hostname)
this will let you browse around and see if your database has been created and the tables are all there.

if you have a database, then you need to modify your focus installation to know where the database is located, and give it login credentials etc.

the file you want to tweak is called "config.inc.php"
and it is probably located at
/var/www/focus/  (or whereever you put your wwwroot for focus.

once that is all in place, goto:
[http://focushost/focus](http://focushost/focus)
and login with admin/admin

---
I hope that helps.


oh, and one last thought.  if you pull it down from the svn, there is a 2.3 that is relatively stable that might have some additional features worth the time it talkes to check it out front the dev tree.

---

