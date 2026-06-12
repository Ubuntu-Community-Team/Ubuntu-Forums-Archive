---
title: "the mysterious postgres user"
date: 2011-01-11
forum: Server Platforms
---

### Post by psvr on 2011-01-11
Hello everybody. This is my first time posting my question on ubuntu forum. My problem is that after I have apt-get'ed postgresql and followed the following guide

[https://help.ubuntu.com/community/PostgreSQL](https://help.ubuntu.com/community/PostgreSQL)

to set my initial database system by disguising my self as user `postgres`, I don't know what kind of role is the user `postgres` playing. First of all , I don't know the unix password of the user `postgres`. It seems like that postgresql has its own password system and does not rely on the unix password of the user `postgres`. Nor can I reset the password of `postgres` because I don't know the current password:

sudo -u postgres passwd
Changing password for postgres.
(current) UNIX password: 
passwd: Authentication token manipulation error
passwd: password unchanged

It seems like that `postgres` user is created during apt-get process. So what kind of role is this `postgres` user playing? :confused:

Thank you very much for your reply!

---

### Post by SeijiSensei on 2011-01-13
The "postgres" user is the equivalent to root in the PostgreSQL authentication system. At the Unix system level, the postgres user owns all the Postgres files under /var/lib/postgresql.  Within PostgreSQL, the postgres user can perform SQL operations on any database regardless of ownership.

I use sudo and su to become the postgres user in order to create PostgreSQL users with the "createuser" command like this:

```

sudo su -c "createuser username" postgres

```

This runs the createuser command as the shell user postgres to create a PostgreSQL account for user "username".  In response to the questions the createuser script asks, I choose not to make ordinary users PostgreSQL superusers, I do allow them to create databases, but I don't allow them to create new roles.

Now if user "username" logs in, he or she can create a personal PostgreSQL database using the "createdb" command.  That database will be owned by the corresponding Postgres user with the same name.

(If you want to add passwords for new users, use "createuser -P" to generate a password prompt.  See "man createuser" for more details.)

---

