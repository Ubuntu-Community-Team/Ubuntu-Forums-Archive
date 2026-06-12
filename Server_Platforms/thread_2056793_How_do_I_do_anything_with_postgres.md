---
title: "How do I do anything with postgres?"
date: 2012-09-12
forum: Server Platforms
---

### Post by bobdobbs on 2012-09-12
I'm using ubuntu 12.01 and postgres 9.15.

I've installed postgres, but I can't access it for anything. Every

When I try to create a db, I get this:

```
createdb: could not connect to database postgres: FATAL:  role "root" does not exist
```

I googled for postgres "roles". I found syntax for creating roles. In order to create roles, I have to work from the psql prompt. However, when I invoke the psql prompt, I get the same message.

This doesn't make much sense to me, and it is frustrating.

Is there a way to access to prompt without a role? Is there a way to create a role without the prompt?

---

### Post by Bachstelze on 2012-09-12
You sound like you really need to read this [http://www.postgresql.org/docs/9.1/interactive/tutorial.html](http://www.postgresql.org/docs/9.1/interactive/tutorial.html)

---

### Post by SeijiSensei on 2012-09-12
The postgres "superuser" is called "postgres" in both Ubuntu and on RedHat-flavored distros like CentOS.  There is no "root" user like MySQL has.

Databases in Postgres are typically owned by Unix users.  So let's suppose user daisy wants to create a database.  There are two steps involved, first creating a Postgres user named daisy that corresponds to the Unix account.  Once that is done, daisy can create her database.

Step 1:  Become the postgres user and add daisy to the user list
```

sudo su
[Enter your password]
su postgres
createuser daisy
[reply to the questions; let daisy create databases but not other users]
exit
exit

```

Now log in as daisy and use "createdb name_of_db".  If you omit a name for the database, it will create one with the same name as the user's account.

One other important difference between PostgreSQL and MySQL is access control.  There are no 'user'@'hostname' accounts in PostgreSQL.  Access control is managed by the /var/lib/pgsql/data/pg_hba.conf file.  By default users can only access their own databases and only over the localhost (127.0.0.1) interface.  Read the pg_hba.conf file to learn about other options.

And, yes, I agree with Bachstelze that you need to read that tutorial.  If you approach PostgreSQL expecting everything to work just as it did with MySQL, you'll be quickly frustrated.

---

### Post by jchan172 on 2013-06-16
Thanks! This solved my problem. I'm on OSX, though, and kept getting "FATAL: role MYUSERNAME does not exist."

---

