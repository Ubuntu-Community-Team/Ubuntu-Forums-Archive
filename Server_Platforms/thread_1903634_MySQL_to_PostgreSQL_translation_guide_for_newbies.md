---
title: "MySQL to PostgreSQL translation guide for newbies?"
date: 2012-01-02
forum: Server Platforms
---

### Post by memilanuk on 2012-01-02
So... I've tinkered with mysql a bit off and on, enough to be able to get around in it well enough using either the console or phpMyAdmin.  Usually I can find what I need via searching.

For some reason I keep running into a wall with postgresql, though.  There are *way* fewer books on it, and most of those seem targeted more towards professional DBAs - folks who already know what the terms they throw around mean, not someone who is still more or less a newbie.  Most of the tutorials I find for postgres cover using it as a developer - not much that I can find for the new guy with an old PC running Linux in the basement that wants to dabble with PostgreSQL.

Basically the admin documentation for postgres seems to be more of a reference, assuming the reader already knows what they want to do and just needs a refresher on the syntax.  There is a *very* short beginner section towards the end of the postgres docs on setting up a couple tables, but thats about it.

For some reason phpPgAdmin just kicks my behind.  Maybe its because I'm not understanding the postgresql terminology?

Does anyone else feel this way about the PostgreSQL docs?  Am I missing something?  Is there some kind of commercial documentation (i.e. books) out there that bridge this gap that I'm not finding?

TIA,

Monte

---

### Post by dazman19 on 2012-01-05
the best thing to do is use pgadmin III.

The best resource is still the postgres website. 

you can use it to make queries for you etc, at least until you get the knack of it.

I am doing my first proj in postgreSQL coming from mysql and postgreSQL is defiantly a more advanced database.

Its arguable things that it does better/worse vs mysql but i find using proper sql convention when doing selects inserts etc is the best way to go. 

Fortunately for me i learned Oracle 9i when i was at uni so i didnt have "too" much trouble going to postgres. 

remember things like `table`.`column` where as mysql is pretty cowboy and will allow for table.column and on windows systems even table.coLuMn which is pretty unconventional to say the least.

---

### Post by w3develop on 2012-01-25
You may refer dev MySQL for MySQL installation and PostgreSQL doc for PostgreSQL installation. 
But, I think for beginners, this [MySQL Installation]("http://www.w3resource.com/mysql/mysql-installation-on-linux-and-windows.php") and [PostgreSQL Installation]("http://w3resource.com/PostgreSQL/install-postgresql-on-linux-and-windows.php") docs are also very useful.

---

### Post by SeijiSensei on 2012-01-25
It would help if we knew a bit more about where your problems lay.  Is it with installation (probably not if you use apt-get), configuration (usually the defaults are fine), data entry, query design, or what exactly?

Why not give us a concrete example of something you're trying to do?  It might help focus our answers a bit better.

I use the psql command-line client for everything; once you know the syntax it's far faster and easier than using a web-based GUI.  Also it's much simpler to create and manage users in PostgreSQL than MySQL.  PG comes with command-line programs like "createuser" and "createdb" that avoid all those ridiculous contortions you have to go through in MySQL just to create a user and give her a database to use.

If you're having problems with database access, you need to look at the pg_hba.conf file.  The defaults are pretty restrictive; basically only connections to localhost are permitted.  In MySQL you have the 'user'@'hostname' types of restrictions.  In PostgreSQL all access controls are managed in the pg_hba.conf file.

Personally, the only GUI client I use with PostgreSQL is Microsoft Access with the Postgres ODBC connector.  For complex multi-table relational queries, Access can be very helpful.

---

### Post by memilanuk on 2012-01-25
Generally I don't have too much trouble getting PostgreSQL installed and setup; as mentioned the packages for it do most of the hard stuff.

I can get around okay in the mysql command line client; there are some things that I find easier to do by just typing in the SQL commands and some things (like user privileges) I find easier to do in phpMyAdmin.  Using that tool, I pretty much do both - use the GUI stuff when its easier and issue straight SQL commands when appropriate.

I think a lot of my frustration comes from trying to use pgadmin or phpPgAdmin... they seem like nice tools, but for some reason  they just don't seem intuitive for me.  Some of it may be syntactic differences... in mysql I create a database; apparently in postgreql I already am 'in' the database so I create a 'schema', which is functionally the same thing? Dunno.  After that... I guess its just so much 'stuff' is exposed in that tree under a given schema that I'm not entirely sure what to do with it all; what I need and what I should just leave alone for now.  I do get somewhat the same feeling of being overwhelmed when trying to navigate MySQL Workbench... its really nifty and all, but it just seems like so much 'fluff' wrapped around the bare essentials of what I really need.

Maybe I'll be able to spend some time with just the psql command-line client and come to grips with things that way...

---

### Post by SeijiSensei on 2012-01-25
Give this a shot:

```

$ sudo adduser thedonald
[answer some questions]
$ sudo su
# su postgres 
$ createuser thedonald
[answer some questions]
$ exit
# su thedonald
$ createdb donaldsdb
$ psql donaldsdb

```

You should be at the psql prompt with an empty database.  I've left out database passwords to simplify matters for instructional purposes.  I've also included the "$" and "#" prompt to distinguish between users and root.

Notice I had to use su a couple of times so I had the correct identity.  By default PG requires that the user connecting to the database have the same Unix identity as the database's owner.  That's something you can change in pg_hba.conf when you've got more experience.*  In this case I first became the "postgres" administrative user to create a PG user, then became that user to create his database.

__________

[size=1]*I routinely edit pg_hba.conf so that local connections use "trust" rather than "ident" which makes things simpler.[/size]

---

### Post by memilanuk on 2012-01-25
Alright, I'll give that a try when I get home tonight.  I have a TurnKey Linux PostgreSQL 8.4 server running in a VM on my laptop that I can connect to easily enough.

Thanks,

Monte

---

### Post by memilanuk on 2012-01-26
Okay, got that part working.  I can ssh into the machine and connect via psql to a database with the same name as the user.

I'm working on connecting to the database directly from another machine, either via psql, pgadmin, etc.  So far the 'postgres' user can connect with no problems, but the user 'monte' can't connect to the database 'monte' other than from local.

Onwards and upwards.

---

### Post by drdos2006 on 2012-01-26
For me to experiment with PostgreSQL I found having Webmin installed on the server was very useful to me. Could control users, host address connections, editing of configuration files etc. via Firefox browser rather than phppgadmin.

 I also found this site useful.
[http://ygamretuta.me/2011/01/30/setting-up-development-postgresql-and-phppgadmin-in-ubuntu-10-10-maverick/](http://ygamretuta.me/2011/01/30/setting-up-development-postgresql-and-phppgadmin-in-ubuntu-10-10-maverick/)

and here.
[http://www.techrepublic.com/blog/howdoi/how-do-i-use-php-with-postgresql/110](http://www.techrepublic.com/blog/howdoi/how-do-i-use-php-with-postgresql/110)
and here
[http://en.wikibooks.org/wiki/Converting_MySQL_to_PostgreSQL](http://en.wikibooks.org/wiki/Converting_MySQL_to_PostgreSQL)

regards

---

### Post by SeijiSensei on 2012-01-27
> **memilanuk said:**
> I'm working on connecting to the database directly from another machine, either via psql, pgadmin, etc.  So far the 'postgres' user can connect with no problems, but the user 'monte' can't connect to the database 'monte' other than from local.

You need to edit pg_hba.conf and authorize connections from the remote client machine.  Remote connections are disallowed by default.

---

### Post by memilanuk on 2012-01-27
I gathered as much.  Just haven't had the time to work out the syntax I want/need.  Hopefully I'll get to that later today.

---

### Post by memilanuk on 2012-01-29
As it turns out, the problem wasn't the pg_hba.conf file per se.  The postgresql server I'm using (a database appliance from TurnKey Linux) has the pg_hba.conf configured to allow access on the local network already.  The problem was (I think) that when the user was created in postgresql, it (the user) was never assigned a password by default.  Took me a couple go-arounds before  I could figure why I could run psql locally (on the server) as either postgres or the new user ('monte'), and could connect remotely using psql or pgadmin as postgres, but not as the new user.  I assigned a password to the new user using the webmin interface, and voila! all was good (for now) ;)

---

